---
tags: [dev-software-ia, mba]
materia: "Desenvolvimento de Software e Aplicações com IA"
tema: "Bootstrap de Projetos Greenfield"
status: revisado
---

# Bootstrap de Projetos Greenfield

> [!summary] TL;DR
> - Greenfield: projeto do zero; a questão no dia zero é quanto delegar e quanto controlar, sem extremos ("8 ou 80").
> - Com IA surge uma segunda fundação ao lado da do framework: o projeto precisa nascer operável por agentes (CLAUDE.md, skills, testes, scripts, logs, navegação no browser).
> - Recomendação do autor: skill de bootstrap como wrapper/wizard sobre o scaffold nativo ou o boilerplate da empresa, usando scripts e templates em vez de a IA gerar arquivos.
> - `nextjs-bootstrap`: SKILL.md de ~50 linhas, `scripts/bootstrap.sh` e pasta `templates` com placeholders.
> - No StreamTube, a IA "crua" acumulou débito técnico em 3 minutos; a fundação de IA vem antes das features.

## Conceitos-chave

- **Greenfield**: projeto sem código, restrições herdadas ou convenções; diferença brutal frente a legado. Permite definir stack, organização e fundação de IA de forma intencional.
- **Delegar vs controlar**: extremos improdutivos são microgerenciar (pedir pasta por pasta) ou não usar IA no início. Equilíbrio: controle em decisões de arquitetura, convenções e direção; automação no repetitivo, estrutural e verificável. Critério por tarefa: comparar custo de geração, custo de revisão e valor da automação.
- **Custo oculto da IA sem estratégia**: tempo, tokens, dinheiro e esforço cognitivo de revisão (se revisar custa mais que fazer, perdeu a vantagem).
- **Bootstrap**: etapa inicial que cria a primeira estrutura operacional (diretórios, convenções, base de código) e define a fluidez do restante.
- **3 abordagens para iniciar**: 1) scaffolding nativo do framework (Spring Boot, Next.js, Laravel, Django) com um comando; 2) pedir à IA a estrutura do zero (cuidado); 3) skill customizada seguindo o padrão da empresa (foco do capítulo).
- **FOMO**: sentir que precisa usar IA o tempo todo; se gerar do zero com IA demora mais, não vale.
- **Abordagem vanilla**: começar o mais próximo do nativo, com mínimo de customização. Conhecer o framework é pré-requisito para distinguir recurso nativo de necessidade real de customização.
- **Automação redundante vs útil**: redundante quando a IA executa o que você faria com menos esforço; útil quando interpreta contexto e sintetiza. `/commit` é útil (olha arquivos soltos, entende contexto, escreve mensagem decente); push via IA é excesso.
- **Problema do Hello World**: a estrutura gerada pelo comando oficial raramente é seguida no resto do projeto (muda para testes, clean architecture etc.), até em frameworks opinativos. Analogia do iceberg: o Hello World é a ponta, o preparo é o que vale.
- **Segunda fundação**: condições para o agente entender, executar, validar e depurar sem operar no escuro. "Hello World com IA" = projeto que já nasce operável por agentes.
- **Mínimo viável da segunda fundação**: AGENTS.md/CLAUDE.md como contrato operacional (ver [[Arquivos de Inicialização do Agente]]), skills, regras e forma de rodar testes (testes como canal de feedback, ver [[Testes Automatizados vs IA]]), scripts de inicialização (ver [[Ambiente e Scripts de Inicialização]]), logs para a IA depurar, navegação no browser e testes de UI. Skills entram depois da base operacional.
- **Skill de bootstrap como wrapper/wizard**: chama `git clone` do boilerplate ou `create-next-app`, aplica customizações por contexto (auth, ORM, testes de UI só se houver front-end) e cria a segunda fundação no dia zero. Boilerplate é insumo, não produto final.
- **Skill vs boilerplate clonado**: a skill permite customizar na geração ("não bota o Jest"); sem testes, CLAUDE.md e pastas saem sem nada de teste. Recomendada mesmo com boilerplate existente.
- **Next.js Bootstrap (skill do autor)**: exemplo didático, não para produção; independe de agente; no Claude Code chamada por `/nextjs-bootstrap` ou linguagem natural ("faça o setup de um Next.js bootstrap"). Wizard pergunta diretório atual ou outro, nome (MyApp), diretório, descrição. Stack do repositório: Next.js 16 App Router, TypeScript strict, Prisma 7, PostgreSQL, NextAuth v5, Tailwind CSS 4, Zod, bcryptjs, Jest + Testing Library, CLAUDE.md e scripts operacionais (na aula também citado Inngest).
- **Encadeamento da skill**: SKILL.md (front matter + coleta de parâmetros) -> `scripts/bootstrap.sh` (execução) -> pasta `templates` (arquivos-base com `{{PROJECT_NAME}}`, `{{PROJECT_DESCRIPTION}}`, `{{PROJECT_DB_NAME}}`).
- **Passos do `bootstrap.sh`**: 1) `create-next-app@latest` se não existir `package.json`; 2) remove `tailwind.config` e recria `postcss.config.mjs` com `@tailwindcss/postcss`; 3) instala Prisma, NextAuth, bcryptjs, Zod, dotenv-cli e Jest; 4) copia scripts init, down, check, watch, tmux-dev, deploy; 5) copia `lib/db`, `lib/auth`, `lib/validations`, middleware, rota NextAuth, layout e page, Jest config e testes de exemplo; 6) Prisma schema, config e seed; 7) `.env.example` e `.env.test`; 8) CLAUDE.md; 9) scripts no package.json (`db:push`, `db:push:test`, `db:seed`, `db:migrate`, `db:reset`, `lint:fix`, `test`, `test:watch`, `test:coverage`); 10) `.gitignore`; 11) `prisma generate`. Nome do banco deriva do nome do projeto em snake_case.
- **Templates**: config básica do Jest; config e schema Prisma com autenticação e Postgres; env.example com credenciais do Postgres e range de portas; CLAUDE.md template (mais completo que o original, muda conforme o pedido); `seed.ts`; scripts de inicialização; estilização do "olá mundo" (a página inicial mostra a stack).
- **Projeto gerado "pronto para uso"**: CLAUDE.md com overview, scripts operacionais, comandos básicos, tech stack, estrutura e seção de testes. Premissa: a IA sempre pode trabalhar com o projeto zerado, a inicialização tem que ser reproduzível após `--clean`. "Inicie o sistema" chama o script, cria `.env.local` e sobe na porta 3000 sem a IA explorar o código. A diferença não é que a IA desenvolve, é como desenvolve.
- **Range de portas**: init verifica ocupação, escolhe porta livre e grava no `.env.local`, evitando que testes e navegação de um agente misturem com processo de outro.
- **`ln -s CLAUDE.md AGENTS.md`**: uma fonte de verdade; a Anthropic não lia AGENTS.md por padrão no momento da gravação (ver [[CLAUDE.md e AGENTS.md (Instruções de Projeto)]]).
- **Scripts do projeto gerado**: `init.sh` (.env, dependências, `prisma generate`, `prisma db push`, seeds, sobe servidor, health check); `down.sh` (mata servidor), `--force` (também Playwright, Jest, zumbis), `--clean` (variáveis, node_modules, .next); `check.sh` (servidor rodando e saudável), `--fix` (mata órfãos, reinicia e sobe); `watch.sh` (tail dos logs), `--ps` (processos ativos, a IA não precisa inferir comandos).
- **StreamTube (projeto prático)**: plataforma de vídeos; navegação pública sem login; upload e ações que alteram o sistema exigem autenticação; cada conta tem um canal. Front Next.js + React + TypeScript sem regra de negócio local; API REST NestJS como núcleo; Postgres; storage de vídeo (local em dev, S3 em produção); fila para processamento assíncrono do upload; worker NestJS com FFmpeg extraindo duração e metadados; serviço de e-mail para confirmação de conta e recuperação de senha; front e back no mesmo monorepo (contexto global para a IA).
- **Dinâmica de desenvolvimento do StreamTube**: 1) criar o NestJS no monorepo e a fundação de IA do back-end; 2) desenvolver features de back-end avaliando o impacto da fundação; 3) criar o front Next.js do zero com sua fundação, reaproveitando a existente (ver [[Fundação de IA do Next.js]]); 4) planejar e testar uma feature full stack.
- **Pasta inicial do StreamTube**: só `.gitignore`, planejamento geral (contexto e funcionalidades) e diagrama Mermaid da arquitetura.
- **Backend com NestJS CLI**: Node.js via FNM (no Windows, WSL); pedir explicitamente o uso do CLI, porque a IA gerando o projeto direto tende a vir desatualizado.
- **Docker no projeto**: docker compose com API NestJS e Postgres 17; `Dockerfile.dev` com `node:25.6.0-slim`, `procps` (ps para o Nest) e `curl`, WORKDIR, usuário não root; `tail -f /dev/null` mantém o container vivo como workspace para a IA rodar servidor, testes e debugging; porta 3000:3000; volume da pasta do projeto; Postgres na 5432 com healthcheck para a API só subir com o banco ok. Container desacopla do SO e a IA não instala nada na máquina.
- **Prova dos noves com IA crua**: Opus 4.6 com 1 milhão de tokens; prompt genérico em plan mode + bypass de permissões delegou decisões demais. A IA inferiu TypeORM, Passport, Bcrypt, e-mail, módulos, canal criado com o usuário, refresh token, testes E2E, tabelas users e channels. Histórico disponível em branch separada do repositório.

