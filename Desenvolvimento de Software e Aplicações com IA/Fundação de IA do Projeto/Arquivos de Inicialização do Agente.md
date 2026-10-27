---
tags: [dev-software-ia, mba]
materia: "Desenvolvimento de Software e Aplicações com IA"
tema: "Arquivos de Inicialização do Agente"
status: revisado
---

# Arquivos de Inicialização do Agente

> [!summary] TL;DR
> - CLAUDE.md / AGENTS.md entram no contexto antes da 1a ação; o README é descoberto durante a navegação. "O README documenta; o arquivo de inicialização orienta a primeira execução."
> - Só entra o que muda a decisão do agente e que ele não obtém com segurança sozinho: comandos exatos, state do ambiente, testabilidade, policies e gotchas.
> - Em monorepo: CLAUDE.md global com o que vale para todos os subprojetos e sub CLAUDE.md por subprojeto, carregado só quando a IA entra na pasta.
> - `/init` gera esqueleto; o arquivo intencional nasce de refino guiado por erros observados e é tratado como código-fonte.
> - Ciclo de feedback: erro recorrente vira regra, gotcha, rule, skill ou automação.

## Conceitos-chave

- **Arquivo de inicialização**: CLAUDE.md, AGENTS.md ou equivalente, recebido antes da 1a ação; índice operacional pré-carregado, não documentação extensa (base geral em [[CLAUDE.md e AGENTS.md (Instruções de Projeto)]]).
- **Scripts x arquivo**: scripts executam; o arquivo diz quais usar e quando ([[Ambiente e Scripts de Inicialização]]). Critério de qualidade: se o agente ainda varre diretórios para subir o ambiente, o arquivo está incompleto ou genérico.
- **Conteúdo mínimo operacional**: project overview; environment setup and running; environment status; init de back-end, front-end e ambos; variantes com migrations para 1a execução; parar, resetar, limpar volumes e containers; executar serviços; estado das migrations; regras operacionais (ex: rodar comandos dentro do container omitindo `-it`).
- **1a linha**: o que o projeto é, tecnologia principal e problema que resolve.
- **Concisão**: o arquivo compete por contexto, custa tokens e partes podem ser ignoradas; sem ficar vago (impacto em [[Gestão de Context Window em Prompts]]).
- **Comandos com parâmetros exatos**: build e testes completos, para o agente não inventar flags.
- **Guias de estilo específicos**: "TypeScript strict mode, indentação de 2 espaços, proibir `any`" em vez de "formate corretamente".
- **Diretórios-chave**: só onde há múltiplos caminhos plausíveis (monorepos).
- **Microcomportamentos de workflow**: abertura de PR, padrão de branches, critérios de code review, limites de escopo, quando verificação manual é obrigatória.
- **Políticas locais restritivas**: nunca push na main, revisar descrição do commit, evitar testes redundantes; importantes em enterprise.
- **Importação de referências**: guia de coding style em arquivo separado; o índice orienta, as referências aprofundam.
- **O que NÃO entra**: nomes de arquivos, funções e classes dedutíveis pela navegação; genéricos ("use boas práticas"); informação volátil (envelhece e é pior que omissão, o agente confia no caminho errado); documentação extensa de API/bibliotecas.
- **Teste de poda**: muda com frequência? é grande demais? se explica sozinho? então remover. Exceção: arquivos marcantes (pegadinha conhecida, comportamento vital, armadilha não dedutível); um arquivo crítico citado é cirúrgico, muitos viram inventário frágil.
- **Exemplo Videomax** (back e front no mesmo repo): overview de 1 parágrafo com domínio, fluxo e peculiaridades (FFmpeg WebAssembly no browser, transcrição com Whisper, sumários vinculados por timestamp); comandos de ambiente com destaque para status (evita reinicializar tudo); execução obrigatória dentro do container, sem `-it` porque modo interativo quebra execução automática; estrutura como visão geral, não inventário; códigos de erro recorrentes do domínio; regras de auth resumidas (Bearer no header, expiração do access token, refresh HTTP-only, lockout); guidelines nascidas de erro observado escritas como bad vs good; detalhes de stack e pipeline que evitam explorar package.json/requirements.txt (upload chunkado, resume de sessão, verificação SHA-256).
- **Testabilidade no arquivo**: marcadores de teste (unit, integration, slow) e suas dependências ("integração precisa de banco"); inventário de fixtures, usuários de teste, estados de auth e helpers do conftest (ex: `createTestUserData`, `createLoginData`); comandos exatos dentro do container (suíte completa, por nome, só unit, só integração); flags não interativas (Jest `--watchAll=false`, Playwright `--reporter=list`); escopo: durante a interação só testes ligados aos arquivos alterados, antes de PR ou mudança grande a suíte completa; o que não testar e o que priorizar (detalhado em [[Edge Cases e Test Guidelines]]); limites contra exagero: máximo de testes por arquivo, máximo de mocks por teste, comparar tamanho do teste com o da implementação.
- **Git policy**: proibir hábitos perigosos (force push, hard reset, alterar configuração sem pedido) e definir formato de commit (conventional commits).
- **Hooks**: interceptam ações antes/durante comandos (linting, validações); o arquivo registra a regra crítica, a automação reforça.
- **Gotchas**: armadilhas não óbvias registradas como certo/errado a partir de erros observados; exemplos React/formulários: propagação de clique em links, elementos interativos dentro de Next.js Link, override indevido de refs do react-hook-form, wrappers HTML que não preservam onChange.
- **Notas operacionais estáveis**: compatibilidade de tipos de banco, rodar `alembic upgrade head` após puxar migrations, desenvolver o front isolado com MSW mocks ([[Testes no Front-end com MSW]]).
- **Tamanho**: ~287 linhas pode ser adequado se denso e acionável ("o que é útil para o projeto e não muda toda hora?").
- **`/init`**: explora o codebase e gera esqueleto (descreve o projeto); o arquivo intencional orienta como trabalhar com previsibilidade. No projeto de vídeos o `/init` acertou a arquitetura mas sugeriu subir o ambiente de forma incompatível com Docker. Sem `/init`, pedir à IA rascunho a partir da árvore de arquivos.
- **4 pilares do refino**: inicialização, state, testabilidade e feedback.
- **Crescimento controlado**: separar em arquivos auxiliares com títulos claros; conteúdo esporádico ou específico vai para skills (on-demand); uma fonte de verdade por conhecimento entre principal e skills ([[Fundamentos de Skills]]).
- **Arquivo legado grande**: não podar direto; primeiro validar contra si mesmo, porque contradições e regras duplicadas distorcem o agente mais que ausência de contexto. Manter fatos centrais, externalizar o resto com linkagem explícita e gatilhos de carregamento (tipo de tarefa, erro recorrente, decisão específica); transformar regras vagas em concretas; evitar minimalismo excessivo; erro recorrente não captado justifica manter no principal temporariamente.
- **Artefatos da fundação no Claude Code** (equivalentes em Cursor, Copilot, Gemini): CLAUDE.md global na raiz (Git, estrutura de pastas, comandos globais; carregado em todo prompt); sub CLAUDE.md / nested por subprojeto (feature de back não carrega o do front); [[Rules do Claude Code]]; skills on-demand pela description do front matter; skills como user command (`/nome`); commands personalizados em modo legacy; servidores MCP ([[MCPs do Projeto Context7 e Postgres]]).
- **Fundação de IA em 4 categorias**: 1) carregados automaticamente: CLAUDE.md global, sub CLAUDE.md, rules; 2) skills sob demanda: boas práticas NestJS, TypeORM e Test Guide do projeto ([[Curadoria de Skills]]); 3) skills user command: gerador do Test Guide, planejador da fase, busca apurada no planejamento ([[Planejamento de Fases com plan-phase]], [[Skill de Research e Decisões Técnicas]]); 4) MCPs: Context7 e Postgres. Comparação final: fase de autenticação feita com fundação vs com IA crua ([[Bootstrap de Projetos Greenfield]]).
- **CLAUDE.md global em monorepo**: só o que é geral. O `/init` gerou ~200 linhas com itens do NestJS (estrutura interna, comandos, Docker, testes, arquitetura modular, variáveis de ambiente); o do autor tinha ~58 linhas na criação: descrição, referência ao plano, estrutura só de 1o nível (front marcado "not yet initialized" para a IA não priorizar), diagrama C4 em Mermaid gerado a partir do planejamento, working principles, Git Flow, política de testes, limites de escopo. Não copiar CLAUDE.md de outro projeto; perfeição é utopia.
- **Sub CLAUDE.md do NestJS**: carregado só se a IA acessar a pasta (sem garantia); ~94 linhas na criação. Instrução crucial: iniciar, derrubar e verificar o ambiente sem "ratear". "Iniciar ambiente" sobe só a infraestrutura; o servidor Nest só sobe com pedido explícito; confirmar containers e readiness do banco antes de agir; todo comando dentro do container (modelos como Haiku tentam rodar no host); mapa de serviços (`nestjs-api`, `db`); processos long-running em background (senão o agente espera para sempre).
- **Regra transversal vai no global**: o erro de `localhost` dentro de container virou a seção "Docker Networking" do CLAUDE.md global, não do NestJS ([[Rules do Claude Code]] traz o prompt).
- **Memórias do Claude Code**: ficam fora do projeto (pasta do usuário), não versionadas nem portáveis; conhecimento do projeto vai para os arquivos versionados.
- **Feedback pós-implementação**: concluir a funcionalidade não encerra a fase; o `.progress.md` por SI é feedback estruturado (alternativa: exportar a sessão). Mudanças aplicadas: Definition of Done técnica (testes afetados, `tsc --noEmit`, lint; redundância intencional com a skill [[Implementação de Fases com implement-phase]]); SRP com extração imediata (derivado da extração do `ChannelsModule`); bloco em negrito "comandos de teste dentro do container" com listas host-only vs container; `--runInBand` em integração e e2e (banco único; paralelismo do Jest causa violação de FK e deadlocks, e a IA foi treinada com Jest paralelo); convenção de nomes de teste movida das rules para o CLAUDE.md; config do Jest; assets não TS em `nest-cli.json` `compilerOptions.assets`.
- **Onde cada conhecimento mora**: rule com `paths` só carrega quando a IA lê/escreve arquivo que bate com o padrão; o que influencia decisões antes de criar o arquivo (nome de arquivo de teste, execução de testes) vai para o CLAUDE.md. Exemplo real: a IA criou `*.integration-spec.ts`, a rule de testes não carregou e ela não usou `Test.createTestingModule`.
- **Modelo mais barato**: contexto inicial preciso embute inteligência e permite modelos rápidos/baratos em tarefas complexas recorrentes.

