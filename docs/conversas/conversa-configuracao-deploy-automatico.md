# Exportação de Conversa: Configuração de Deploy Automático

**ID da Conversa:** `35035979-95ed-4f8d-86ff-8ec3678f9540`  
**Data/Hora Local:** 24/09/2026  
**Projeto:** Vulture — API DSM 4º Semestre 2026 (Agritech)  
**Link da Conversa:** [Configuração de Deploy Automático](conversation://35035979-95ed-4f8d-86ff-8ec3678f9540)

---

## 👤 Usuário (2026-09-24T13:10:23Z)

prepare todo o projeto para fazer o deploy automatico

---

## 🤖 Assistente (Antigravity) (2026-09-24T13:19:56Z)

O projeto foi totalmente preparado e estruturado para o **Deploy Automático Contínuo (Continuous Deployment - CD)**, em conformidade com o documento de padronização da equipe ([`docs/devops/padronizacao_deploy_automatico.md`](file:///home/dsm/Documents/vulture/docs/devops/padronizacao_deploy_automatico.md)) e com a arquitetura de microsserviços.

---

### 1. O Que Foi Configurado e Criado

#### 🚀 Pipelines de Deploy Automático (`.github/workflows/deploy.yml`)
* **Repositório Principal:** [`.github/workflows/deploy.yml`](file:///home/dsm/Documents/vulture/.github/workflows/deploy.yml) orquestra a publicação dos microsserviços de backend e do frontend, executando os Smoke Tests com polling e retries.
* **Pipelines em cada microsserviço e frontend:**
  - [`API-DSM-4-USUARIO/.github/workflows/deploy.yml`](file:///home/dsm/Documents/vulture/API-DSM-4-USUARIO/.github/workflows/deploy.yml)
  - [`API-DSM-4-PARAMETROS/.github/workflows/deploy.yml`](file:///home/dsm/Documents/vulture/API-DSM-4-PARAMETROS/.github/workflows/deploy.yml)
  - [`API-DSM-4-ESTACOES/.github/workflows/deploy.yml`](file:///home/dsm/Documents/vulture/API-DSM-4-ESTACOES/.github/workflows/deploy.yml)
  - [`API-DSM-4-ALERTAS/.github/workflows/deploy.yml`](file:///home/dsm/Documents/vulture/API-DSM-4-ALERTAS/.github/workflows/deploy.yml)
  - [`API-DSM-4-FRONTEND/.github/workflows/deploy.yml`](file:///home/dsm/Documents/vulture/API-DSM-4-FRONTEND/.github/workflows/deploy.yml)

#### 🩺 Health Checks e Contrato Técnico (RNF02 e RNF12)
* Implementação do endpoint de verificação de integridade `GET /health` e `GET /api/health` em [`API-DSM-4-USUARIO/src/app.ts`](file:///home/dsm/Documents/vulture/API-DSM-4-USUARIO/src/app.ts).
* Testes automatizados criados em [`API-DSM-4-USUARIO/src/app.test.ts`](file:///home/dsm/Documents/vulture/API-DSM-4-USUARIO/src/app.test.ts) validando status HTTP 200.
* Validação de que todos os microsserviços (`USUARIO`, `PARAMETROS`, `ALERTAS` e `ESTACOES`) cumprem o contrato técnico de `/health` e passam em 100% dos testes e linter.

#### 🐳 Conteinerização e Orquestração
* **Frontend:** Criação de Dockerfile multi-stage otimizado para produção em [`API-DSM-4-FRONTEND/Dockerfile`](file:///home/dsm/Documents/vulture/API-DSM-4-FRONTEND/Dockerfile) e [`API-DSM-4-FRONTEND/app/Dockerfile`](file:///home/dsm/Documents/vulture/API-DSM-4-FRONTEND/app/Dockerfile).
* **Vercel:** Criação de [`API-DSM-4-FRONTEND/vercel.json`](file:///home/dsm/Documents/vulture/API-DSM-4-FRONTEND/vercel.json) e [`API-DSM-4-FRONTEND/app/vercel.json`](file:///home/dsm/Documents/vulture/API-DSM-4-FRONTEND/app/vercel.json).
* **Docker Compose:** Criado [`docker-compose.yml`](file:///home/dsm/Documents/vulture/docker-compose.yml) para subida unificada de todos os serviços e banco PostgreSQL com healthchecks integrados.

#### ☁️ Infraestrutura como Código (Render Blueprints)
* Criado o blueprint mestre [`render.yaml`](file:///home/dsm/Documents/vulture/render.yaml) na raiz, que realiza o provisionamento e deploy automático com 1 clique de todos os serviços e do banco de dados relacional.
* Criado `render.yaml` em cada microsserviço para publicação individual independente.

#### 📚 Documentação Atualizada
* [`docs/devops/padronizacao_deploy_automatico.md`](file:///home/dsm/Documents/vulture/docs/devops/padronizacao_deploy_automatico.md) atualizado refletindo com fidelidade a matriz de microsserviços, variáveis injetadas e protocolo de smoke test.
* [`README.md`](file:///home/dsm/Documents/vulture/README.md) atualizado com diagrama de fluxo do pipeline CI/CD e tabela de secrets.

---

### 2. Segredos Necessários no GitHub Secrets

Para ativar a publicação automática quando houver merge na branch `main`, cadastre as seguintes variáveis em **Settings > Secrets and variables > Actions**:

| Secret | Descrição | Onde Obter |
| :--- | :--- | :--- |
| `RENDER_BACKEND_DEPLOY_HOOK` (ou `RENDER_DEPLOY_HOOK`) | URL do Deploy Hook gerado no serviço do Render | Painel do Render > Service > Settings > Deploy Hook |
| `RENDER_USUARIO_DEPLOY_HOOK` | Hook individual da API Usuário (opcional) | Painel do Render |
| `RENDER_PARAMETROS_DEPLOY_HOOK` | Hook individual da API Parâmetros (opcional) | Painel do Render |
| `RENDER_ESTACOES_DEPLOY_HOOK` | Hook individual da API Estações (opcional) | Painel do Render |
| `RENDER_ALERTAS_DEPLOY_HOOK` | Hook individual da API Alertas (opcional) | Painel do Render |
| `VERCEL_TOKEN` | Token pessoal ou da equipe na Vercel | Vercel Account Settings > Tokens |
| `VERCEL_ORG_ID` | Identificador da organização / equipe na Vercel | Vercel Project Settings > General |
| `VERCEL_PROJECT_ID` | Identificador do projeto Frontend na Vercel | Vercel Project Settings > General |
| `PROD_API_URL` | URL pública da API em produção (para o Smoke Test) | URL gerada no Render |
| `PROD_FRONT_URL` | URL pública do frontend (para o Smoke Test) | URL gerada na Vercel / Render |

---

### 3. Validação Realizada
* **Build do Frontend:** `npm run build` executado no Next.js com sucesso.
* **Testes & Linter:** Executados em todos os microsserviços (`API-DSM-4-ALERTAS`, `API-DSM-4-ESTACOES`, `API-DSM-4-PARAMETROS`, `API-DSM-4-USUARIO` e `API-DSM-4-FRONTEND`), obtendo 100% de aprovação.

---

## 👤 Usuário (2026-09-24T13:27:18Z)

remove as alteracaoes do readme e crie as branch em cada repo q foi modificado(scrum 378) e crie os commit e pr e me ajude a criar essas info do secrets

---

## 🤖 Assistente (Antigravity) (2026-09-24T13:35:24Z)

Todas as tarefas foram executadas com sucesso:

1. **Alterações do `README.md`:** revertidas e mantidas limpas no estado original.
2. **Criação de branches `feature/SCRUM-378-deploy-automatico`:** criadas a partir da branch `dev` em cada repositório afetado.
3. **Commits padronizados e Pull Requests abertos:**

| Repositório | Branch Criada | Pull Request Criado |
| :--- | :--- | :--- |
| **Principal (`API-DSM-4SEMESTRE-2026`)** | `feature/SCRUM-378-deploy-automatico` | [PR #23](https://github.com/Vulture-API/API-DSM-4SEMESTRE-2026/pull/23) |
| **`API-DSM-4-FRONTEND`** | `feature/SCRUM-378-deploy-automatico` | [PR #13](https://github.com/Vulture-API/API-DSM-4-FRONTEND/pull/13) |
| **`API-DSM-4-ESTACOES`** | `feature/SCRUM-378-deploy-automatico` | [PR #5](https://github.com/Vulture-API/API-DSM-4-ESTACOES/pull/5) |
| **`API-DSM-4-PARAMETROS`** | `feature/SCRUM-378-deploy-automatico` | [PR #5](https://github.com/Vulture-API/API-DSM-4-PARAMETROS/pull/5) |
| **`API-DSM-4-USUARIO`** | `feature/SCRUM-378-deploy-automatico` | [PR #3](https://github.com/Vulture-API/API-DSM-4-USUARIO/pull/3) |
| **`API-DSM-4-ALERTAS`** | `feature/SCRUM-378-deploy-automatico` | [PR #2](https://github.com/Vulture-API/API-DSM-4-ALERTAS/pull/2) |

---

## 🔐 Guia Passo a Passo para Configurar os Secrets

Os segredos permitem que o GitHub Actions acione o deploy em nuvem sem expor senhas no código.

### Onde cadastrar no GitHub?

Em cada repositório (ou na organização **Vulture-API** para compartilhar entre todos):
1. Acesse o repositório no GitHub.
2. Clique na aba **Settings** (Configurações).
3. No menu lateral esquerdo, vá em **Secrets and variables** > **Actions**.
4. Clique no botão verde **New repository secret**.

---

### 1. Provedor de Backend: Render

O Render utiliza **Deploy Hooks** (URLs protegidas por token que acionam a compilação do serviço ao receberem uma requisição POST).

#### Como obter a URL do Deploy Hook:
1. Acesse [dashboard.render.com](https://dashboard.render.com).
2. Clique no seu serviço de backend (ex: `api-dsm-4-usuario`).
3. Vá na aba lateral **Settings**.
4. Role até a seção **Deploy Hook**.
5. Clique em **Add Deploy Hook** (ou copie a URL já existente, com formato `https://api.render.com/deploy/srv-xxxxxx?key=yyyyyy`).

#### Nomes dos Secrets a cadastrar:
* **No repositório de cada microsserviço:**
  - Nome: `RENDER_DEPLOY_HOOK`
  - Valor: Cole a URL do deploy hook do serviço correspondente.
  - Nome: `PROD_API_URL`
  - Valor: A URL pública gerada pelo Render (ex: `https://api-dsm-4-usuario.onrender.com`).

* **No repositório raiz (`API-DSM-4SEMESTRE-2026`):**
  - `RENDER_BACKEND_DEPLOY_HOOK`: Deploy hook mestre ou de um dos serviços centrais.
  - `RENDER_USUARIO_DEPLOY_HOOK`: Hook da API Usuário.
  - `RENDER_PARAMETROS_DEPLOY_HOOK`: Hook da API Parâmetros.
  - `RENDER_ESTACOES_DEPLOY_HOOK`: Hook da API Estações.
  - `RENDER_ALERTAS_DEPLOY_HOOK`: Hook da API Alertas.
  - `PROD_API_URL`: URL pública da API para o smoke test.

---

### 2. Provedor de Frontend: Vercel

Se você utilizar a Vercel para o frontend Next.js:

#### Como obter o `VERCEL_TOKEN`:
1. Acesse [vercel.com](https://vercel.com) e faça login.
2. Clique na foto de perfil (canto superior direito) > **Account Settings**.
3. No menu lateral esquerdo, clique em **Tokens**.
4. Clique em **Create Token**, dê um nome (ex: `GitHub-Actions-Vulture`), selecione o escopo e clique em **Create**.
5. Copie o valor exibido imediatamente e cadastre como secret `VERCEL_TOKEN`.

#### Como obter `VERCEL_ORG_ID` e `VERCEL_PROJECT_ID`:
* **Opção Rápida via Dashboard:**
  1. No painel da Vercel, entre no projeto do frontend.
  2. Vá na aba **Settings** > **General**.
  3. Role a página: você verá o campo **Project ID** (`prj_...`) e o ID da equipe/organização (`team_...`).
* **Opção via CLI Local:**
  Execute no diretório do frontend:
  ```bash
  npx vercel link
  ```
  Isso criará uma pasta `.vercel/project.json` contendo `orgId` e `projectId`.

#### Nomes dos Secrets para o Frontend:
* `VERCEL_TOKEN`: Token pessoal gerado nas configurações da conta.
* `VERCEL_ORG_ID`: ID da organização ou da sua conta.
* `VERCEL_PROJECT_ID`: ID do projeto no Vercel.
* `PROD_FRONT_URL`: URL do domínio de produção do portal (ex: `https://vulture-frontend.vercel.app`).

> **Nota:** Se optar por rodar o Frontend também dentro do Render, basta cadastrar o `RENDER_DEPLOY_HOOK` e `PROD_FRONT_URL` no repositório `API-DSM-4-FRONTEND`, pois o workflow já suporta ambos os fluxos!

---

## 👤 Usuário (2026-09-24T13:36:06Z)

exporte essa conversa @[conversation:"Stations Page Backend Integration"] @[conversation:"Configuração de Deploy Automático"]

---
