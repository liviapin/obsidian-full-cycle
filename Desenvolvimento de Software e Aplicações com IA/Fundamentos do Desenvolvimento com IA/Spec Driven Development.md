---
tags: [dev-software-ia, mba]
materia: "Desenvolvimento de Software e Aplicações com IA"
tema: "Spec Driven Development"
status: revisado
---

# Spec Driven Development

> [!summary] TL;DR
> - SDD: o trabalho da IA é guiado por especificações estruturadas, não por pedidos soltos.
> - A spec converte intenção em instrução operacional (escopo, objetivo, direção) e é o principal mecanismo de direção.
> - Depende de maturidade de processo e de revisão de artefatos: especificar mal escala o erro.
> - O nome pode mudar; o princípio permanece: problema formalizado em specs, IA executa a partir delas.

## Conceitos-chave

- **Spec Driven Development (SDD)**: síntese de workflow, documentação, arquitetura e produto; a IA executa a partir de specs que formalizam o problema (contexto em [[Papel do Dev e Workflows com IA]]).
- **Spec como instrução operacional**: traduz intenção em escopo, objetivo e direção para o agente.
- **Maturidade de processo**: SDD só funciona com revisão dos artefatos; spec ruim gera implementação coerente com o texto e incoerente com o produto.
- **Ponte para os pilares**: o ciclo é definir, revisar, validar e evoluir artefatos (ver [[Pilares e Ferramentas de Desenvolvimento com IA]]).
- **Ambiente spec-driven**: Amazon Kiro usa a spec como interface principal; primeiro a spec orienta, depois implementa.
- **Contradições entre documentos**: em SDD a IA gera múltiplos documentos e ela mesma cria contradições; a skill de validação construída em [[Criando Skills]] lê os arquivos em trabalho e aponta contradição direta, ambiguidade e lacuna lógica entre código, docs e specs.
- **Aplicação no projeto**: o princípio aparece no plano por fases e nos test specs do [[Workflow RPI Research Plan Implement]].

## Erros comuns / Cuidados

- Adotar o termo ou um template sem processo.
- Decorar a buzzword em vez do raciocínio estrutural.

## Tags de busca

`#dev-software-ia` `#spec-driven-development` `#sdd` `#especificacao`
