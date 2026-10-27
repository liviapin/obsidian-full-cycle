---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Configurações do GitHub Copilot"
status: revisado
---

# Configurações do GitHub Copilot

> [!summary] TL;DR
> - Buscar "copilot" e "chat" nos settings do VS Code; as opções relevantes ficam em Chat, GitHub Copilot e Features > Chat.
> - Muitas opções são experimentais e mudam quase diariamente; testar, manter se ajudar, desabilitar se não.
> - Configuração base: arquivos com inline suggestion, code search, dicas do chat, detecção de participante e edição de requests.
> - Settings podem ser editados pela UI ou em JSON, no global ou no `.vscode/settings.json` do projeto.

## Conceitos-chave

- **Seções relevantes**: Chat (desabilitar IA, unificar extensões, Skills), GitHub Copilot (maior parte das opções), Features > Chat (dezenas de opções), GitHub Pull Requests.
- **Tag experimental**: opções em desenvolvimento contínuo; podem gerar comportamento inesperado ou funcionar bem.
- **Abrir arquivos editados**: opção de acessibilidade que abre os arquivos que o agente edita, para acompanhar e aprovar.
- **`github.copilot.enable`**: mapa de linguagens em que o inline suggestion é permitido (`true`/`false`). Ver [[Inline Suggestions e Ghost Text]].
- **Code Search Enabled**: permite ao modo agente buscar no código conforme o prompt quando se usa codebase. Ver [[Context Mentions e Tools]].
- **Chat Tips Enabled**: mostra dicas de uso eventualmente.
- **Detect Participant Enabled**: mostra no histórico qual participante do chat foi usado. Ver [[Participantes do Chat]].
- **Edit Requests**: permite editar e reenviar uma mensagem já enviada; modo "hover" mostra o botão ao passar o mouse. Ver [[Checkpoints do Copilot]].
- **Projeto x global**: settings no `.vscode/settings.json` valem só para aquele projeto.

## Erros comuns / Cuidados

- Revisar periodicamente novas opções e a documentação; mudanças simples (ex: fonte) alteram a experiência.

## Materiais complementares

### Conteúdo extra

- Configuração base citada na aula (valores do instrutor):
```json
{
  "github.copilot.enable": {
    "*": true,
    "markdown": false,
    "plaintext": false
  },
  "github.copilot.chat.codesearch.enabled": true,
  "chat.tips.enabled": true,
  "chat.detectParticipant.enabled": true,
  "chat.editRequests": "hover"
}
```
- O instrutor promete disponibilizar as configurações completas dele ao final do curso.

## Tags de busca

`#github-copilot` `#settings` `#vscode` `#configuracao`
