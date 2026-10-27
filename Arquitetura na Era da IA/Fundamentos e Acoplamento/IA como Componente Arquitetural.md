---
tags: [arquitetura-era-ia, mba]
materia: "Arquitetura na Era da IA"
tema: "IA como Componente Arquitetural"
status: revisado
---

# IA como Componente Arquitetural

> [!summary] TL;DR
> - Ordem correta: problema, contexto, restrições, decisões e só então ferramentas.
> - A pergunta não é "qual o LLM mais poderoso", e sim "onde a IA entra na solução e quais consequências essa decisão traz".
> - Na solução, a IA é uma decisão sobre papel e autonomia; no software, é um componente cercado de autenticação, autorização, banco etc.
> - IA generativa varia mesmo com entrada parecida: o objetivo é cercá-la de limites, validações, rastreabilidade e fallbacks, não torná-la 100% determinística.
> - Surgem novas camadas: orquestração, integração com modelos, ferramentas, avaliação e observabilidade específica.

## Conceitos-chave

- **Arquitetura como decisão**: decisão que faça sentido para negócio, time, operação, custo, segurança, evolução e manutenção, não só "funciona na minha máquina", demo ou PoC. Dev sênior, tech lead, CTO e até dev júnior tomam decisões arquiteturais (ver [[Tipos de Arquitetura]]).
- **Novo papel do dev**: passa de escritor de código a quem direciona a construção (dá contexto, especificação, revisa).
- **Capacidade de interpretação**: antes o sistema era fluxo, regra, tela, banco, integração e processo (clica, preenche, valida, grava, chama API); com IA generativa o usuário expressa intenção (pede análise, recomendação).
- **IA na arquitetura de solução**: decidir o papel no processo. Ajuda a pessoa ou fala com o cliente? Sugere ou decide? Consulta dados internos? Aciona ferramentas? Mexe em sistemas? Fluxo crítico ou de baixo risco?
- **Níveis de autonomia**: assistente, copiloto, parte do fluxo principal, executa ação, precisa de aprovação.
- **Limites a definir**: autonomia, dados, ação, custo e responsabilidade.
- **IA na arquitetura de software**: um componente poderoso cercado pelos demais (autenticação, autorização, banco).
- **Variabilidade**: sistemas convencionais têm contratos explícitos e falhas conhecidas (timeout, bug, rede); a saída da IA depende de modelo, prompt, contexto e dados recuperados, e pode variar com entrada parecida (ver [[Alucinação em LLMs]]).
- **Novas camadas**: orquestração, integração com modelos ([[AI Gateway]]), ferramentas ([[Operação de Agentes e Tool Calling]]), avaliação ([[Arquitetura de Evaluation e Experiments]]) e observabilidade específica ([[Observabilidade com OpenTelemetry]]).
- **Riscos novos**: interpretação, geração e acionamento de ferramentas trazem superfícies de risco que não existiam (ver [[Threat Model e OWASP para IA]]).

### Perguntas antes de escolher modelo ou framework

- O problema precisa de IA? Ela traz valor ou só deixa mais caro e complexo?
- Uma regra tradicional (ex: regex) resolveria melhor?
- A IA só sugere ou executa ação?
- Quais dados pode e não pode acessar?
- Qual o risco se responder errado? Quem valida a resposta?
- Qual o custo por usuário, chamada, tarefa e mês?
- Como saber se a resposta está boa? Como auditar?

### Novas perguntas arquiteturais

- Como montar o contexto enviado ao modelo e de onde vêm os dados ([[Fundamentos de RAG]], [[Retrieval e Montagem de Contexto]])?
- Como garantir que o usuário só receba o que tem permissão de ver?
- Como registrar prompt, contexto, resposta e ações?
- Como evitar acoplamento a um único provider ([[LiteLLM SDK e Proxy]])?
- Como lidar com latência alta ([[Fluxos de Chamada Síncrono, Streaming e Assíncrono]])?
- Como controlar custo por chamada ([[Custos, Budgets e Governança de IA]])?
- Como testar comportamento variável ([[Testes Determinísticos e de Contrato]])?
- Como criar fallback quando o modelo falha ([[Resiliência e Fallback de LLMs]])?

## Erros comuns / Cuidados

- Começar pela tecnologia da moda e encaixar o problema nela. Com IA ficou mais fácil começar pelo lugar errado ("GPT, Claude, Gemini ou local? LangChain, LangGraph, CrewAI, Google SDK, banco vetorial?").
- IA ajuda a implementar, sugerir, gerar código, revisar, documentar e testar, mas não tem responsabilidade pelo negócio nem conhece restrições políticas, comerciais e regulatórias.
- Armadilha da sensação de que software ficou fácil: o mercado não paga caro por quem gera o básico, e sim por software que se sustenta em produção (integrado, seguro, escalável, observável, com custo controlado, evolutivo, IA usada com critério).
- Risco depende do papel: IA resumindo histórico para o atendente tem risco menor; respondendo direto ao cliente, maior.
- Validar se a resposta se baseia em fontes confiáveis e se a ação de ferramenta é permitida e respeita a permissão do usuário.
- Protótipos funcionam, mas em produção ficam frágeis (custo alto, resultado ruim, segurança fraca).
- Usar IA para desenvolver dá produtividade; software integrado com IA é um desafio diferente e maior.

## Tags de busca

`#arquitetura-era-ia` `#decisao-arquitetural` `#autonomia-da-ia` `#ia-como-componente`