## Fluxograma / Processo

```mermaid
flowchart TD
    A[Rodar init ou pedir rascunho] --> B[Inspecionar resultado]
    B --> C[Corrigir inicializacao state testabilidade feedback]
    C --> D[Code review do arquivo e teste de comportamento do agente]
    D --> E[Usar em tarefas reais]
    E --> F[Pedir lista concisa de dificuldades]
    F --> G{Erro recorrente?}
    G -->|sim| H[Virar regra gotcha rule skill ou hook]
    H --> E
    G -->|nao| I[Podar ou mover para skills o que deixou de ser decisivo]
```

Refatoração de arquivo legado: detectar conflitos explícitos e implícitos, extrair fatos centrais, decidir o que externalizar (arquivos ou skills) e linkar, propor gatilhos de carregamento, reescrever regras vagas como concretas, gerar os arquivos e revisar se o principal não ficou minimalista demais.

## Erros comuns / Cuidados

- IA colocando metadados de tarefa (ids, notas) em comentários, docblocks e commits: virou guideline bad vs good no exemplo Videomax.
- Agente gerando testes demais quando o arquivo não delimita o que validar; refinar com exemplos por falha observada.
- Arquivo desatualizado induz erro com aparência de verdade.
- Ver o erro e não mudar a fundação: o problema volta e culpa-se o modelo.
- Se a IA sofre o tempo todo, o problema pode ser estrutural (workflow, prompt ou codebase), não o arquivo.
- Rules com `paths` não carregam no planejamento: regra que precisa valer antes do arquivo existir não pode ficar só nelas.

