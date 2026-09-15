# API DSM 4º SEMESTRE 2026


<h2 align="center"> [VULTURE / PROJETO] </h2>

<p align="center">
  <a href="#cliente">Cliente</a> |
  <a href="#dor">Dor do Cliente</a> |
  <a href="#desafio">Desafio</a> |
  <a href="#solucao">Solução</a> |
  <a href="#backlog">Backlog do Produto</a> |
  <a href="#dor-ready">DoR</a> |
  <a href="#dod">DoD</a> |
  <a href="#requisitos">Requisitos</a> |
  <a href="#arquitetura">Arquitetura</a> |
  <a href="#devops">DevOps</a> |
  <a href="#cicd">CI/CD</a> |
  <a href="#branch">Estratégia de Branch</a> |
  <a href="#jira">Integração Jira + GitHub</a> |
  <a href="#instalacao">Manual de Instalação</a> |
  <a href="#soft">Manual de Software</a> |
  <a href="#sprint">Cronograma de Sprints</a> |
  <a href="#tecnologias">Tecnologias</a> |
  <a href="#equipe">Equipe</a>
</p>

> **Status do Projeto:** Planejamento / Pré-Kick-off ⏳
>
> **Documentação:** [Adicionar link]
>
> **Jira:** [Acessar o Jira do projeto](https://vultureapi.atlassian.net/jira/software/projects/SCRUM/boards/1/backlog)
>
> **Vídeo do Projeto:** [Adicionar link]

---

## 🏢 Cliente <a id="cliente"></a>

A **Tecsus** é a empresa cliente do projeto AgroClima 360.

O projeto está sendo desenvolvido com foco na expansão do portfólio de soluções IoT da empresa, por meio da criação de uma solução de monitoramento meteorológico capaz de coletar, processar, armazenar e disponibilizar dados ambientais.

A proposta busca validar uma estrutura tecnológica que possa evoluir futuramente para diferentes aplicações de monitoramento ambiental e agronegócio.
---

## 😢 Dor do Cliente <a id="dor"></a>

A **Tecsus** busca expandir seu portfólio de soluções IoT para o segmento de monitoramento ambiental.

Atualmente, a empresa necessita validar uma solução baseada em estação meteorológica que possua uma estrutura básica de software capaz de:

- receber dados provenientes de uma estação meteorológica;
- processar e tratar essas informações;
- armazenar os dados de forma persistente;
- disponibilizar as informações por meio de uma aplicação web;
- permitir evolução futura da solução para múltiplas estações, sensores e cenários de monitoramento.

A dor principal, portanto, não está relacionada a uma necessidade agronômica específica de plantio, colheita ou pulverização, mas à necessidade de **validar uma nova solução tecnológica que possa futuramente integrar o portfólio da empresa**.

O projeto AgroClima 360 surge como uma prova funcional dessa solução, priorizando inicialmente uma estrutura simples, integrada e evolutiva.

---

## 🏅 Desafio <a id="desafio"></a>

O principal desafio do projeto é construir uma solução de monitoramento meteorológico que valide, de forma simples e funcional, a proposta tecnológica da Tecsus.

A equipe deverá desenvolver uma arquitetura capaz de integrar diferentes etapas do fluxo de dados, desde a origem das medições até sua disponibilização para o usuário final.

Entre os principais desafios estão:

- estruturar uma arquitetura modular e preparada para evolução;
- receber dados meteorológicos provenientes de estações e sensores;
- tratar e validar os dados recebidos;
- armazenar as informações de forma consistente;
- disponibilizar os dados por meio de uma aplicação web;
- manter baixo acoplamento entre os componentes do sistema;
- permitir evolução futura para múltiplas estações, sensores e regras de negócio;
- garantir rastreabilidade entre requisitos, desenvolvimento, testes e entregas;
- desenvolver a solução mesmo com dependência parcial de validações externas e com o hardware físico ainda indisponível nas primeiras etapas.

Para a primeira entrega, o desafio foi reduzido ao menor incremento capaz de demonstrar a viabilidade da solução, priorizando:

- arquitetura definida;
- banco de dados operacional;
- CRUD funcional;
- front-end integrado.
---

## 💡 Solução <a id="solucao"></a>

O **AgroClima 360** propõe uma solução de monitoramento meteorológico baseada em uma arquitetura modular, capaz de receber, processar, armazenar e disponibilizar dados ambientais por meio de uma aplicação web.

A solução foi estruturada para permitir evolução gradual, começando por um fluxo funcional mínimo e preparado para futura integração com hardware real.

A proposta contempla:

- estações meteorológicas e sensores responsáveis pela origem dos dados;
- comunicação entre os componentes por meio de serviços de integração;
- armazenamento temporário para recepção e processamento dos dados;
- tratamento e validação das informações recebidas;
- persistência em banco de dados definitivo;
- APIs para cadastro, consulta e gerenciamento das informações do sistema;
- aplicação web para administração e visualização dos dados;
- estrutura preparada para monitoramento, testes automatizados, integração contínua e evolução futura da solução.

Durante as primeiras etapas do desenvolvimento, a equipe poderá utilizar **dados simulados** para representar o comportamento esperado das estações meteorológicas, permitindo que backend, banco de dados e front-end sejam desenvolvidos mesmo antes da disponibilização do hardware físico.

Para a primeira entrega, a solução será concentrada no menor incremento funcional capaz de demonstrar a viabilidade do projeto, incluindo:

- arquitetura da solução definida;
- banco de dados operacional;
- CRUD das entidades priorizadas;
- front-end funcional e integrado ao backend.

A arquitetura detalhada permanece em processo de validação e poderá evoluir conforme novos alinhamentos com os professores e o cliente.

---

# 📋 Backlog do Produto <a id="backlog"></a>

O Product Backlog do **AgroClima 360** é mantido e refinado continuamente pela equipe no Jira e no Confluence.

As User Stories foram priorizadas de acordo com o valor para o produto, dependências técnicas e objetivos de cada Sprint. As estimativas foram realizadas por meio de **Planning Poker**.

> **Importante:** o Jira e o Confluence devem ser considerados as fontes oficiais e mais atualizadas do backlog.  
> O resumo abaixo representa a versão atualmente planejada do produto.

| ID | Prioridade | User Story | Planning Poker | Sprint |
| :--: | :--: | --- | :--: | :--: |
| US1 | Alta | Como Administrador, quero cadastrar e gerenciar estações meteorológicas, para controlar as estações instaladas. | 8 | 1 |
| US2 | Alta | Como Administrador, quero cadastrar sensores e parâmetros, para permitir diferentes tipos de medições. | 8 | 1 |
| US3 | Alta | Como Administrador, quero cadastrar e gerenciar usuários, para incluí-los no sistema. | 8 | 1 |
| US4 | Alta | Como Gerente Agrícola, quero visualizar o status das estações, para identificar problemas de comunicação. | 5 | 1 |
| US5 | Alta | Como Gerente Agrícola, quero cadastrar e configurar alertas meteorológicos, para ser avisado sobre condições críticas. | 5 | 1 |
| US6 | Alta | Como Cliente, quero contar com a disponibilidade e escalabilidade do sistema, para suportar o crescimento das estações e atender ao SLA definido. | 13 | 1 |
| US7 | Alta | Como Gerente Agrícola, quero visualizar os dados meteorológicos atuais, para acompanhar as condições climáticas. | 8 | 2 |
| US8 | Alta | Como Gerente Agrícola, quero visualizar o histórico dos dados, para analisar períodos anteriores. | 8 | 2 |
| US9 | Média | Como Administrador, quero identificar estações ou sensores com falhas ou dados inconsistentes, para facilitar a manutenção. | 13 | 2 |
| US10 | Média | Como Administrador, quero gerenciar o acesso de usuários cadastrados no sistema, para controlar os níveis de acesso. | 8 | 2 |
| US11 | Média | Como Gerente Agrícola, quero visualizar estatísticas dos dados, para analisar o comportamento do clima e visualizar previsões futuras. | 13 | 2 |
| US12 | Média | Como Gerente Agrícola, quero receber os dados tratados das estações, para centralizar as informações. | 8 | 2 |
| US13 | Baixa | Como Gerente Agrícola, quero gerar três tipos de relatórios meteorológicos, para consultar os dados coletados. | 5 | 3 |
| US14 | Baixa | Como Cliente, quero visualizar os dados meteorológicos disponibilizados, para acompanhar as condições climáticas. | 8 | 3 |
| US15 | Baixa | Como Cliente, quero que o sistema possua um pipeline de IC, para automação de testes e validações de código. | 13 | 3 |
| US16 | Baixa | Como Administrador, quero configurar o datalogger e a coleta dos dados, para permitir o funcionamento da estação meteorológica. | 13 | 3 |

### Distribuição atual por Sprint

- **Sprint 1:** 47 pontos
- **Sprint 2:** 58 pontos
- **Sprint 3:** 39 pontos
- **Total planejado:** 144 pontos

### Gestão do Backlog

O backlog poderá ser atualizado conforme:

- novos alinhamentos com o cliente e professores;
- refinamento das User Stories;
- descoberta de dependências técnicas;
- validações realizadas durante as Sprints;
- feedback obtido nas Sprint Reviews.

Alterações relevantes de escopo, prioridade ou distribuição entre Sprints devem ser registradas na documentação de mudanças do projeto.
---

# ✅ Definition of Ready e Definition of Done

## 🏃 DoR — Definition of Ready <a id="dor-ready"></a>

Uma User Story ou Task estará pronta para entrar em desenvolvimento quando possuir informações suficientes para que a equipe consiga executá-la sem depender de interpretações excessivas ou decisões ainda não identificadas.

### Critérios de Ready

- [ ] A necessidade ou objetivo da atividade está claro.
- [ ] A User Story está alinhada à Dor do Cliente e ao objetivo do produto.
- [ ] Os critérios de aceite estão definidos e compreendidos pela equipe.
- [ ] As principais regras de negócio relacionadas estão documentadas.
- [ ] Dependências conhecidas foram identificadas.
- [ ] Impedimentos críticos foram identificados ou possuem estratégia de tratamento.
- [ ] A equipe possui informações suficientes para estimar a atividade.
- [ ] A User Story foi refinada com participação dos Developers.
- [ ] A prioridade e a Sprint estão definidas.
- [ ] A atividade pode ser decomposta em Tasks técnicas executáveis.

> Quando existir alguma decisão ainda não validada pelo cliente/professor, a equipe poderá avançar utilizando uma assunção documentada, desde que a decisão seja reversível e o impacto de uma possível mudança esteja registrado.

---

## 🏆 DoD — Definition of Done <a id="dod"></a>

Uma User Story ou Task será considerada concluída somente quando atender aos critérios de qualidade e integração definidos pela equipe.

### Critérios de Done

- [ ] A implementação prevista foi concluída.
- [ ] Os critérios de aceite aplicáveis foram atendidos.
- [ ] O código foi versionado na branch correta.
- [ ] Os commits seguem o padrão definido pela equipe.
- [ ] A Pull Request foi aberta para a `dev`.
- [ ] A Pull Request foi revisada por pelo menos um Developer diferente do autor.
- [ ] Os comentários e ajustes obrigatórios do Code Review foram resolvidos.
- [ ] Os testes pertinentes foram executados.
- [ ] Testes unitários foram adicionados ou atualizados quando aplicável.
- [ ] Testes de integração foram realizados quando aplicável.
- [ ] A integração com banco de dados, API ou front-end foi validada quando necessária.
- [ ] Não existem erros críticos conhecidos relacionados à entrega.
- [ ] A documentação necessária foi atualizada.
- [ ] Não existem credenciais, tokens, senhas ou informações sensíveis versionadas no repositório.
- [ ] A Pull Request foi aprovada e integrada à `dev`.
- [ ] A rastreabilidade entre Jira, branch, commits e Pull Request está preservada.
- [ ] A atividade está disponível para demonstração ou validação.
- [ ] O item foi atualizado para **Concluído** no Jira.

> A conclusão de uma atividade não depende apenas da implementação do código. Testes, revisão, integração, documentação e rastreabilidade fazem parte da Definition of Done da Equipe Vulture.

---

## 🏆 DoD — Definition of Done <a id="dod"></a>

Uma User Story ou Task será considerada concluída somente quando atender aos critérios de qualidade, revisão, integração e rastreabilidade definidos pela Equipe Vulture.

### Critérios de Done

- [ ] A implementação prevista foi concluída.
- [ ] Os critérios de aceite aplicáveis foram atendidos.
- [ ] O código foi desenvolvido na branch correta da atividade.
- [ ] Os commits seguem o padrão definido pela equipe.
- [ ] A Pull Request foi aberta para a branch `dev`.
- [ ] A Pull Request foi revisada por pelo menos um Developer diferente do autor.
- [ ] Os comentários e ajustes obrigatórios do Code Review foram resolvidos.
- [ ] Os testes pertinentes foram executados.
- [ ] Testes unitários foram adicionados ou atualizados quando aplicável.
- [ ] Testes de integração foram realizados quando aplicável.
- [ ] A integração com banco de dados, API e/ou front-end foi validada quando necessária.
- [ ] Não existem erros críticos conhecidos relacionados à entrega.
- [ ] A documentação necessária foi atualizada.
- [ ] Não existem credenciais, tokens, senhas ou informações sensíveis versionadas no repositório.
- [ ] A Pull Request foi aprovada e integrada à `dev`.
- [ ] A rastreabilidade entre Jira, branch, commits e Pull Request está preservada.
- [ ] A entrega está disponível para demonstração ou validação.
- [ ] O item foi atualizado para **Concluído** no Jira.

> Uma atividade não é considerada concluída apenas porque o código foi implementado.  
> Testes, Code Review, integração, documentação e rastreabilidade também fazem parte da Definition of Done da Equipe Vulture.

---

# 📝 Requisitos <a id="requisitos"></a>

Os requisitos do **AgroClima 360** foram definidos a partir da Dor do Cliente, do Product Backlog, das orientações dos professores e dos refinamentos realizados pela equipe.

Os requisitos podem evoluir ao longo das Sprints conforme novas validações sejam realizadas. Alterações relevantes deverão ser registradas no Jira, Confluence e no Registro de Mudanças e Decisões do projeto.

---

## 🎯 Requisitos Funcionais — RF

Os Requisitos Funcionais representam as funcionalidades e comportamentos que o sistema deverá disponibilizar aos usuários.

| ID | Requisito Funcional | Descrição |
| :--: | --- | --- |
| **RF01** | Gerenciar estações meteorológicas | O sistema deverá permitir cadastrar, consultar, atualizar e gerenciar estações meteorológicas. |
| **RF02** | Gerenciar sensores | O sistema deverá permitir cadastrar e associar sensores às estações meteorológicas. |
| **RF03** | Gerenciar parâmetros meteorológicos | O sistema deverá permitir cadastrar e configurar parâmetros utilizados pelos sensores e pelas medições. |
| **RF04** | Gerenciar usuários | O sistema deverá permitir cadastrar, consultar, atualizar e gerenciar usuários. |
| **RF05** | Autenticar usuários | O sistema deverá permitir autenticação dos usuários cadastrados para acesso às funcionalidades protegidas. |
| **RF06** | Controlar níveis de acesso | O sistema deverá permitir diferentes níveis de acesso conforme o perfil do usuário. |
| **RF07** | Visualizar estações | O sistema deverá disponibilizar uma listagem das estações cadastradas contendo informações como nome, localização e status. |
| **RF08** | Consultar status de comunicação | O sistema deverá informar o estado de comunicação das estações, permitindo identificar se estão online ou offline. |
| **RF09** | Receber dados meteorológicos | O sistema deverá receber dados provenientes das estações meteorológicas ou de dados simulados durante as etapas iniciais. |
| **RF10** | Tratar dados recebidos | O sistema deverá validar, tratar e preparar os dados meteorológicos recebidos antes da persistência definitiva. |
| **RF11** | Armazenar dados meteorológicos | O sistema deverá armazenar de forma persistente as informações tratadas das estações e sensores. |
| **RF12** | Consultar dados meteorológicos atuais | O sistema deverá permitir a visualização dos dados meteorológicos mais recentes. |
| **RF13** | Consultar histórico | O sistema deverá permitir consultas aos dados meteorológicos armazenados anteriormente. |
| **RF14** | Configurar alertas meteorológicos | O sistema deverá permitir cadastrar e configurar regras e limites para alertas meteorológicos. |
| **RF15** | Listar alertas cadastrados | O sistema deverá disponibilizar uma listagem dos alertas configurados. |
| **RF16** | Identificar falhas ou inconsistências | O sistema deverá auxiliar na identificação de estações, sensores ou dados que apresentem falhas ou inconsistências. |
| **RF17** | Disponibilizar dados por API | O backend deverá disponibilizar endpoints para comunicação com o front-end e demais componentes da solução. |
| **RF18** | Exibir informações em aplicação web | O sistema deverá possuir uma interface web para cadastro, gerenciamento e visualização das informações. |

> Os recursos de notificações visuais dinâmicas, como popups ou indicadores de alerta em tempo real, poderão ser incorporados em Sprints futuras conforme priorização do Product Backlog.

---

## ⚙️ Requisitos Não Funcionais — RNF

Os Requisitos Não Funcionais definem características de qualidade, desempenho, segurança, manutenção e operação da solução.

| ID | Requisito Não Funcional | Descrição |
| :--: | --- | --- |
| **RNF01** | Arquitetura modular | A solução deverá possuir uma arquitetura organizada em componentes ou serviços com responsabilidades bem definidas. |
| **RNF02** | Escalabilidade | A arquitetura deverá permitir crescimento da quantidade de estações, sensores e volume de dados sem exigir reestruturação completa da solução. |
| **RNF03** | Disponibilidade | O sistema deverá ser estruturado para manter os serviços essenciais disponíveis conforme os requisitos de SLA definidos para o projeto. |
| **RNF04** | Desempenho | O fluxo de dados deverá considerar como referência uma latência de até **1,5 segundo** para operações consideradas próximas de tempo real. |
| **RNF05** | Persistência dos dados | Dados tratados que necessitem de histórico deverão ser armazenados em banco de dados persistente. |
| **RNF06** | Uso de armazenamento temporário | Dados recebidos poderão utilizar armazenamento intermediário antes de seu tratamento e persistência definitiva. |
| **RNF07** | Cache | Informações frequentemente consultadas poderão utilizar mecanismos de cache para reduzir tempo de resposta e carga sobre o banco de dados. |
| **RNF08** | Segurança | O sistema não deverá armazenar no repositório credenciais, tokens, senhas ou segredos de ambiente. |
| **RNF09** | Controle de acesso | Funcionalidades administrativas deverão ser protegidas de acordo com o nível de acesso do usuário. |
| **RNF10** | Rastreabilidade | O desenvolvimento deverá manter rastreabilidade entre Jira, branches, commits, Pull Requests, Code Reviews e entregas. |
| **RNF11** | Versionamento | O código deverá ser versionado utilizando Git e o fluxo oficial de branches da equipe. |
| **RNF12** | Code Review | Alterações deverão passar por Pull Request e revisão de pelo menos um Developer diferente do autor antes da integração. |
| **RNF13** | Testabilidade | Os componentes deverão ser desenvolvidos de forma que permitam execução de testes unitários e de integração quando aplicável. |
| **RNF14** | Integração contínua | O projeto deverá evoluir para possuir pipeline de integração contínua responsável por automatizar verificações, testes e validações de código. |
| **RNF15** | Observabilidade | A solução deverá permitir evolução para monitoramento por meio de logs, métricas, status dos serviços e acompanhamento de latência. |
| **RNF16** | Manutenibilidade | O código deverá seguir padrões de organização, nomenclatura e estrutura definidos pela equipe. |
| **RNF17** | Documentação | APIs, contratos, arquitetura, banco de dados e processos técnicos relevantes deverão possuir documentação atualizada. |
| **RNF18** | Evolução independente | Os componentes da solução deverão ser estruturados de forma a reduzir acoplamento e facilitar manutenção e evolução futura. |

---

### 📌 Observação

Os requisitos apresentados representam o entendimento atual do projeto.

Requisitos ainda sujeitos a validação com os professores ou cliente deverão ser tratados como **assunções documentadas**, permitindo que a equipe avance em decisões reversíveis sem perder rastreabilidade.

Mudanças relevantes deverão ser registradas antes de serem incorporadas definitivamente ao desenvolvimento.

---

## Fluxo planejado

```text
Planejamento
     ↓
Desenvolvimento
     ↓
Versionamento
     ↓
Integração Contínua
     ↓
Build
     ↓
Testes
     ↓
Quality Check
     ↓
Deploy
     ↓
Monitoramento
     ↓
Feedback
```


---


# 📖 Manual de Instalação <a id="instalacao"></a>

## ⚙️ Pré-requisitos

[Preencher.]

---

## 🚀 Passo a Passo de Instalação

### 1. Clonar o repositório

```bash
git clone [URL_DO_REPOSITORIO]
cd [NOME_DO_REPOSITORIO]
```

### 2. Instalar dependências

```bash
[COMANDO]
```

### 3. Configurar ambiente

```text
[Preencher.]
```

### 4. Executar aplicação

```bash
[COMANDO]
```

### 5. Acessar o sistema

```text
[URL / PORTA]
```

---

# 📘 Manual de Software <a id="soft"></a>

[Preencher conforme o sistema for desenvolvido.]

---

# 🗓️ Cronograma de Sprints <a id="sprint"></a>

[Preencher após definição oficial do calendário.]

|  Sprint  | Período | Objetivo | Status |
| :------: | ------- | -------- | :----: |
| Sprint 1 |         |          |    ⏳   |
| Sprint 2 |         |          |    ⏳   |
| Sprint 3 |         |          |    ⏳   |

---

# 🛠️ Tecnologias Utilizadas <a id="tecnologias"></a>

[Definir após o Kick-off.]

## Frontend

[Preencher.]

## Backend
'
[Preencher.]

## Banco de Dados

[Preencher.]

## DevOps / Infraestrutura

[Preencher.]

## Testes

[Preencher.]

## Gestão

* GitHub
* Jira

---

## 👥 Equipe <a id="equipe"></a>

| Integrante | Papel | GitHub | LinkedIn |
| :--- | :--- | :---: | :---: |
| **Aline** | Master / Developer / DevOps | <a href="https://github.com/AlineRaquelC"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/aline-oliveira-60ab6265/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Ana Julia (Rubim)** | Product Owner / DevOps | <a href="https://github.com/anajrubim"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/ana-j%C3%BAlia-rubim/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Lucas Marins** | Developer / DevOps | <a href="https://github.com/lucasMarinsSantos"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/lucasmarinssantos/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Enrico Germano** | Developer / DevOps | <a href="https://github.com/EnricoGermano"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/enrico-de-chiara-germano-022894204/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Leonardo da Silva** | Developer / DevOps | <a href="https://github.com/leodaslb"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/leonardo-silva-lopes-aab435283/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |

---

# 📚 Documentação

## Documentação Geral

[Adicionar links.]

## Atas de Reunião

[Adicionar links.]

## Documentação das Sprints

[Adicionar links.]

## Diagramas

[Adicionar links.]

---

# 📹 Vídeos das Entregas

|  Sprint  | Vídeo       |
| :------: | ----------- |
| Sprint 1 | [Adicionar] |
| Sprint 2 | [Adicionar] |
| Sprint 3 | [Adicionar] |

---

# 📌 Status do Projeto

**Fase atual:** Pré-Kick-off.

O conteúdo técnico e funcional deste README será atualizado após o Kick-off oficial, conforme definição do problema, requisitos, arquitetura, tecnologias e planejamento das Sprints.
