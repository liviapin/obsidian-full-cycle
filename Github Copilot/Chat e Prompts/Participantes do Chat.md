---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Participantes do Chat"
status: revisado
---

# Participantes do Chat

> [!summary] TL;DR
> - Símbolo `@` (chat participant ou @mentions): invoca um especialista em uma área.
> - Resposta mais assertiva e rápida que um pedido comum.
> - Só um participante por mensagem; não dá para combinar.
> - Principais: `@vscode`, `@github`, `@github.pr` (via extensão Pull Requests), `@workspace`, `@terminal`.
> - `@workspace` é subestimado e deveria ser o mais usado.

## Conceitos-chave

- **Participante**: agente especialista que aparece em destaque no chat e responde dentro do seu domínio. Extensões podem adicionar novos.
- **Descobrir capacidades**: perguntar "quais as suas skills?" ao participante.
- **`@vscode`**: dúvidas sobre o VS Code, settings, comandos e atalhos. Ex: aponta `window.border` e abre o setting direto.
- **`@github`**: vem com o Copilot. Pesquisa no GitHub e responde sobre repositórios usando a conta associada, com busca semântica no código. Lida com issues, URLs e categorização.
- **`@github.pr`**: da extensão GitHub Pull Requests. Gerencia PRs: abrir, revisar, ver conflitos e as delegadas a você. Pode delegar implementação ao [[Coding Agent do Copilot]].
- **`@workspace`**: especialista no projeto aberto; adiciona contexto do projeto e devolve referências clicáveis a arquivos, classes e símbolos.
- **`@terminal`**: especialista no terminal; combinado com `/explain`, explica a saída.
- **Repositório no prompt**: informar `dono/repo` evita perguntas extras e interações perdidas.
- **Combinação**: participante + [[Slash Commands do Copilot]] + [[Context Mentions e Tools]].

## Erros comuns / Cuidados

- Pedido sem participante faz o agente descobrir repositório, tools e MCPs sozinho: mais lento e elaborado que o necessário.
- `@github.pr` sem dizer "não use o Coding Agent" pode iniciar implementação na nuvem que você não esperava.

## Materiais complementares

### Prompts

**Dúvida de configuração do VS Code**
```text
@vscode como mudar a cor de borda do VS Code?
```

**Listar capacidades do participante**
```text
@vscode quais as suas skills?
```

**Pesquisa de biblioteca no GitHub**
```text
@github como instalar a lib axios/axios
```

**Explicar o projeto com contexto**
```text
@workspace me explique como este projeto funciona
```

**Abrir PR sem Coding Agent (reconstituído da narração da aula)**
```text
@github.pr abra uma pull request do branch dev para o branch main no repositório <dono/repo>, com o título <título> e a descrição <descrição>. Não use o Coding Agent.
```

## Tags de busca

`#github-copilot` `#chat-participants` `#workspace` `#pull-request`
