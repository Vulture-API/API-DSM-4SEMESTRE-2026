# Tasks da Sprint 2

## Sprint 2

Este documento registra as principais Tasks técnicas vinculadas às User Stories executadas durante a Sprint 2.

---

## US06 — Disponibilidade e escalabilidade

**User Story:** Como Cliente, quero contar com a disponibilidade e escalabilidade do sistema, para suportar o crescimento das estações e atender ao SLA definido.

| Jira | Task |
|---|---|
| SCRUM-469 | [DEVOPS] Implementar monitoramento de disponibilidade e tempo de resposta |
| SCRUM-470 | [DEVOPS] Implementar mecanismo de registro e acompanhamento de indisponibilidades |
| SCRUM-471 | [DEVOPS] Configurar monitoramento de recursos e desempenho da aplicação |
| SCRUM-472 | [DEVOPS/QA] Implementar testes de carga e validação da capacidade do sistema |
| SCRUM-473 | [DEVOPS] Validar disponibilidade do sistema conforme SLA de 99% |

---

## US07 — Dados meteorológicos atuais

**User Story:** Como Gerente Agrícola, quero visualizar os dados meteorológicos atuais, para acompanhar as condições climáticas.

| Jira | Task |
|---|---|
| SCRUM-408 | [UX] Criar protótipo da tela de dados meteorológicos atuais no Figma |
| SCRUM-409 | [BACK] Criar endpoint para consulta dos dados meteorológicos atuais |
| SCRUM-410 | [BACK] Criar serviço de processamento e disponibilização dos dados atuais |
| SCRUM-411 | [FRONT] Desenvolver tela de visualização dos dados meteorológicos atuais |
| SCRUM-412 | [FRONT] Implementar atualização automática das novas medições |
| SCRUM-413 | [INTEGRAÇÃO] Integrar tela de dados atuais com API |
| SCRUM-414 | [QA] Criar testes da consulta e atualização dos dados atuais |
| SCRUM-489 | [BACK] Disponibilizar atualização em tempo real dos dados atuais via WebSocket |

---

## US08 — Histórico meteorológico

**User Story:** Como Gerente Agrícola, quero visualizar o histórico dos dados, para analisar períodos anteriores.

| Jira | Task |
|---|---|
| SCRUM-415 | [UX] Criar protótipo da tela de histórico meteorológico no Figma |
| SCRUM-416 | [BACK] Criar endpoint para consulta do histórico meteorológico |
| SCRUM-417 | [BACK] Implementar filtro do histórico por período |
| SCRUM-418 | [BACK] Implementar filtro do histórico por estação |
| SCRUM-419 | [FRONT] Desenvolver tela de consulta do histórico meteorológico |
| SCRUM-420 | [INTEGRAÇÃO] Integrar tela de histórico com API |
| SCRUM-421 | [QA] Criar testes da consulta e filtros do histórico |

---

## US09 — Falhas e inconsistências

**User Story:** Como Administrador, quero identificar estações ou sensores com falhas ou dados inconsistentes, para facilitar a manutenção.

| Jira | Task |
|---|---|
| SCRUM-422 | [UX] Criar protótipo da tela de ocorrências no Figma |
| SCRUM-423 | [BACK] Criar rotina para identificação de estações sem comunicação |
| SCRUM-424 | [BACK] Implementar validação dos limites configurados nos sensores |
| SCRUM-425 | [BACK] Criar registro de ocorrências de falhas e inconsistências |
| SCRUM-426 | [DB] Criar estrutura de persistência para ocorrências |
| SCRUM-427 | [FRONT] Desenvolver tela para consulta das ocorrências |
| SCRUM-428 | [INTEGRAÇÃO] Integrar consulta de ocorrências com API |
| SCRUM-429 | [QA] Criar testes de identificação e registro de falhas |

---

## US10 — Controle de acesso

**User Story:** Como Administrador, quero gerenciar o acesso de usuários cadastrados no Sistema, para controlar os níveis de acesso.

| Jira | Task |
|---|---|
| SCRUM-430 | [UX] Criar protótipo das telas de perfis e permissões no Figma |
| SCRUM-431 | [BACK] Implementar cadastro e gerenciamento de perfis de acesso |
| SCRUM-432 | [BACK] Implementar controle de permissões por perfil |
| SCRUM-433 | [BACK] Implementar bloqueio e desbloqueio de acesso dos usuários |
| SCRUM-434 | [BACK] Implementar validação de autorização para acesso às funcionalidades |
| SCRUM-435 | [DB] Atualizar modelo de dados para perfis e permissões |
| SCRUM-436 | [FRONT] Desenvolver interface de gerenciamento de perfis e permissões |
| SCRUM-437 | [INTEGRAÇÃO] Integrar gerenciamento de acesso com API |
| SCRUM-438 | [QA] Criar testes de perfis, permissões e autorização |
| SCRUM-546 | [UX] Criar protótipo de tela de login |
| SCRUM-547 | [FRONT] Criar tela de login |
| SCRUM-548 | [INTEGRAÇÃO] Fazer integração de sistema de login e autenticação |
| SCRUM-549 | [QA] Validar login, autenticação JWT e ciclo da sessão |
| SCRUM-550 | [QA] Validar permissões de páginas, menus e ações |