## Materiais complementares

### Prompts

**Regra operacional do arquivo de inicialização (narrado na aula)**
```text
Sempre rode comandos dentro do container, omitindo o -it
```

**Linha de abertura de exemplo (narrado na aula)**
```text
API REST em FastAPI para autenticação de usuários
```

**Regras restritivas de exemplo (narrado na aula)**
```text
Nunca faça push na main.
Revise a descrição do commit antes de enviar.
Evite testes redundantes.
```

**Git policy (narrado na aula)**
```text
Nunca use force push na main ou master.
Nunca pule hooks com --no-verify.
Só use amend quando for realmente seguro.
Use conventional commits.
```

**Fim de tarefa custosa para alimentar o arquivo (narrado na aula)**
```text
Liste de forma extremamente concisa os pontos em que você encontrou dificuldade nesta tarefa e que poderiam entrar no CLAUDE.md para evitar erros futuros.
```

**Testes do sub CLAUDE.md com Haiku (narrado na aula)**
```text
Inicie o ambiente.
```
```text
Agora derrube o ambiente.
```
```text
Eu quero iniciar o ambiente com o back API rodando.
```

**Análise do progresso da fase para melhorar a fundação (sessão real do repositório, `_claude-sessions/10-melhorias-na-fundacao-ia.txt`)**
```text
dado o arquivo de progress da fase 02, olhando as obsevações de cada SI
implementado, pense em pontos que poderíamos melhorar no CLAUDE.md global e
no CLAUDE.md do nestjs-project e nas .claude/rules
permitindo que tenhamos execuções mais assertivas
```
```text
quero que edite os arquivos, mas não é para mencionar SI
```
```text
acho que tem trechos que estão nas .claude/rules que poderiam ficar no
claude.md do nestjs e talvez tenha trechos de .claude/rules que confrontando
pelo frontmatter talvez não fazem sentido ou nem seja acionados, talvez
poderiam estar em outra rule nova ou já existente
```
```text
um trecho como este não faz sentido estar neste arquivo, já que só é
disparado de acordo com o frontmatter quando já está manipulando os testes.
corrija isto e renalise outros casos semelhantes
```
```text
esta parte selecionada é outro exemplo, é execução dos testes
```
```text
liste todos os arquivos modificados nesta sessão
```

