---
tags: [github-copilot, mba]
materia: "Github Copilot"
tema: "Sessions do Copilot"
status: revisado
---

# Sessions do Copilot

> [!summary] TL;DR
> - Sessão é o histórico completo de uma conversa; todas ficam guardadas e ordenadas por data.
> - Ficam só na máquina (pasta de configuração do VS Code), não na nuvem. Backup via Export Chat (JSON).
> - Status por sessão: em progresso, aguardando ação sua (ícone azul), erro.
> - Indicador de janela de contexto mostra tokens usados; ao chegar em 128 mil, o histórico é sumarizado.

## Conceitos-chave

- **Nova sessão**: nova conversa no painel; sessões anteriores podem ser retomadas de onde pararam.
- **Armazenamento local**: arquivo na pasta de configuração do VS Code de cada sistema operacional; copiável para outra máquina.
- **Export Chat**: salva JSON com mensagens, tools usadas e demais detalhes; pode virar Markdown.
- **Layout**: side-by-side (lista ao lado, obrigatório em tela cheia) ou stacked (abre uma sessão por vez).
- **Status**: em progresso, normal, aguardando autorização de comando, erro. Útil com várias sessões em paralelo.
- **Archive x Delete**: delete remove definitivamente; archive (atalho Delete) guarda e permite restaurar.
- **Outras ações**: abrir em aba, lado a lado, nova janela, marcar como lida (VS Code 1.109).
- **Sessão ligada a tarefa**: delegação ao [[Coding Agent do Copilot]] mantém a sessão marcada até a PR ser mesclada ou fechada.
- **Histórico de prompts**: seta para cima recupera mensagens anteriores.
- **Stateless**: LLMs recebem todo o histórico a cada interação, limitado pela janela de contexto.
- **Indicador de contexto**: percentual de system instructions, definição de tools, mensagens do usuário e outros.
- **Sumarização**: em 128 mil tokens o Copilot resume o histórico para liberar espaço, perdendo detalhes.

## Erros comuns / Cuidados

- Sessões não têm backup automático em nuvem.
- Uso sem discernimento do contexto leva a alucinação; acompanhar o indicador.
- Mudanças de arquivo por mensagem são controladas em [[Checkpoints do Copilot]].

## Tags de busca

`#github-copilot` `#sessions` `#contexto` `#historico`