## Fluxograma / Processo

```mermaid
flowchart TD
    A[Intencao de criar a aplicacao] --> B[SKILL.md coleta nome descricao e diretorio]
    B --> C{Scaffold nativo ou boilerplate?}
    C -- nativo --> D[create-next-app]
    C -- boilerplate --> E[git clone do template]
    D --> F[bootstrap.sh copia templates e troca placeholders]
    E --> F
    F --> G[Aplica variacoes auth ORM testes]
    G --> H[Gera CLAUDE.md e scripts operacionais]
    H --> I[Report e orientacao para rodar init]
    I --> J[init.sh sobe ambiente com health check]
```

## Erros comuns / Cuidados

- Se o comando que você pediria à IA é o mesmo que sabe de cabeça, digite o comando (desperdício de token por preguiça; o autor admite esquecer comandos básicos por delegar).
- Criar projeto com o comando oficial e sair usando IA sem o bloco inicial gera curva enorme até ficar produtivo; ir de forma progressiva sem estrutura personalizada gasta tempo e token.
- IA sem logs é "alguém corrigindo um sistema vendado".
- A demora do bootstrap vem do `create-next-app` e da instalação de node_modules, não só da IA.
- Bootstrap remove grande parte do sofrimento inicial, mas não resolve pontos arquiteturais nem estilo de programação, que só aparecem quando já há muito código; testes e regras de como testar precisam estar organizados no dia zero (ver [[Edge Cases e Test Guidelines]]).
- Problemas da IA crua no StreamTube: MailHog no docker-compose (sem manutenção há mais de 4 anos); login recebendo id, email e status em vez de email e senha (erro de contrato); PassportModule desnecessário (JwtModule basta), overengineering por treino em versões velhas do Nest; teste unitário do AuthService com 425 linhas mockando tudo, sem verificar JWT com assinatura correta; `UnauthorizedException` na camada de serviço acoplando regra de negócio a transporte; testes E2E criados e não executados ("requer Postgres" com Postgres disponível); não usou Docker e ficou "rateando". Em 3 minutos acumulou débito técnico: "antes um dev demorava muito tempo para estragar o projeto".
- Padronizar comandos de subir/derrubar ambiente para a IA não errar pasta ou container.
- Windows: Docker via WSL2 (Docker Desktop ou Engine direto no WSL2); Linux: não usar pacotes `docker.io` do apt padrão, geralmente desatualizados; macOS: imagens sem build arm64 rodam via Rosetta, mais lento, priorizar multi-arch.

