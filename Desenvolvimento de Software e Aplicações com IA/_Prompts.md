---
tags: [dev-software-ia, mba, prompts]
materia: "Desenvolvimento de Software e Aplicações com IA"
tema: "Prompts consolidados"
status: revisado
---

# Prompts consolidados: Desenvolvimento de Software e Aplicações com IA

## Front-end e Design System

**Criar design no Figma a partir de print (narrado na aula)** ([[Figma MCP]])
```text
Eu quero criar um design do YouTube no Figma utilizando esta imagem [imagem anexada]. Use esta URL [URL do arquivo Figma].
```

**Gerar HTML a partir do design recém-criado (narrado na aula)** ([[Figma MCP]])
```text
Eu quero implementar o design recém-construído, criando um arquivo HTML com o CSS já embutido.
```

**Implementar página via MCP local com link do palco (narrado na aula)** ([[Figma MCP]])
```text
Quero implementar o design desta página [nome da página] que está no link [URL] no HTML + CSS.
```

**Pedido granular com node-id (narrado na aula)** ([[Figma MCP]])
```text
Eu quero colocar um botão no sidebar da esquerda que fica nesse endereço desse frame [URL com node-id]
```

**Atualizar o CLAUDE.md do Next com /init (literal de `_claude-sessions/13-criando-fundacao-ia-nextjs-e-atualizando-a-do-nestjs.txt`)** ([[Fundação de IA do Next.js]])
```text
/init quero atualizar o @next-frontend/CLAUDE.md, mas ele já tem muitas coisas do projeto Next.js e design system, queria adicionar informações de ambiente, execução e arquitetura como o @nestjs-project/CLAUDE.md, vamos planejar isto
```

**Reordenar seções fora do bloco Figma (literal da mesma sessão)** ([[Fundação de IA do Next.js]])
```text
um trecho como o Project Structure & Path Aliases está dentro do Figma MCP, acho que deveria estar fora, analise este trecho e outros que você vê que deveriam ser reordenados
```

**Guideline de controllers do Nest (narrado na aula)** ([[Fundação de IA do Next.js]])
```text
Toda vez que eu tiver um controller, eu quero documentá-lo.
```

**Triagem das 3 frentes da base do front (narrado na aula)** ([[Fundação de IA do Next.js]])
```text
/decide Eu quero adicionar uma base de configuração do next-frontend para organizar variáveis de ambiente, tipo como fizemos para o nestjs-project. Eu quero integrar OpenAPI com o next-frontend, permitindo que o next-frontend trabalhe fortemente tipado nas chamadas HTTP do BFF para o NestJS. E também tipar as chamadas dos componentes para o BFF. Quero criar toda a base do MSW, handlers e pilares para permitir que a cada fase seja incluído as partes pertinentes da API fake e os testes no front-end possam ter a mesma experiência de fazer as chamadas para a API do NestJS.
```

**Corrigir a decisão do OpenAPI por causa do Docker (narrado na aula)** ([[Fundação de IA do Next.js]], [[Skill de Research e Decisões Técnicas]])
```text
/research Eu quero que a decisão recém criada mencione que nós vamos pegar uma cópia do OpenAPI JSON do nestjs-project. Ou seja, vamos usar o arquivo local porque estamos usando Docker. Faça as mudanças.
```

**Atualizar o CLAUDE.md após integrar o OpenAPI (narrado na aula)** ([[Fundação de IA do Next.js]])
```text
Eu quero atualizar o CLAUDE.md do next-frontend. Dado que tivemos essa mudança, temos que deixar claro que a comunicação é baseada no contrato do OpenAPI. Documente de forma breve como funciona o que fizemos.
```

**Refatorar CLAUDE.md para Claude Rules (narrado na aula, parcial)** ([[Fundação de IA do Next.js]])
```text
Analise alguns trechos do CLAUDE.md, pois parece que poderíamos criar Claude Rules para essas instruções. Só vira Claude Rules se a instrução vai afetar a leitura ou escrita do arquivo que bate com o path; sem isso, guia geral, deve permanecer no CLAUDE.md. Por exemplo, a linha 355 deve ficar porque é um guia de como lidar com os assets; já a instrução de import do Next Image é detalhe de implementação das imagens. A parte do required Figma-to-code flow é um guia de como lidar com a implementação das telas virando código, também fica no CLAUDE.md. Sobre types.gen e contracts.ts, não precisamos de uma tabela, mas é importante mencionar que essa informação guia o contrato do front-end com o BFF e com o NestJS.
```

**Implementação de uma vez (narrado na aula)** ([[Fundação de IA do Next.js]], [[Implementação de Fases com implement-phase]])
```text
/implement Faça no modo continuous mode.
```

**Ajuste de referência do Figma (narrado na aula)** ([[Inventário de Telas]])
```text
Use a referência do Figma do next-frontend CLAUDE.md.
```

**Recorte de escopo das telas (narrado na aula)** ([[Inventário de Telas]])
```text
Nós só vamos implementar as telas de cadastro da conta, tela de login e reset da senha. Pegue as telas no Figma. O restante não iremos implementar agora.
```

**Teste de extração ingênuo, Opus esforço alto (narrado na aula)** ([[Sincronização de Design Tokens]])
```text
Quero puxar os tokens de design do Figma para o globals.css. O link do Figma é este: [URL do Figma]
```

**Correção após a IA colapsar os temas (narrado na aula)** ([[Sincronização de Design Tokens]])
```text
Mas lá no Figma eu tenho os temas Light e Dark. Você fez essa implementação sem considerar outros temas.
```

**Resolver scale gaps com prefixos do Tailwind (narrado na aula)** ([[Sincronização de Design Tokens]])
```text
Destes estilos que não corresponderam, eu quero criar variáveis usando os prefixos do Tailwind em que já são geradas classes para usarmos diretamente nas páginas.
```

**Reauditoria do globals.css após o shadcn (narrado na aula)** ([[Sincronização de Design Tokens]])
```text
Depois da instalação do shadcn, ele modificou o globals.css alterando os valores das variáveis de hexadecimal para oklch. Eu quero manter o hexadecimal das variáveis, os valores já existentes, e para as variáveis adicionadas manter também o hexadecimal. Eu quero que você mantenha o @media do dark e não deixe o .dark adicionado. O :root e o @media dark precisam estar sincronizados, então faça uma auditoria para não acontecer drift entre os temas. Identifique possíveis discrepâncias na nova configuração do globals e faça um relatório de tudo.
```

**Correção dos tokens de link (narrado na aula)** ([[Sincronização de Design Tokens]])
```text
Eu quero adicionar um range de blue nos primitivos do Figma e não teríamos mais a cor link e link-dark, mas no tema light/dark pegando do mesmo range.
```

**Aplicar a mudança no Figma via MCP (narrado na aula)** ([[Sincronização de Design Tokens]])
```text
Aqui está o link. Aplique as mudanças no design.
```

**Implementar o botão (narrado na aula, junto com a URL do componente no Figma)** ([[shadcn e Componentes do Design System]])
```text
[URL do componente Button no Figma] Use tudo já existente no globals.css, que já está sincronizado, para implementar o button, que está em Button.tsx.
```

