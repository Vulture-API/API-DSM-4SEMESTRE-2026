# MANUAL DE INSTALAÇÃO — PORTAL AGROCLIMA 360

**Projeto:** Sistema de Estações Meteorológicas IoT — Cenário 01 (Agritech / Equipe Vulture)  
**Instituição / Parceiro:** Fatec São José dos Campos / Tecsus — Tecnologias para a Sustentabilidade  
**Curso / Semestre:** 4º DSM — Semestre 2026-2  
**Frente:** Documentação de Infraestrutura, Implantação e Operação  
**Versão:** 1.0  
**Última atualização:** 21/11/2026  

---

## Sumário

1. [Objetivo e Visão Geral da Arquitetura](#1-objetivo-e-visão-geral-da-arquitetura)
   - [1.1. Topologia dos Serviços](#11-topologia-dos-serviços)
   - [1.2. Repositórios da Solução](#12-repositórios-da-solução)
   - [1.3. Mapa de Serviços e Portas Padrão](#13-mapa-de-serviços-e-portas-padrão)
2. [Pré-requisitos de Ambiente](#2-pré-requisitos-de-ambiente)
3. [Preparação do Banco de Dados (`API-DSM-4-BANCO`)](#3-preparação-do-banco-de-dados-api-dsm-4-banco)
   - [3.1. Aplicação do Schema, Migrations e Seed](#31-aplicação-do-schema-migrations-e-seed)
   - [3.2. Permissões Iniciais dos Perfis](#32-permissões-iniciais-dos-perfis)
4. [Instalação do Ambiente Integrado Local (`API-DSM-4-INFRA`)](#4-instalação-do-ambiente-integrado-local-api-dsm-4-infra)
   - [4.1. Clonagem do Repositório e Submódulos](#41-clonagem-do-repositório-e-submódulos)
   - [4.2. Configuração das Variáveis de Ambiente (`.env`)](#42-configuração-das-variáveis-de-ambiente-env)
   - [4.3. Inicialização da Stack com Docker Compose](#43-inicialização-da-stack-com-docker-compose)
   - [4.4. Ativação Controlada e Operação da Telemetria (`telemetry.py`)](#44-ativação-controlada-e-operação-da-telemetria-telemetrypy)
   - [4.5. Simulador de Estações e Conexão de Hardware (ESP32)](#45-simulador-de-estações-e-conexão-de-hardware-esp32)
5. [Execução Isolada dos Serviços (Desenvolvimento Individual)](#5-execução-isolada-dos-serviços-desenvolvimento-individual)
   - [5.1. Backend (`API-DSM-4-BACKEND`)](#51-backend-api-dsm-4-backend)
   - [5.2. Frontend (`API-DSM-4-FRONTEND`)](#52-frontend-api-dsm-4-frontend)
   - [5.3. Recepção de Telemetria (`API-DSM-4-RECEPCAO-DADOS`)](#53-recepção-de-telemetria-api-dsm-4-recepcao-dados)
   - [5.4. Persistência de Telemetria (`API-DSM-4-PERSISTENCIA-DADOS`)](#54-persistência-de-telemetria-api-dsm-4-persistencia-dados)
6. [Validação da Instalação, Testes E2E e QA Integrada](#6-validação-da-instalação-testes-e2e-e-qa-integrada)
   - [6.1. Ambiente Descartável de Testes (E2E)](#61-ambiente-descartável-de-testes-e2e)
   - [6.2. Suíte de QA Integrada de Telemetria](#62-suíte-de-qa-integrada-de-telemetria)
   - [6.3. Checklist de Validação Pós-Instalação](#63-checklist-de-validação-pós-instalação)
7. [Implantação em Produção na AWS (`API-DSM-4-DEPLOY`)](#7-implantação-em-produção-na-aws-api-dsm-4-deploy)
   - [7.1. Provisionamento da Infraestrutura via CloudFormation](#71-provisionamento-da-infraestrutura-via-cloudformation)
   - [7.2. Bootstrap da Instância EC2](#72-bootstrap-da-instância-ec2)
   - [7.3. Configuração de Secrets no GitHub e Deploy Contínuo](#73-configuração-de-secrets-no-github-e-deploy-contínuo)
   - [7.4. Pausa de Emergência e Rollback](#74-pausa-de-emergência-e-rollback)
8. [Solução de Problemas (Troubleshooting)](#8-solução-de-problemas-troubleshooting)
9. [Referências](#9-referências)

---

## 1. Objetivo e Visão Geral da Arquitetura

Este manual descreve os procedimentos oficiais para instalar, configurar, validar e implantar a plataforma **AgroClima 360** (Equipe Vulture), tanto em ambiente local de desenvolvimento quanto em produção na nuvem (AWS).

A solução adota uma arquitetura composta por:

* **Backend monolítico modular** em **Node.js 24 + Fastify** (`API-DSM-4-BACKEND`), unificando os domínios de usuários, perfis/permissões, parâmetros/sensores, propriedades, estações, monitoramento em tempo real (REST + WebSocket), alertas (motor de regras) e ocorrências.
* **Frontend web** em **Next.js 16 (App Router) + React 19** (`API-DSM-4-FRONTEND`), com autenticação baseada em cookies `HttpOnly` e proxy autenticado para o backend.
* **Pipeline de ingestão de telemetria desacoplado** em **Python 3.12+**:
  * **Recepção (`API-DSM-4-RECEPCAO-DADOS`):** consome pacotes MQTT (QoS 1) do broker **Eclipse Mosquitto** e grava no **Redis 7 Stream** (`telemetry:ingest`), sem acesso ao PostgreSQL.
  * **Persistência (`API-DSM-4-PERSISTENCIA-DADOS`):** consome o Redis Stream por grupo de consumidores (`postgres-persister`), valida relações, calibração e limites, e grava leituras, ocorrências ou quarentena no **PostgreSQL**.
* **Proxy Reverso (`Nginx`):** centraliza o acesso ao portal web, repassa os cabeçalhos `Host` e `X-Forwarded-Proto` (exigidos na validação de origem do login) e encaminha conexões WebSocket.
* **Banco de Dados Externo (`PostgreSQL 16+`):** mantido fora do Docker Compose principal (ex.: Neon em desenvolvimento ou Amazon RDS em produção), com schema e migrations versionados no `API-DSM-4-BANCO`.

### 1.1. Topologia dos Serviços

```mermaid
flowchart LR
  User["Navegador / Operador"] -->|"HTTP/HTTPS + WS"| Nginx["Nginx (:8080 local / :80 EC2)"]
  Nginx --> Front["Frontend Next.js (:3010)"]
  Front -->|"/api/backend + WS"| Back["Backend Fastify (:3000)"]

  IoT["Estação IoT (ESP32) ou Simulador"] -->|"MQTT QoS 1 (:1883)"| Mqtt["Eclipse Mosquitto"]
  Mqtt --> Recep["Recepção Python (MQTT -> Redis)"]
  Recep -->|"XADD telemetry:ingest"| Redis["Redis 7 (AOF + noeviction)"]
  Redis -->|"Consumer Group"| Persist["Persistência Python (Redis -> PG)"]

  Back -->|"DATABASE_URL (SSL)"| PG["PostgreSQL Externo (Neon / RDS)"]
  Persist -->|"DATABASE_URL (SSL)"| PG
```

### 1.2. Repositórios da Solução

| Repositório | Responsabilidade |
| :--- | :--- |
| `Vulture-API/API-DSM-4SEMESTRE-2026` | Documentação geral do projeto, sprints, requisitos, manuais e diretrizes de DevOps. |
| `Vulture-API/API-DSM-4-INFRA` | Orquestração integrada via Docker Compose, submódulos fixados por commit, scripts de telemetria (`telemetry.py`), simulador e suítes E2E/QA. |
| `Vulture-API/API-DSM-4-BANCO` | Schema completo, migrations idempotentes (`migrations/manifest.txt`), seeds e benchmarks PostgreSQL. |
| `Vulture-API/API-DSM-4-BACKEND` | API Fastify monolítica modular, autenticação JWT/RBAC, WebSocket, motor de regras e ocorrências. |
| `Vulture-API/API-DSM-4-FRONTEND` | Portal web AgroClima 360 em Next.js (`app/`). |
| `Vulture-API/API-DSM-4-RECEPCAO-DADOS` | Serviço Python de recepção (`MQTT -> Redis Stream`) e retenção segura do Stream. |
| `Vulture-API/API-DSM-4-PERSISTENCIA-DADOS` | Serviço Python de tratamento, validação e persistência (`Redis Stream -> PostgreSQL`). |
| `Vulture-API/API-DSM-4-DEPLOY` | Infraestrutura como Código (CloudFormation/IAM), scripts de bootstrap/deploy na EC2 e pipeline CD na AWS. |

### 1.3. Mapa de Serviços e Portas Padrão

| Serviço | Porta Local Padrão | Exposição Padrão | Responsabilidade |
| :--- | :---: | :--- | :--- |
| `nginx` | `8080` | `127.0.0.1` | Proxy reverso do portal web (ponto de entrada principal local) |
| `frontend` | `3010` | `127.0.0.1` | Aplicação Next.js (acessada via `nginx` ou diretamente em dev) |
| `backend` | `3000` | `127.0.0.1` | APIs REST, WebSocket, autenticação JWT, motor de regras e ocorrências |
| `mosquitto` | `1883` | `127.0.0.1` (`MQTT_BIND`) | Broker MQTT local (sem autenticação em dev; use `0.0.0.0` para ESP32 na LAN) |
| `redis` | Interna (`6379`) | Rede Docker | Armazenamento AOF com política `noeviction` e Stream `telemetry:ingest` |
| `recepcao` | Sem porta HTTP | Rede Docker | Ingestão Python (`MQTT -> Redis`) |
| `persistencia` | Sem porta HTTP | Rede Docker | Tratamento Python (`Redis -> PostgreSQL`) |
| `simulador` *(perfil `demo`)* | Sem porta HTTP | Rede Docker | Publicação sintética optativa de telemetria MQTT |

---

## 2. Pré-requisitos de Ambiente

Antes de iniciar a instalação, certifique-se de que a máquina possua:

| Ferramenta | Versão Mínima | Onde é Necessária |
| :--- | :--- | :--- |
| **Git** | 2.30+ | Clonagem dos repositórios e gerenciamento de submódulos |
| **Docker Engine + Docker Compose v2** | Compose v2.x | Execução da stack integrada (`API-DSM-4-INFRA`) e ambiente de QA |
| **Node.js + npm** | **Node 24 LTS** | Execução local do Backend, Frontend, scripts do Banco (`apply.mjs`) e testes E2E |
| **Python + pip + venv** | **Python 3.12+** | Scripts operacionais (`telemetry.py`), suíte de QA (`qa/`) e serviços Python |
| **PostgreSQL externo** | **PostgreSQL 16+** | Banco principal (ex.: Neon ou Amazon RDS) com credenciais e permissão de DDL |
| **AWS CLI v2** *(opcional)* | 2.x | Apenas para provisionamento e deploy na AWS (`API-DSM-4-DEPLOY`) |

> [!NOTE]
> Não é necessário instalar o cliente `psql` para aplicar o schema e as migrations: o repositório `API-DSM-4-BANCO` fornece o script `setup/apply.mjs` em Node.js utilizando o driver `pg`.

---

## 3. Preparação do Banco de Dados (`API-DSM-4-BANCO`)

O ambiente principal do `API-DSM-4-INFRA` **não** sobe um container PostgreSQL embutido — ele se conecta a um banco PostgreSQL externo previamente migrado. As migrations são pré-requisito obrigatório validado automaticamente na inicialização da persistência.

### 3.1. Aplicação do Schema, Migrations e Seed

1. Acesse o repositório `API-DSM-4-BANCO` (ou o submódulo `API-DSM-4-INFRA/services/API-DSM-4-BANCO`):

```bash
cd API-DSM-4-BANCO
npm install
```

2. Configure o arquivo `.env` a partir do `.env.example` informando a `DATABASE_URL` do PostgreSQL de destino:

```bash
cp .env.example .env
# Edite .env e defina:
# DATABASE_URL=postgresql://usuario:senha@host:5432/banco?sslmode=require
```

3. Aplique o schema base, todas as migrations listadas em `migrations/manifest.txt` (`015` a `024`, em ordem idempotente) e o seed de desenvolvimento:

```bash
npm run db:setup
```

**Comandos auxiliares disponíveis:**

```bash
npm run db:schema   # Aplica somente schema-neon.sql e migrations 015+ do manifest.txt
npm run db:seed     # Aplica somente os dados mínimos de desenvolvimento (seed-dev.sql)

# Apontar para outro banco sem alterar o .env:
node setup/apply.mjs "postgresql://usuario:senha@host.neon.tech/neondb?sslmode=require"
```

> [!WARNING]
> **Cuidados críticos com o banco de dados:**
> * **Não aplique as migrations `010`, `011` e `012` (particionamento) em produção ou no Neon compartilhado sem janela de manutenção e backup.** Elas movimentam dados e renomeiam tabelas (consulte `API-DSM-4-BANCO/docs/otimizacoes.md`).
> * **Não execute `seed-demo.sql` no banco compartilhado da equipe**; ele se destina apenas a ambientes isolados de demonstração/QA.
> * O script `apply.mjs` é **idempotente**: reexecutá-lo sobre um banco já migrado não apaga nem duplica registros.

### 3.2. Permissões Iniciais dos Perfis

Na instalação inicial, a migration `015_role_permissions.sql` cria o catálogo de permissões e concede **todas as permissões apenas ao perfil Administrador**. Os perfis **Gerente Agrícola** e **Cliente** iniciam sem concessões automáticas e devem ter suas permissões configuradas pelo Administrador (via tela **Administração → Perfis e permissões** ou via `PUT /api/roles/:id/permissions`):

| Perfil | Permissões Recomendadas |
| :--- | :--- |
| **Administrador** | Catálogo completo de permissões do backend (concedido na instalação inicial). |
| **Gerente Agrícola** | `monitoring.read`, `stations.read`, `sensors.read`, `sensor-types.read`, `properties.create`, `properties.read`, `properties.update`, `properties.delete`, `alert-configs.create`, `alert-configs.read`, `alert-configs.update`, `alert-configs.delete`, `triggered-alerts.read`, `triggered-alerts.acknowledge`, `occurrences.read`. |
| **Cliente** | `monitoring.read`, `stations.read`, `sensors.read`, `sensor-types.read`, `properties.read`. |

---

## 4. Instalação do Ambiente Integrado Local (`API-DSM-4-INFRA`)

Esta é a forma recomendada para executar toda a plataforma localmente com todos os serviços integrados.

### 4.1. Clonagem do Repositório e Submódulos

Clone o repositório `API-DSM-4-INFRA` trazendo os submódulos exatamente nos commits fixados:

```bash
git clone --recurse-submodules https://github.com/Vulture-API/API-DSM-4-INFRA.git
cd API-DSM-4-INFRA
```

Caso já tenha clonado sem `--recurse-submodules`, inicialize os submódulos com:

```bash
git submodule update --init --recursive
```

> [!IMPORTANT]
> Os submódulos em `services/` são fixados em commits validados pela esteira de CI/E2E. **Nunca utilize `git submodule update --remote`** em ambientes de validação ou produção. Para desenvolver usando checkouts locais em pastas irmãs (`../API-DSM-4-BACKEND`, etc.), altere `SERVICES_DIR=..` no `.env`.

### 4.2. Configuração das Variáveis de Ambiente (`.env`)

Crie o arquivo `.env` a partir do modelo fornecido (nunca versione credenciais no Git):

```bash
cp .env.example .env
```

Preencha obrigatoriamente as variáveis abaixo no `.env`:

| Variável | Obrigatória | Padrão | Descrição e Orientação |
| :--- | :---: | :--- | :--- |
| `DATABASE_URL` | **Sim** | — | String de conexão do PostgreSQL externo já migrado (ex.: `postgresql://user:pass@host:5432/db?sslmode=require`). |
| `JWT_SECRET` | **Sim** | — | Segredo aleatório com **32 ou mais caracteres**. Sem ele, o login responde `503` e o portal não abre. Gere com `openssl rand -hex 32`. |
| `PERSIST_SOURCE_ID` | **Sim** | — | Identidade estável desta história Redis (ex.: `vulture-local-dev`). **Nunca regenere** esse valor em reinícios sobre o mesmo volume Redis. |
| `SERVICES_DIR` | Não | `./services` | Origem do código dos serviços (`./services` para submódulos ou `..` para pastas irmãs). |
| `ACCESS_CONTROL_ENABLED` | Não | `true` | Mantém a autorização RBAC ativa em todas as rotas e WebSocket do backend. |
| `OCCURRENCES_ENABLED` | Não | `true` | Ativa o monitor de falhas de comunicação e leituras fora dos limites (US09). |
| `MQTT_BIND` | Não | `127.0.0.1` | Interface de escuta do Mosquitto. Use `0.0.0.0` apenas em rede confiável para receber dados de um ESP32 físico. |
| `BACKEND_PORT` / `FRONTEND_PORT` / `PROXY_PORT` / `MQTT_PORT` | Não | `3000` / `3010` / `8080` / `1883` | Portas publicadas em `localhost` pelo Docker Compose. |
| `TELEMETRY_STREAM` / `PERSIST_GROUP` | Não | `telemetry:ingest` / `postgres-persister` | Nome do Redis Stream e do grupo de consumidores; preserve os mesmos valores em retomadas. |
| `SIMULADOR_EMAIL` / `SIMULADOR_PASSWORD` | Somente perfil `demo` | — | Credenciais de uma conta ativa (com `stations.read`, `sensors.read`, `sensor-types.read`) usada pelo simulador quando `ACCESS_CONTROL_ENABLED=true`. |
| `INGEST_RETENTION_ENABLED` | Não | `false` | Retenção automática do Redis Stream. Mantenha `false` até validar todos os grupos em `INGEST_RETENTION_REQUIRED_GROUPS`. |

### 4.3. Inicialização da Stack com Docker Compose

Construa as imagens e inicie todos os serviços em segundo plano:

```bash
docker compose up -d --build
```

Acompanhe o status e os healthchecks até que todos os serviços apareçam como `healthy` (ou `running`):

```bash
docker compose ps
```

**Endereços locais disponíveis após a subida:**

* **Portal Web (via Nginx — recomendado):** `http://localhost:8080`
* **Portal Web (direto no Next.js):** `http://localhost:3010`
* **API Backend (Healthcheck):** `http://localhost:3000/health`
* **Broker MQTT:** `localhost:1883`

Para encerrar os containers preservando o volume do Redis (`redis_data`):

```bash
docker compose down
```

> [!CAUTION]
> **Nunca execute `docker compose down -v` no ambiente principal ou em produção.** O volume `redis_data` armazena o histórico AOF (`noeviction`) e o vínculo de identidade `PERSIST_SOURCE_ID`. O uso de `down -v` é restrito ao ambiente descartável de QA.

### 4.4. Ativação Controlada e Operação da Telemetria (`telemetry.py`)

O script `scripts/telemetry.py` coordena a pré-verificação, ativação e pausa segura do consumidor de persistência (`persistencia`) sem interromper `mosquitto`, `redis`, `recepcao` ou `PostgreSQL`, gerando evidências sem credenciais em `reports/`:

```bash
# 1. Pré-verificação de schema, configuração, volumes e estado do Stream/grupo
python3 scripts/telemetry.py preflight --project vulture --evidence reports/preflight.json

# 2. Ativação controlada do consumidor de persistência
python3 scripts/telemetry.py activate --project vulture --evidence reports/activation.json

# 3. Pausa segura (mantém MQTT -> Redis, backlog e pendências PEL intactas)
python3 scripts/telemetry.py pause --project vulture --evidence reports/pause.json
```

> [!WARNING]
> **Boas práticas de governança da telemetria:**
> * Um único operador deve coordenar `telemetry.py` por projeto; não execute `docker compose up` em paralelo durante uma troca.
> * Em caso de falha na persistência, **pause o consumidor** e inspecione os relatórios e logs. **Nunca** use `XACK` manual, reset de grupo (`XGROUP SETID`), exclusão de pendências ou limpeza manual do Stream para contornar erros.

### 4.5. Simulador de Estações e Conexão de Hardware (ESP32)

* **Publicação automática com o Simulador (perfil `demo`):**
  Configure `SIMULADOR_EMAIL` e `SIMULADOR_PASSWORD` no `.env` e inicie o perfil `demo`:

  ```bash
  docker compose --profile demo up -d
  ```

* **Conexão de Estação Física (ESP32) na Rede Local:**
  1. Defina `MQTT_BIND=0.0.0.0` no `.env` e reinicie o serviço `mosquitto` (`docker compose up -d mosquitto`).
  2. Libere a porta TCP `1883` no firewall apenas para a rede local confiável (o broker de desenvolvimento não exige autenticação).
  3. Configure o datalogger para publicar em **MQTT QoS 1** no tópico `estacoes/<MAC>/dados` com payload JSON UTF-8 contendo `estacao_id` e as chaves configuradas como `local_identifier` dos sensores da estação.

---

## 5. Execução Isolada dos Serviços (Desenvolvimento Individual)

Caso precise desenvolver ou depurar um serviço específico fora do Docker Compose, siga os passos do módulo correspondente.

### 5.1. Backend (`API-DSM-4-BACKEND`)

Requisitos: **Node.js 24** e **PostgreSQL** já migrado pelo `API-DSM-4-BANCO`.

```bash
cd API-DSM-4-BACKEND
npm ci
cp .env.example .env
# Configure DATABASE_URL e JWT_SECRET (32+ caracteres) no .env
npm run dev
```

* Escuta por padrão em `http://localhost:3000`.
* Em desenvolvimento local, `RULES_ENGINE_ENABLED`, `OCCURRENCES_ENABLED` e `ACCESS_CONTROL_ENABLED` vêm como `false` no `.env.example` para não avançar checkpoints em bancos compartilhados. Habilite-os quando testar alertas, ocorrências ou login com o frontend.
* Para rodar a versão compilada: `npm run build && npm start`.
* **Verificação de qualidade e testes:**

  ```bash
  npm run lint
  npm run typecheck
  npm run test:unit
  npm run test:int
  npm run build
  ```

### 5.2. Frontend (`API-DSM-4-FRONTEND`)

Requisitos: **Node.js 24** e **Backend** rodando (com `JWT_SECRET` configurado).

```bash
cd API-DSM-4-FRONTEND/app
cp .env.example .env.local
npm install
npm run dev
```

* Escuta por padrão em `http://localhost:3010` (tela de login em `http://localhost:3010/login`).
* As variáveis de destino (`USERS_API_URL`, `PARAMETERS_API_URL`, `ALERTS_API_URL`, `STATIONS_API_URL`) são **variáveis de servidor** (sem `NEXT_PUBLIC_`) apontando para `http://localhost:3000`.
* **Atenção ao WebSocket:** o rewrite de `/api/stations/current/ws` é fixado em tempo de build; se alterar o destino do WebSocket para produção, execute `npm run build` novamente.
* **Verificação de qualidade e testes:**

  ```bash
  npm run lint
  npx tsc --noEmit
  npm test
  npm run build
  ```

### 5.3. Recepção de Telemetria (`API-DSM-4-RECEPCAO-DADOS`)

Requisitos: **Python 3.12+**, **Broker MQTT** e **Redis 7** acessíveis (não usa PostgreSQL).

```bash
cd API-DSM-4-RECEPCAO-DADOS
python3 -m venv .venv
source .venv/bin/activate
pip install -e '.[test,lint]'
cp .env.example .env
python -m station_ingest
```

* Não execute duas instâncias simultâneas com o mesmo `INGEST_MQTT_CLIENT_ID`.
* **Verificação:** `ruff check .`, `ruff format --check .` e `pytest`.

### 5.4. Persistência de Telemetria (`API-DSM-4-PERSISTENCIA-DADOS`)

Requisitos: **Python 3.12+**, **Redis 7** e **PostgreSQL** migrado.

```bash
cd API-DSM-4-PERSISTENCIA-DADOS
python3 -m venv .venv
source .venv/bin/activate
pip install -e '.[test,lint]'
cp .env.example .env
# Configure PERSIST_REDIS_URL, PERSIST_DATABASE_URL e PERSIST_SOURCE_ID no .env

# Modos disponíveis:
station-persist status             # Healthcheck / status do consumidor
station-persist inspect --validate # Inspeção somente leitura (sem XACK ou escrita)
station-persist consume            # Modo de produção (consome e persiste)
```

---

## 6. Validação da Instalação, Testes E2E e QA Integrada

### 6.1. Ambiente Descartável de Testes (E2E)

O `API-DSM-4-INFRA` disponibiliza scripts que sobem um ambiente totalmente isolado com **PostgreSQL descartável interno** (aplicando automaticamente schema, migrations e seed), geram um `JWT_SECRET` temporário e executam o teste ponta a ponta (`scripts/e2e.mjs`), sem tocar no `.env` nem no banco externo:

**Linux / macOS:**
```bash
cd API-DSM-4-INFRA
./scripts/testar.sh --down           # Usa os submódulos em ./services
./scripts/testar.sh --local --down   # Usa os checkouts irmãos (..)
```

**Windows (PowerShell):**
```powershell
cd API-DSM-4-INFRA
./scripts/testar.ps1 -Down
./scripts/testar.ps1 -Local -Down
```

### 6.2. Suíte de QA Integrada de Telemetria

Para executar a bateria de testes de resiliência e falhas (`qa/` — indisponibilidade, lock PostgreSQL, ACL Redis, quarentena e precisão numérica) sobre um projeto Docker descartável (`vulture-qa-<id>`):

```bash
cd API-DSM-4-INFRA
python3 -m venv .venv
.venv/bin/python -m pip install -r qa/requirements.txt

# Com o overlay de teste (docker-compose.test.yml) ativo em COMPOSE_PROJECT_NAME=vulture-qa-<id>:
.venv/bin/pytest qa --junitxml=reports/telemetry.xml
.venv/bin/python scripts/require-results.py
python3 scripts/check-components.py
python3 scripts/evidence.py   # Gere evidências antes de executar down -v no projeto QA
```

> [!NOTE]
> Os cenários da suíte `qa/` interrompem propositalmente serviços do projeto QA para simular falhas. Nunca execute essa suíte contra o projeto principal (`vulture`) nem contra o banco compartilhado.

### 6.3. Checklist de Validação Pós-Instalação

Após subir o ambiente principal, valide os itens abaixo:

1. **Saúde do Backend:** `curl -s http://localhost:3000/health` retorna HTTP `200` com `{"status":"ok","rules_engine":true}`.
2. **Saúde da Persistência:** `docker compose exec persistencia python -m station_persist status` encerra com código `0`.
3. **Acesso ao Portal:** abrir `http://localhost:8080` redireciona para `/login` e permite autenticar com uma conta ativa.
4. **Fluxo de Telemetria:** ao publicar um pacote MQTT válido (via simulador ou `mosquitto_pub`), a leitura aparece no Dashboard (`/dashboard`) e no Histórico (`/historico`).

---

## 7. Implantação em Produção na AWS (`API-DSM-4-DEPLOY`)

A implantação em produção utiliza **Amazon EC2 (Ubuntu 24.04 LTS) + Docker Compose**, combinando o `docker-compose.yml` do `API-DSM-4-INFRA` com o override `aws/docker-compose.aws.yml` do `API-DSM-4-DEPLOY`. A entrega contínua (CD) usa **GitHub Actions com AWS OIDC + AWS Systems Manager (SSM)**, sem chaves estáticas AWS e sem expor a porta SSH (`22`).

> [!TIP]
> Para detalhes completos de arquitetura cloud, políticas IAM avulsas e custos, consulte o [Padronização de Deploy Automático](devops/padronizacao_deploy_automatico.md).

### 7.1. Provisionamento da Infraestrutura via CloudFormation

No repositório `API-DSM-4-DEPLOY`, execute com a AWS CLI autenticada:

```bash
aws cloudformation deploy \
  --stack-name vulture-prod-ec2 \
  --template-file aws/cloudformation-ec2-stack.yaml \
  --capabilities CAPABILITY_NAMED_IAM \
  --region us-east-1 \
  --parameter-overrides \
    EnvironmentName=vulture-prod \
    InstanceType=t3.small \
    GitHubOrg=Vulture-API \
    GitHubDeployRepo=API-DSM-4-DEPLOY \
    AllowedMqttCidr=0.0.0.0/0 \
    CreateGitHubOIDCProvider=true \
    AllocateElasticIp=true
```

Consulte e anote os outputs (`InstanceId`, `PublicIp` e `GitHubActionsRoleArn`):

```bash
aws cloudformation describe-stacks \
  --stack-name vulture-prod-ec2 \
  --region us-east-1 \
  --query "Stacks[0].Outputs" \
  --output table
```

### 7.2. Bootstrap da Instância EC2

1. Conecte-se à instância pelo **AWS Systems Manager → Session Manager** (ou `aws ssm start-session --target <INSTANCE_ID>`).
2. Execute o script de preparação inicial como `root` (cria swap de 2 GB, instala Docker/Compose v2, configura rotação de logs, clona `API-DSM-4-INFRA` em `/opt/vulture/API-DSM-4-INFRA` e gera `.env` com `chmod 600`, `JWT_SECRET` e `PERSIST_SOURCE_ID`):

```bash
sudo -i
curl -fsSL https://raw.githubusercontent.com/Vulture-API/API-DSM-4-DEPLOY/main/scripts/ec2-bootstrap.sh -o /tmp/ec2-bootstrap.sh
chmod +x /tmp/ec2-bootstrap.sh
/tmp/ec2-bootstrap.sh
rm -f /tmp/ec2-bootstrap.sh
```

3. Edite `/opt/vulture/API-DSM-4-INFRA/.env` e preencha `DATABASE_URL` com o PostgreSQL de produção (previamente migrado pelo `API-DSM-4-BANCO`):

```bash
nano /opt/vulture/API-DSM-4-INFRA/.env
```

4. Execute o primeiro deploy e validação local na EC2:

```bash
/opt/vulture/scripts/deploy-ec2.sh
```

### 7.3. Configuração de Secrets no GitHub e Deploy Contínuo

No repositório **`Vulture-API/API-DSM-4-DEPLOY`** (**Settings → Secrets and variables → Actions**), cadastre:

| Tipo | Nome | Descrição |
| :--- | :--- | :--- |
| **Secret** | `AWS_ROLE_ARN` | Output `GitHubActionsRoleArn` do CloudFormation |
| **Secret** | `AWS_EC2_INSTANCE_ID` | Output `InstanceId` da instância EC2 |
| **Variable** | `AWS_REGION` | Região AWS (ex.: `us-east-1`) |
| **Secret** | `PROD_FRONT_URL` | URL pública do portal (ex.: `https://vulture.seudominio.com` ou `http://<PublicIp>`) |
| **Secret** | `PROD_API_URL` | URL pública da API *(opcional, caso exposta externamente)* |

No fluxo contínuo, um push aprovado na `main` do `API-DSM-4-INFRA` com E2E verde dispara automaticamente o `deploy-aws.yml` no `API-DSM-4-DEPLOY` (também acionável manualmente via **Actions → Continuous Deployment (AWS EC2) → Run workflow**).

> [!IMPORTANT]
> Em produção, publique o portal atrás de **HTTPS** (ex.: Cloudflare Proxy ou AWS ALB) preservando `Host` e `X-Forwarded-Proto`, pois os cookies de sessão (`agritech_session` e `agritech_ws_token`) utilizam a flag `Secure`. Restrinja também `AllowedMqttCidr` no Security Group ao IP das estações/redes autorizadas.

### 7.4. Pausa de Emergência e Rollback

* **Pausar apenas a persistência** (em manutenção do banco ou anomalia, mantendo `MQTT -> Redis`):

  ```bash
  cd /opt/vulture/API-DSM-4-INFRA
  sudo python3 scripts/telemetry.py pause --project vulture --evidence reports/pause.json
  ```

* **Rollback de versão via Git:**

  ```bash
  git checkout main && git pull origin main
  git revert HEAD --no-edit
  git push origin main
  ```

  O script `deploy-ec2.sh` também realiza rollback automático para o commit anterior da EC2 caso os smoke tests locais falhem durante o deploy.

---

## 8. Solução de Problemas (Troubleshooting)

| Sintoma / Erro | Causa Provável | Resolução |
| :--- | :--- | :--- |
| **Login retorna `503` ou portal não autentica** | Variável `JWT_SECRET` ausente ou com menos de 32 caracteres no backend. | Defina um valor aleatório de 32+ caracteres em `JWT_SECRET` no `.env` e reinicie o serviço `backend`. |
| **Login aceito, mas tela exibe "Acesso Negado"** | Perfil do usuário (ex.: Gerente ou Cliente) ainda não possui permissões concedidas no banco. | Acesse com uma conta **Administrador** e configure as permissões em **Administração → Perfis e permissões** (ou `PUT /api/roles/:id/permissions`). |
| **`telemetry.py activate` falha na pré-verificação** | Faltam migrations no PostgreSQL, `PERSIST_SOURCE_ID` foi alterado ou existe container legado órfão. | Aplique `npm run db:setup` no `API-DSM-4-BANCO`, restaure o `PERSIST_SOURCE_ID` original e inspecione `reports/preflight.json`. |
| **Estação física (ESP32) não conecta no Mosquitto** | `MQTT_BIND` está em `127.0.0.1` (padrão) ou porta `1883` bloqueada no firewall/Security Group. | Configure `MQTT_BIND=0.0.0.0` no `.env`, reinicie `mosquitto` e libere TCP `1883` apenas para a rede autorizada. |
| **Atualizações em tempo real (WebSocket) não chegam** | Proxy sem repasse de `Upgrade`/`Connection` ou URL de destino alterada sem rebuild do Next.js. | Verifique `nginx/nginx.conf` e execute `docker compose up -d --build frontend` após alterar destinos de API. |
| **Erro de memória (`OOM`) durante build na EC2** | Build simultâneo de Next.js/Fastify/Python em instância `t3.micro` sem swap configurado. | Execute `ec2-bootstrap.sh` (cria `/swapfile` de 2 GB) ou utilize instância `t3.small`. |
| **Simulador (`demo`) retorna `401` ao consultar estações** | `ACCESS_CONTROL_ENABLED=true` sem `SIMULADOR_EMAIL` e `SIMULADOR_PASSWORD` válidos no `.env`. | Cadastre ou informe no `.env` uma conta ativa com permissões `stations.read`, `sensors.read` e `sensor-types.read`. |

---

## 9. Referências

* [README Principal do Projeto](../README.md)
* [Manual do Usuário — Portal AgroClima 360](manual-do-usuario.md)
* [Padronização de Deploy Automático](devops/padronizacao_deploy_automatico.md)
* [Requisitos Não Funcionais](requisitos/requisitos-nao-funcionais.md)
* [Repositório de Infraestrutura — `API-DSM-4-INFRA`](https://github.com/Vulture-API/API-DSM-4-INFRA)
* [Repositório de Deploy AWS — `API-DSM-4-DEPLOY`](https://github.com/Vulture-API/API-DSM-4-DEPLOY)
* [Confluence Oficial da Equipe Vulture](https://vultureapi.atlassian.net/wiki/x/AYA7)