---

## US11 — Estatísticas e previsões meteorológicas

**User Story:** Como Gerente Agrícola, quero visualizar estatísticas dos dados, para analisar o comportamento do clima e visualizar previsões futuras.

| Jira | Task |
|---|---|
| SCRUM-439 | [UX] Criar protótipo do dashboard de estatísticas no Figma |
| SCRUM-440 | [BACK] Criar serviço para cálculo das estatísticas meteorológicas |
| SCRUM-441 | [BACK] Implementar filtros para seleção do período de análise |
| SCRUM-442 | [FRONT] Desenvolver gráficos e indicadores meteorológicos |
| SCRUM-443 | [INTEGRAÇÃO] Integrar serviço de previsão meteorológica |
| SCRUM-444 | [FRONT] Exibir previsão meteorológica na interface |
| SCRUM-445 | [INTEGRAÇÃO] Integrar dashboard de estatísticas com API |
| SCRUM-446 | [QA] Validar cálculos estatísticos, filtros e previsão |
| SCRUM-490 | [BACK] Criar endpoint de estatísticas meteorológicas |

---

## US12 — Recepção e tratamento dos dados

**User Story:** Como Gerente Agrícola, quero receber os dados tratados das estações, para centralizar as informações.

| Jira | Task |
|---|---|
| SCRUM-447 | [BACK] Implementar recebimento dos dados enviados pelas estações |
| SCRUM-448 | [TRATAMENTO] Validar os dados consumidos do Redis |
| SCRUM-449 | [TRATAMENTO] Registrar inconsistências e colocar dados inválidos em quarentena |
| SCRUM-450 | [TRATAMENTO] Resolver as relações entre medição, sensor e estação |
| SCRUM-451 | [TRATAMENTO/DB] Persistir medições e relações com integridade e idempotência |
| SCRUM-452 | [ARQ] Documentar os contratos e responsabilidades da recepção e do tratamento |
| SCRUM-453 | [QA] Validar o fluxo MQTT → Redis → tratamento → PostgreSQL |
| SCRUM-529 | [TRATAMENTO] Estruturar serviço Python independente e consumidor do Redis Stream |
| SCRUM-530 | [TRATAMENTO] Implementar recuperação, quarentena e reprocessamento seguro |
| SCRUM-531 | [INFRA] Integrar os serviços separados e substituir o persistidor antigo |
| SCRUM-532 | [RECEPÇÃO] Remover persistência PostgreSQL e dependências de tratamento |
| SCRUM-533 | [RECEPÇÃO] Corrigir recebimento MQTT e gravação rápida no Redis |

---

## US13 — Gerenciamento de propriedades agrícolas

**User Story:** Como Gerente Agrícola, quero cadastrar e gerenciar propriedades agrícolas, para associá-las às estações meteorológicas e organizar o monitoramento climático de cada propriedade.

| Jira | Task |
|---|---|
| SCRUM-454 | [UX] Criar protótipo da gestão de propriedades no Figma |
| SCRUM-455 | [DB] Atualizar modelagem para propriedades agrícolas |
| SCRUM-456 | [BACK] Criar cadastro de propriedades agrícolas |
| SCRUM-457 | [BACK] Implementar edição e atualização de propriedades |
| SCRUM-458 | [BACK] Implementar exclusão e gerenciamento de propriedades |
| SCRUM-459 | [BACK] Implementar associação entre propriedades e estações |
| SCRUM-460 | [FRONT] Desenvolver tela de cadastro e gestão de propriedades |
| SCRUM-461 | [INTEGRAÇÃO] Integrar gestão de propriedades com API |
| SCRUM-462 | [QA] Criar testes do CRUD e associação de propriedades |

---

## US16 — Integração Contínua

**User Story:** Como Cliente, quero que o sistema possua um pipeline de CI, para automação de testes e validações de código.

| Jira | Task |
|---|---|
| SCRUM-463 | [DEVOPS] Configurar pipeline de Integração Contínua |
| SCRUM-464 | [DEVOPS] Configurar execução automática dos testes e processo de teste |
| SCRUM-465 | [DEVOPS] Implementar etapa automática de validação e build |
| SCRUM-466 | [DEVOPS] Configurar análise automática da qualidade do código |
| SCRUM-467 | [DEVOPS] Configurar registro dos resultados das execuções do pipeline |
| SCRUM-468 | [DOC] Documentar pipeline, etapas e critérios de falha |

---

## Observação

As Tasks acima representam a decomposição técnica registrada no Jira para a Sprint 2.

Durante a execução da Sprint, algumas User Stories receberam Tasks adicionais de correção, integração ou refinamento técnico conforme necessidades identificadas durante o desenvolvimento.

A rastreabilidade completa entre requisitos, User Stories, Tasks, branches, commits e Pull Requests permanece registrada no Jira e no GitHub.
