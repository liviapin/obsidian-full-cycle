---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Smart Actions"
status: revisado
---

# Smart Actions

> [!summary] TL;DR
> - Ações inteligentes espalhadas pelo VS Code que rodam sem escrever prompt nem abrir o Chat View.
> - Lâmpada com estrelinhas indica Smart Action disponível.
> - Cobrem rename, getters/setters, revisão, documentação, testes, fix, mensagem de commit e resolução de conflitos.
> - Mensagem de commit pode ser guiada por instruções no settings.

## Conceitos-chave

- **Rename (F2)**: sugestões de nome geradas com IA usando o contexto do arquivo, documentação e arquivos abertos.
- **Lâmpada com estrelas**: ao selecionar código, oferece gerar getter/setter, modificar ou revisar o trecho.
- **Review**: abre comentários do Copilot sobre o trecho (ex: thread safety), iguais aos de revisão de PR.
- **Clique direito > Generate Code**: gerar documentação (usa `/doc`), testes, fix e review. Equivale a selecionar, `Ctrl+I` e usar o slash command. Ver [[Slash Commands do Copilot]].
- **Fix de erro**: estrelinhas ao lado do erro explicam o problema no Chat View e aplicam `/fix`.
- **Mensagem de commit**: estrelinhas no campo de commit geram a mensagem a partir dos arquivos staged; clicar de novo regenera.
- **`github.copilot.chat.commitMessageGeneration.instructions`**: array de instruções de formato. No `.vscode/settings.json` vale só para o projeto; no settings global, para todos.
- **Resolução de conflitos**: no Merge Editor, abre o Chat View focado em resolver o merge.

## Erros comuns / Cuidados

- Mensagem de commit gerada sem instrução pode descrever mal a mudança; guiar com Conventional Commits e verbos imperativos.

## Materiais complementares

### Conteúdo extra

- Configuração de mensagem de commit mostrada na aula (texto das instruções reconstituído da narração):
```json
{
  "github.copilot.chat.commitMessageGeneration.instructions": [
    { "text": "Use o formato Conventional Commits (feat, fix, chore, etc)." },
    { "text": "Use verbos no imperativo." }
  ]
}
```
- Documentação de Smart Actions na página do VS Code (referência citada pelo instrutor).

## Tags de busca

`#github-copilot` `#smart-actions` `#commit-message` `#code-review`