**Debug do texto invisível (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Ao renderizar o button no light, o background ficou correto, mas o texto não apareceu. Isto para o button que está no page.tsx.
```

**Gerar as regras do design system (literal de `_claude-sessions/11-criando-design-system-rules.txt`)** ([[shadcn e Componentes do Design System]])
```text
/figma:figma-create-design-system-rules para o projeto next-frontend
```

**Correção de ícones (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Quero fazer uma melhoria para o CLAUDE.md do Next front-end. Na parte de ícones: não estamos utilizando o Lucide. Serão ícones personalizados, SVG sem biblioteca externa, e os ícones estarão dentro de components/icons, porque eles serão componentes também.
```

**Remover Lucide (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Remova menções ao Lucide React. Não estamos utilizando ele.
```

**Enxugar regras em plan mode (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Eu acho que este arquivo está muito grande. Poderíamos resumi-lo mantendo a mesma qualidade. Faça uma análise disso.
```

**Reimplementar login (com Implement Design + URL da tela, narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Implemente esta tela.
```

**Debug de erro de CSS (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Ao rodar a página de login, aconteceu este erro: "<erro colado entre aspas>"
```

**Sincronizar primitivos shadcn com o Figma (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Pegue os primitivos do shadcn e veja se eles estão condizentes com o Figma e faça as modificações necessárias.
```

**Nova regra de reconciliação (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Eu quero adicionar no CLAUDE.md do Next front-end que toda vez que um primitivo do shadcn for instalado e tiver um correspondente no Figma, este precisa ser atualizado para estar condizente com o Figma.
```

**Resumir a regra (narrado na aula)** ([[shadcn e Componentes do Design System]])
```text
Eu quero que isto seja mais resumido e prático.
```

## Fundação de IA do Projeto

**Pedido usado como contraexemplo num repo sem instrução de bootstrap (narrado na aula)** ([[Ambiente e Scripts de Inicialização]])
```text
inicie o ambiente e rode os testes
```

**Script de inicialização `templates/scripts/init.sh` da skill nextjs-bootstrap (arquivo literal do repositório skills-mba)** ([[Ambiente e Scripts de Inicialização]])
```bash
#!/bin/bash

# Initialization Script
# Sets up env, database, and starts dev server with health check

PROJECT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")/.." && pwd)"
cd "$PROJECT_DIR"

PROJECT_NAME=$(basename "$PROJECT_DIR")
LOG_FILE="/tmp/${PROJECT_NAME}-server.log"
HEALTH_TIMEOUT=60
HEALTH_INTERVAL=2

echo "$PROJECT_NAME Initialization"
echo ""

# Setup env if needed
FIRST_RUN=false
if [ ! -f .env.local ]; then
  cp .env.example .env.local
  echo ".env.local created"
  FIRST_RUN=true
fi

# Read SERVER_PORT and PORT_RANGE from .env.local
SERVER_PORT=$(grep '^SERVER_PORT=' "$PROJECT_DIR/.env.local" 2>/dev/null | cut -d'=' -f2 | tr -d '"')
SERVER_PORT="${SERVER_PORT:-3000}"
PORT_RANGE=$(grep '^PORT_RANGE=' "$PROJECT_DIR/.env.local" 2>/dev/null | cut -d'"' -f2)
PORT_RANGE="${PORT_RANGE:-3000 3010}"
PORT_START=$(echo "$PORT_RANGE" | awk '{print $1}')
PORT_END=$(echo "$PORT_RANGE" | awk '{print $2}')

# On first run, find a free port if default is occupied
if [ "$FIRST_RUN" = true ] && lsof -ti:$SERVER_PORT >/dev/null 2>&1; then
  echo "Port $SERVER_PORT in use, finding a free port..."
  for P in $(seq $PORT_START $PORT_END); do
    if ! lsof -ti:$P >/dev/null 2>&1; then
      SERVER_PORT=$P
      sed -i '' "s/^SERVER_PORT=.*/SERVER_PORT=$P/" "$PROJECT_DIR/.env.local"
      sed -i '' "s|^NEXTAUTH_URL=.*|NEXTAUTH_URL=\"http://localhost:$P\"|" "$PROJECT_DIR/.env.local"
      echo "Assigned port $P"
      break
    fi
  done
fi

# Install dependencies if needed
if [ ! -d node_modules ]; then
  echo "Installing dependencies..."
  npm install
  echo ""
fi

# Read DATABASE_URL from .env.local
export DATABASE_URL=$(grep '^DATABASE_URL=' "$PROJECT_DIR/.env.local" 2>/dev/null | cut -d'=' -f2- | tr -d '"')

npx prisma generate > /dev/null 2>&1

# Setup database (PostgreSQL)
echo "Setting up PostgreSQL database..."
createdb {{PROJECT_DB_NAME}} 2>/dev/null
createdb {{PROJECT_DB_NAME}}_test 2>/dev/null
npx prisma db push
npm run db:seed 2>/dev/null
echo ""

# Check if port is already in use
PORT_PID=$(lsof -ti:$SERVER_PORT 2>/dev/null | head -1)
if [ -n "$PORT_PID" ]; then
  PROC_CWD=$(lsof -p $PORT_PID 2>/dev/null | grep cwd | awk '{print $9}')
  if [ "$PROC_CWD" == "$PROJECT_DIR" ]; then
    HTTP_STATUS=$(curl -s -o /dev/null -w "%{http_code}" --max-time 3 "http://localhost:$SERVER_PORT/" 2>/dev/null)
    if [ "$HTTP_STATUS" -ge 200 ] 2>/dev/null && [ "$HTTP_STATUS" -lt 500 ] 2>/dev/null; then
      echo "Server already running!"
      echo "URL: http://localhost:$SERVER_PORT"
      echo "PID: $PORT_PID"
      exit 0
    fi
  fi
  echo "Port $SERVER_PORT in use (PID $PORT_PID), killing..."
  kill -9 $PORT_PID 2>/dev/null
  sleep 1
fi

echo ""
echo "Starting server on port $SERVER_PORT..."

# Start server in background
PORT=$SERVER_PORT npm run dev > "$LOG_FILE" 2>&1 &
SERVER_PID=$!

# Wait for server to become healthy
ELAPSED=0
HEALTHY=false

while [ $ELAPSED -lt $HEALTH_TIMEOUT ]; do
  if ! kill -0 $SERVER_PID 2>/dev/null; then
    echo ""
    echo "ERROR: Server process died. Last 20 lines of log:"
    tail -20 "$LOG_FILE"
    exit 1
  fi

  HTTP_STATUS=$(curl -s -o /dev/null -w "%{http_code}" --max-time 3 "http://localhost:$SERVER_PORT/" 2>/dev/null)
  if [ "$HTTP_STATUS" -ge 200 ] 2>/dev/null && [ "$HTTP_STATUS" -lt 500 ] 2>/dev/null; then
    HEALTHY=true
    break
  fi

  sleep $HEALTH_INTERVAL
  ELAPSED=$((ELAPSED + HEALTH_INTERVAL))
  printf "."
done

echo ""

if [ "$HEALTHY" = true ]; then
  echo "Server is ready!"
  echo "URL: http://localhost:$SERVER_PORT"
  echo "PID: $SERVER_PID"
  echo "Log: $LOG_FILE"
else
  echo "ERROR: Server failed to become healthy after ${HEALTH_TIMEOUT}s"
  echo "Last 20 lines of log:"
  tail -20 "$LOG_FILE"
  echo ""
  echo "Killing unresponsive server (PID $SERVER_PID)..."
  kill -9 $SERVER_PID 2>/dev/null
  exit 1
fi
```

**Script de diagnóstico `templates/scripts/check.sh` (arquivo literal do repositório skills-mba)** ([[Ambiente e Scripts de Inicialização]])
```bash
#!/bin/bash

# Status Check Script
# Displays OK/PENDING/DEGRADED status for environment setup items
#
# Usage:
#   ./scripts/check.sh        # Diagnostic only (read-only)
#   ./scripts/check.sh --fix  # Diagnostic + auto-fix degraded/stopped server and orphan processes

PROJECT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")/.." && pwd)"
PROJECT_NAME=$(basename "$PROJECT_DIR")
HEALTH_TIMEOUT=3
AUTO_FIX=false
SERVER_STATUS="none"

SERVER_PORT=$(grep '^SERVER_PORT=' "$PROJECT_DIR/.env.local" 2>/dev/null | cut -d'=' -f2 | tr -d '"')
SERVER_PORT="${SERVER_PORT:-3000}"

if [ "$1" == "--fix" ]; then
  AUTO_FIX=true
fi

echo "$PROJECT_NAME Status Check"
echo ""

if [ -f "$PROJECT_DIR/.env.local" ]; then
  echo "[OK] .env.local configured"
else
  echo "[PENDING] .env.local not found"
fi

DATABASE_URL=$(grep '^DATABASE_URL=' "$PROJECT_DIR/.env.local" 2>/dev/null | cut -d'=' -f2- | tr -d '"')
if [ -n "$DATABASE_URL" ]; then
  echo "[OK] Database configured (PostgreSQL)"
else
  echo "[PENDING] DATABASE_URL not configured"
fi

PORT_PID=$(lsof -ti:$SERVER_PORT 2>/dev/null | head -1)
if [ -n "$PORT_PID" ]; then
  PROC_CWD=$(lsof -p $PORT_PID 2>/dev/null | grep cwd | awk '{print $9}')
  if [ "$PROC_CWD" == "$PROJECT_DIR" ]; then
    HTTP_STATUS=$(curl -s -o /dev/null -w "%{http_code}" --max-time $HEALTH_TIMEOUT "http://localhost:$SERVER_PORT/" 2>/dev/null)
    if [ "$HTTP_STATUS" -ge 200 ] 2>/dev/null && [ "$HTTP_STATUS" -lt 500 ] 2>/dev/null; then
      echo "[OK] Development server running"
      echo "     URL: http://localhost:$SERVER_PORT"
      echo "     Health: responding (HTTP $HTTP_STATUS)"
      SERVER_STATUS="healthy"
    else
      echo "[DEGRADED] Development server on port $SERVER_PORT (PID $PORT_PID) is NOT responding"
      echo "           HTTP status: ${HTTP_STATUS:-timeout}"
      SERVER_STATUS="degraded"
    fi
  else
    echo "[PENDING] Development server not running (port $SERVER_PORT used by another process)"
    SERVER_STATUS="pending"
  fi
else
  echo "[PENDING] Development server not running"
  SERVER_STATUS="pending"
fi

ORPHAN_COUNT=0
for PROC_NAME in playwright jest; do
  PIDS=$(pgrep -f "$PROC_NAME.*$PROJECT_DIR" 2>/dev/null)
  if [ -n "$PIDS" ]; then
    COUNT=$(echo "$PIDS" | wc -l | tr -d ' ')
    ORPHAN_COUNT=$((ORPHAN_COUNT + COUNT))
  fi
done

if [ "$ORPHAN_COUNT" -gt 0 ]; then
  echo ""
  echo "[WARNING] $ORPHAN_COUNT orphan test process(es) detected (playwright/jest)"
fi

if [ "$AUTO_FIX" = true ]; then
  FIXED_SOMETHING=false

  if [ "$ORPHAN_COUNT" -gt 0 ]; then
    echo ""
    echo "Fixing: killing orphan processes..."
    "$PROJECT_DIR/scripts/down.sh" --force 2>/dev/null
    FIXED_SOMETHING=true
    if [ "$SERVER_STATUS" == "healthy" ]; then
      sleep 1
      PORT_PID=$(lsof -ti:$SERVER_PORT 2>/dev/null | head -1)
      if [ -z "$PORT_PID" ]; then
        SERVER_STATUS="pending"
      fi
    fi
  fi

  if [ "$SERVER_STATUS" == "degraded" ]; then
    echo ""
    echo "Fixing: killing degraded server and restarting..."
    "$PROJECT_DIR/scripts/down.sh" --force 2>/dev/null
    rm -rf "$PROJECT_DIR/.next" 2>/dev/null
    echo ""
    "$PROJECT_DIR/scripts/init.sh"
    FIXED_SOMETHING=true
  fi

  if [ "$SERVER_STATUS" == "pending" ]; then
    echo ""
    echo "Fixing: cleaning .next and starting server..."
    rm -rf "$PROJECT_DIR/.next" 2>/dev/null
    "$PROJECT_DIR/scripts/init.sh"
    FIXED_SOMETHING=true
  fi

  if [ "$FIXED_SOMETHING" = false ] && [ "$SERVER_STATUS" == "healthy" ]; then
    echo ""
    echo "Nothing to fix. All good."
  fi
else
  if [ "$SERVER_STATUS" != "healthy" ] || [ "$ORPHAN_COUNT" -gt 0 ]; then
    echo ""
    echo "Run './scripts/check.sh --fix' to auto-fix issues"
  fi
fi
```

**Script de shutdown `templates/scripts/down.sh` (arquivo literal do repositório skills-mba)** ([[Ambiente e Scripts de Inicialização]])
```bash
#!/bin/bash

# Shutdown Script
#
# Usage:
#   ./scripts/down.sh                # Stop server (graceful)
#   ./scripts/down.sh --force        # Kill server + orphan processes (playwright, jest, next-server)
#   ./scripts/down.sh --clean        # Stop server + remove .env.local, node_modules, .next, .turbo
#   ./scripts/down.sh --force --clean # Force kill everything + clean

PROJECT_DIR="$(cd "$(dirname "${BASH_SOURCE[0]}")/.." && pwd)"
PROJECT_NAME=$(basename "$PROJECT_DIR")

# Read SERVER_PORT from .env.local
SERVER_PORT=$(grep '^SERVER_PORT=' "$PROJECT_DIR/.env.local" 2>/dev/null | cut -d'=' -f2 | tr -d '"')
SERVER_PORT="${SERVER_PORT:-3000}"

# Parse flags
FORCE=false
CLEAN=false
for arg in "$@"; do
  case "$arg" in
    --force) FORCE=true ;;
    --clean|-clean) CLEAN=true ;;
  esac
done

echo "$PROJECT_NAME Shutdown"
echo ""

if [ "$FORCE" = true ]; then
  KILLED=false

  PORT_PIDS=$(lsof -ti:$SERVER_PORT 2>/dev/null)
  if [ -n "$PORT_PIDS" ]; then
    echo "$PORT_PIDS" | xargs kill -9 2>/dev/null
    echo "Killed process(es) on port $SERVER_PORT"
    KILLED=true
  fi

  PLAYWRIGHT_PIDS=$(pgrep -f "playwright.*$PROJECT_DIR" 2>/dev/null)
  if [ -n "$PLAYWRIGHT_PIDS" ]; then
    echo "$PLAYWRIGHT_PIDS" | xargs kill -9 2>/dev/null
    COUNT=$(echo "$PLAYWRIGHT_PIDS" | wc -l | tr -d ' ')
    echo "Killed $COUNT orphan Playwright process(es)"
    KILLED=true
  fi

  JEST_PIDS=$(pgrep -f "jest.*$PROJECT_DIR" 2>/dev/null)
  if [ -n "$JEST_PIDS" ]; then
    echo "$JEST_PIDS" | xargs kill -9 2>/dev/null
    COUNT=$(echo "$JEST_PIDS" | wc -l | tr -d ' ')
    echo "Killed $COUNT orphan Jest process(es)"
    KILLED=true
  fi

  NEXT_PIDS=$(pgrep -f "next-server.*$PROJECT_DIR" 2>/dev/null)
  if [ -n "$NEXT_PIDS" ]; then
    echo "$NEXT_PIDS" | xargs kill -9 2>/dev/null
    COUNT=$(echo "$NEXT_PIDS" | wc -l | tr -d ' ')
    echo "Killed $COUNT orphan Next.js server process(es)"
    KILLED=true
  fi

  if [ "$KILLED" = false ]; then
    echo "No processes found"
  fi
else
  PORT_PID=$(lsof -ti:$SERVER_PORT 2>/dev/null | head -1)
  if [ -n "$PORT_PID" ]; then
    PROC_CWD=$(lsof -p $PORT_PID 2>/dev/null | grep cwd | awk '{print $9}')
    if [ "$PROC_CWD" == "$PROJECT_DIR" ]; then
      kill -9 $PORT_PID 2>/dev/null
      echo "Stopped server on port $SERVER_PORT"
    else
      echo "Port $SERVER_PORT is not this project's server"
    fi
  else
    echo "No server running on port $SERVER_PORT"
  fi
fi

if [ "$CLEAN" = true ]; then
  echo ""
  [ -f "$PROJECT_DIR/.env.local" ] && rm "$PROJECT_DIR/.env.local" && echo ".env.local removed"
  [ -d "$PROJECT_DIR/node_modules" ] && rm -rf "$PROJECT_DIR/node_modules" && echo "node_modules removed"
  [ -d "$PROJECT_DIR/.next" ] && rm -rf "$PROJECT_DIR/.next" && echo ".next removed"
  [ -d "$PROJECT_DIR/.turbo" ] && rm -rf "$PROJECT_DIR/.turbo" && echo ".turbo removed"
  [ -d "$PROJECT_DIR/.playwright-cli" ] && rm -rf "$PROJECT_DIR/.playwright-cli" && echo ".playwright-cli removed"
fi

echo ""
echo "Done"
```

**Variáveis lidas pelos scripts `templates/env-example.txt` (arquivo literal do repositório skills-mba)** ([[Ambiente e Scripts de Inicialização]], [[Bootstrap de Projetos Greenfield]])
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

**Regra operacional do arquivo de inicialização (narrado na aula)** ([[Arquivos de Inicialização do Agente]])
```text
Sempre rode comandos dentro do container, omitindo o -it
```

**Linha de abertura de exemplo (narrado na aula)** ([[Arquivos de Inicialização do Agente]])
```text
API REST em FastAPI para autenticação de usuários
```

**Regras restritivas de exemplo (narrado na aula)** ([[Arquivos de Inicialização do Agente]])
```text
Nunca faça push na main.
Revise a descrição do commit antes de enviar.
Evite testes redundantes.
```

**Git policy (narrado na aula)** ([[Arquivos de Inicialização do Agente]])
```text
Nunca use force push na main ou master.
Nunca pule hooks com --no-verify.
Só use amend quando for realmente seguro.
Use conventional commits.
```

**Fim de tarefa custosa para alimentar o arquivo (narrado na aula)** ([[Arquivos de Inicialização do Agente]])
```text
Liste de forma extremamente concisa os pontos em que você encontrou dificuldade nesta tarefa e que poderiam entrar no CLAUDE.md para evitar erros futuros.
```

**Testes do sub CLAUDE.md com Haiku (narrado na aula)** ([[Arquivos de Inicialização do Agente]], [[MCPs do Projeto Context7 e Postgres]])
```text
Inicie o ambiente.
```

**Análise do progresso da fase para melhorar a fundação (sessão real do repositório, `_claude-sessions/10-melhorias-na-fundacao-ia.txt`)** ([[Arquivos de Inicialização do Agente]])
```text
dado o arquivo de progress da fase 02, olhando as obsevações de cada SI
implementado, pense em pontos que poderíamos melhorar no CLAUDE.md global e
no CLAUDE.md do nestjs-project e nas .claude/rules
permitindo que tenhamos execuções mais assertivas
```

**CLAUDE.md global do Streamtube (arquivo literal do repositório mba-ia-greenfield-project, até a seção Agent Skill Usage)** ([[Arquivos de Inicialização do Agente]])
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

**Sub CLAUDE.md `nestjs-project/CLAUDE.md` (arquivo literal do repositório mba-ia-greenfield-project)** ([[Arquivos de Inicialização do Agente]])
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

**Template de CLAUDE.md da skill nextjs-bootstrap `templates/claude-md.md` (arquivo literal do repositório skills-mba)** ([[Arquivos de Inicialização do Agente]])
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

**Refino da description da skill NestJS em plan mode (narrado na aula)** ([[Curadoria de Skills]])
```text
A skill NestJS de boas práticas deve ser chamada quando estivermos planejando e/ou implementando features que envolvem o NestJS. No momento, sua descrição é muito genérica. Analise a description da skill para ver o que é preciso melhorar. Também queremos continuar reforçando o fundamento da skill ser carregada on-demand, especificando cenários onde ela não deveria ser carregada. Também precisa mudar o "When to apply".
```

**Correção da proposta de description (narrado na aula)** ([[Curadoria de Skills]])
```text
A description precisa ter em média 100 tokens. E você colocou no not trigger questões não relevantes que não carregariam a skill. Pense novamente.
```

**Teste de carregamento em plan mode (narrado na aula)** ([[Curadoria de Skills]])
```text
Planeje a implementação da fase 2. Use as skills disponíveis.
```

**Refatoração da skill TypeORM em plan mode (narrado na aula)** ([[Curadoria de Skills]])
```text
A skill de TypeORM não está seguindo as boas práticas do padrão de skills do guia de skills da Anthropic. Ela tem 600 linhas, não tem estrutura modular, referências lazy, nem índice leve. Na description precisamos reforçar o que está sendo dito na outra skill que já construímos, sobre o que queremos que seja disparada quando estivermos planejando e/ou implementando features que envolvem banco de dados. E a description deve ter 100 tokens.
```

**Correção do plano de refatoração (narrado na aula)** ([[Curadoria de Skills]])
```text
Não podemos referenciar documentos em outras pastas que não sejam dentro da própria skill. Não use nada da skill de boas práticas.
```

**Teste com proibição de outras branches (narrado na aula)** ([[Curadoria de Skills]])
```text
Planeje a implementação da fase 2. Use as skills disponíveis. Não leia outras branches do git.
```

**Confronto rules x skills (sessão real do repositório, `_claude-sessions/01-correcao-contradicoes-rules-vs-skills.txt`)** ([[Curadoria de Skills]])
```text
confronte as rules com as skills disponíveis para ver se há contradição ou se
são complementares
```

**Decisões sobre as contradições encontradas (sessão real do repositório)** ([[Curadoria de Skills]])
```text
Para o  1. não quero mudar o exemplo da skill, pois podemos decidir usar
outra estratégia para os ids futuramente, e a skill é um guia

Para o 2. sim, alinhar com a skill

Para o 3. sim, alinhar com a skill

Para o 4. O exemplo na skill deve mudar. Isto de orquestração de service não é
necessário, o ponto é que
o controller deve apenas invocar a camada de serviços, as vezes ele pode usar
um ou mais serviços para
consultar alguma coisas e decidir invocar um service que vai mudar o estado do
sistema, não significa que
 ele tem que sempre chamar um service e responder alguma coisa, não é isto, mas
 todo cerne de regras de
negócio ficam no service. Então, precisamos corrigir a skill neste ponto.

Para o 5. Sim, não quero expor entities diretamente como DTO, isto serve para
segurança. Acho que reestruturar é melhor
```

**Hook que lembra de ativar skills `.claude/settings.json` (arquivo literal do repositório)** ([[Curadoria de Skills]])
```json
{
  "hooks": {
    "UserPromptSubmit": [
      {
        "hooks": [
          {
            "type": "command",
            "command": "echo 'Identify and activate relevant skills for this task.'"
          }
        ]
      }
    ]
  },
  "enabledPlugins": {
    "figma@claude-plugins-official": true
  }
}
```

**Uso do Context7 por intenção (narrado na aula)** ([[MCPs do Projeto Context7 e Postgres]])
```text
Quero implementar a autenticação do projeto, use o Context7.
```

**Seção "Library Documentation Lookup" do CLAUDE.md global (arquivo literal do repositório mba-ia-greenfield-project)** ([[MCPs do Projeto Context7 e Postgres]])
```markdown
## Library Documentation Lookup

Before implementing any feature, you MUST use the **context7** MCP tool to look up the relevant library APIs and official documentation.

Always:

- Check the installed library version in the project manifest
- Retrieve the corresponding documentation using context7
- Cross-reference APIs to avoid deprecated or incompatible patterns
- Follow the official documentation over training data

Skip documentation lookup only for trivial operations such as:

- Variable declarations
- Basic control flow
- Simple CRUD using established project patterns

If a library is involved and there is uncertainty, documentation lookup is mandatory.
If the documentation returned does not match the installed version, flag the discrepancy before proceeding.
```

**Instalação do Context7 no escopo do usuário (comando da página de instalação do Context7 para Claude Code, conforme a aula)** ([[MCPs do Projeto Context7 e Postgres]])
```bash
claude mcp add --scope user context7 -- npx -y @upstash/context7-mcp --api-key <SUA_API_KEY>
```

**Configuração de MCPs do projeto `.mcp.json.example` (arquivo literal do repositório; a entrada `figma` foi adicionada depois, no bloco de design system)** ([[MCPs do Projeto Context7 e Postgres]])
```json
{
  "mcpServers": {
    "postgres": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-postgres",
        "postgresql://streamtube:streamtube@localhost/streamtube"
      ]
    },
    "figma": {
      "type": "http",
      "url": "http://127.0.0.1:3845/mcp"
    }
  }
}
```

**Transformar o erro de localhost em regra (sessão real do repositório, `_claude-sessions/03-atualizacao-claude-md-info-docker.txt`)** ([[Rules do Claude Code]], [[Higiene do Workflow com IA]])
```text
na sua última implementação, você usou localhost como host para conectar no
banco de dados, mas estamos em containers docker, o localhost diz respeito
somente ao próprio container.
quero atualizar as rules, para que você não cometa este mesmo erro
```

**Gerenciar a memória criada pela IA (sessão real do repositório)** ([[Rules do Claude Code]], [[Higiene do Workflow com IA]])
```text
me mostre as memorias que você tem
```

**Estrutura do front matter de uma rule (reconstituído a partir da aula)** ([[Rules do Claude Code]])
```markdown
---
paths:
  - "nestjs-project/src/**/*.ts"
---
# regras aqui (sem este front matter a rule é global)
```

**Front matters reais das rules do projeto (arquivos literais de `.claude/rules/`, só o cabeçalho)** ([[Rules do Claude Code]])
```yaml
# auth-jwt.md
paths:
  - 'nestjs-project/src/auth/**'
description: 'JWT and refresh-token rotation rules'
# nestjs-common-conventions.md
paths:
  - 'nestjs-project/src/**/*.ts'
description: 'NestJS common conventions'
# nestjs-controllers.md
paths:
  - 'nestjs-project/**/*.controller.ts'
description: 'Controller conventions - REST compliance, no silent errors, prefer exception filters over try/catch'
# nestjs-dtos.md
paths:
  - 'nestjs-project/**/*.dto.ts'
description: 'DTO conventions for input validation and data transfer'
# nestjs-entities.md
paths:
  - 'nestjs-project/**/*.entity.ts'
description: 'TypeORM entity conventions for database models'
# nestjs-layer-separation.md
paths:
  - 'nestjs-project/**/*.controller.ts'
  - 'nestjs-project/**/*.guard.ts'
  - 'nestjs-project/**/*.interceptor.ts'
  - 'nestjs-project/**/*.pipe.ts'
  - 'nestjs-project/**/*.filter.ts'
description: 'Layer separation - business logic belongs exclusively in services; controllers, guards, interceptors, pipes, and filters must delegate to services'
# nestjs-modules.md
paths:
  - 'nestjs-project/src/**/*.module.ts'
description: 'NestJS module structure conventions'
# nestjs-services.md
paths:
  - 'nestjs-project/**/*.service.ts'
description: 'Service layer error handling - errors must always propagate to upper layers'
# nestjs-testing.md
paths:
  - 'nestjs-project/**/*.spec.ts'
  - 'nestjs-project/**/*.integration-spec.ts'
  - 'nestjs-project/**/*.e2e-spec.ts'
  - 'nestjs-project/test/**'
description: 'Testing conventions for NestJS unit, integration, and e2e tests'
# typeorm-migrations.md
paths:
  - 'nestjs-project/**/migrations/**'
  - 'nestjs-project/**/*data-source.ts'
description: 'Database migration safety rules'
# typeorm-queries.md
paths:
  - 'nestjs-project/src/**/*.service.ts'
  - 'nestjs-project/src/**/*.repository.ts'
description: 'TypeORM query pitfalls - silent footguns when reading/writing through repositories'
# typescript-strict.md
paths:
  - 'nestjs-project/src/**/*.ts'
  - 'nestjs-project/test/**/*.ts'
description: 'TypeScript strictness rules - keep tsc --noEmit clean at all times'
```

**Rule `nestjs-common-conventions.md` (arquivo literal)** ([[Rules do Claude Code]])
```markdown
---
paths:
  - 'nestjs-project/src/**/*.ts'
description: 'NestJS common conventions'
---

# NestJS Standard Conventions

## Naming

| Artifact   | File Name              | Class Name          |
|---|---|---|
| Module     | `users.module.ts`      | `UsersModule`       |
| Service    | `users.service.ts`     | `UsersService`      |
| Controller | `users.controller.ts`  | `UsersController`   |
| Entity     | `user.entity.ts`       | `User`              |
| DTO        | `create-user.dto.ts`   | `CreateUserDto`     |
| Guard      | `auth.guard.ts`        | `AuthGuard`         |
| Constants  | `auth.constants.ts`    | (named exports)     |

- **Files:** kebab-case
- **Classes:** PascalCase
- **Modules:** pluralize (`UsersModule`); **Entities:** singularize (`User`)
- **Variables/Functions:** camelCase


## Dependency Injection

- Inject via constructor: `constructor(private readonly service: SomeService) {}`
- Never use `new` to instantiate services or repositories
- Use `private readonly` by default; `protected` only for subclasses
- Use `@Inject()` only when needed: for custom providers with string/symbol tokens (e.g., `@Inject('CONFIG')`) or NestJS symbols (e.g., `APP_GUARD`). For standard class-based providers, constructor injection without `@Inject()` is sufficient

## Async/Await

- Every I/O method: `async` with explicit `Promise<T>` return type
- Use `await`, never `.then()` / `.catch()`
- No un-awaited Promises

## Constants

- Repeated strings/numbers in `<module>.constants.ts` (e.g., `auth.constants.ts`)
- Always `as const` for literal types
- Group related constants: `AUTH_COOKIES = { ACCESS_TOKEN: '...', ... } as const`
- Never duplicate string literals across files
```

**Rule `nestjs-modules.md` (arquivo literal)** ([[Rules do Claude Code]])
```markdown
---
paths:
  - 'nestjs-project/src/**/*.module.ts'
description: 'NestJS module structure conventions'
---

# NestJS Module Structure

- `@Module()` property order: `imports` → `controllers` → `providers` → `exports`
- `TypeOrmModule.forFeature([...])` goes in domain module `imports`, never in `AppModule`
- **Every entity must be registered in `TypeOrmModule.forFeature([Entity])` of its owning module.** Even with `autoLoadEntities: true`, the entity is only discovered if some module imports it via `forFeature`. Forgetting this does not cause a clear error: the app starts, but any repository injection or query against the missing entity fails at runtime (or, worse, the entity is silently absent from migrations). When you create or move an entity, immediately update the owning module's imports.
- `AppModule` only contains global infrastructure (ConfigModule, TypeOrmModule) and domain modules - no business providers
- `exports` only for dependencies other modules need; don't export by default
- When a module exposes shared infrastructure (e.g., `JwtModule.registerAsync`, repository providers), it must `exports` them - and consumer test modules must include the same registration. Test modules are NestJS modules: missing imports here cause "Nest can't resolve dependencies" errors that look like production bugs but are test-setup bugs.
```

**Rule `nestjs-entities.md` (arquivo literal)** ([[Rules do Claude Code]])
```markdown
---
paths:
  - 'nestjs-project/**/*.entity.ts'
description: 'TypeORM entity conventions for database models'
---

# Entity Rules

## Naming and Structure

- Always pass an explicit table name to `@Entity('table_name')` - do not rely on auto-generated names
- Use UUID as primary key: `@PrimaryGeneratedColumn('uuid')`
- Always include timestamp columns: `@CreateDateColumn()` and `@UpdateDateColumn()`

## Column Conventions

- Sensitive fields (passwords, tokens) must use `{ select: false }` to exclude from default queries
- Use `{ unique: true }` for naturally unique fields (email, slug)
- Define explicit column types when the default mapping is ambiguous

## Relationships

- Always define both sides of a relationship (e.g., `@OneToMany` + `@ManyToOne`)
- Prefer explicit relation loading (`relations: [...]`) - load only what each query needs
- Use eager loading only for low-cardinality, always-needed relations (e.g., `user.role`)
- Use lazy loading only when the relation is rarely accessed and the `Promise<>` type is acceptable

## Schema Changes

- Never modify an entity without creating a corresponding migration
- Never use `synchronize: true` in production - only in early development if at all
- Generate migrations via TypeORM CLI, not by hand
```

**Rule `nestjs-services.md` (arquivo literal, já ajustada após o confronto com as skills: escopo HTTP vs background)** ([[Rules do Claude Code]])
````markdown
---
paths:
  - 'nestjs-project/**/*.service.ts'
description: 'Service layer error handling - errors must always propagate to upper layers'
---

# Service Error Handling Rules

## Never Swallow Errors

Services must never catch an error and silently ignore it. Every error must either:
1. **Propagate naturally** - don't catch it at all, let it bubble up
2. **Be re-thrown** - catch to add context or transform, then re-throw

A `try/catch` that logs and returns `null`, `undefined`, `false`, or an empty value instead of throwing is a silent failure. This hides bugs and makes debugging extremely difficult.

## Bad: swallowing the error

```typescript
async findById(id: string): Promise<User | null> {
  try {
    return await this.userRepository.findOneByOrFail({ id });
  } catch (error) {
    this.logger.error('User not found', error);
    return null; // caller has no idea something went wrong
  }
}
```

## Good: let it propagate or re-throw with context

```typescript
async findById(id: string): Promise<User> {
  const user = await this.userRepository.findOneBy({ id });
  if (!user) {
    throw new EntityNotFoundException('User', id);
  }
  return user;
}
```

## Good: catch, enrich, re-throw

```typescript
async createChannel(dto: CreateChannelDto): Promise<Channel> {
  try {
    return await this.channelRepository.save(dto);
  } catch (error) {
    if (error.code === '23505') {
      throw new DuplicateEntityException('Channel', 'name');
    }
    throw error; // unknown errors propagate as-is
  }
}
```

## The Rule

### Request lifecycle (services invocados por controllers)

- `catch` blocks must always end with a `throw` - either the original error or a more specific one
- The only exception is when the catch is intentionally converting an error into a valid domain result (e.g., `findOneBy` returning `null` is not an error - a `try/catch` that swallows `findOneByOrFail` is)
- Throw domain exceptions (custom `Error` subclasses) - never throw NestJS HTTP exceptions (`NotFoundException`, `ConflictException`, etc.) from services. Services must not be aware of the transport layer. Exception filters are responsible for mapping domain exceptions to HTTP responses
- Logging inside a catch is fine, but logging is not a substitute for throwing

### Background tasks, event handlers e cron jobs

- In these contexts, rethrowing would crash the process. `catch` blocks should log the error and optionally queue for retry or send to a dead letter queue
- These are the **only** contexts where catch-and-log without rethrowing is acceptable
````

## Skills

**SKILL.md da nextjs-bootstrap (literal, repositório skills-mba)** ([[Bootstrap de Projetos Greenfield]])
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

**Trecho do template `claude-md.md`: scripts e regras (literal; arquivo completo de 179 linhas em `nextjs-bootstrap/templates/claude-md.md`, com seções Project Overview, Environment Setup, Tech Stack, Project Structure, Testing, Database, Development, Rules)** ([[Bootstrap de Projetos Greenfield]])
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

**Pedido após o bootstrap (narrado na aula)** ([[Bootstrap de Projetos Greenfield]])
```text
Inicie o sistema.
```

**Prompt "cru" usado como contraexemplo no StreamTube, em plan mode (narrado na aula)** ([[Bootstrap de Projetos Greenfield]])
```text
Implemente a fase 2 do documento, a parte da autenticação. Quero implementar toda a fase, mas somente o back-end. Pense numa boa arquitetura, use boas práticas de Node.js e TypeScript e crie todos os testes possíveis, valide todos os cenários.
```

**One-shot para criar servidor MCP com a MCP Builder (narrado na aula)** ([[Criando Skills]])
```text
Criar um servidor MCP em TypeScript, onde, dentro dessa pasta guides-mcp, eu crio guias de algumas linguagens de programação com boas práticas de desenvolvimento. O servidor vai ser capaz de localizar, listar, criar algumas tools para listar os guias disponíveis, fazer uma busca no conteúdo sobre um guia e fazer perguntas específicas sobre uma linguagem baseada no conteúdo daquele guia. Fazer uma evaluation de qualidade pra garantir que o servidor tá funcionando.
```

**Exemplo de uso da MCP Builder com chamada explícita da skill (narrado na aula)** ([[Criando Skills]])
```text
crie um MCP para integrar com a API dos Correios
```

**Página de boas-vindas com a skill de design system (narrado na aula, digitado "de qualquer jeito")** ([[Criando Skills]])
```text
Seu objetivo é criar uma página web de boas-vindas ao aluno que acessar a plataforma de cursos da Full Cycle. Use a identidade visual da plataforma para fazer isso. Mantenha um menu no topo, igual da plataforma, no centro uma página de mensagem linda de boas-vindas. Pode fazer normalmente usando HTML, Tailwind se você quiser, para facilitar. Disponibilize essa página em um servidor simples, em Python, na porta 8822, para eu visualizar, ou seja, localhost:8822. O arquivo é index.html.
```

**Pedido base para a Skill Creator criar a Critical Review (narrado/digitado na aula)** ([[Criando Skills]])
```text
Eu gostaria de criar uma skill que valide inconsistências gerais dentro do codebase / docs dos nossos projetos.
Busque por contradições: por exemplo, o código faz X, mas a especificação diz que faz Y.
Identifique ambiguidades: termos vagos, critérios indefinidos ou múltiplas interpretações possíveis.
Busque lacunas lógicas: especialmente em explicações passo a passo que apresentem um buraco no meio do raciocínio.
```

**Exemplos de trigger fornecidos à Skill Creator (narrado na aula)** ([[Criando Skills]])
```text
Revise esse documento / encontre problemas / compare o código com a especificação / Busque por contradições, ambiguidades ou qualquer coisa que gere inconsistência entre os arquivos.
```

**Pedido que acionou a Critical Review (narrado na aula)** ([[Criando Skills]])
```text
Busque por contradições, ambiguidades nos documentos dentro da pasta @.codekit e verifique se ela não possui inconsistências, problemas, entre outros.
```

**Tradução da skill gerada** ([[Criando Skills]])
```text
Traduza o @skill.md para inglês.
```

**Sequência de pedidos com a Next.js Project Setup (narrado na aula)** ([[Criando Skills]])
```text
Gostaria de fazer o setup de um novo projeto em Next.js.
```

**README do repositório skills-mba (literal)** ([[Ecossistema de Skills]])
```text
# Skills

Skills based on examples from the **MBA in Software Engineering with AI** by Full Cycle. Each skill extends the AI agent's capabilities with specialized workflows and domain knowledge.

---

## nextjs-bootstrap

Bootstraps a new Next.js project with standard architecture: App Router, TypeScript strict, Prisma 7, PostgreSQL, NextAuth v5, and Tailwind CSS 4. Generates a complete CLAUDE.md, operational scripts (init, down, check, watch, tmux, deploy), and project structure ready for AI-assisted development.

**When to use:** "new project", "bootstrap", "scaffold", "setup nextjs", "create app from scratch".

---

## e2e-nav-test

Generates and executes E2E test cases for any web application (SPA, server-rendered, or hybrid). Analyzes the codebase to discover routes, components, auth flows, forms, modals, roles/permissions, and navigation patterns, producing a structured test-cases document with dependency trees and checklists. Works with any framework: Next.js, React, Vue, Angular, Django, Laravel, Rails, Flask, Go, and more.

**When to use:** "test navigation", "generate e2e tests", "test user flows", "create test cases", "map user journeys".

---

## test-guide

Guide for writing and auditing tests across all layers (unit, integration, and E2E). Defines what is worth testing and what is not, mock health criteria, and the purpose of each layer. Use when writing new tests, deciding what to test at each layer, choosing between unit vs integration vs E2E, auditing existing tests, cleaning up redundant tests, or identifying missing coverage.

**When to use:** "write tests", "add tests", "create unit/integration/e2e tests", "audit tests", "review test quality".
```

**Instrução para induzir a leitura de referências no CLAUDE.md/AGENTS.md (narrado na aula)** ([[Fundamentos de Skills]])
```text
Important: before starting any activity, understand what docs below are relevant for your task and read them first.
```

**Front matter real com description de trigger amplo (e2e-nav-test, repositório skills-mba)** ([[Fundamentos de Skills]])
```text
---
name: e2e-nav-test
description: >
  Generate and execute E2E test cases for any web application - SPA, server-rendered,
  or hybrid. Analyzes the codebase to discover routes, components, auth flows, forms,
  modals, roles/permissions, and navigation patterns, then produces a structured
  test-cases document with dependency trees and todo checklists. Works with any
  framework: Next.js, React, Vue, Angular, Django, Laravel, Rails, Flask, Go,
  Symfony, Spring, ASP.NET, PHP, and more. Use this skill whenever the user asks to
  "test navigation", "generate e2e tests", "test user flows", "create test cases",
  "run navigation tests", "e2e test plan", "check all flows", "test my app flows",
  "map user journeys", "test my app", or anything related to end-to-end flow testing.
  Also trigger when the user mentions "test-cases.md", "flow coverage", or
  "navigation coverage". Even if they just say "test my app" or "run e2e",
  this skill is likely what they need.
---
```

**Front matter real com lista "Triggers on" (test-guide, repositório skills-mba)** ([[Fundamentos de Skills]])
```text
---
name: test-guide
description: >
  Guide for writing and auditing tests across all layers - unit, integration, and E2E.
  Use this skill when writing new tests, creating test files, deciding what to test at each layer,
  choosing between unit vs integration vs E2E, and also when auditing existing tests, cleaning up
  redundant tests, or finding missing coverage. Triggers on: "write tests", "add tests for",
  "create unit tests", "create integration tests", "create e2e tests", "should I test this",
  "what layer should this test be", "audit tests", "test cleanup", "which tests can I delete",
  "what tests am I missing", "review test quality".
---
```

## Testes com IA

**Auditoria de edge cases ausentes em plan mode, sessão limpa (narrado na aula)** ([[Edge Cases e Test Guidelines]])
```text
Avalie todos os testes do sistema, incluindo front-end e back-end. Identifique os testes automatizados e os principais aspectos que esses testes estão cobrindo. Porém, baseado nesse mapeamento, verifique testes de edge cases, ou seja, testes que tragam um possível caminho triste, que não estão cobertos pelos testes atuais, como Error Handling, Rate Limiting, Segurança, fluxos principais que podem ter exceções não tratadas, entre outros. Explore o código, entenda seus principais fluxos, comportamentos e possíveis problemas que podem acontecer e que não estão previstos no código, validações ou mesmo a nível de feature. Categorize esses tipos de teste, incluindo os de back-end e front-end, e traga exatamente o que não está coberto e o motivo pelo qual deveríamos implementar. No final, faça um resumo e traga a quantidade esperada de novos testes que deverão ser criados apenas nesses tipos de situação.
```

**Prompt gerado pela skill para o subagente de unit tests do back-end (narrado parcialmente na aula, o original é maior)** ([[Edge Cases e Test Guidelines]])
```text
You are a test quality auditor. Read every test file in backend/tests/unit and classify each individual test as KEEP, REMOVE, or note as MISSING TESTS. Removal criteria: framework/ORM persistence tests, validation pass-through, ...
```

**Skill test-guide (literal do repositório, `skills-mba/test-guide/SKILL.md`)** ([[Edge Cases e Test Guidelines]])
````markdown
---
name: test-guide
description: >
  Guide for writing and auditing tests across all layers - unit, integration, and E2E.
  Use this skill when writing new tests, creating test files, deciding what to test at each layer,
  choosing between unit vs integration vs E2E, and also when auditing existing tests, cleaning up
  redundant tests, or finding missing coverage. Triggers on: "write tests", "add tests for",
  "create unit tests", "create integration tests", "create e2e tests", "should I test this",
  "what layer should this test be", "audit tests", "test cleanup", "which tests can I delete",
  "what tests am I missing", "review test quality".
---

# Test Guide

Write tests that verify the system behaves correctly at each layer. Each test must have a clear purpose - what behavior it proves and at which boundary. Go beyond happy paths: test edge cases, error scenarios, and boundary conditions where bugs actually hide.

---

## The Criteria

These rules apply whether you're writing new tests or auditing existing ones.

### Worth testing

- **Business logic with branching** - conditionals, state machines, permission checks, domain rules
- **Security boundaries** - auth, authorization, rate limiting, input sanitization, xss, csrf, sql injection, etc.
- **Data integrity** - transformations, serialization, migrations, calculations where wrong output = corrupt data
- **Error handling** - what happens when external services fail, database is down, user is unauthorized
- **Critical user flows** - auth, payment, upload, core CRUD that users depend on
- **Race conditions** - concurrent operations, optimistic locking, queue processing
- **Boundary/edge cases** - null, empty, max values, off-by-one, overflow conditions
- **External integrations** - webhooks, unexpected API responses, timeouts, contract mismatches

### NOT worth testing

- **Framework behavior** - Trust what the framework guarantees: rendering, routing, request handling, ORM persistence, loading states. If the framework works, these work. Test your logic on top of it.
- **Validation passthrough** - Validation libraries already enforce their rules. One test proving the validator is wired is enough - not one per rule on the same code path. Keep one happy-path test per validator to prove valid input passes, but don't duplicate every rejection rule.
- **Mirror tests** - When the assertion copies the return value of the implementation. The test can never catch a bug - it can only break when you intentionally change the code.
- **Duplicate coverage across layers** - Each test must catch a bug no other test catches. If a behavior is verified at a higher layer, a lower-layer test for the same path adds nothing unless the logic is complex enough to need fault isolation. This includes: functions re-tested by their callers.
- **Wiring tests** - Tests that only verify a side-effect call was made with the right arguments. These test glue, not logic. They break on refactors, not on bugs. Only test wiring when there's transformation, conditional logic, or error handling between caller and callee.
- **Static structure assertions** - Field existence, column types, initial state values, default config, type checks. If the structure is wrong, every other test that depends on it already fails.
- **Output shape without behavior** - Tests that verify static output (rendered text, response field presence, visual properties, source file contents) without exercising any logic. If a behavioral test in the same file already produces the same output, the shape-only test is redundant.
- **Variant repetition without branching** - Multiple tests exercising the same code path with different inputs. If the logic doesn't branch, one representative test (or one parameterized test) is enough.
- **Single-path utilities** - Functions with no conditionals, no error handling, no edge cases. Simple getters, setters, one-liner delegations. If the function branches, it's worth testing.

### Mock health

- **Max 3 mocks per test.** More than that means you're testing wiring, not behavior.
- If a test needs 4+ mocks, rewrite it as an integration test or remove it.
- Frontend tests are especially prone to over-mocking. A component test with mocked router, mocked context, mocked API, and mocked hooks tests nothing real.

### Each layer has a purpose

**Unit tests** prove isolated logic works - branching, calculations, domain rules. They're fast and pinpoint exactly what broke. Write them for functions with complex conditionals where fault isolation matters. Not every behavior needs a unit test - if the logic is simple and an integration test already covers it, the unit test is duplicate coverage.

**Integration tests** prove pieces work together - API + DB, service + repository, component + context. They catch contract mismatches and wiring bugs that unit tests can't see.

**E2E tests** prove a complete flow works end-to-end - a full API call traversing all layers (request → middleware → service → DB → response), a browser-driven test that triggers backend calls, or a flow that includes external services. They validate that the entire chain works together, not just individual pieces.

| Layer | Test | Skip |
|-------|------|------|
| **Unit** | Functions with conditionals, calculations, domain rules, state machines | Getters, trivial utils, config, schema validation |
| **Integration** | API endpoints (auth, permissions, errors), services + DB, component + context | Simple CRUD already covered by E2E, static rendering |
| **E2E** | Critical user flows (auth, upload, core workflows), full API traversals | Flows already well-covered by integration tests |

---

## Mode: Writing Tests

When creating new tests, apply the criteria above before writing anything.

1. Check the code against the **"Worth testing"** and **"NOT worth testing"** categories above.
2. If it matches "Worth testing" and not "NOT worth testing" → write it. Focus assertions on behavior, not only granular implementation details.
3. Otherwise → don't write the test. Move on.

When writing:
- Test behavior and outcomes, not a very granular implementation details.
- One concept per test - if you need `and` in the test name, split it
- Name tests after what they verify: `test_locked_account_returns_403`, not `test_login_3`
- Prefer real dependencies over mocks **when feasible** (in-memory DB over mocked repository). If its not a greenfield project, follow the project's conventions.

---

## Mode: Audit

When auditing existing tests, use the same criteria to classify each test.

### Phase 1: Understand the project's test definitions

Before judging, understand what unit/integration/E2E mean **in this specific project** - these terms are ambiguous:

- Read project docs, test configs, CI pipeline, directory structure
- Confirm your understanding with the user before proceeding

### Phase 2: Explore, Count & Classify

- **Step 1**: Explore the application code (not just tests) - understand modules, business logic, critical flows, and what each area of the codebase does. This context is essential to judge whether a test is worth keeping.
- **Step 2**: Find all test files (Glob) to know the total scale.
- **Step 3**: Based on the number of test files/dirs/modules and the app structure, decide how many parallel agents to launch. Each agent gets a specific scope (files, dirs, or modules - match the project's organization). Each agent also receives context about the production code its tests relate to.
- **Step 4**: Each agent, in a single pass per file, does:
  - Count every individual test case precisely (read each file, count exact declarations - no estimates, no sampling). Maximum precision on test counts is required.
  - Classify each test: **Remove** / **Keep** / **Missing** - using knowledge of the production code to judge worthiness against the criteria above.
- **Step 5**: Aggregate all agent results - total counts + classifications.

### Phase 3: Report

```
# Test Audit Report

## Test Count Overview
| Metric | Count |
|--------|-------|
| **Total tests in system** | X |
| **Tests to remove** | Y |
| **Projected count after cleanup** | Z |

## Project Test Definitions
[What each category means in this project]

## Summary
- Test files analyzed: X
- Remove: X | Keep: X | Missing critical: X | Missing edge cases: X

## Tests to Remove
### [filename:test_name]
- **Category**: [matching category from NOT worth testing list above]
- **Why**: [1-2 sentences]

## Missing Tests (Priority Order)
### Critical
[What to test and why it matters]

### Edge Cases
[Scenario descriptions]

## Mock Health
[Files with excessive mocking and suggested refactors]
```

### Execution modes

Ask the user which mode they want:

- **Report only** (default) - generate report, make no changes
- **Report + Delete** - report, then remove confirmed tests one at a time
- **Report + Scaffold** - report, then scaffold missing tests with TODO placeholders
- **Full automation** - report, delete confirmed tests, scaffold missing tests with TODO placeholders

---

## Principles

- Read the actual test code - don't judge by name alone
- Apply the criteria consistently - if a test matches NOT worth testing and doesn't match Worth testing, remove it
- Respect project conventions (test configs)
- The test pyramid is a guideline, not a law - if logic lives in API handlers, integration tests may matter more than unit tests
````

**Prompt inicial em plan mode (narrado na aula)** ([[TDD com IA]])
```text
Desejo criar um sistema de gerenciamento de prompts de IA. Esse sistema deverá ter opções para eu cadastrar, editar, deletar meus prompts. A visualização dele poderá ser via markdown, mas nesse momento faremos apenas o back-end. Quero utilizar Clean Architecture, onde as regras de negócio devem ser autocontidas dentro de uma entidade de domínio. Por exemplo, um prompt pode ter status diferentes, como draft, revisão, publicado, mas, por exemplo, eu não posso publicar um prompt diretamente de draft para publicado. Ele deve ser revisado antes. Logo, isso são regras de negócio que precisamos testar. Quero utilizar TDD para fazer todo esse processo. Utilizaremos o banco de dados PostgreSQL e você utilizará o codebase atual para programar. Monte um plano de implementação para fazermos isso usando TDD.
```

**Crítica ao plano sobre o momento do refactor (narrado na aula)** ([[TDD com IA]])
```text
Você fará a refatoração depois de tudo implementado ou vai seguir o TDD e refatorar a cada implementação de um teste que já passou?
```

**Auditoria pós-TDD (narrado na aula)** ([[TDD com IA]])
```text
/test-guide Auditing. Report only. Apenas na parte back-end referente ao gerenciamento de prompts e suas APIs. Nada de front-end.
```

**Plano de auditoria de testes sem valor, escrito em plan mode (narrado na aula)** ([[Testes Automatizados vs IA]])
```text
Quero que você mapeie todos os testes back-end e front-end, avalie quais testes realmente geram valor para a aplicação e cobrem fluxos importantes de negócio, de feature, que garantem realmente problemas de regressão. Baseado nisso, entenda quais são os testes considerados desnecessários, redundantes, inúteis, que não geram valor para aplicação e que não deveriam existir. Obviamente, se há regras de negócio e componentes que precisam manter a consistência e estado do projeto, esses testes deverão existir. Traga para mim a quantidade aproximada de testes que eu poderia remover e que não geraria um impacto negativo no projeto, principalmente referente a regressões. Evite totalmente testes que já, em tese, são cobertos pelas próprias bibliotecas. Exemplo, o Zod. Traga para mim a quantidade de testes separado entre back-end e front-end.
```

**Prompt que o Claude Code gerou para o subagente Explore MapFrontEndTestInventory (narrado na aula, parafraseado)** ([[Testes Automatizados vs IA]])
```text
Do a thorough investigation of all front-end tests in <pasta>. First, list directories and files. Use glob pattern *.test.* or *.spec.* in this folder. Then read all tests and categorize each test call:
- Valuable: multi-behavior, user interactions, state logic, error handling, business rules
- Zod library validation: tests that just justify Zod schema validation, required fields, type checking, things that Zod already guarantees
- Render smoke: only "renders without crashing", no meaningful assertion
- Trivial: static display elements, CSS classes, anything that does not bring regression problems
- Redundant: duplicated logic already tested elsewhere
For each file, bring the path, total tests, count per category and specific examples of tests that can be removed. Be very thorough, read all cases.
```

**Pedido ad hoc de teste de navegação (narrado na aula)** ([[Testes E2E com Playwright CLI]])
```text
Faça um teste de navegação com o Playwright CLI, fazendo o login e criando uma nova categoria no sistema chamada de vídeos de worship. Use --headed.
```

**Execução do test case gerado (narrado na aula)** ([[Testes E2E com Playwright CLI]])
```text
/e2e-nav-test Realize os testes de navegação com Playwright CLI, no formato headed, baseado no @docs/e2e-navigation-tests-role-user.md
```

**Interrupção com atualização parcial do report (narrado na aula)** ([[Testes E2E com Playwright CLI]])
```text
Atualize o report parcialmente com o que você já testou.
```

**Skill e2e-nav-test (literal do repositório, `skills-mba/e2e-nav-test/SKILL.md`: frontmatter, Phase 2, Phase 4 e Principles; Phase 1, template completo da Phase 3 e Reference Files estão no arquivo original)** ([[Testes E2E com Playwright CLI]])
````markdown
---
name: e2e-nav-test
description: >
  Generate and execute E2E test cases for any web application - SPA, server-rendered,
  or hybrid. Analyzes the codebase to discover routes, components, auth flows, forms,
  modals, roles/permissions, and navigation patterns, then produces a structured
  test-cases document with dependency trees and todo checklists. Works with any
  framework: Next.js, React, Vue, Angular, Django, Laravel, Rails, Flask, Go,
  Symfony, Spring, ASP.NET, PHP, and more. Use this skill whenever the user asks to
  "test navigation", "generate e2e tests", "test user flows", "create test cases",
  "run navigation tests", "e2e test plan", "check all flows", "test my app flows",
  "map user journeys", "test my app", or anything related to end-to-end flow testing.
  Also trigger when the user mentions "test-cases.md", "flow coverage", or
  "navigation coverage". Even if they just say "test my app" or "run e2e",
  this skill is likely what they need.
---

# E2E Test Case Generator

Analyze a web application codebase (SPA, server-rendered, or hybrid), generate a structured test plan with dependency awareness, and optionally execute the tests using browser automation.


[...]

## Phase 2: Build the Dependency Tree

This is the most critical phase. Every test flow has prerequisites. Model them explicitly.

### Dependency rules

1. **A flow depends on another if it cannot be tested without that flow succeeding first.** Example: "Create a prompt" depends on "Login" because you must be authenticated.

2. **If a dependency fails, all flows that depend on it are automatically BLOCKED.** Document this clearly. Example: if Login fails, everything behind auth is BLOCKED.

3. **Independent flows run regardless of other failures.** Example: "Visit landing page" and "Visit signup page" are independent of each other.

4. **Avoid redundant testing.** If Login was already verified as a dependency, subsequent flows that need auth should note "Requires: Login (tested in T01)" but NOT re-test the login steps. They start from an already-authenticated state.

5. **Chain dependencies, don't repeat them.** If "Edit prompt" depends on "Create prompt" which depends on "Login", then "Edit prompt" lists only "Create prompt" as its direct dependency. The transitive dependency on Login is implicit.

### Dependency tree format

Build the tree as a visual hierarchy that shows parent-child relationships at a glance. Use ASCII tree connectors (`├─`, `└─`, `│`) to convey structure. Every test gets a short ID (T01, T02, ...) for easy referencing.

```
T01 Landing Page
 ├─ T02 Signup
 └─ T03 Login
     └─ T04 Dashboard
         ├─ T05 Create Item
         │   ├─ T06 Edit Item
         │   └─ T07 Delete Item
         ├─ T08 Search
         └─ T09 Theme Toggle
 └─ T10 Logout
```

Root nodes (T01) have no dependencies. A child can only execute if its parent passed. Siblings are independent of each other - if T06 fails, T07 still runs. Note that Search (T08) depends on Dashboard (T04), not on Create Item (T05) - place each test under its actual dependency, not under an unrelated sibling.


[...]

## Phase 4: Execute Tests (Optional)

After generating the document, ask the user: "Test cases are ready. Would you like me to execute them now using browser automation?"

If yes:

### Execution rules

1. **Read the Prerequisites section** from the generated test-cases document - it already contains the start command, base URL, and test credentials (discovered during Phase 1). If executing in the same session that generated the document, these values are already known. If executing later, read them from the document.

2. **Ensure the server is running** before any test. If the project has a startup script, use it. If not, run the dev server command discovered above.

3. **Use available browser automation** (playwright-cli or whatever tool is available) in headless mode.

4. **Follow the dependency tree order** - execute root tests first, then their children.

5. **On dependency failure**: mark all child tests as BLOCKED, do not attempt them.

6. **On independent failure**: continue with the next independent test.

7. **Take a screenshot on failure.** Save screenshots in a `screenshots/` subfolder next to the test-cases document. Name the file after the failing test: `screenshots/t05-create-item-step3.png`. Never save screenshots in the project root.

8. **After each navigation**: check browser console for errors - any compilation or runtime error means FAILURE for that step.

### Updating the document after execution

Mark each step with its result:

- `[x]` - passed
- `[ ]` - not executed yet
- `[FAIL]` - failed (add brief reason inline)
- `[BLOCKED]` - skipped because a parent dependency failed

### Observations section

After execution, fill in the Observations section at the bottom of the document using the format shown in the document template above (Failed Tests, Blocked Tests table, Summary counts).

---

## Principles

- **Discover before assuming.** Read actual code, not just file names. A route might exist but redirect. A form might be disabled. An auth check might be client-side only.
- **Respect the dependency tree.** Never execute a flow if its dependency failed. This avoids cascading false failures that obscure the real problem.
- **No redundant login steps.** If login was tested and passed in T01, subsequent flows start from an authenticated browser session. Do not repeat login steps - just note the dependency.
- **Be framework-aware but not framework-dependent.** The discovery phase adapts to the framework, but the output format and execution logic stay the same regardless of stack.
- **Binary outcomes only.** Every step passes or fails. "Partially works" is a failure with a note.

````

**Skill plan-test-specs (literal do repositório, `mba-ia-greenfield-project/.claude/skills/plan-test-specs/SKILL.md`: frontmatter, Spec format e Lifecycle states; Preflight, Procedure, Integration points e Failure modes estão no arquivo original)** ([[Testes E2E com Playwright CLI]])
````markdown
---
name: plan-test-specs
description: "Stage 5 of the plan pipeline (post-build). Generates and syncs <subproject>/specs/<scenario>.plan.md files from phase/task plans, in Microsoft spec-driven format. Specs are later consumed by /implement Step 3a - frontend path loads the playwright-cli Skill for Playwright pattern reference and LLM-authors the E2E test file; backend path LLM-authors its E2E test file (file path/suffix per the per-subproject testing-guide skill; what-to-test and best practices per artifact come from that same skill, already loaded at /implement Step 2). Use after /plan-build completes. Triggers: 'plan-test-specs NN', 'plan-test-specs <slug>', 'gerar test specs da fase X'."
disable-model-invocation: true
---

# Plan Pipeline - Stage 5: Test Specs

This is **Stage 5** (optional, post-build) of the plan pipeline defined in `.claude/skills/plan-pipeline/SKILL.md`. Read that file first for the cross-stage convention (frontmatter format, registered values, stage interaction). Stage 1-4 produce/edit a phase or task plan; Stage 5 derives external **spec files** from screen-wiring / controller-wiring / cross-layer SIs of that plan.

The skill is **skippable**: legacy plans (frontmatter without `test_specs_aware: true`) are routed to an abort message instructing migration; modern plans without any SI carrying `**Test Specs:**` (e.g., backend-pure phases) fall through silently.

[...]

## Spec format (universal)

The spec file is **NOT** a planning artifact - it does not follow `kind:` / `name:` convention from `.claude/skills/plan-pipeline/SKILL.md`. Specs are test contracts, parallel to `library-refs.md` exemption.

```markdown
---
subproject: backend | frontend       # canonical runner discriminator (consumed by /implement Step 3a)
runner: <runner-tag>                 # informational only - `playwright` for frontend; per-backend runner tag for backend (e.g., `jest+supertest`, `pytest`, `gotest`); must match `subproject:`; `subproject:` is canonical
scope: phase-NN-{slug} | task-{slug}
si: SI-NN.X | SI-N
target_file: <resolved E2E test path>         # 1 arquivo de teste por spec; cenários viram test() blocks.
                                              # Path concreto (pasta + sufixo + nome) derivado da convenção E2E
                                              # do subprojeto via testing-guide-{subproject} e resolvido por
                                              # /plan-test-specs na geração - NÃO hardcodar pasta/sufixo aqui.
---

# <Screen | Endpoint> Test Plan

## Application Overview

<Um parágrafo descrevendo o que esta tela / endpoint faz e por quê.>

## Test Scenarios

### 1. <Group Name - verbatim from screen-inventory ou API Contract>

**Setup:** <fixture reference (frontend) | DB cleanup + module bootstrap (backend)>

#### 1.1. <kebab-case-scenario-name>

**Covers AC:** #1, #4
**Source:** auto
**Last sync:** 2026-05-02T14:30:00Z

**Steps:**
  1. <user-actor or API-caller voice - depending on subproject>
    - expect: <observable outcome>
    - expect: <another outcome>
  2. <next step>
    - expect: <outcome>
```

### File-naming convention

- **1 spec → 1 test file**, declarado via `target_file:` no frontmatter. O path concreto (pasta + sufixo + nome) é derivado da convenção E2E do subprojeto via `testing-guide-{subproject}` (ver Reason abaixo) e resolvido por `/plan-test-specs` na geração - esta skill NÃO fixa pasta nem sufixo.
- **N cenários no spec → N `test()` blocks** dentro de um único `test.describe('<feature>')` no arquivo gerado.
- Cenário individual NÃO tem `**File:**` field - caminho é shared via `target_file:`.

Reason: the project's frontend testing convention is *"one file per feature/flow"* with `test.describe('<feature>')` agrupando. Adotar 1 arquivo por cenário (Microsoft canonical) violaria essa regra. The `testing-guide-{subproject}` Skill (loaded by `/implement` Step 2 for the frontend subproject) is the canonical entry point for that convention. It is also the single source of truth for the `target_file:` path itself (folder + suffix per subproject); `/plan-test-specs` reads that convention at generation time and writes a concrete `target_file:` - no folder or suffix is hardcoded in this skill.

### Per-subproject vocabulary

| Field / Voice | Frontend | Backend |
|---|---|---|
| `Setup:` | `<frontend-subproject>/tests/fixtures.ts` (MSW network fixture auto-applied) | `beforeEach` truncate test DB; bootstrap backend test module (e.g., NestJS: `Test.createTestingModule(...).compile()`) |
| Step voice | "Usuário clica em Sign in" (user-actor) | "POST /auth/register com body X" (API-caller) |
| Expect vocabulary | DOM-observable + URL state + toast text | HTTP status + response body shape + DB state + side-effects |
| File path (per spec) | per `testing-guide-frontend` E2E convention - resolved at generation, no folder/suffix hardcoded here | per `testing-guide-backend` E2E convention - idem |
| Import in generated test | the MSW network fixture, imported from its path per `testing-guide-frontend` (NEVER `'@playwright/test'`) | backend test bootstrap module + HTTP client (e.g., NestJS `Test` module + Supertest) |

### Boundary - what externalizes vs stays inline

| Camada | Localização | Razão |
|---|---|---|
| Playwright E2E (frontend) | `<frontend-subproject>/specs/*.plan.md` | externaliza |
| E2E (backend) | `<backend-subproject>/specs/*.plan.md` | externaliza |
| Unit (frontend) | inline na Tests table do SI | fica inline |
| Integration (frontend - e.g., Route Handlers / msw/node) | inline na Tests table do SI | fica inline |
| MSW handler tests (`auth-handlers.spec.ts`) | inline no SI próprio | fica inline (não é screen wiring) |
| Unit (backend - services / repos) | inline na Tests table do SI | fica inline |
| Backend integration (ORM repos / modules - e.g., TypeORM, Prisma, SQLAlchemy, Hibernate) | inline na Tests table do SI | fica inline |

## Lifecycle states (MVP - L2 revisado)

| State | Detection | v1 action |
|---|---|---|
| **NEW** | AC do plano sem cenário cobrindo | gerar cenário, marcar `Source: auto`, set `Last sync` ao timestamp da operação |
| **PRESERVED** | Cenário existe; mtime do source (phase plan) ≤ `Last sync` do cenário | re-stamp Last sync (Edit cirúrgica substitui só a linha) - atualiza file mtime como side-effect |
| **MANUAL** | Cenário com `Source: manual` ou sem `Source` field | skip silently |
| **UPDATED** | Cenário com `Source: auto` E mtime do plano > `Last sync` | warning no delta report; user edita à mão |
| **DELETED** | Cenário com `Source: auto` cobrindo apenas ACs que sumiram do plano | warning no delta report |
| **ORPHAN** | `Covers AC: #N` aponta a AC inexistente no SI atual | warning no delta report |

````

**Spec E2E gerada pelo plan-test-specs (literal do repositório, `mba-ia-greenfield-project/next-frontend/specs/login.plan.md`)** ([[Testes E2E com Playwright CLI]])
````markdown
---
subproject: frontend
runner: playwright
scope: phase-02-auth-frontend
si: SI-02.11b
target_file: tests/auth-login.e2e-spec.ts
---

# Tela de login - Test Plan

## Application Overview

A tela `/login` autentica um usuário com e-mail e senha e inicia a sessão. É uma rota anônima: um shell RSC compõe o form `"use client"` (`components/auth/login-form.tsx`, react-hook-form + Zod), que submete via `fetch("/api/auth/login")` ao Route Handler BFF, que proxia `POST /auth/login` no NestJS upstream. Em `200` o BFF sela o cookie `iron-session` encriptado (carregando `access_token`/`refresh_token` + fingerprint mínimo do usuário) - os tokens nunca chegam ao browser - e o form dispara `router.refresh()` para o chrome refletir o estado autenticado. Erros `401` (credenciais inválidas), `403` (e-mail não confirmado) e `400` (validação) são mapeados para alertas/feedback; a validação client-side espelha o backend 1:1.

## Test Scenarios

### 1. Autenticar usuário com e-mail e senha e iniciar sessão

**Setup:** `next-frontend/tests/fixtures.ts` (MSW network fixture auto-applied; server-side upstream faked via `instrumentation.ts`, no browser `page.route()` of `/api/**`)

#### 1.1. login-sucesso-sessao-iniciada

**Covers AC:** #1
**Source:** auto
**Last sync:** 2026-05-16T21:32:09Z

**Steps:**
  1. Usuário navega para `/login`
    - expect: o `Card` de login renderiza com campos de e-mail e senha e o botão "Sign in"
  2. Usuário preenche credenciais válidas e clica em "Sign in"
    - expect: a requisição `POST /api/auth/login` é disparada com payload tipado
    - expect: enquanto a mutation está em voo, o `SubmitButton` fica desabilitado / em loading
  3. Backend responde `200` e o BFF sela o cookie de sessão
    - expect: nenhum `access_token`/`refresh_token` aparece no corpo da resposta visível ao client nem em storage do browser
    - expect: a UI reflete o estado autenticado (chrome atualizado via `router.refresh()`) / redireciona para a área autenticada

#### 1.2. login-erros-401-403-400

**Covers AC:** #2
**Source:** auto
**Last sync:** 2026-05-16T21:32:09Z

**Steps:**
  1. Usuário submete o form com credenciais inválidas (reserved trigger upstream → `401`)
    - expect: um `Alert` form-level de "credenciais inválidas" é renderizado
    - expect: nenhuma sessão é estabelecida
  2. Usuário submete com um e-mail cuja conta não foi confirmada (reserved trigger → `403`)
    - expect: um `Alert` form-level de "e-mail não confirmado" é renderizado, com CTA de reenvio de confirmação
  3. Usuário submete com payload que dispara validação upstream (reserved trigger → `400`)
    - expect: a mensagem `400` é renderizada inline abaixo do campo ofensor

#### 1.3. login-validacao-client-side-bloqueia-submit

**Covers AC:** #3
**Source:** auto
**Last sync:** 2026-05-16T21:32:09Z

**Steps:**
  1. Usuário navega para `/login` e clica em "Sign in" com o form vazio
    - expect: nenhuma requisição `POST /api/auth/login` é disparada (submit bloqueado client-side)
    - expect: mensagens de validação inline aparecem nos campos obrigatórios
  2. Usuário preenche valores que violam as regras espelhadas do backend (e.g. e-mail malformado)
    - expect: o submit permanece bloqueado e as mensagens inline espelham o backend 1:1
  3. Usuário corrige os campos para valores válidos
    - expect: o submit é liberado e `POST /api/auth/login` é disparada
````

**Atualizar o CLAUDE.md do Next com a decisão de testes, via /init em plan mode (narrado na aula)** ([[Testes no Front-end com MSW]])
```text
Quero atualizar o CLAUDE.md do Next front-end para a decisão de testes. Para testes end-to-end vamos usar o Playwright, para testes de unidade e integração das páginas, componentes e outros artefatos, usaremos o Vitest. Para o caso do BFF, que é chamado de Route Handler no Next.js, não criaremos testes apontando para a API do Nest. Teremos uma API fake, feita com MSW handlers, usando o msw/node para ele subir um servidor para essa API fake. Então podemos fazer esses testes usando o Vitest, chamando apenas a função Route Handler diretamente. Serão testes de integração. Todos os testes de unidade e de integração ficarão em pastas com __test__, perto do artefato que testam. Já os end-to-end ficarão numa pasta tests na raiz do front-end. Dada a estrutura que já temos no CLAUDE.md, analise as mudanças nas seções existentes e também novas seções que serão criadas.
```

**Seção de testes do `next-frontend/CLAUDE.md` (literal do repositório)** ([[Testes no Front-end com MSW]])
````markdown
## Testing

Stack decisions for this project:

- **Vitest** for unit and integration tests of pages, components, hooks, utils, and BFF route handlers.
- **Playwright** for end-to-end tests (full browser flow).
- **MSW (`msw` + `msw/node`)** as the fake API for BFF tests: route handlers are tested **as functions** - they are imported and called directly, while `msw/node` intercepts the `fetch` calls they make to the NestJS API and returns fixtures. BFF tests **never** point to the real NestJS API.
- **MSW (`msw/node` via `instrumentation.ts`)** as the fake API for E2E tests: the dev server boots server-side MSW so the **real** `/api/**` Route Handlers run; only their upstream NestJS `fetch` is faked, reusing the `mocks/` handler set (no browser-level/BFF handler set). See "E2E architecture" below.

## Test type selection - apply mechanically

The suffix is a contract. It drives the runner (Vitest vs. Playwright), where the file lives, and what is allowed inside it.

| Suffix | When | Runner | External I/O | Location |
|---|---|---|---|---|
| `*.test.ts` / `*.test.tsx` | **Unit** - pure logic, collaborators mocked (utils, hooks, a single component in isolation). | Vitest | Forbidden. | `__tests__/` next to the artifact. |
| `*.integration.test.ts` / `*.integration.test.tsx` | **Integration** - multiple artifacts wired together; route handlers called as functions with `msw/node` intercepting `fetch` to the upstream API. | Vitest | MSW only (no real network). | `__tests__/` next to the artifact. |
| `*.e2e-spec.ts` | **End-to-end** - full browser flow; real `/api/**` run server-side, upstream faked (see "E2E architecture"). | Playwright | server-side MSW via instrumentation - no real network. | `tests/` at root. |

Routing decision tree (apply in order; first match wins):

- Renders a component or invokes a hook/util in isolation with mocks for collaborators → **`*.test.ts`** (or `.tsx` if rendering JSX).
- Imports a route handler (`import { GET } from "@/app/api/.../route"`), builds a `Request`/`NextRequest`, calls the handler, and asserts on its `Response`, with MSW intercepting fetches to the upstream API → **`*.integration.test.ts`**.
- Drives the full app in a real browser (navigation, forms, assertions on rendered DOM) → **`*.e2e-spec.ts`** under `tests/`.

### Running tests during development

Run only what is relevant to the change in progress:

```bash
# Vitest (single file or pattern) - inside the container
docker compose exec next-frontend npm test -- path/to/file.test.ts

# Playwright (single spec) - on the HOST
npx playwright test tests/foo.e2e-spec.ts
```

### E2E test prerequisites - start the environment before running Playwright

Playwright runs on the **host** and targets the **containerized** dev server. Before running any `*.e2e-spec.ts`, the dev server must be running inside the container with `MSW_ENABLED=true`. Follow these steps in order:

```bash
# 1. Ensure the container is up (idempotent)
docker compose up -d

# 2. Start the dev server with MSW enabled - runs in background (never exits)
docker compose exec -d next-frontend sh -c "MSW_ENABLED=true npm run dev"

# 3. Wait until the server is ready (retries up to ~30 s)
curl --retry 15 --retry-delay 2 --retry-connrefused -I http://localhost:3001

# 4. Run the E2E suite on the host
npx playwright test

# Or a single spec
npx playwright test tests/xxxx.e2e-spec.ts
```

**Important rules:**
- Step 2 must use `MSW_ENABLED=true` - without it `instrumentation.ts` skips MSW and upstream calls will fail or hit the real NestJS API.
- Never add `webServer` to `playwright.config.ts` - Playwright must not manage the dev server process (it runs inside Docker, not on the host).
- If the dev server is already running from a previous session, skip steps 2–3 and go straight to step 4.

### MSW + Vitest - wired

Vitest roda em `environment: "node"` (default) e carrega `mocks/setup.ts` via `setupFiles`; MSW sobe com `onUnhandledRequest: "error"` - qualquer `fetch` não interceptado falha o teste com `"request unhandled"`. Layout de `mocks/` (handlers por domínio + barrel, factories, server).

### E2E architecture

Real browser → real Next.js (RSC, layouts, real `/api/**` Route Handlers server-side) → upstream NestJS **faked at the server**. Only the NestJS API is fake; real `iron-session` cookies are set, so auth/session flows are genuinely testable.

**Mechanism.**

1. `instrumentation.ts` `register()` - when `NEXT_RUNTIME === "nodejs"` **and** `MSW_ENABLED=true`, dynamically imports `mocks/server.ts` and calls `server.listen({ onUnhandledRequest: "bypass" })`.
2. Reuses the `mocks/` upstream handlers (same set as Vitest); no browser-level handler set, no `tests/handlers/`.
3. Per-scenario outcomes via **reserved trigger fixtures** in the shared handlers (e.g. `email: "conflict@example.com"` → 409, `"badrequest@example.com"` → 400; else success). No per-test `server.use()`. Keep the trigger table small.
4. Playwright runs on the **host** (`npx playwright test`, `http://localhost:3001`); the containerized `next dev` must run with `MSW_ENABLED=true`. No `webServer` in `playwright.config.ts` (dev server is containerized).

**Hard rules.**

- E2E specs **MUST NOT** browser-intercept `/api/**` (`page.route()` or any browser-level mock) - it short-circuits the Route Handlers.
- E2E specs **MUST NOT** reach a real NestJS API - upstream is always the server-side `mocks/` MSW.
- Upstream handlers are **shared** with Vitest - no E2E-only fork; per-scenario deviation is a reserved trigger fixture branch, not a runtime override. Trigger values must not collide with Vitest fixture values.
- `onUnhandledRequest`: `"error"` in Vitest, **`"bypass"`** in instrumentation - never copy `"error"` into `instrumentation.ts`.
````

**Rule `.claude/rules/next-frontend-testing.md` (literal do repositório)** ([[Testes no Front-end com MSW]])
````markdown
---
paths:
  - 'next-frontend/**/__tests__/**'
  - 'next-frontend/tests/**'
  - 'next-frontend/**/*.test.ts'
  - 'next-frontend/**/*.test.tsx'
  - 'next-frontend/**/*.integration.test.ts'
  - 'next-frontend/**/*.integration.test.tsx'
  - 'next-frontend/**/*.e2e-spec.ts'
description: 'Test type routing, file placement, forbidden patterns (no real-network Vitest tests)'
---

# next-frontend - Testing Rules

## Forbidden pattern - never hit the upstream API directly

A test file that opens a network connection to the real upstream API **MUST NOT** exist in this project. If you find yourself wanting one, the right tool is:

- **`*.e2e-spec.ts`** (Playwright) - drives the running app, which talks to whatever upstream the running environment is wired to.
- **`*.integration.test.ts`** (Vitest + MSW) - with hand-written handlers under `mocks/handlers.ts` or per-test overrides via `server.use(...)`.

Never write a Vitest test that opens a real `fetch` to the upstream host. The contract for integration tests is "BFF as functions, MSW as fake upstream" - see the MSW rule for the 4-step pattern.

## File placement summary

- **Unit / Integration tests live next to the code they exercise**, in a `__tests__/` directory:
  - `components/<feature>/__tests__/*.test.tsx` for component unit tests.
  - `app/api/<route>/__tests__/*.integration.test.ts` for Route Handler integration tests.
  - `lib/__tests__/*.test.ts` for util unit tests.
- **E2E tests live at the project root**: `next-frontend/tests/*.e2e-spec.ts`.

## DOM rendering opt-in

**DOM rendering opt-in:** o ambiente default `node` não renderiza componentes/páginas. Testes que renderizam JSX/TSX (componentes, páginas - linhas da tabela "Test type selection") devem optar pelo DOM **por arquivo** com o docblock `// @vitest-environment jsdom` no topo do arquivo (`jsdom` e `@testing-library/react` já estão instalados). Sem esse docblock, apenas lógica pura/hooks/utils rodam sob `node`.
````

**Rule `.claude/rules/next-frontend-msw-mocks.md` (literal do repositório)** ([[Testes no Front-end com MSW]])
````markdown
---
paths:
  - 'next-frontend/mocks/**'
  - 'next-frontend/**/*.integration.test.ts'
  - 'next-frontend/**/*.integration.test.tsx'
description: 'MSW handler typing convention + Route Handler integration test pattern (paths-anchored fixtures)'
---

# next-frontend - MSW Mocks Rules

These rules govern MSW handler authoring (per-domain modules under `mocks/handlers/<domain>.ts`, the barrel, the `msw/node` server, and per-test `server.use(...)` overrides) and the BFF integration-test pattern that drives them.

## Where MSW lives

By convention, MSW lives under `next-frontend/mocks/`. The tree is per-domain - each phase contributes one new domain file plus one line in the barrel:

- `mocks/handlers/<domain>.ts` - handlers for a single API domain (e.g., `auth.ts`, `videos.ts`, `channels.ts`). One handler per `(method, path)` entry from the OpenAPI `paths`; per-test deviations layer via `server.use(...)`.
- `mocks/handlers/index.ts` - barrel re-export. Each phase appends one `import { handlers as <domain>Handlers } from "./<domain>"` line plus one spread into the exported `handlers` array.
- `mocks/factories/<domain>.ts` - response-body factories for the domain. Each shape exports a `buildX(overrides?: Partial<X>): X` function.
- `mocks/server.ts` - `setupServer(...handlers)` from `msw/node`, imported by Vitest's `setupFiles`.
- `mocks/setup.ts` - Vitest setup file that registers the MSW lifecycle (`listen` / `resetHandlers` / `close`).

Tests override fixtures per-case via `server.use(http.get(...))` inside `beforeEach` or individual `it` blocks.

## Lifecycle (Vitest `setupFiles`)

The MSW server is started once per Vitest run, reset between tests, and torn down at the end:

```ts
// next-frontend/mocks/setup.ts
import { afterAll, afterEach, beforeAll } from "vitest";
import { server } from "./server";

beforeAll(() => server.listen({ onUnhandledRequest: "error" }));
afterEach(() => server.resetHandlers());
afterAll(() => server.close());
```

`onUnhandledRequest: "error"` is load-bearing: any `fetch` that escapes the handler set fails the test loudly with `"request unhandled"`. That is the discipline that keeps the coverage matrix in sync with the contract - there is no silent passthrough to the real network.

`resetHandlers` runs after every test so a `server.use(...)` override in one test does not leak into the next.

## Factories convention

Hand-written deterministic factories under `mocks/factories/<domain>.ts` are the default. Every shape gets a `buildX(overrides?: Partial<X>): X` function that composes a hand-coded `baseX: X` literal with the caller's overrides:

```ts
// next-frontend/mocks/factories/<domain>.ts
import type { User } from "@/lib/api/contracts";

const baseUser: User = {
  id: "user-1",
  email: "alice@example.com",
  // mirror User from @/lib/api/contracts verbatim
};
export const buildUser = (overrides: Partial<User> = {}): User => ({
  ...baseUser,
  ...overrides,
});
```

`@faker-js/faker` is **opt-in** and scoped to bulk-collection builders only (e.g., `buildVideoList(n, seed)`). When used, call `faker.seed(N)` **immediately before** generating the collection so determinism is local to that builder and does not interact with the global cursor. Faker is not installed at foundation - the first phase that authors a `buildXList` triggers the install.

## Route Handler + MSW integration test pattern

For every test under `app/api/**/__tests__/*.integration.test.ts`:

1. **Import the handler directly from the route module** - `import { GET, POST } from "@/app/api/.../route"`.
2. **Construct a `Request`** (or `NextRequest`) with the URL, method, headers, and body the handler expects, then `await` the handler.
3. **`msw/node` intercepts** the `fetch` calls the handler makes to the upstream API - configured **once** in Vitest's `setupFiles` (see `mocks/setup.ts` and `mocks/server.ts`) - and returns fixtures defined in `mocks/handlers/<domain>.ts` (override per-test with `server.use(...)`).
4. **Assert on the `Response`** returned by the handler: status, headers, JSON body.

Why this pattern: it isolates the BFF from the upstream suite (no cross-project test coupling), is fully deterministic, and runs at unit-test speed. Any change to the upstream contract is reflected in the fixtures, not by hitting a live service.

## Typing convention - paths-anchored, hand-written

Handlers in `mocks/handlers/<domain>.ts` (and per-test `server.use(...)` overrides) **MUST** type their fixture bodies via the same `paths` symbol that types the BFF's `openapi-fetch` client. The contract chain - `openapi.json` → `lib/api/types.gen.ts` → `paths` → handler fixture - is end-to-end typed, so a stale fixture fails `tsc --noEmit` after `types.gen.ts` regenerates.

**Hand-written handlers only.** No `faker`-randomized auto-generated handlers - BFF integration tests need deterministic fixture bodies to assert on specific values.

```ts
// next-frontend/mocks/handlers/auth.ts
import { http, HttpResponse } from "msw";
import type { paths } from "@/lib/api/types.gen";
import { env } from "@/lib/env";

type GetVideoOk = paths["/videos/{id}"]["get"]["responses"][200]["content"]["application/json"];

export const handlers = [
  http.get(`${env.API_URL}/videos/:id`, () =>
    HttpResponse.json<GetVideoOk>({ /* deterministic fixture body */ }),
  ),
];
```

```ts
// next-frontend/mocks/server.ts
import { setupServer } from "msw/node";
import { handlers } from "./handlers";

export const server = setupServer(...handlers);
```

### Exception to the contracts-barrel rule

The BFF rule (`next-frontend-bff-api.md`) says **only** `lib/api/contracts.ts` may import `paths` directly from `@/lib/api/types.gen`. **Modules under `mocks/` are the documented exception** - they import `paths` directly because their job is to mirror the wire shape, not to expose named aliases. Feature code (Route Handlers, Components) still imports named aliases from `@/lib/api/contracts`.

### Per-test overrides reuse the same indexing pattern

```ts
server.use(
  http.get(`${env.API_URL}/videos/:id`, () =>
    HttpResponse.json<paths["/videos/{id}"]["get"]["responses"][404]["content"]["application/json"]>(
      { /* error fixture body */ },
      { status: 404 },
    ),
  ),
);
```

### URL composition

Use `${env.API_URL}/...` so the handler matches the value the BFF actually calls - the test runtime sets `API_URL` to whatever the test environment routes through.

### Endpoint coverage

Every endpoint added to the BFF's `paths` index **MUST** have a corresponding hand-written handler (or per-test override) before its integration test can run. `msw/node` fails with `"request unhandled"` if a fetch goes unintercepted - that is the discipline that keeps the coverage matrix in sync with the contract.

````

**Skill gerada `testing-guide-next-frontend/SKILL.md` (literal do repositório; `artifacts/` e `references/` estão na mesma pasta)** ([[Testes no Front-end com MSW]])
````markdown
---
name: testing-guide-next-frontend
description: >
  Testing guide for next-frontend. Reference this skill when planning features,
  implementing code, creating tests, or reviewing changes in next-frontend.
  Covers what to test, at which layer, and how to set up each test - organized
  by artifact type. Triggers on: planning next-frontend features, implementing
  next-frontend features, writing tests for next-frontend, reviewing
  next-frontend code, reviewing next-frontend tests, what should I test in
  next-frontend, how to test next-frontend, next-frontend test guide.
---

## 0. Purpose

This guide helps you decide **what to test**, at **which layer**, and **how to set up tests** for each type of artifact in `next-frontend`. When working on a specific artifact type (page, client component, route handler, hook, utility, …), read the corresponding file in `artifacts/` for the complete recipe. Supporting references (MSW boundary, mock health, file conventions, gotchas) are in `references/`.

The contract is fixed by `next-frontend/CLAUDE.md` § "Testing" and the four `.claude/rules/next-frontend-*.md` rule files:

- **Vitest 4** runs unit + integration tests (`*.test.ts(x)`, `*.integration.test.ts(x)`). Default `environment: "node"`; tests that render JSX opt into jsdom **per-file** with the `// @vitest-environment jsdom` docblock.
- **Playwright** runs end-to-end tests (`*.e2e-spec.ts` under `tests/`) - see §6 and `references/gotchas.md` for the containerized architecture.
- **MSW (`msw/node`)** is the **only** fake for the NestJS upstream API. **No** Vitest test may open a real network connection to the upstream host (`.claude/rules/next-frontend-testing.md`).

> **Tooling status (2026-05):** Vitest + MSW are fully wired - `vitest.config.ts`, `mocks/setup.ts`, `mocks/server.ts`, the per-domain handler barrel, and the `npm test` script all exist and run. **Playwright is not yet installed** (no `@playwright/test`, no `playwright.config.ts`, no `test:e2e` script). E2E recipes below are the binding contract for browser flows; the first phase that needs a browser test triggers the Playwright install - no rule below changes when it lands.

## 1. Testability Foundations

These principles connect the universal layered-testing model to the Next.js 16 / React 19 / RSC reality of this project. They justify every decision in the artifact guides.

- **The server boundary is the real boundary in App Router.** A page or layout is a Server Component that may `fetch()`. A route handler is a server module the browser calls over HTTP. The one interesting "external system" for nearly every artifact is the **NestJS upstream API**, reached through the typed `upstream` client (`lib/api/upstream.ts`). The only two sanctioned ways to stand in for it are `msw/node` (Vitest) and the server-side MSW that `instrumentation.ts` boots for Playwright. **Never `vi.mock` global `fetch`; never point a Vitest test at the live API** - `mocks/setup.ts` runs MSW with `onUnhandledRequest: "error"`, so an unintercepted fetch fails the test loudly with `"request unhandled"`. That error *is* the contract-coverage discipline.
- **Async Server Components are not Vitest-renderable.** React 19 + Next.js 16 still cannot render `async function Page()` in jsdom - Vitest and React Testing Library both document this as unsupported (confirmed May 2026; no change since the prior generation). Behavior of async RSCs is proven via Playwright only. Synchronous Server Components and Client Components **are** unit-renderable under the `jsdom` docblock.
- **Mock owned collaborators across module boundaries, not within.** If `<LoginPage>` composes `<BrandLogo>` and `<AuthFooter>`, do **not** mock those - render them together. The mock boundary is the `fetch` to upstream (intercepted by MSW), `next/navigation` hooks (no Node implementation - must be mocked when a client component under unit test calls `useRouter`/`usePathname`/`useSearchParams`), and irreversible side effects (`router.push`, analytics). Everything else in the tree stays real.
- **Configured framework features are real in tests.** `next/image`, `next/link`, `next/font`, `cn()` from `lib/utils`, `cva` variants, design tokens, the Zod 4 `env` schema, the `openapi-fetch` `upstream` client - never mock these. Mocking them hides whether you wired them correctly (a wrong `href`, a missing `alt`, a token typo, a bad `API_URL` schema). They are the project's *configured dependency contracts* - verify them with real instances and test config, never a stub.
- **A Vitest+MSW test does not test the NestJS contract - it tests the BFF logic.** It proves the route handler asks the right URL/method/body and reshapes the response correctly *against a fixture*. Whether the real backend honors that shape is the upstream project's own integration suite plus Playwright against a running stack. Chain: Vitest+MSW proves BFF logic ↔ upstream's tests prove the API ↔ Playwright proves the rendered app. None substitutes another.
- **Tailwind classNames are not behavior.** `expect(el).toHaveClass("bg-primary")` is a mirror test - it copies the implementation. Assert what the user perceives: role, accessible name, `aria-*`, `data-slot`/`data-variant` attributes. Variant *visual correctness* is a Playwright/visual concern, not a Vitest assertion.
- **Module/config artifacts fail only at runtime.** `lib/env.ts` (Zod schema), `lib/api/upstream.ts` (server-only client), `lib/api/contracts.ts` (the sole `paths` importer), and the MSW handler barrel are wiring that TypeScript cannot fully prove. A wrong `API_URL` schema, a missing `server-only` guard, or a stale fixture only bites at runtime - these get boundary/integration coverage, not skipped as "just config".

## 2. Testing Criteria

### Worth testing in `next-frontend`

- **Route handlers under `app/api/**/route.ts`** that branch, check auth/session, validate the request body, or reshape the upstream response → `*.integration.test.ts` with MSW for the NestJS contract (plus a `*.test.ts` for any pure branching helper they extract).
- **`lib/` utilities and boundary modules with branching or system-shape assumptions** - `cn()` (`tailwind-merge` conflict resolution), `lib/env.ts` (Zod schema accept/reject), `lib/api/contracts.ts` aliases that *reshape* (`Pick`/composed) the wire shape.
- **Client components (`"use client"`) with state, handlers, or conditional rendering** - form submit/validation states, error display, disabled/loading transitions.
- **Auth/session flows** (login, signup, logout, forgot-password) - the critical user paths; covered end-to-end via Playwright and at the BFF seam via `*.integration.test.ts`.
- **The BFF↔NestJS wire contract** - every endpoint added to `paths` needs a hand-written MSW handler; a missing/stale fixture is a real bug that `"request unhandled"` or `tsc --noEmit` must catch.

### NOT worth testing in `next-frontend`

- **shadcn UI primitives (`components/ui/*`)** - configured-library wrappers; testing them duplicates `cva`/Radix coverage. Cover via consumers.
- **Icon components (`components/icons/*`)** - static SVG output; a render assertion is a mirror test.
- **Presentational feature components with no logic** (`components/<feature>/*` that only compose primitives) - covered via the page's E2E.
- **Static synchronous pages/layouts with no logic** - framework rendering; cover only if part of a critical flow (then E2E).
- **Tailwind class strings / static prop shape** - mirror tests.
- **Pass-through `contracts.ts` aliases** that merely index `paths` with no reshaping - `tsc` already proves them.

## 3. Feature Implementation Checklist

When implementing a feature, walk this checklist. For each artifact created or modified, read the linked guide and verify the required tests exist.

| Artifact created | Required tests | Guide |
|---|---|---|
| **Page** - sync RSC, static, no logic | None at component level; cover only if part of a critical flow → `*.e2e-spec.ts` | `artifacts/pages.md` |
| **Page** - sync RSC composing client children | Test client children directly; cover rendered page via `*.e2e-spec.ts` | `artifacts/pages.md` |
| **Page** - async RSC (`async function Page()` with `await`) | `*.e2e-spec.ts` only - Vitest cannot render it | `artifacts/pages.md` |
| **Layout** (`layout.tsx`) | None unless it adds logic (auth gate, conditional render); else via E2E | `artifacts/layouts.md` |
| **Client component** (`"use client"`) with state/handlers | `*.test.tsx` - RTL + `jsdom` docblock, mock `next/navigation`, MSW for fetch | `artifacts/client-components.md` |
| **Feature component** (server, composes primitives) | Skip unit; cover via the page's E2E | `artifacts/feature-components.md` |
| **shadcn UI primitive** (`components/ui/*`) | None - trust the library; cover via consumers | `artifacts/ui-primitives.md` |
| **Icon** (`components/icons/*`) | None | `artifacts/icons.md` |
| **`lib/` utility / boundary module** with branching or shape assumptions | `*.test.ts` | `artifacts/utilities.md` |
| **Custom hook** (`hooks/*`) | `*.test.ts(x)` with `renderHook`, `jsdom` docblock | `artifacts/hooks.md` |
| **Route handler** (`app/api/**/route.ts`) - proxy or with branching | `*.integration.test.ts` with MSW (+ `*.test.ts` for extracted pure logic) | `artifacts/route-handlers.md` |
| **Server action / middleware / error-loading-not-found / metadata** | See guide - depends on type | `artifacts/future-types.md` |

**How to use:** after implementing, walk every row. If a row doesn't apply (you didn't create that artifact type), skip it. Before declaring done, run the gates in `references/file-conventions.md` (Vitest suite, Playwright suite once installed, `tsc --noEmit`, `lint`) - see global `CLAUDE.md` → "Definition of Done (Technical)".

## 4. Artifact Type Testing Guide

When creating or modifying an artifact, read the corresponding guide for the complete recipe (what to test, layer, setup template, when to skip, project examples).

| Artifact Type | Pattern | Test Layer(s) | Guide |
|---|---|---|---|
| Pages | `app/**/page.tsx` | E2E for async; client-child unit; skip static | `artifacts/pages.md` |
| Layouts | `app/**/layout.tsx` | E2E only (when it has logic) | `artifacts/layouts.md` |
| Route handlers | `app/api/**/route.ts` (exports `GET`/`POST`/…) | Integration (Vitest+MSW) + Unit for extracted logic | `artifacts/route-handlers.md` |
| Client components | files with `"use client"` directive | Vitest unit (`*.test.tsx`) | `artifacts/client-components.md` |
| Feature components | `components/<feature>/*.tsx` (server, no logic) | Skip - covered via consumers | `artifacts/feature-components.md` |
| shadcn UI primitives | `components/ui/*.tsx` | None | `artifacts/ui-primitives.md` |
| Icons | `components/icons/*.tsx` | None | `artifacts/icons.md` |
| Utilities & boundary modules | `lib/**/*.ts` | Vitest unit (when branching / shape) | `artifacts/utilities.md` |
| Custom hooks | `hooks/*.ts` | Vitest unit | `artifacts/hooks.md` |
| Future types | Server actions, middleware, error/loading/not-found, metadata | See guide | `artifacts/future-types.md` |

## 5. Anti-patterns - Do NOT Do This

- ❌ **Open a real network connection to the upstream NestJS API from Vitest** - every fetch a route handler makes must be intercepted by `msw/node`. The rule is absolute (`references/external-systems.md`, `.claude/rules/next-frontend-testing.md`).
- ❌ **Mock `fetch` with `vi.mock`/`vi.fn` in BFF tests** - use MSW. A raw `fetch` stub hides URL/method/header mistakes that `"request unhandled"` would catch (`references/mock-health-rules.md`).
- ❌ **Try to render an async Server Component in Vitest** - unsupported in React 19/Next 16. Use Playwright (§1, `artifacts/pages.md`, `references/gotchas.md`).
- ❌ **Mock owned components inside a unit test** - render `<LoginPage>` with the real `<BrandLogo>`/`<AuthFooter>`. The mock boundary is `fetch`, `next/navigation`, side-effect APIs (`references/mock-health-rules.md`).
- ❌ **Assert Tailwind class strings** - `toHaveClass("bg-primary")` is a mirror test. Assert role, accessible name, `aria-*`, `data-slot`/`data-variant` (§1).
- ❌ **Unit-test shadcn primitives in `components/ui/`** - configured-library wrappers; test consumers (`artifacts/ui-primitives.md`).
- ❌ **Unit-test icon components** - static SVG is a mirror test (`artifacts/icons.md`).
- ❌ **Render a JSX/TSX test without the `// @vitest-environment jsdom` docblock** - default env is `node`; the render silently has no DOM (`references/gotchas.md`).
- ❌ **Skip the `next/navigation` mock when unit-testing a client component that uses `useRouter`/`usePathname`/`useSearchParams`** - the hook throws outside the Next runtime (`references/gotchas.md`).
- ❌ **Add `webServer` to `playwright.config.ts` or run Playwright against a production build** - the e2e contract is host Playwright → the **containerized `next dev`** with `MSW_ENABLED=true`; the dev server is not Playwright-managed (`references/file-conventions.md`, `references/gotchas.md`).
- ❌ **`page.route()` / browser-level interception of `/api/**` in an e2e spec** - it short-circuits the real Route Handlers; upstream is faked server-side via `instrumentation.ts` only (`artifacts/pages.md`, `references/external-systems.md`).
- ❌ **Copy `onUnhandledRequest: "error"` into `instrumentation.ts`** - it must be `"bypass"` there, `"error"` only in Vitest's `mocks/setup.ts` (`references/external-systems.md`).
- ❌ **Hand-write a DTO or hardcode the upstream base URL in a test/handler** - derive shapes from `paths`, compose URLs as `${env.API_URL}/...` (`references/external-systems.md`).
- ❌ **Hand-write an MSW handler that does not type its body via `paths`** - a stale fixture must fail `tsc --noEmit` after `types.gen.ts` regenerates (`artifacts/route-handlers.md`).

## 6. E2E Terminology Note

This guide uses **E2E** to mean *full browser flow via Playwright* - a real browser driving the running Next.js app (navigation, forms, assertions on rendered DOM). Architecture (per `next-frontend/CLAUDE.md`): real browser → containerized real Next.js (RSC, layouts, real `/api/**` Route Handlers server-side) → **upstream NestJS faked at the server** by the `mocks/` MSW that `instrumentation.ts` boots when `MSW_ENABLED=true`. This is stricter than the "HTTP integration" sense in the universal fundamentals: this project has **no supertest-style HTTP layer** for the Next app - route handlers are tested *as functions* in the `*.integration.test.ts` lane, not over HTTP. When external sources say "Next.js E2E", expect this Playwright meaning.

## 7. References

| Topic | File |
|---|---|
| NestJS upstream + Object Storage strategy; MSW boundary; Vitest vs instrumentation config | `references/external-systems.md` |
| Mock health rules; what to mock vs keep real | `references/mock-health-rules.md` |
| File naming, directory layout, scripts, build gates, coverage philosophy | `references/file-conventions.md` |
| Stack-specific gotchas (async RSC, jsdom docblock, `next/navigation`, containerized Playwright, Vitest 4) | `references/gotchas.md` |

## 8. How to Use This Guide

This guide is a multi-file skill:

- **`SKILL.md`** (this file) - always loaded. Core rules, quick reference, anti-patterns.
- **`artifacts/`** - one file per artifact type. Read the relevant file when creating or modifying that type.
- **`references/`** - supporting content. Read for MSW boundary details, mock-boundary rules, naming conventions, or pitfall reminders.

When working on a feature:

1. Use §3 (Feature Implementation Checklist) to identify which artifacts need tests.
2. Read the corresponding `artifacts/*.md` for each - that file carries the setup template to copy.
3. Consult `references/` for cross-cutting topics (MSW, mocking, naming, gotchas).
4. Before declaring done: run the full Vitest suite, the Playwright suite (once installed), `npx tsc --noEmit`, and `npm run lint` inside the container (`references/file-conventions.md`).

````

**Skill geradora `generate-test-guide/SKILL.md` (literal do repositório: frontmatter, abertura, Phase 2, Phase 3 e Constraints; Phase 1 completa e Phase 4 de composição estão no arquivo original, junto com `testing-fundamentals.md`)** ([[Testes no Front-end com MSW]])
````markdown
---
name: generate-test-guide
description: >
  Analyzes a project's tech stack, searches the web for testing best practices,
  asks the user clarifying questions, and generates a project-specific testing
  multi-file skill at `.claude/skills/testing-guide-<project>/` with main SKILL.md and artifact/reference sub-files. Invoke with `/generate-test-guide <project-folder>`.
disable-model-invocation: true
---

# Generate Test Guide

You are a testing architecture expert. Your job is to analyze a project, research its stack, consult the user, and produce a **concrete, project-specific testing skill** file.

**Input:** `$ARGUMENTS` is the path to the project folder (default: current working directory).

**Output:** a multi-file skill at `.claude/skills/testing-guide-<project>/` (e.g., `testing-guide-nestjs-project`) with a main `SKILL.md` (~200-250 lines) and detailed guides in `artifacts/` and `references/` subdirectories. Each project gets its own skill, enabling monorepo support.

---

[...]

## Phase 2 - Web Research

For each major technology/framework detected, use **WebSearch** to find:

1. **Testing best practices** for the framework - search both broadly and version-specifically to maximize useful results (e.g., "NestJS testing best practices" AND "NestJS 11 testing best practices", using the version detected in Phase 1)
2. **How to test each artifact type** - search for testing guidance specific to each artifact type in the detected framework (e.g., "how to test NestJS guards", "testing NestJS pipes best practices", "testing NestJS interceptors"). Also search for types not yet present in the project, as these will receive proactive guidance.
3. **Mock vs real strategies** for the external systems detected (e.g., "testing with real PostgreSQL Docker vs mocking", "NestJS testing with TypeORM real database")
4. **Common testing pitfalls** for the stack (e.g., "Jest common mistakes NestJS", "e2e testing gotchas Express")

**Version-aware curation:** when evaluating search results, use the framework and library versions detected in Phase 1 as a compatibility filter. Discard advice that references APIs, decorators, configuration options, or patterns introduced in versions newer than what the project uses - this applies to frameworks (e.g., NestJS), ORMs (e.g., TypeORM), test runners (e.g., Jest), and any other dependency in the stack. If a result doesn't specify which version it applies to, cross-check its recommendations against the project's actual dependency versions before including them. This is especially important for projects using older versions, where modern best practices may reference features that don't exist in the project's stack.

Extract actionable insights - concrete patterns, recommended libraries, configuration tips, and pitfalls to avoid. Discard advice that applies to any project regardless of technology (e.g., "write small focused tests", "use descriptive names") - keep only advice specific to the detected frameworks, versions, or external systems that goes beyond what the fundamentals already cover.

---

## Phase 3 - User Questions

Output a structured message to the user with your findings and all questions below. Then use **AskUserQuestion** to wait for their response before proceeding to Phase 4.

### Summary to present (required elements)

The summary must include:
1. Detected languages, framework names, and versions
2. Detected test runner and configuration files
3. Type-grouped artifact summary showing instance counts and dominant testing patterns per type (e.g., "Services (*.service.ts): 2 instances - AuthService [branching → unit], UsersService [DB access → integration]. Dominant pattern: depends on characteristics."). Also list common framework artifact types not yet present in the project (e.g., "Not yet present: pipes, interceptors, filters, exception filters").
4. List of all external systems found
5. Summary of existing test file patterns and naming conventions
6. Any contradictions found between existing skills/rules (if any - ask the user for resolution)

### Questions to ask

1. **Confirmation** - "I detected [technologies/frameworks/external systems]. Is this accurate? Anything missing?"
2. **Test layers** - "Which test layers do you want covered? (unit / integration / e2e / all three)"
   - Note: always include module compilation and configured-lib tests in the generated guide regardless of the user's layer selection - these are mandatory per the fundamentals.
3. **External system strategy** - "For each external system, how should tests interact with it?"
   - Provide a pre-filled table based on your analysis with recommended defaults from the fundamentals' "Real vs Fake" table.
   - For any external system not covered in the fundamentals' table, apply the decision rule: if it can run locally in Docker in under 5 seconds with no external cost or flakiness risk, default to real; otherwise default to fake.
   - Ask the user to confirm or override each row.
4. **Team conventions** - "Are there any team-specific testing rules, naming conventions, or policies I should incorporate?"
5. **Coverage philosophy** - "What's the team's testing philosophy?"
   - **Pragmatic** - test what matters: focus on business-critical paths and system boundaries; skip tests for trivial or low-risk code.
   - **Thorough** - high coverage targets: include coverage targets in the File Conventions section; test more edge cases.
   - **Specific guidance** - let the user describe their own approach.

---

[...]

## Constraints

- **Do not modify** any existing files in `.claude/skills/` other than the generated `.claude/skills/testing-guide-<project>/` directory.
- **Do not modify** any existing files in `.claude/rules/`.
- **Do not create** test files - this skill only generates the testing skill documents.
- **Do not skip** any phase - all four phases (analysis, web research, user questions, generation) are mandatory.
- If `$ARGUMENTS` is empty, use the current working directory as the project path. However, if the current directory contains multiple sub-projects (multiple manifest files like `package.json` at different depths), do not analyze the root automatically - ask the user to specify the target sub-project.
- If the project path doesn't exist or has no recognizable project structure, inform the user and stop.

````

## Workflow RPI

**Simplificar o código da fase** ([[Higiene do Workflow com IA]])
```text
/simplify
```

**Criar branch da fase** ([[Higiene do Workflow com IA]])
```text
Quero criar uma branch de implementação desta fase. A dev já existe. Eu vou criar a partir dela.
```

**Commit e merges com IA** ([[Higiene do Workflow com IA]])
```text
/commit-commands:commit
```

**Contraexemplo: fase inteira de uma vez** ([[Higiene do Workflow com IA]])
```text
Implemente a fase 2 e crie uma lista de tarefas para que nós possamos acompanhar
```

**Implementar a fase com plano pronto** ([[Implementação de Fases com implement-phase]])
```text
Implemente a fase 01 configuração base
```

**Implementar só o que falta após atualizar o plano** ([[Implementação de Fases com implement-phase]])
```text
Implemente a fase 1. Tem coisas já feitas, como o SI01 e SI02. Precisamos implementar apenas o que está faltando.
```

**Invocar a skill** ([[Implementação de Fases com implement-phase]])
```text
/implement-phase fase 02
```

**Compactação orientada entre SIs** ([[Implementação de Fases com implement-phase]])
```text
/compact Preserve os documentos MD lidos e resuma a implementação, não guarde código fonte lido
```

**Teste humano da fase 2** ([[Implementação de Fases com implement-phase]])
```text
Verifique se o banco de dados tem as tabelas.
```

**Regra sugerida após a revisão do código** ([[Implementação de Fases com implement-phase]])
```text
Quando estiver avaliando erros, faça avaliação detalhada do tipo do erro.
```

**Planejar correções da fase já concluída** ([[Implementação de Fases com implement-phase]])
```text
/plan-phase A fase 2 já está concluída, mas temos algumas correções e melhorias:
- 11 erros do TypeScript.
- O canal está acoplado ao módulo de usuário. Crie o módulo do canal; o serviço de usuário vai chamar o do canal.
- Nas retentativas, ao criar o canal, consulte se o canal a ser criado existe, assim evita forçar um erro. Se mesmo assim der erro na criação, continuam as retentativas, sempre pautadas por essa consulta.
- Não temos um teste para rodar as migrações. Crie um teste para isso.
- O endpoint de confirmação de e-mail deve ser GET, com o token recebido na query string, não no corpo, pois o link vai no e-mail.
- Os templates de e-mail não estão sendo copiados para a pasta dist. Eles precisam ter o comportamento de watch como dos arquivos TypeScript tradicionais.
```

**Reajustar um SI implementado errado** ([[Implementação de Fases com implement-phase]])
```text
/plan-phase fase 2 já feita. Temos mais uma correção. Aconteceu um erro de implementação no SI 2.15, porque o ChannelsModule não tem controle sobre o canal. Ele deve criar canal, ter acesso ao repositório, ter controle sobre o nickname. O UsersModule apenas usa o ChannelService. Reajuste o SI 2.15 para podermos reimplementá-lo, mas verifique com cuidado as mudanças nos testes correlacionados para não quebrar a implementação.
```

**Conferir E2E no front** ([[Implementação de Fases com implement-phase]])
```text
Você testou o E2E? Usou o instrumentation.ts?
```

**Subir os servidores para teste manual do front** ([[Implementação de Fases com implement-phase]])
```text
Levante o servidor do Next.js.
```

**Gerar o plano da fase** ([[Planejamento de Fases com plan-phase]])
```text
/plan-phase fase 01
```

**Corrigir o plan mode que tentou implementar** ([[Planejamento de Fases com plan-phase]])
```text
eu só quero que você salve o plano
```

**Atualizar o plano existente com nova decisão, sem implementar** ([[Planejamento de Fases com plan-phase]])
```text
/plan-phase fase 01. Ela já existe. Queremos atualizá-la com as Decisões Técnicas 1. É só para atualizar o plano. Não implemente nada na codebase.
```

**Apontar gap que a validação não detectou** ([[Planejamento de Fases com plan-phase]])
```text
Eu quero a opção 1, mas você não identificou problemas quando usuários com mesmo prefixo de e-mail tentarem criar suas contas. Haverá conflito. Precisamos pensar nisso.
```

**Melhorar a validação da skill a partir da transcrição exportada** ([[Planejamento de Fases com plan-phase]])
```text
numa inteiração para criar o plano de implementação da fase 02 do projeto
(auth), quando você passou na parte de validação para validar
inconsistencias, decisões faltantes e tudo mais, você não identificou que
poderia ter conflito de canais quando o prefixo de mail dos usuários fosse
igual, aqui está a transcrição
@2026-04-06-213454-local-command-caveatcaveat-the-messages-below.txt

eu quero melhorar @.claude/skills/plan-phase/SKILL.md para que neste parte de
 validação, não deixemos passar este tipo de detalhes.

me ajude a identificar que tipo de detalhe é para acrescentar ou atualizar a
parte de validação para identificar coisas como estas e outras decisões
obscuras do projeto
```

**Apontar inconsistência no plano** ([[Planejamento de Fases com plan-phase]])
```text
Nesta linha temos a menção de um Refresh Token opaco. Não definimos isso nas specs.
```

**Ensinar convenções REST à skill** ([[Planejamento de Fases com plan-phase]])
```text
No plano de impl. @docs/phases/phase-02-auth.md , temos
  no contrato da api, mensagem redundante quando temos
  sucesso da operação, isto não é uma boa prática do rest.
  Se a operação foi feita com sucesso e não temos nada a
  retornar na resposta http, podemos usar o status code
  204. Este é apenas um exemplo, me ajude a pensar padrões
  do REST que deveríamos estar especificados no
  @.claude/skills/plan-phase/SKILL.md para que ela não
  cometa estes erros, ou seja, siga as boas práticas do
  REST
```

**Atualizar contratos com as novas diretrizes** ([[Planejamento de Fases com plan-phase]])
```text
/plan-phase Atualize a fase de autenticação, atualizando o contrato da API seguindo as novas diretrizes.
```

**Migrar fases implementadas para o formato do pipeline** ([[Planejamento de Fases com plan-phase]])
```text
dado o que existe as skills plan-* (não considere plan-phase e
implement-phase) e /implement,  quero adaptar 2 fases já desenvolvidas para o
 novo formato de como as skills trabalham para gerar as fases e seus
arquivos.
analise as skills, rastreie as mudanças e gere as alterações
```

**Revalidar a migração** ([[Planejamento de Fases com plan-phase]])
```text
Revalide as mudanças que foram feitas, temos o nextjs-project que está em
docs, mas o projeto é next-frontend.
Revalide se o formato dos novos docs está adequado ao que as skills geram
```

**Declarar adiamento para fechar UI Gap no planValidate** ([[Planejamento de Fases com plan-phase]])
```text
A tela de confirmação da conta não será implementada nesta fase corrente. Será adiada.
```

**Contestar missing decision no planResolve** ([[Planejamento de Fases com plan-phase]])
```text
Dado o que você disse, eu rodei o /research conforme recomendado.
```

**Research de fase pelo comando** ([[Skill de Research e Decisões Técnicas]])
```text
/research fase 2 somente para o front-end
```

**Research de sistema de configuração da fase 1** ([[Skill de Research e Decisões Técnicas]])
```text
/research Eu quero planejar a fase 1, mas quero adicionar um sistema de configuração para não ficar lendo as variáveis de ambiente diretamente no Nest.js. Importante também ver como organizar as variáveis de ambiente.
```

**Registrar no arquivo de decisões as decisões técnicas tomadas no planejamento** ([[Skill de Research e Decisões Técnicas]])
```text
/research Quero atualizar as decisões técnicas que foram tomadas no planejamento da fase 02 do arquivo <arquivo da fase 02>
```

**Documentar decisão técnica retroativa** ([[Skill de Research e Decisões Técnicas]])
```text
Como nós fizemos a implementação da fase 2, você decidiu a lógica do sufixo do canal com os caracteres permitidos a partir do prefixo do e-mail, e ainda, se do prefixo não se tirar nada, gera um aleatório. Quero documentar essa decisão técnica.
```

**Migrar as TDs existentes para o novo formato da skill** ([[Skill de Research e Decisões Técnicas]])
```text
dado o que existe no @.claude/skills/research/SKILL.md quero adaptar os TD
existentes para o formato que a SKILL gerada depois das mudanças que fizemos
nela.
analise como a SKILL gera as TD, rastreie as mudanças nos TDS existentes e
gere as alterações
```

**Triagem da task de documentação da API** ([[Subagentes e Tasks Ad Hoc]])
```text
/decide Eu quero implementar a Doc OpenAPI no projeto NestJS. Não quero fazer o front aqui logo de cara.
```

**Corrigir falso positivo de UI no planContext** ([[Subagentes e Tasks Ad Hoc]])
```text
Isto é apenas uma documentação da API que vai gerar o JSON. Não tem telas nem front-end.
```

**Reabrir a decisão para enriquecer o OpenAPI** ([[Subagentes e Tasks Ad Hoc]])
```text
/decide A integração do OpenAPI com o NestJS foi feita. Porém, o OpenAPI JSON gerado foi genérico. Ele não tem detalhes dos parâmetros das requests, dados retornados na response, erros, status codes e etc. Eu quero fazer essa adaptação.
```

**planBuild em append mode sobre plano já implementado** ([[Subagentes e Tasks Ad Hoc]])
```text
O planejamento já existe e já foi implementado. Mas tivemos uma mudança no contexto que deve gerar novos SIs no planejamento já existente. Faça isso.
```