## Materiais complementares

### Prompts

**SKILL.md da nextjs-bootstrap (literal, repositório skills-mba)**
````text
---
name: nextjs-bootstrap
description: |
  Bootstrap a new Next.js project with our standard architecture, CLAUDE.md, and operational scripts.
  Use this skill whenever the user wants to start a new Next.js project, scaffold a new app, create a new
  project from scratch, or set up a greenfield application. Also use it when the user says things like
  "new project","bootstrap", "scaffold","setup nextjs", or "setup a nextjs using AI".
---

# Next.js Project Bootstrap

Sets up a new Next.js project with a battle-tested architecture: App Router, TypeScript strict, Prisma 7, PostgreSQL, NextAuth v5, and Tailwind CSS 4. Generates a complete CLAUDE.md, operational scripts (init, down, check, watch, tmux, deploy), and project structure ready for AI-assisted development.

## Workflow

### 1. Gather Project Info

Ask the user for:

1. **Project name** (kebab-case, used for directory, DB name, tmux session)
2. **Project description** (one-liner for CLAUDE.md)
3. **Target directory** (where to create/setup the project)

### 2. Run Bootstrap Script

Run the bootstrap script with the gathered info:

```bash
<skill-path>/scripts/bootstrap.sh <project-name> "<project-description>" <target-directory>
```

The script will:
- Create a Next.js app (if target is empty/missing)
- Remove Tailwind 4 incompatible files (tailwind.config, postcss.config)
- Install all dependencies (Prisma, NextAuth, bcryptjs, Zod)
- Copy and configure operational scripts (init, down, check, watch, tmux, deploy)
- Copy source file templates (lib/db, lib/auth, lib/validations, middleware, auth route)
- Set up Prisma schema, config, and seed file
- Generate CLAUDE.md and .env.example with correct project values
- Add package.json scripts (db:push, db:seed, db:migrate, etc.)
- Update .gitignore and generate Prisma client

All templates live in `<skill-path>/templates/` as plain, editable files. The script replaces `{{PROJECT_NAME}}`, `{{PROJECT_DESCRIPTION}}`, and `{{PROJECT_DB_NAME}}` placeholders.

