# Tasks Sprint 1

## Atividades gerais

- Configurar um repositório de template para os microsserviços de API.
- Modelar o banco de dados completo.
- Definir o contrato de API.

---

## US01 - Como Administrador, quero cadastrar e gerenciar estações meteorológicas, para controlar as estações instaladas.

| Item | Detalhes |
|---|---|
| **Back - Criar microsserviço "Estações"** | Estruturar a base do serviço dedicado exclusivamente ao gerenciamento das estações meteorológicas, garantindo o isolamento das regras de negócio. |
| **Back - Criar endpoints CRUD para Estações** | Implementar as funcionalidades completas de criação, leitura, atualização e exclusão. O endpoint CREATE deve validar os campos obrigatórios (Nome, Localização e Ativo/Inativo). |
| **Front - Criar tela para listagem de estações** | Desenvolver uma interface em formato de tabela ou cards que exiba todas as estações cadastradas, permitindo visualizar rapidamente a localização e o status atual de operação. |
| **Front - Criar tela para cadastro e gerenciamento de estações** | Desenvolver um formulário validado para a inserção de novas estações meteorológicas e edição dos dados das estações já existentes na base. |

---

## US02 - Como Administrador, quero cadastrar sensores e parâmetros, para permitir diferentes tipos de medições.

| Item | Detalhes |
|---|---|
| **Back - Estruturar Modelo de Dados Dinâmico** | Modelar tabelas no Postgres que suportem a vinculação de múltiplos tipos de sensores (vento, índice pluviométrico, umidade, temperatura e pressão) a uma mesma estação. |
| **Back - Criar endpoints CRUD para Parâmetros e Sensores** | Implementar rotas para registrar novos tipos de sensores, definir suas unidades de medida e realizar a associação dinâmica com as estações cadastradas. |
| **Front - Criar tela de gestão de parâmetros meteorológicos** | Construir a interface para o Administrador adicionar, visualizar, editar ou remover parâmetros de medição do sistema. |
| **Front - Integrar sensores ao gerenciamento da estação** | Modificar a tela de gerenciamento de estações (criada na US01) para incluir uma seção onde o Administrador possa selecionar e vincular os sensores físicos presentes no datalogger daquela unidade. |

---

## US03 - Como Administrador, quero cadastrar e gerenciar usuários, para incluí-los no Sistema.

| Item | Detalhes |
|---|---|
| **Back - Criar endpoints CRUD de Usuários** | Implementar rotas para a criação, listagem, atualização de perfis e exclusão/desativação de usuários no sistema. |
| **Front - Criar tela de listagem de usuários** | Construir um painel onde seja possível visualizar a lista de usuários. |
| **Front - Criar tela de gestão de usuários** | Construir um painel onde seja possível cadastrar e gerenciar usuários. |

---

## US04 - Como Gerente Agrícola, quero visualizar o status das estações, para identificar problemas de comunicação.

| Item | Detalhes |
|---|---|
| **Back - Desenvolver serviço de recepção e status** | Criar a lógica para processar os dados enviados pelas estações. Implementar um endpoint que calcule o status de comunicação (Online/Offline) baseado no intervalo de tempo da última recepção do datalogger. |
| **Front - Criar Dashboard de monitoramento de comunicação** | Desenvolver uma interface visual interativa focada na usabilidade para exibir o status em tempo real de todas as estações implantadas no campo. |
| **Front - Implementar indicativos visuais de falha** | Adicionar alertas visuais dinâmicos (como ícones de erro ou alteração de cores) na listagem e no dashboard de monitoramento caso uma estação ultrapasse o tempo limite sem enviar dados. |

---

## US05 - Como Gerente Agrícola, quero cadastrar e configurar alertas meteorológicos, para ser avisado sobre condições críticas.

| Item | Detalhes |
|---|---|
| **Back - Criar motor de processamento de regras** | Estruturar um serviço em background que avalie continuamente os dados meteorológicos recebidos e cruze essas informações com os parâmetros críticos definidos pelo usuário. |
| **Back - Criar endpoints CRUD para Alertas** | Desenvolver rotas para a criação automática de notificações baseadas em limites de condições meteorológicas específicas, bem como sua edição e exclusão. |
| **Front - Criar tela de configuração de limites e regras** | Desenvolver um formulário onde o Gerente Agrícola possa definir regras (ex: "Avisar se Temperatura > 35ºC") e associá-las a estações específicas. |
| **Front - Criar tela de gestão de alertas** | Desenvolver uma tela para listagem e gestão de alertas cadastrados. |

---

## US06 - Como Cliente, quero contar com a disponibilidade e escalabilidade do sistema, para suportar o crescimento das estações e atender ao SLA definido.

| Item | Detalhes |
|---|---|
| **DevOps - Configurar Pipeline de Integração Contínua (IC)** | Implementar um pipeline de IC para a execução automática de testes e validação de código a cada atualização no repositório. |
| **DevOps - Configurar Deploy Automatizado** | Estruturar a entrega contínua garantindo que o deploy seja feito de acordo com as necessidades do produto, visando manter o SLA de disponibilidade rigoroso (99,9%). |
| **Back - Otimizar persistência para alto volume de dados** | Projetar e aplicar otimizações no banco de dados Postgres (como índices e particionamento) para garantir ganho de performance na recepção massiva e processamento de dados do IoT em tempo real. |
