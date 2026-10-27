---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Inline Suggestions e Ghost Text"
status: revisado
---

# Inline Suggestions e Ghost Text

> [!summary] TL;DR
> - Sugestões de código aparecem no editor enquanto se digita, como texto fantasma (ghost text).
> - `Tab` aceita tudo, `Esc` rejeita, `Ctrl+→` aceita palavra por palavra.
> - `Alt+[` e `Alt+]` navegam entre sugestões alternativas.
> - Comentário em linguagem natural ("gere", "faça", "construa") vira código sem abrir o chat.
> - Sugestões não são determinísticas: dependem de comentários, arquivos abertos, nomes e projeto.

## Conceitos-chave

- **Pré-requisito**: `editor.inlineSuggest.enabled` ligado. Recomendado ligar também o syntax highlight da sugestão para não ficar cinza.
- **Arquivos habilitados**: engrenagem em Inline Suggestions no ícone do Copilot. Ex: todos habilitados, plaintext negado. Ver [[Configurações do GitHub Copilot]].
- **Ghost text**: trecho pálido sugerido. `Esc` some, voltar a digitar faz reaparecer, `Tab` aceita e pode puxar nova sugestão.
- **Alternativas**: passar o mouse mostra quantas existem e força o carregamento. Pode haver delay de 1 a 2 segundos.
- **Aceite parcial**: `Ctrl+→` aceita palavra a palavra (inclusive espaços, parênteses e chaves).
- **Snooze**: no ícone do Copilot, pausa sugestões por 5 minutos, acumulando a cada clique.
- **Geração via comentário**: comentário imperativo gera a implementação. Detalhar no comentário muda o resultado (ex: pedir versão recursiva).
- **Contexto da sugestão**: comentários, arquivos abertos (10 abertos influenciam), variáveis, nomes de função e o projeto.
- **Edições encadeadas**: ver [[Next Edit Suggestions]].

## Erros comuns / Cuidados

- Pedido vago no comentário gera solução genérica; ser expressivo.
- Código claro e comentado no topo do arquivo aumenta a assertividade.

## Materiais complementares

### Prompts

**Gerar função via comentário**
```text
// gere uma função que retorna a sequência de Fibonacci
```

**Refinar via comentário**
```text
// função recursiva de sequência Fibonacci
```

## Tags de busca

`#github-copilot` `#inline-suggestions` `#ghost-text` `#atalhos`
