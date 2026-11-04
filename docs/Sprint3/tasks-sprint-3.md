# Tasks da Sprint 3

**Sprint 3 · 02/11/2026 a 22/11/2026**

[Backlog](backlog-sprint-3.md) · [Cenários](cenarios-sprint-3.md) · [Critérios de aceitação](criterios-aceitacao.md) · [Tasks](tasks-sprint-3.md)


## Tarefas sem pai informado no Jira

| Jira | Task |
|---|---|
| [SCRUM-543](https://vultureapi.atlassian.net/browse/SCRUM-543) | [QA] Validar compatibilidade da aplicação nos navegadores suportados |
| [SCRUM-544](https://vultureapi.atlassian.net/browse/SCRUM-544) | [DEVOPS/DB] Implementar estratégia de backup e restauração do banco de dados |
| [SCRUM-545](https://vultureapi.atlassian.net/browse/SCRUM-545) | [UX/QA] Validar usabilidade das principais interfaces do sistema |
| [SCRUM-596](https://vultureapi.atlassian.net/browse/SCRUM-596) | [DEVOPS][TESTE] Estruturar e nomear etapas de testes unitários e de integração na pipeline de CI |

## US15 - Como Gerente Agrícola, quero gerar três tipos de relatórios meteorológicos, para consultar os dados coletados.

| Jira | Task |
|---|---|
| [SCRUM-558](https://vultureapi.atlassian.net/browse/SCRUM-558) | [BACK] Implementar serviço para geração dos três tipos de relatórios meteorológicos |
| [SCRUM-559](https://vultureapi.atlassian.net/browse/SCRUM-559) | [TESTE][BACK] Criar testes unitários do serviço de geração de relatórios meteorológicos |
| [SCRUM-560](https://vultureapi.atlassian.net/browse/SCRUM-560) | [BACK] Criar endpoints para solicitação e consulta dos relatórios |
| [SCRUM-561](https://vultureapi.atlassian.net/browse/SCRUM-561) | [TESTE][INTEGRAÇÃO] Validar geração, consulta e visualização dos relatórios |
| [SCRUM-562](https://vultureapi.atlassian.net/browse/SCRUM-562) | [BACK] Aplicar filtros por período e estação na geração de relatórios |
| [SCRUM-563](https://vultureapi.atlassian.net/browse/SCRUM-563) | [TESTE][BACK] Criar testes unitários dos filtros de relatórios |
| [SCRUM-564](https://vultureapi.atlassian.net/browse/SCRUM-564) | [FRONT] Desenvolver interface para seleção e visualização dos relatórios |
| [SCRUM-565](https://vultureapi.atlassian.net/browse/SCRUM-565) | [TESTE][FRONT] Criar testes unitários da interface de relatórios |
| [SCRUM-566](https://vultureapi.atlassian.net/browse/SCRUM-566) | [INTEGRAÇÃO] Implementar exportação dos relatórios em formato adequado |
| [SCRUM-567](https://vultureapi.atlassian.net/browse/SCRUM-567) | [TESTE][BACK] Criar testes unitários das regras de exportação de relatórios |

## US16 - Como Cliente, quero visualizar os dados meteorológicos disponibilizados, para acompanhar as condições climáticas.

| Jira | Task |
|---|---|
| [SCRUM-568](https://vultureapi.atlassian.net/browse/SCRUM-568) | [TESTE][BACK] Criar testes unitários do serviço de disponibilização dos dados meteorológicos |
| [SCRUM-569](https://vultureapi.atlassian.net/browse/SCRUM-569) | [TESTE][FRONT] Criar testes unitários dos componentes de visualização dos dados meteorológicos |
| [SCRUM-570](https://vultureapi.atlassian.net/browse/SCRUM-570) | [BACK] Aplicar filtros por período e estação aos dados meteorológicos disponibilizados |
| [SCRUM-571](https://vultureapi.atlassian.net/browse/SCRUM-571) | [TESTE][BACK] Criar testes unitários dos filtros dos dados meteorológicos disponibilizados |
| [SCRUM-572](https://vultureapi.atlassian.net/browse/SCRUM-572) | [FRONT] Exibir data e hora da última atualização dos dados meteorológicos |
| [SCRUM-573](https://vultureapi.atlassian.net/browse/SCRUM-573) | [TESTE][FRONT] Criar testes unitários da exibição da última atualização |
| [SCRUM-595](https://vultureapi.atlassian.net/browse/SCRUM-595) | [TESTE][INTEGRAÇÃO] Validar consulta, visualização e atualização dos dados meteorológicos |

## US17 - Como Cliente, quero que o sistema possua um pipeline de CI, para automação de testes e validações de código.

| Jira | Task |
|---|---|
| [SCRUM-574](https://vultureapi.atlassian.net/browse/SCRUM-574) | [DEVOPS][BACK] Separar testes unitários e de integração no pipeline |
| [SCRUM-575](https://vultureapi.atlassian.net/browse/SCRUM-575) | [DEVOPS][FRONT] Separar testes unitários e de integração no pipeline |
| [SCRUM-576](https://vultureapi.atlassian.net/browse/SCRUM-576) | [DEVOPS][RECEPÇÃO] Separar testes unitários e de integração no pipeline |
| [SCRUM-577](https://vultureapi.atlassian.net/browse/SCRUM-577) | [DEVOPS] Atualizar template de PR e configurar checks obrigatórios |
| [SCRUM-593](https://vultureapi.atlassian.net/browse/SCRUM-593) | [DEVOPS][DEPLOY] Publicar e validar a versão integrada da Sprint 3 |

## US18 - Como Administrador, quero configurar o datalogger e a coleta dos dados, para permitir o funcionamento da estação meteorológica.

| Jira | Task |
|---|---|
| [SCRUM-578](https://vultureapi.atlassian.net/browse/SCRUM-578) | [HARDWARE] Selecionar componentes eletrônicos da estação meteorológica |
| [SCRUM-579](https://vultureapi.atlassian.net/browse/SCRUM-579) | [HARDWARE] Montar estação meteorológica com ESP32 e sensores |
| [SCRUM-580](https://vultureapi.atlassian.net/browse/SCRUM-580) | [HARDWARE/FIRMWARE] Configurar sensores meteorológicos no ESP32 |
| [SCRUM-581](https://vultureapi.atlassian.net/browse/SCRUM-581) | [FIRMWARE] Desenvolver rotina de coleta e processamento dos dados dos sensores |
| [SCRUM-582](https://vultureapi.atlassian.net/browse/SCRUM-582) | [FIRMWARE] Configurar parâmetros de comunicação MQTT do datalogger |
| [SCRUM-583](https://vultureapi.atlassian.net/browse/SCRUM-583) | [FIRMWARE] Implementar configuração da frequência de coleta dos dados |
| [SCRUM-584](https://vultureapi.atlassian.net/browse/SCRUM-584) | [INTEGRAÇÃO] Integrar datalogger ESP32 ao serviço de recepção via MQTT |
| [SCRUM-585](https://vultureapi.atlassian.net/browse/SCRUM-585) | [FIRMWARE] Validar leituras e payload antes da publicação MQTT |
| [SCRUM-586](https://vultureapi.atlassian.net/browse/SCRUM-586) | [FIRMWARE] Registrar status da coleta e falhas do datalogger |
| [SCRUM-587](https://vultureapi.atlassian.net/browse/SCRUM-587) | [BACK] Disponibilizar configuração da frequência de coleta do datalogger |
| [SCRUM-588](https://vultureapi.atlassian.net/browse/SCRUM-588) | [TESTE][BACK] Criar testes unitários da configuração da frequência de coleta |
| [SCRUM-589](https://vultureapi.atlassian.net/browse/SCRUM-589) | [FRONT] Desenvolver interface de configuração e acompanhamento da coleta |
| [SCRUM-590](https://vultureapi.atlassian.net/browse/SCRUM-590) | [TESTE][FRONT] Criar testes unitários da interface de configuração da coleta |
| [SCRUM-591](https://vultureapi.atlassian.net/browse/SCRUM-591) | [TESTE][INTEGRAÇÃO] Validar integrações do datalogger e da estação meteorológica |
| [SCRUM-594](https://vultureapi.atlassian.net/browse/SCRUM-594) | [QA][INTEGRAÇÃO] Validar o fluxo de dados do ESP32 até a interface |

## US06 - Como Cliente, quero contar com a disponibilidade e escalabilidade do sistema, para suportar o crescimento das estações e atender ao SLA definido.

| Jira | Task |
|---|---|
| [SCRUM-592](https://vultureapi.atlassian.net/browse/SCRUM-592) | [DEVOPS][MONITORAMENTO] Validar o monitoramento da aplicação e da telemetria da estação ESP32 |