### 3. Report Results

Tell the user:
1. Run `./scripts/init.sh` to start everything (env, database, dev server)
2. The CLAUDE.md is ready -- Claude Code will follow the project patterns
3. Suggest next steps: create first feature, add seed data, etc.

## Adaptation Rules

- **Project name** replaces all instances of project-specific values (DB name, tmux session, log file path)
- **DB names** are derived from project name: `project_name` (dev), `project_name_test` (test)
- Scripts always read `SERVER_PORT` from `.env.local` -- never hardcoded
- Scripts use `PROJECT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")/.." && pwd)"` for portability
- All scripts are idempotent -- safe to run multiple times

## Code Patterns

All code patterns and conventions are defined in the generated CLAUDE.md template (`<skill-path>/templates/claude-md.md`). Follow those patterns when generating any code during bootstrap.

## Rules
- .env.example must never contain real credentials
- Always ask before installing additional packages beyond the core stack
````

**Template `env-example.txt` da nextjs-bootstrap (literal)**
```text
# Database
DATABASE_URL="postgresql://postgres:postgres@localhost:5433/{{PROJECT_DB_NAME}}"
DATABASE_URL_TEST="postgresql://postgres:postgres@localhost:5433/{{PROJECT_DB_NAME}}_test"

# NextAuth
NEXTAUTH_SECRET="development-secret-change-in-production"
NEXTAUTH_URL="http://localhost:3000"

# Server
SERVER_PORT=3000
PORT_RANGE="3000 3010"
```

**Trecho do template `claude-md.md`: scripts e regras (literal; arquivo completo de 179 linhas em `nextjs-bootstrap/templates/claude-md.md`, com seções Project Overview, Environment Setup, Tech Stack, Project Structure, Testing, Database, Development, Rules)**
````text
### Scripts

```bash
./scripts/init.sh                  # Setup: .env + deps + prisma generate + db push + seed + start server + health check
./scripts/down.sh         # Stop server (graceful)
./scripts/down.sh --force # Kill server + orphan processes (playwright, jest, next-server)
./scripts/down.sh --clean # Stop server + remove .env.local, node_modules, .next, .turbo
./scripts/down.sh --force --clean # Force kill everything + clean
./scripts/check.sh        # Diagnostic: status (OK/PENDING/DEGRADED) with HTTP health check
./scripts/check.sh --fix  # Diagnostic + auto-fix: kills orphans, restarts if degraded/stopped
./scripts/watch.sh        # Tail server logs
./scripts/watch.sh --ps   # Show running processes (updates every 1s)
```

**Server port:** Configured via `SERVER_PORT` in `.env.local`. All scripts read from this variable. **Obs:** If using worktrees, always use ./scripts/down.sh --force --clean in order to clean the port and start a new server by using the init script.

## Rules
- Never skip a task because you don't have a running server. Always run `./scripts/init.sh`.
- Never run `npm run dev` or `next dev` directly. Always use `./scripts/init.sh` to start the server.
- Never install packages or dependencies without asking the user first.


### Tmux

Run `./scripts/tmux-dev.sh` to create a detached tmux session named after the project. Attach with: `tmux attach -t {{PROJECT_NAME}}`
````

**Pedido após o bootstrap (narrado na aula)**
```text
Inicie o sistema.
```

**Prompt "cru" usado como contraexemplo no StreamTube, em plan mode (narrado na aula)**
```text
Implemente a fase 2 do documento, a parte da autenticação. Quero implementar toda a fase, mas somente o back-end. Pense numa boa arquitetura, use boas práticas de Node.js e TypeScript e crie todos os testes possíveis, valide todos os cenários.
```

### Conteúdo extra

- Comandos do backend NestJS:
```bash
npm install -g @nestjs/cli
nest new <projeto>        # escolher npm como gerenciador
npm run start:dev
curl http://localhost:3000   # "Hello World"
```
- Docker: `docker compose up`, `docker compose exec nestjs-api bash`; verificação da instalação: `docker version`, `docker compose version`, `docker run hello-world`.
- Código-fonte das skills: https://github.com/devfullcycle/skills-mba
- Código-fonte StreamTube: https://github.com/devfullcycle/mba-ia-greenfield-project.git
- Guia de instalação do Docker: https://gist.github.com/argentinaluiz/211ac4389a3d6fefede270c01b2acb5c ; https://github.com/codeedu/wsl2-docker-quickstart ; https://docs.docker.com/engine/install/ ; https://docs.docker.com/desktop/install/linux/ ; https://docs.docker.com/desktop/install/mac-install/

## Tags de busca

`#dev-software-ia` `#greenfield` `#bootstrap` `#nextjs-bootstrap` `#streamtube`
