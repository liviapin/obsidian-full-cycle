---
tags: [dev-software-ia, mba]
materia: "Desenvolvimento de Software e Aplicações com IA"
tema: "MCPs do Projeto Context7 e Postgres"
status: revisado
---

# MCPs do Projeto Context7 e Postgres

> [!summary] TL;DR
> - MCP (Model Context Protocol, Anthropic, padrão aberto) estende o que o modelo acessa sem a LLM inferir chamadas nem receber credenciais.
> - Context7 (Upstash) entrega documentação da versão exata da lib, resolvendo a defasagem entre o que o modelo treinou e a stack real; uso obrigatório definido no CLAUDE.md global.
> - MCP Postgres (read-only) converte linguagem natural em SQL para inspecionar o banco e o que os testes fazem; só funciona com o ambiente de pé.
> - Context7 no escopo do usuário (`~/.claude.json`, evita gerenciar API key por projeto); Postgres no escopo do projeto (`.mcp.json` na raiz, específico do banco).
> - Escolher bem quais servidores ativar: tools em excesso inflam a janela de contexto.

## Conceitos-chave

- **MCP**: padrão aberto (modelcontextprotocol.io) para acessar bancos e APIs (GitHub, Sentry, Microsoft, Google, Slack, Google Maps). Sem ele a LLM inferiria chamadas, gastaria tokens a cada sessão e precisaria receber credenciais (a senha do banco entraria no modelo). Visão geral da ferramenta em [[MCP no Claude Code]].
- **Arquitetura**: MCP Server (intermediário que expõe capacidades) e MCP Client (Claude Desktop, Claude Code, Cursor, VS Code); transportes HTTP, Server-Sent Events e STDIO.
- **Três artefatos**: Tools (operações com entrada/saída, invocadas quando a LLM infere que precisa agir), Resources (dados só leitura), Prompts (templates reutilizáveis, ex: prompt do servidor GitHub para descrever pull request).
- **Discovery e fluxo**: o client descobre tools/resources/prompts e passa os metadados à LLM; prompt + tools vão à LLM, ela decide chamar uma tool com argumentos, o client invoca o server, o server chama a API e o resultado volta à LLM.
- **Inflação de contexto**: historicamente 200 tools de 50 servidores entravam todas no contexto; hoje ferramentas passam só as tools correlacionadas. O Claude Code carrega tools sob demanda; em outras ferramentas, habilitar tools ou criar grupos ([[Context Window em LLMs]]).
- **Lugar na fundação**: 4a categoria, "sistemas externos", ao lado de CLAUDE.md, rules e skills ([[Arquivos de Inicialização do Agente]]). MCPs úteis para dev citados: Chrome DevTools (inspecionar elementos, debug) e Playwright ([[Testes E2E com Playwright CLI]]); o Figma entra depois ([[Figma MCP]]).
- **Context7**: "GitHub das documentações", aberto a contribuições, já em texto, segmentado por biblioteca, tema e versão (ex: Next.js 12, 13, 14). Cobre Nest, TypeORM, Next.js, Jest, Spring, Laravel etc. Mais eficiente que a IA buscar HTML da documentação (remover tags e JS gasta tempo e tokens). Expõe duas tools só leitura: resolver a biblioteca (`resolve-library-id`) e consultar a documentação (`query-docs`).
- **Plano e chave**: gratuito atende a maioria; uso anônimo é mais limitado, gerar API token.
- **Escopos de instalação**: usuário (todos os projetos, `~/.claude.json`) ou projeto (`.mcp.json` na raiz); também instalável pela lista de MCPs do VS Code.
- **`/mcp`**: lista servidores do projeto e do usuário, mostra as tools, permite reconectar ou desabilitar.
- **`/context`**: mostra o uso da janela (system prompt, custom agents, memória, MCPs); conectores desnecessários como Gmail e Google Calendar podem ser desabilitados; uma tool aparece como carregada quando foi usada recentemente.
- **Invocação por intenção**: sem dizer "MCP", a IA chamou `resolve-library-id` e `query-docs` pedindo só trechos (autenticação JWT, Passport, Guards, configuração do módulo JWT do Nest); pede permissão a cada tool se não houver auto-aprovação.
- **Consulta obrigatória**: a seção "Library Documentation Lookup" do CLAUDE.md global exige Context7 antes de implementar qualquer feature, conferindo a versão instalada; usado no planejamento ([[Planejamento de Fases com plan-phase]]) e na implementação.
- **MCP Postgres**: do repositório oficial `modelcontextprotocol/servers`, hoje na seção de servidores arquivados por brechas de segurança: ok para desenvolvimento, não para produção. Read-only (mais seguro e simples); existem outros que permitem escrita. Expõe uma única tool `query`; a IA pede autorização antes de rodar o SQL.
- **Docker vs npx**: o servidor Postgres pode rodar como container (Docker Hub), mas containers em redes distintas exigiriam `host.docker.internal`; optou-se por `npx`.
- **Dependência do ambiente**: com o container do banco parado o MCP falha; "inicie o ambiente" fez o Claude Code seguir o sub CLAUDE.md (`docker compose up`, `docker ps`, checagem do banco), ver [[Ambiente e Scripts de Inicialização]].
- **Separação de responsabilidades**: Context7 para documentação ao planejar e implementar; Postgres para inspeção esporádica dos dados; outros MCPs entram depois para debug.