**CLAUDE.md global do Streamtube (arquivo literal do repositório mba-ia-greenfield-project, até a seção Agent Skill Usage)**
```markdown
# CLAUDE.md

## Project Overview

StreamTube - a video sharing platform (YouTube-like). Users can upload, manage, and publish videos. Anonymous users can watch freely; social features (comments, subscriptions, likes) require authentication.

More info in the project overview: [docs/project-plan.md](docs/project-plan.md)

## Repository Structure

This is a monorepo with two main areas:

- `nestjs-project/` - Backend API (NestJS 11, TypeScript, Express). Contains modules for users, channels, videos, comments, etc.
- `docs/` - Project documentation, architecture diagrams, and planning.
- `next-frontend/` (Next.js) - not yet initialized

## Architecture (C4 Container Diagram)

See `docs/diagrams/software-arch.mermaid` for the full diagram. Key containers:

- **Frontend** (Next.js) → calls API via REST, streams from Object Storage
- **API** (Nest.js) → business rules, auth, reads/writes DB, uploads to storage, publishes jobs to queue, sends emails
- **Video Worker** (FFmpeg) → consumes jobs from queue, processes videos, updates DB and storage
- **Database** (PostgreSQL) → users, channels, videos, comments, likes
- **Object Storage** (S3/MinIO) → video files and thumbnails
- **Message Queue** (TBD) → video processing job queue
- **Email Service** (SMTP) → account confirmation and password recovery

## Docker Networking

This project runs entirely in Docker containers. When configuring connections between services (database, cache, queue, etc.), **always use the Docker Compose service name** as the host - never `localhost` or `127.0.0.1`.

Inside a container, `localhost` refers to the container itself, not the host machine or other containers. Services communicate through the Docker Compose network using their service names (e.g., `db`, `nestjs-api`).

- **Correct:** `DB_HOST=db` (the Compose service name)
- **Wrong:** `DB_HOST=localhost`

This applies to all environment variables, configuration files, and code that references service hosts.

## Working Principles

- **Single Responsibility:** each module, service, and function should have a clear, focused responsibility. Re-evaluate adherence at every step - when a module starts owning logic or entities that are not its own (e.g., a service creating an entity from another domain), extract it immediately into the proper module instead of deferring to a later corrective task.
- **Type Safety:** Strict TypeScript usage across all layers.
- **Testing:** Strong emphasis on pyramid testing at all levels to ensure reliability and maintainability.
- **Code Quality:** Use ESLint and Prettier for consistent code style. Code reviews should focus on readability, maintainability, and adherence to best practices.
- **Documentation:** Comprehensive docs for architecture, setup, and troubleshooting in `docs/`.

## Definition of Done (Technical)

A change is only considered complete when **all** of the following pass:

1. The relevant test suite passes (unit + integration + e2e affected by the change).
2. The full test suite passes before finishing the task.
3. TypeScript compiles cleanly: `npx tsc --noEmit` exits with code 0. Compilation errors must never be left as debt for future tasks.
4. Lint passes: `npm run lint`.

If any of these fails, the task is not done - fix the underlying issue before declaring completion.


## Git Conventions

- **Main branch:** `main` - never commit directly to it
- Branches: `feature/*`, `bugfix/*`, `hotfix/*`, `docs/*`
- **Commits:** short, descriptive messages focused on the "why" of the change
- **Workflow:** Git Flow conventions. Two long-lived branches:
  - `main` - stable, production-ready code 
  - `dev` - integration branch; all feature/bugfix/hotfix branches start from `dev` and merge back into `dev`
  - When `dev` is stable, it is merged into `main`

## Testing Policy

Every change must be tested. During development, run only the tests related to the modified code. Before finishing, always run the full test suite to ensure nothing is broken.

## Scope Limits

- Work on **one feature, fix, or refactoring at a time** - do not mix scopes
- Do not include cosmetic changes (formatting, renaming) alongside functional changes
- If something out of scope comes up during work, note it as a separate task instead of acting on it
- Focus on the defined scope for each task to ensure clarity and maintainability of the codebase.
- If you identify a necessary change that is out of scope, create a new issue or task for it instead of including it in the current work.

## Agent Skill Usage

When working on any task (planning, implementing, debugging, refactoring, 
reviewing, etc.), decompose the request into its underlying subtasks and 
concerns, then identify which available skills match any of them and activate 
those skills.
```

A seção final do arquivo, "Library Documentation Lookup", está reproduzida literalmente em [[MCPs do Projeto Context7 e Postgres]].

**Sub CLAUDE.md `nestjs-project/CLAUDE.md` (arquivo literal do repositório mba-ia-greenfield-project)**
````markdown
# CLAUDE.md

## Environment Startup Verification

**Default behavior:** starting the environment means starting **only infrastructure services** (database, mail, etc.) - **never** start the NestJS application server unless the user explicitly asks to run/serve the project (e.g., "rode o projeto", "suba o servidor", "run the app").

After starting infrastructure, always confirm the containers are up before proceeding:

```bash
docker compose ps   # all services must show status "running"
```

Then verify each infrastructure service is actually ready to accept connections - not just running:

- **PostgreSQL:** `docker compose exec db pg_isready -U streamtube` - expect `accepting connections`

Only start the NestJS dev server (`npm run start:dev`) when the user **explicitly** asks to run the application - never as part of "start the environment".

## Development Environment

This project runs inside Docker. Always use the container for development:

```bash
# Start containers
docker compose up -d

# Install dependencies (first time only)
docker compose exec nestjs-api npm install

# Run the dev server (watch mode)
docker compose exec nestjs-api npm run start:dev
```

Services:
- `nestjs-api` - NestJS API, port `3000`
- `db` - PostgreSQL 17, port `5432`, database `streamtube`, user/password `streamtube`

All verification and teardown commands run on the **host machine**:

```bash
# Verify NestJS is running (expect 200 + "Hello World!")
curl http://localhost:3000

# Verify PostgreSQL is ready (runs inside the db container)
docker compose exec db pg_isready -U streamtube

# Check container logs
docker compose logs nestjs-api
docker compose logs db

# Tear down the entire environment
docker compose down
```

## Commands

**Strict rule:** every `npm`, `npx`, `node`, `tsc`, and test command runs **inside the container**, never on the host. Running on the host causes env-var divergence (`DB_HOST` resolves to `localhost` instead of the Compose service), uses a different Node version, and produces results that do not reflect what runs in CI/prod.

### Container-only commands (always prefix with `docker compose exec nestjs-api`)

```bash
npm run start:dev                        # Dev server with hot-reload
npm run build                            # Compile to dist/
npm run start:prod                       # Run compiled build

npm test                                 # Unit tests
npm run test:watch                       # Unit tests in watch mode
npm run test:cov                         # Coverage report
npm run test:e2e                         # End-to-end tests (always with --runInBand)

npx tsc --noEmit                         # Type-check (required before declaring a task done)
npm run lint                             # ESLint with auto-fix
npm run format                           # Prettier formatting
```

### Host-only commands (Docker / connectivity probes)

```bash
docker compose ps
docker compose logs nestjs-api
docker compose exec db pg_isready -U streamtube
curl http://localhost:3000
```

### Test execution

Integration and e2e suites share a single test database. They **must** be run with `--runInBand`:

```bash
docker compose exec nestjs-api npm test -- --runInBand
docker compose exec nestjs-api npm run test:e2e   # already configured
```

Parallel execution causes FK violations, deadlocks, and cross-suite contamination because suites truncate or seed shared tables concurrently.

During active development, run only the tests related to the file being changed (`npm test -- path/to/file.spec.ts`). Before declaring a task done, run the full suite - see the global `CLAUDE.md` → "Definition of Done (Technical)".

## Long-running Processes

Commands that never exit (dev server, watch modes) must be run in background in the Bash tool - otherwise the agent blocks indefinitely waiting for the process to return.

This applies to: `start:dev`, `start:prod`, `test:watch`, and any other persistent process.

## Test Type Selection

Choose the suffix by what the test really does, not by where the code under test lives. The suffix is a contract that drives Jest config (`testRegex`, parallelism), CI steps, and reader expectations.

| Suffix                  | Purpose                                                              | DB / external I/O | Location                     |
|-------------------------|----------------------------------------------------------------------|-------------------|------------------------------|
| `*.spec.ts`             | **Unit** - pure logic, all collaborators mocked                      | Forbidden         | Next to the source file      |
| `*.integration-spec.ts` | **Integration** - exercises real DB, real repositories, real modules | Required          | Next to the source file      |
| `*.e2e-spec.ts`         | **End-to-end** - full HTTP cycle via `supertest`                     | Required          | `nestjs-project/test/`       |

A test that constructs a `TypeOrmModule.forRoot`, opens a connection, or hits the `db` service **must** be `*.integration-spec.ts`, never `*.spec.ts`. A test that boots the full Nest application and makes HTTP calls **must** be `*.e2e-spec.ts`.

Conventions for **how to write** each kind of test (mocking patterns, AAA structure, override strategies for global guards, etc.) live in `.claude/rules/nestjs-testing.md` and load when you edit a test file.

## Jest Configuration

These settings are required in `package.json` (jest config) and `test/jest-e2e.json` for the project's tests to work correctly:

- `setupFiles: ["dotenv/config"]` - without this, `.env` is not loaded inside the Jest process. `DB_HOST`, `JWT_SECRET`, etc. fall back to undefined or to the host's `localhost`, breaking container-to-container DNS.
- `testRegex: '.*\\.(spec|integration-spec)\\.ts$'` - covers both unit (`*.spec.ts`) and integration (`*.integration-spec.ts`) suffixes.

Do not add new test-file suffixes; if a new test type is needed, update the regex deliberately.

## Environment File Conventions

`.env` is parsed by both Docker Compose and `dotenv` - values containing shell-special characters (`<`, `>`, `|`, `&`, spaces) **must be quoted** or rewritten:

```dotenv
# Wrong - the unquoted angle brackets are shell redirection syntax and break parsing
MAIL_FROM=StreamTube <noreply@streamtube.local>

# Right - quote the value
MAIL_FROM="StreamTube <noreply@streamtube.local>"
```

Whenever possible, prefer storing only the bare address in `.env` and composing display names in code (e.g., in `mail.config.ts`) so the file stays shell-safe.

## Build Assets

`tsc` (and therefore `nest build`) only emits compiled `.ts` files to `dist/`. Any non-TypeScript runtime asset - Handlebars templates (`.hbs`), JSON fixtures, static config files, etc. - must be declared in `nest-cli.json` under `compilerOptions.assets` (with `watchAssets: true` for dev). Without that, the file exists in `src/` but is missing in `dist/` and runtime fails only after build.

## Architecture

NestJS with standard module structure. Source lives in `src/`, compiled output in `dist/`.

- Each domain feature gets its own module (e.g., `UsersModule`, `VideosModule`) registered in `AppModule`
- Controllers handle HTTP routing; Services hold business logic; both are scoped to their module

## Code Conventions

- **TypeScript:** `nodenext` module resolution, `ES2023` target, `strictNullChecks` on, `noImplicitAny` off
- **Decorators:** `emitDecoratorMetadata` + `experimentalDecorators` enabled - required for NestJS DI
- **Prettier:** single quotes, trailing commas everywhere
- **ESLint:** `no-explicit-any` allowed; `no-floating-promises` and `no-unsafe-argument` are warnings

## REST Conventions

This is a RESTful API. All endpoints must follow standard REST conventions - correct HTTP methods, proper status codes, plural resource nouns, and consistent URL structure. Details are enforced via rules on controller files.
````

**Template de CLAUDE.md da skill nextjs-bootstrap `templates/claude-md.md` (arquivo literal do repositório skills-mba)**
````markdown
## Project Overview

{{PROJECT_DESCRIPTION}}. Built with Next.js 16+ (App Router), TypeScript, Tailwind CSS 4, and Prisma 7.

## Environment Setup

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

### Common Commands

```bash
npm run build               # Production build
npm run lint                # ESLint check
npm run lint:fix            # ESLint with auto-fix
npm run db:push             # Sync schema to dev DB (prisma db push)
npm run db:push:test        # Sync schema to test DB
npm run db:seed             # Seed database with test data
npm run db:migrate          # Generate PostgreSQL migration (production only)
npm run db:reset            # Reset DB + migrate + seed
npm test                    # Jest tests (uses test DB)
npm run test:watch          # Jest watch mode
npm run test:coverage       # Jest coverage report
```

## Tech Stack

- Next.js 16 (App Router)
- React 19
- TypeScript (strict mode)
- Tailwind CSS 4 (tokens via `@theme inline` in globals.css, NO tailwind.config.js)
- NextAuth.js v5 beta
- Prisma 7 (client generated in src/generated/prisma/)
- PostgreSQL (dev, test, and production). Driver: pg + @prisma/adapter-pg

## Project Structure

```
├── src/
│   ├── app/
│   │   ├── api/
│   │   │   └── auth/[...nextauth]/
│   │   ├── globals.css                 # Tailwind 4 tokens (@theme inline)
│   │   ├── layout.tsx
│   │   └── page.tsx
│   ├── components/
│   │   ├── layout/
│   │   └── shared/
│   ├── generated/prisma/           # Prisma 7 client (gitignored)
│   ├── lib/                        # auth, db, validations
│   ├── tests/
│   │   ├── helpers/
│   │   │   ├── db.ts               # Test DB client + cleanup utilities
│   │   │   └── auth.ts             # NextAuth session mocking helpers
│   │   └── examples/               # Reference patterns (safe to delete)
│   └── middleware.ts
├── prisma/
│   ├── schema.prisma
│   └── seed.ts
├── scripts/                        # init, down, check, watch, tmux, deploy
├── .env.example
├── prisma.config.ts                # Prisma 7 config (dotenv loading)
├── next.config.ts
├── tsconfig.json
└── eslint.config.mjs
```

## Testing

- Before running tests, verify the environment is set up and the server is running. Otherwise, run `./scripts/init.sh`.

### Test Quality Rules

**Test behavior and logic, not implementation details.**
- Every test must validate a business decision or user flow, not static markup.
- Do not test CSS classes, static HTML attributes, or element presence without interaction.
- Do not mock an entire dependency -- if everything is mocked, the test validates mocks, not code.

### Unit & Integration Tests (Jest)

**Commands:**

```bash
npm test                    # Run all Jest tests (uses .env.test DB)
npm run test:watch          # Watch mode (re-runs on file save)
npm run test:coverage       # Coverage report (output in coverage/)
npm run db:push:test        # Sync schema to test DB (run after schema changes)
```

**Test file locations:**
- Unit tests: colocated alongside source files as `*.test.ts` / `*.test.tsx`
- Shared helpers: `src/tests/helpers/` (db.ts, auth.ts)
- Example tests: `src/tests/examples/` (reference only, safe to delete)

**Patterns:**

1. **Pure logic (Zod schemas, utils):** No setup needed. Import and call directly.
2. **DB integration tests:** Use `getTestPrisma()` from `@/tests/helpers/db`. Call `resetDb()` in `beforeEach`. Call `disconnectTestDb()` in `afterAll`.
3. **API route tests with auth:** Mock `@/lib/auth` and `@/lib/db` at the top of the file (before imports). Use `mockAuth.mockResolvedValue(TEST_USER_SESSION)` per test.
4. **React component tests:** Add `@jest-environment jsdom` docblock at top. Use `@testing-library/react`.

**Rules:**
- Always run `npm run db:push:test` after changing `prisma/schema.prisma`.
- Update `cleanupTestDb()` in `src/tests/helpers/db.ts` when adding new models (FK-safe delete order).
- Never import from `@/lib/db` in test helpers - use `getTestPrisma()` directly.
- `jest.mock(...)` calls must appear before `import` statements (Jest hoists them automatically).

### E2E Verification Rules

- Run `./scripts/check.sh --fix` before E2E tests to ensure the server is running.

**Rules:**

1. Read `SERVER_PORT` from `.env.local`. Use it in all URLs: `http://localhost:<SERVER_PORT>/path`.
2. Use playwright-cli for navigation, web testing, form filling, and screenshots.
3. After each navigation, check browser console for errors -- any compilation/runtime error means FAILURE.
4. Use playwright-cli with headless mode.
5. Never create playwright test files for E2E UI verification.
6. Save screenshots to `.playwright-cli/`, never the project root.
7. After testing, remove all files in `.playwright-cli/` folder.

## Database

PostgreSQL for all environments (dev, test, production).

- Dev: `postgresql://postgres:postgres@localhost:5433/{{PROJECT_DB_NAME}}`
- Test: `postgresql://postgres:postgres@localhost:5433/{{PROJECT_DB_NAME}}_test`
- Production: `POSTGRES_URL_NON_POOLING` or `DIRECT_DATABASE_URL` (Vercel/Supabase)

### How it works

- `src/lib/db.ts` uses `pg.Pool` + `PrismaPg` adapter. Prisma 7 always requires an adapter.

### Schema changes

- **Dev/test:** `npm run db:push` (dev DB) or `npm run db:push:test` (test DB).
- **Production:** `prisma migrate dev --name <name>` to generate, `prisma migrate deploy` to apply.
- **First deploy:** Run `npx prisma migrate dev --name init` locally before the first production deploy to generate the initial migration.

## Development

### Code Patterns

- Private components in `_components/` inside each route folder
- `"use client"` only on interactive components (modals, forms, managers)
- API routes: session check -> Zod validation -> Prisma query -> NextResponse.json()
- Always use `@/` import alias
- Zod schemas centralized in `lib/validations.ts`

### Commit Convention

```
Format: <type>: <description in English>
Types: feat, fix, docs, test, chore, refactor
- Lowercase after the type
- Co-Authored-By is included automatically
```

## Rules
- Never skip a task because you don't have a running server. Always run `./scripts/init.sh`.
- Never run `npm run dev` or `next dev` directly. Always use `./scripts/init.sh` to start the server.
- Never install packages or dependencies without asking the user first.


### Tmux

Run `./scripts/tmux-dev.sh` to create a detached tmux session named after the project. Attach with: `tmux attach -t {{PROJECT_NAME}}`
````

### Conteúdo extra

- O CLAUDE.md do front (`next-frontend/CLAUDE.md`, 303 linhas) está no mesmo repositório e é tratado em [[Fundação de IA do Next.js]].
- Repositórios: https://github.com/devfullcycle/mba-ia-greenfield-project e https://github.com/devfullcycle/skills-mba

## Tags de busca

`#dev-software-ia` `#claude-md` `#agents-md` `#fundacao-de-ia` `#contexto-inicial`
