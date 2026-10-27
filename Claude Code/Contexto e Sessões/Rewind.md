---
tags: [claude-code, mba]
materia: "Claude Code"
tema: "Rewind"
status: revisado
---

# Rewind

> [!summary] TL;DR
> - `/rewind` cria pontos de restauração da sessão, como um histórico navegável.
> - Restaura só o código, só a conversa ou os dois.
> - Uso típico: o modelo perdeu contexto e fez algo fora do planejado; volta ao ponto da falha e replaneja.

## Conceitos-chave

- **`/rewind`**: lista as alterações feitas na sessão e permite escolher para qual ponto voltar.
- **Escopo da restauração**: código, conversa ou ambos. Restaurando a conversa, o prompt volta para ser reeditado.
- **Quando usar**: implementação que saiu diferente do esperado, por falta de contexto ou decisão ruim.
- **Relação com fork**: para testar ideia alternativa sem desfazer o caminho atual, usar [[Fork de Sessão]] em vez de rewind.

## Fluxograma / Processo

```mermaid
flowchart TD
    A[Implementacao nao ficou como esperado] --> B[Rodar /rewind]
    B --> C[Escolher ponto da lista de alteracoes]
    C --> D{O que restaurar?}
    D -->|Codigo| E[Arquivos voltam ao estado do ponto]
    D -->|Conversa| F[Historico volta ao ponto]
    D -->|Ambos| G[Codigo e historico voltam]
    E --> H[Replanejar e pedir de novo]
    F --> H
    G --> H
```

## Erros comuns / Cuidados

- Mudança em variável de ambiente só reflete após reiniciar o servidor (`npm run dev`).

## Materiais complementares

### Prompts

**Gerar uma alteração para depois desfazer com rewind**
```text
Altere o valor na página, modificando o valor da env var para Full Cycle.
```

## Tags de busca

`#claude-code` `#rewind` `#checkpoint` `#sessao`