## Fluxograma / Processo

```mermaid
flowchart TD
    A[Usuario envia prompt com intencao] --> B[Client passa metadados das tools a LLM]
    B --> C{LLM precisa de dado externo?}
    C -->|nao| D[Responde direto]
    C -->|sim| E[LLM escolhe tool e argumentos]
    E --> F[Client pede permissao e invoca o server]
    F --> G[Server chama API ou banco]
    G --> H[Resultado volta para a LLM]
    H --> D
```

## Erros comuns / Cuidados

- API key no comando fica gravada no histórico do shell (Fish, Bash, Zsh): usar prefixo que não grava histórico, fechar e reabrir o terminal, ou apagar a entrada do arquivo de histórico.
- Connection string sem credenciais: o 1o erro do MCP Postgres foi resolvido com `streamtube:streamtube@localhost`.
- MCP Postgres arquivado por segurança: não usar em produção.
- Ativar servidores demais polui a janela de contexto.

## Materiais complementares

### Prompts

**Uso do Context7 por intenção (narrado na aula)**
```text
Quero implementar a autenticação do projeto, use o Context7.
```

**Testes do MCP Postgres (narrado na aula)**
```text
Inicie o ambiente.
```
```text
Quero listar os bancos de dados disponíveis.
```

**Seção "Library Documentation Lookup" do CLAUDE.md global (arquivo literal do repositório mba-ia-greenfield-project)**
```markdown
## Library Documentation Lookup

Before implementing any feature, you MUST use the **context7** MCP tool to look up the relevant library APIs and official documentation.

Always:

- Check the installed library version in the project manifest
- Retrieve the corresponding documentation using context7
- Cross-reference APIs to avoid deprecated or incompatible patterns
- Follow the official documentation over training data

Skip documentation lookup only for trivial operations such as:

- Variable declarations
- Basic control flow
- Simple CRUD using established project patterns

If a library is involved and there is uncertainty, documentation lookup is mandatory.
If the documentation returned does not match the installed version, flag the discrepancy before proceeding.
```

**Instalação do Context7 no escopo do usuário (comando da página de instalação do Context7 para Claude Code, conforme a aula)**
```bash
claude mcp add --scope user context7 -- npx -y @upstash/context7-mcp --api-key <SUA_API_KEY>
```

**Configuração de MCPs do projeto `.mcp.json.example` (arquivo literal do repositório; a entrada `figma` foi adicionada depois, no bloco de design system)**
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://streamtube:streamtube@localhost/streamtube"
      ]
    },
    "figma": {
      "type": "http",
      "url": "http://127.0.0.1:3845/mcp"
    }
  }
}
```

### Conteúdo extra

- https://modelcontextprotocol.io
- https://context7.com
- https://github.com/modelcontextprotocol/servers (servidor postgres em servers-archived)
- Na aula foi mostrado um servidor MCP de exemplo em Python expondo uma tool, um resource e um prompt.

## Tags de busca

`#dev-software-ia` `#mcp` `#context7` `#mcp-postgres` `#documentacao-versionada`
