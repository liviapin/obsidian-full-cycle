---
tags: [claude-code, mba]
materia: "Claude Code"
tema: "Modelos e Effort"
status: revisado
---

# Modelos e Effort

> [!summary] TL;DR
> - `/model` lista e troca modelos: Fable (beta, mais potente), Opus, Sonnet e Haiku.
> - Opus para planejamento e tarefas complexas; Sonnet para implementação diária; Haiku para tarefas rápidas.
> - O modelo escolhido vale para a sessão atual e as próximas até ser trocado; subagentes podem usar outro modelo.
> - `/effort` controla a profundidade de raciocínio: low, medium, high (padrão), xhigh, max, ultracode e auto.
> - Recomendação: manter o padrão high e trocar de modelo quando precisar acelerar.

## Conceitos-chave

- **`/model`**: mostra os modelos disponíveis e o atual. Lista muda conforme novas versões saem.
- **Fable**: modelo mais potente no momento da aula, em fase beta.
- **Opus**: recomendado para tarefas complexas, processos de [[Plan Mode]] e raciocínio estruturado. Padrão atual: Opus 4.8.
- **Sonnet**: meio termo; bom para implementar o que já foi planejado e mais rápido que o Opus.
- **Haiku**: mais abaixo nos benchmarks, rápido, para tarefas sem raciocínio complexo. Não tem ajuste de effort.
- **Subagentes**: o Claude Code escolhe o modelo da tarefa delegada. Exploração e listagem de diretório tendem a usar Haiku pela velocidade.
- **`/effort`**: define o quanto o modelo raciocina. Também ajustável no próprio `/model` com as setas direcionais.
- **low**: resposta rápida e direta. Boilerplates, scripts de CI/CD.
- **medium**: equilibrado, pequenas implementações do dia a dia.
- **high**: padrão do Sonnet, Fable e Opus. Raciocínio mais aprofundado para problemas complexos.
- **xhigh**: implementações bem complexas com pensamento estruturado.
- **max**: consumo de tokens muito alto. Só para decisões críticas de qualidade e segurança.
- **ultracode**: permite ao Claude decidir sozinho quando usar [[Dynamic Workflows]].

## Erros comuns / Cuidados

- Max consome muitos tokens; high já resolve decisões críticas na maioria dos casos.
- Combinação sugerida: Opus para decisão e estruturação, Sonnet para implementação.

## Tags de busca

`#claude-code` `#modelos` `#effort` `#subagentes`
