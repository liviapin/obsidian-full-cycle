---
tags: [dev-software-ia, mba]
materia: "Desenvolvimento de Software e Aplicações com IA"
tema: "Ambiente e Scripts de Inicialização"
status: revisado
---

# Ambiente e Scripts de Inicialização

> [!summary] TL;DR
> - A qualidade percebida da IA depende do estado operacional do projeto: ambiente degradado parece "IA que não consegue fazer algo simples".
> - O agente precisa saber inicializar do zero, reconhecer o state atual (instalado, rodando, quebrado), resetar e validar.
> - Sem instrução de bootstrap, o agente gasta metade do esforço na subtarefa oculta "descobrir como começar".
> - README operacional reduz inferência; scripts com nome semântico (init, down, status/check) viram o contrato operacional do repositório.
> - Derrubar não é limpar: o script de shutdown separa parada, kill forçado e limpeza completa.

## Conceitos-chave

- **Básico operacional**: sabe-se o que fazer e não se faz; tarefas simples se degradam sem disciplina.
- **Ambiente de desenvolvimento**: dependências, configurações, ferramentas e condições locais; precisa responder rápido e de forma consistente.
- **Feedback rápido**: verificar logo se a mudança da IA funcionou encurta a iteração.
- **Economia de tokens**: ambiente ruim gera tentativas extras (reenviar contexto, reformular pedidos), gasto que nada tem a ver com o modelo.
- **Fricção operacional**: atrito ao rodar, validar e reproduzir erros; se multiplica com IA.
- **Diagnóstico de falha**: separar falha de execução, falha de contexto e falha real de capacidade do modelo.
- **Inteligência operacional do agente**: agir certo no ambiente real: instalar pela 1a vez, reconhecer que já está funcional, resetar ou desinstalar.
- **Inicialização**: passos para chegar a um estado executável a partir do zero.
- **State do ambiente**: instalado, rodando, quebrado ou precisando de intervenção; o mesmo comando pode ser certo em um state e errado em outro. Pedir mudança sem informar ou detectar o state força o agente a adivinhar.
- **Reset**: voltar a um ponto conhecido e confiável.
- **Clareza de objetivo além do prompt**: em que condições a tarefa começa e como o resultado será validado.
- **Consistência operacional e testabilidade**: resultados previsíveis e reproduzíveis; validar a mudança num ambiente conhecido (detalhes de testabilidade no [[Arquivos de Inicialização do Agente]]).
- **Bootstrap**: caminho mínimo para colocar o projeto em condição operacional.
- **Ambiguidade operacional**: Docker Compose + package.json + Next + várias pastas sugerem múltiplos caminhos plausíveis.
- **Exploração excessiva**: o agente abre arquivos, inspeciona diretórios, verifica containers e banco antes de agir; trocar modelo thinking por um rápido/barato não resolve contexto ausente (ambos exploram).
- **README operacional**: manual para a IA, não vitrine. Estrutura mínima: ideia do projeto, stack, first-time setup, comandos rápidos recorrentes (instalar dependências, migrations). O agente usa o README.md como fonte principal de decisão; o ganho é redução de inferência, não inteligência extra.
- **First-time setup**: do repo clonado ao ambiente executável: criar `.env`, copiar `.env.local`, subir containers, instalar requirements, `npm install`, migrations; validar depois de subir (`.env` no back-end, `.env.local` no front-end, instalações e migrations feitas).
- **Derrubar vs limpar**: parar/remover containers deixa volumes, redes e resíduos; limpeza completa remove tudo para voltar ao zero e reproduzir problemas.
- **Limite do README**: depende de leitura e execução manual dos passos; motiva a transição para scripts.
- **Scripts como interface operacional**: comandos com intenção explícita, centralizados numa pasta dedicada (ex: `env.scripts`); o README e o [[Arquivos de Inicialização do Agente]] apontam para eles ("scripts executam, o arquivo de inicialização diz quais usar e quando").
- **Granularidade dos scripts**: globais (`init-all`, `down-all`, `status`) para fluxos completos; específicos (`back-end-init`, `back-end-down`, `front-end-status`, `front-end-down`) para cenários parciais.
- **Script de status/check**: responde se os serviços estão ativos, se há tasks em background e se o ambiente está pronto para testes; no template da skill `nextjs-bootstrap` devolve `[OK]`, `[PENDING]`, `[DEGRADED]` e `[WARNING]` para processos órfãos, e `--fix` corrige sozinho.
- **Health check no init**: o `init.sh` sobe o servidor em background, faz polling HTTP (timeout 60 s, intervalo 2 s) e, se não ficar saudável, mostra as últimas 20 linhas do log e mata o processo.
- **Porta por variável**: todos os scripts leem `SERVER_PORT` do `.env.local`; na 1a execução, se a porta estiver ocupada, o init procura uma livre em `PORT_RANGE` e reescreve `SERVER_PORT` e `NEXTAUTH_URL`.
- **Scripts no projeto Streamtube**: no monorepo Docker do projeto prático os scripts são facultativos; o sub CLAUDE.md descreve `docker compose up -d`, verificação de readiness e `docker compose down` (ver [[Arquivos de Inicialização do Agente]]). Os scripts completos vêm da skill de bootstrap ([[Bootstrap de Projetos Greenfield]]).

## Fluxograma / Processo

```mermaid
flowchart TD
    A[Criar pasta de scripts com nomes semanticos] --> B[Definir globais init status down]
    B --> C[Adicionar scripts por parte front e back]
    C --> D[Apontar comandos no README e no CLAUDE.md]
    D --> E{Agente pediu para subir ambiente?}
    E -->|sim| F[Rodar check para ler o state]
    F --> G{Servidor saudavel?}
    G -->|sim| H[Seguir para a tarefa]
    G -->|nao| I[check --fix ou init]
    I --> H
```

## Erros comuns / Cuidados

- Concluir que a IA "não consegue fazer algo simples" quando o ambiente está degradado.
- Repo sem instrução de bootstrap: ao pedir "inicie o ambiente e rode os testes", em vez de `docker compose up -d` e testes, a IA investigou front, back, Next e package.json.
- Sem scripts o agente procura `start.sh` ou outra entrada e vasculha containers; automação espalhada ou implícita volta à inferência.
- Agente assumir que down = ambiente zerado.
- Com worktrees, usar `./scripts/down.sh --force --clean` para liberar a porta e iniciar novo servidor pelo init.

## Materiais complementares

### Prompts

**Pedido usado como contraexemplo num repo sem instrução de bootstrap (narrado na aula)**
```text
inicie o ambiente e rode os testes
```

**Script de inicialização `templates/scripts/init.sh` da skill nextjs-bootstrap (arquivo literal do repositório skills-mba)**
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

**Script de diagnóstico `templates/scripts/check.sh` (arquivo literal do repositório skills-mba)**
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

**Script de shutdown `templates/scripts/down.sh` (arquivo literal do repositório skills-mba)**
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

**Variáveis lidas pelos scripts `templates/env-example.txt` (arquivo literal do repositório skills-mba)**
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

### Conteúdo extra

- Skill `nextjs-bootstrap` e seus templates (`scripts/watch.sh`, `tmux-dev.sh`, `deploy.sh` além dos três acima): https://github.com/devfullcycle/skills-mba
- O template de CLAUDE.md que documenta esses scripts está em [[Arquivos de Inicialização do Agente]].

## Tags de busca

`#dev-software-ia` `#ambiente-de-desenvolvimento` `#scripts-de-inicializacao` `#bootstrap` `#readme-operacional`
