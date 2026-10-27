---
tags: [arquitetura-era-ia, mba]
materia: "Arquitetura na Era da IA"
tema: "Métricas de Acoplamento"
status: revisado
---

# Métricas de Acoplamento

> [!summary] TL;DR
> - Arquitetura é entender o custo da mudança; acoplamento é um dos principais sinais desse custo.
> - Ce (setas saindo) mede de quantos o módulo depende; Ca (setas entrando) mede quantos dependem dele.
> - `I = Ce / (Ce + Ca)` e `A` = proporção de elementos abstratos; a main sequence é `A + I = 1`.
> - Zona de dor = estável e concreto demais (rigidez); zona de inutilidade = abstração demais sem uso (peso).
> - Nenhum número sozinho explica a arquitetura: as métricas servem para decidir onde refatorar primeiro.

## Conceitos-chave

- **Métricas de saúde arquitetural**: acoplamento aferente, eferente, instabilidade, nível de abstração, distância da main sequence e ciclos de dependência. Eram caras de manter manualmente; com IA viram análise recorrente (ver [[Análise de Acoplamento com Scripts e IA]]).
- **Dependência**: módulo importa, chama, instancia ou precisa conhecer outro.
- **Acoplamento eferente (Ce)**: quantas dependências saem do módulo ("de quantos eu dependo"). Ce alto = módulo frágil, conhece coisa demais, sensível a mudanças externas, tende a instável, possível classe Deus (não é questão de linhas de código).
- **Acoplamento aferente (Ca)**: quantos módulos dependem dele ("quantos dependem de mim"). Ca alto = módulo crítico, mudança gera impacto amplo (alterar função em utils e quebrar testes em áreas sem relação aparente).
- **Ca alto nem sempre é ruim**: tipos bem definidos, contratos estáveis e abstrações de domínio podem ser saudáveis. O problema é muitos dependerem de algo concreto, conceitualmente instável ou mal organizado (ex: vários módulos fazendo `new Logger` direto espalham dependência de implementação concreta).
- **Instabilidade (I)**: `I = Ce / (Ce + Ca)`. Perto de 0 = estável (muitos dependem dele, ele depende de pouco); perto de 1 = instável.
- **Instabilidade não é xingamento**: módulo instável em camada externa (infra, integração, formatação, orquestração) pode ser concreto. O problema é instabilidade com baixa coesão e responsabilidade demais.
- **Estabilidade não é sempre virtude**: ótima em abstração bem desenhada, perigosa em dependência concreta e global que ninguém consegue trocar.
- **Abstração (A)**: proporção de elementos abstratos (interfaces, classes abstratas e equivalentes) sobre o total do módulo; o cálculo varia por linguagem.
- **Main sequence (Robert C. Martin, Uncle Bob)**: linha `A + I = 1` de proporção saudável entre abstração e instabilidade. Módulo muito estável deve tender a abstrato, para evoluir, estender ou ser substituído sem quebrar o sistema. A distância dessa linha indica relação problemática.
- **Zona de dor**: estável e concreto demais (database global importado direto, logger com `new` em vários pontos, utilitário misturando moeda, geração de ID e cálculo de total). Difícil de mudar porque muitos dependem e difícil de estender porque nenhuma abstração protege.
- **Zona de inutilidade**: interfaces, contratos e arquivos que não protegem nenhuma dependência, com implementação concreta usada direto (overengineering). Interface usada por um só arquivo já fica perto dela.
- **Inversão de dependência**: protege módulo de alto nível de detalhes concretos (service depende de contrato, não de infraestrutura); não é estética. Componentes estáveis tendem a precisar de mais abstração (aplicada em [[Refatoração Guiada por Acoplamento com IA]]).
- **Abstração desperdiçada**: interface existe (ex: `PaymentGateway`) mas services continuam fazendo `new StripeGateway`; a interface não inverteu nada. Pergunta certa: quem depende da interface? O código depende do contrato ou da implementação?

| Região do gráfico | Leitura |
|---|---|
| Estável + abstrato | Saudável (contratos centrais, tipos bem definidos) |
| Instável + concreto | Aceitável conforme o papel (infra, integração) |
| Estável + concreto | Zona de dor: rigidez |
| Instável + abstrato sem uso | Zona de inutilidade: peso |

### Leitura combinada

- OrderService concreto e instável com Ce 15 = conhece demais, classe Deus; se um dos 15 mudar, pode quebrar.
- Logger estável mas concreto com 14 dependentes diretos = zona de dor clara.
- OrderService que começa coordenando pedido e passa a conhecer catálogo, estoque, pagamento, notificações, cliente, promoções, frete, auditoria e banco vira ponto que puxa o sistema.
- Componentes que dependem de pouco mas dos quais muitos dependem (tipos compartilhados, database global, logger, utils misturado) viram regiões sensíveis.

### Sintomas de dor arquitetural

- Rigidez e fragilidade.
- Abstração desperdiçada.
- Regra duplicada: regra de cupom que deveria estar no serviço de promoção copiada no OrderService evolui num lugar e não no outro e gera respostas diferentes por caminho (sinal de fronteira mal definida).
- Ciclos de dependência: A chama B, que chama C, que volta para A; camadas perdem direção e alterações ficam imprevisíveis.

## Erros comuns / Cuidados

- Criar interface para tudo não resolve: importa se a abstração protege o sistema e se a dependência foi realmente invertida. Criar interface quando o contrato for usado por várias partes do sistema.
- Arquitetura boa não é a que não muda, é a que permite mudar com menos medo, menos efeito colateral e mais controle de impacto, sem overengineering.
- O objetivo não é decorar fórmula, e sim decidir onde refatorar primeiro, que componente merece alerta e qual módulo acumula dependências.
- IA não substitui o julgamento arquitetural; torna a arquitetura observável e complementa a percepção do time com dados.

## Tags de busca

`#arquitetura-era-ia` `#acoplamento` `#main-sequence` `#zona-de-dor` `#instabilidade`
