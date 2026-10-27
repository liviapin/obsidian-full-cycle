---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Coding Agent do Copilot"
status: revisado
---

# Coding Agent do Copilot

> [!summary] TL;DR
> - Agente que implementa a tarefa inteira na nuvem do GitHub, abrindo PR em draft e criando lista de tarefas.
> - Disparado pelo `@github.pr` ou por issue atribuída ao Copilot no GitHub.
> - Seu papel vira só revisar e mesclar quando ele terminar.
> - Também pode ser revisor de PR.

## Conceitos-chave

- **Delegação via chat**: pedir ao `@github.pr` uma PR sem dizer "não use o Coding Agent" faz ele iniciar a implementação na nuvem. Ver [[Participantes do Chat]].
- **PR em draft**: aberta enquanto o agente verifica informações e monta a lista de tarefas.
- **Planejamento**: é possível passar um Markdown com todo o plano para guiar o agente.
- **No GitHub**: atribuir uma issue ao Copilot ou delegar a revisão de uma PR. Ver [[Instalação e Planos do GitHub Copilot]].
- **Sessão vinculada**: a sessão fica marcada até a PR ser mesclada ou fechada, com ação de fechar PR. Ver [[Sessions do Copilot]].
- **Fluxo sugerido**: agente implementa, merge para `dev`, depois decisão de levar para `main`.

## Erros comuns / Cuidados

- Abrir PR pelo `@github.pr` sem instrução clara pode disparar implementação inesperada.

## Tags de busca

`#github-copilot` `#coding-agent` `#pull-request` `#delegacao`
