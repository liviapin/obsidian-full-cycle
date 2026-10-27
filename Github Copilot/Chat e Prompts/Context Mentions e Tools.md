---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Context Mentions e Tools"
status: revisado
---

# Context Mentions e Tools

> [!summary] TL;DR
> - Símbolo `#`: adiciona contexto (arquivos, pastas, símbolos, saída de terminal) ou invoca tools (`#fetch`, `#codebase`).
> - Contexto e tools são coisas diferentes: contexto delimita, tool executa.
> - Sem limite de `#` por mensagem; arrastar arquivo ou pasta para o chat também adiciona contexto.
> - `#codebase` é a tool equivalente ao `@workspace`; sempre acrescentar quando não usar o participante.
> - Os três símbolos (`@`, `/`, `#`) combinados são o primeiro segredo para usar bem o Copilot.

## Conceitos-chave

- **Context mentions**: arquivos, pastas, símbolos, saída de terminal (`#terminalSelection`), issues e PRs do GitHub, instruções e screenshots.
- **Add Context**: menu que mostra os últimos arquivos abertos no topo; abaixo, as tools.
- **Tools**: executam ações (buscar URL, criar diretório, criar arquivo e outras).
- **`#fetch`**: busca conteúdo de uma URL para usar como referência (ex: documentação de uma lib).
- **`#codebase`**: força o Copilot a olhar o código do projeto para seguir os padrões. Depende de code search habilitado ([[Configurações do GitHub Copilot]]).
- **Combinação**: um [[Participantes do Chat]] + um [[Slash Commands do Copilot]] + quantos `#` forem necessários.

## Erros comuns / Cuidados

- Escrever "analise o projeto" no texto não tem o mesmo efeito de `#codebase`.
- Contexto vago gera resposta genérica; delimitar arquivos e pastas.

## Materiais complementares

### Prompts

**Explicação com contexto de arquivo**
```text
@workspace /explain como funciona o #<arquivo>
```

**Implementação com documentação externa (reconstituído da narração da aula)**
```text
Quero persistir os pagamentos deste serviço usando o TypeORM. Se baseie na doc dele: #fetch <url da documentação>
```

**Implementação seguindo padrões do projeto (reconstituído da narração da aula)**
```text
Quero mudar a persistência dos pagamentos de memória para banco de dados Postgres. #codebase se baseie nos padrões do projeto.
```

## Tags de busca

`#github-copilot` `#contexto` `#tools` `#codebase`
