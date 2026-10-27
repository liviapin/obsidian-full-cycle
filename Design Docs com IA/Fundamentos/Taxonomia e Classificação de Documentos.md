---
tags: [design-docs-ia, mba]
materia: "Design Docs com IA"
tema: "Taxonomia e Classificação de Documentos"
status: revisado
---

# Taxonomia e Classificação de Documentos

> [!summary] TL;DR
> - Documentação de software se organiza melhor quando cada categoria responde a uma pergunta diferente do projeto.
> - A fronteira principal está entre documentação de produto (o quê e por quê) e design docs (como, onde, como manter, como trabalhar).
> - Design docs não são um documento único, mas um guarda-chuva de artefatos técnicos com finalidades diferentes.
> - Nem todo artefato é igualmente relevante hoje: existem categorias relevantes, emergentes, secundárias e legadas.
> - Prompt engineering aplicado à documentação depende de indicar categoria, objetivo, escopo e profundidade do artefato pedido.

## Conceitos-chave
- **Mapeamento funcional**: produto responde o quê e por quê; design e arquitetura respondem como; infraestrutura responde onde e com o quê; operacional responde como manter; conhecimento e referência respondem como trabalhar.
- **Design Docs como guarda-chuva**: reúne documentos de design e arquitetura, infraestrutura, operação e conhecimento técnico de referência, todos orientando construção, provisão, manutenção e evolução do software.
- **[[PRD (Product Requirements Document)]]**: documento de produto, não é design doc, mas entra antes dos documentos técnicos como base de contextualização para pessoas e para IA.
- **Encadeamento entre documentos**: PRD descreve o problema e o valor esperado, [[HLD (High Level Design)]] organiza a solução em alto nível, [[FDD (Feature Design Doc)]] detalha uma feature específica, LLD aproxima a solução do código, RFC delibera alternativas, [[ADR (Architecture Decision Record)]] registra a decisão tomada.
- **RFC (Request for Comments)**: documento de deliberação técnica que circula uma proposta para comentários e alternativas antes da decisão final; não registra a decisão definitiva, organiza a discussão que a antecede.
- **LLD (Low Level Design)**: aproxima o design da implementação concreta (endpoints, contratos, campos de API); considerado secundário porque projetos mudam rápido e o documento fica obsoleto com facilidade.
- **Prompt Engineering aplicado à documentação**: pedir "gere um design doc" é vago; pedir um documento técnico de arquitetura, infraestrutura ou operação produz saídas mais úteis porque a categoria já delimita o conteúdo esperado.

## Classificação de documentos (relevância atual)
Documentação de Produto:
- Relevantes: PRD.
- Secundários: User Stories e Epics.
- Legados: FRD (Functional Requirements Document).

Design e Arquitetura:
- Relevantes: HLD, Feature Design Doc, ADR, Modelo C4.
- Emergentes: AI Design Docs e Prompt Specs (documentos novos para desenhar aplicações com IA).
- Secundários: RFCs, Low-Level Design.
- Legados: TRD (Technical Reference Document), LLD no formato RUP.

Documentos de Conhecimento e Referência:
- Relevantes: [[Software Development Guidelines]] e Security Design Doc.
- Emergentes: documentos de como trabalhar com Evaluation (IA/LLM testing).
- Legados: Test Plan e Test Case formal.

Documentos Operacionais e de Infraestrutura:
- Operacionais relevantes: Runbooks e Playbooks.
- Operacionais emergentes: documentos de Observabilidade (SLIs, SLOs, métricas).
- Infraestrutura secundários: Design Docs de infraestrutura e documentos de CI/CD (hoje muitas vezes integrados ao próprio código como IaC).

## Erros comuns / Cuidados
- Chamar qualquer documento de "design doc" apaga diferenças importantes de público, profundidade e uso.
- Usar um template genérico para toda necessidade produz documentos confusos, longos e pouco úteis.
- Nem todo problema de documentação é falta de disciplina; muitas vezes o time não sabe qual documento criar para cada necessidade.

## Materiais complementares
### Conteúdo extra
- Mindmap de classificação de documentos (MindMeister): https://mm.tt/map/3863580263?t=7cHe2Hud6K

## Tags de busca
`#taxonomia` `#classificacao-documentos` `#prd` `#design-docs`
