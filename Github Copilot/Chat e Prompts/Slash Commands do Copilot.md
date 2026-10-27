---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Slash Commands do Copilot"
status: revisado
---

# Slash Commands do Copilot

> [!summary] TL;DR
> - Símbolo `/`: comandos prontos que executam tarefas reaproveitáveis sem escrever prompt longo.
> - Principais: `/doc`, `/explain`, `/fix`, `/tests`, `/new`, `/clear`.
> - Podem estar ligados a um participante (vários são do `@workspace`); nesse caso não precisa digitar o participante.
> - Só um slash command por mensagem.

## Conceitos-chave

- **`/doc`**: gera comentários e documentação.
- **`/explain`**: explica classe, bloco selecionado ou projeto, com detalhamento maior que um prompt comum.
- **`/fix`**: corrige bloco de código ou erro a partir do contexto. Exige arquivo aberto ou bloco selecionado.
- **`/tests`**: gera testes unitários do contexto delimitado; há também setup de testes.
- **`/new`**: gera projeto novo (ex: Spring Boot) arquivo por arquivo.
- **`/clear`**: limpa a sessão.
- **Ligação com participante**: `/explain`, `/fix`, `/new` pertencem ao `@workspace`. Ver [[Participantes do Chat]].
- **Combinação**: `@terminal /explain` explica a saída do terminal de forma mais completa e rápida.
- **Smart Actions** usam slash commands por baixo. Ver [[Smart Actions]].

## Erros comuns / Cuidados

- Slash command tem restrições próprias: `/fix` só com arquivo aberto ou seleção.
- Para implementar funcionalidade nova, `/fix` não é a escolha ideal; descrever a tarefa com contexto via [[Context Mentions e Tools]].

## Materiais complementares

### Prompts

**Explicar o projeto**
```text
/explain me explique como funciona o projeto
```

**Explicar comandos do terminal**
```text
@terminal /explain me explique os comandos que estão no terminal
```

**Gerar projeto novo**
```text
/new eu quero criar um projeto Spring Boot
```

## Tags de busca

`#github-copilot` `#slash-commands` `#explain` `#testes`
