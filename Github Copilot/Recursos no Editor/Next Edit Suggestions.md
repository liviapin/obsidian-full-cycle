---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Next Edit Suggestions"
status: revisado
---

# Next Edit Suggestions

> [!summary] TL;DR
> - NES: uma edição no código desencadeia sugestões das próximas mudanças necessárias, em cascata.
> - Ex: renomear variável e o Copilot sugerir a troca em cada uso abaixo.
> - `Tab` navega até a próxima edição e aceita; também dá para clicar no indicador verde.
> - Funciona em código de qualquer linguagem e em Markdown.

## Conceitos-chave

- **`github.copilot.nextEditSuggestions.enabled`**: setting principal que liga o recurso.
- **Allow whitespace only changes**: permite sugerir mudanças só de indentação e espaços (formatação).
- **NES Fixes**: oferece sugestões para consertar problemas no código.
- **Range estendido**: permite sugerir edição longe do cursor (mudança no início do arquivo afetando o final).
- **Indicador verde**: aparece na linha sugerida com opções de aceitar, rejeitar e alternativas.
- **Contexto**: mesmo mecanismo não determinístico das [[Inline Suggestions e Ghost Text]].

## Fluxograma / Processo

```mermaid
flowchart TD
    A[Editar trecho do codigo] --> B[Copilot detecta edicoes dependentes]
    B --> C[Indicador verde na proxima linha]
    C --> D{Tab ou clique}
    D -->|Aceitar| E[Aplica e salta para a proxima]
    E --> B
    D -->|Rejeitar| F[Segue editando manualmente]
```

## Tags de busca

`#github-copilot` `#next-edit-suggestions` `#refatoracao` `#atalhos`
