# Cenários

## Sprint 2

### US06

**História de Usuário:** Como Cliente, quero contar com a disponibilidade e escalabilidade do sistema, para suportar o crescimento das estações e atender ao SLA definido.

#### Cenário 1 - Monitoramento da disponibilidade do sistema

**Dado que** o sistema está em funcionamento

**Quando** o serviço de monitoramento verificar a disponibilidade da aplicação

**Então** o sistema deve registrar o período de disponibilidade e identificar eventuais períodos de indisponibilidade.

#### Cenário 2 - Identificação de indisponibilidade

**Dado que** o sistema apresentar uma interrupção no serviço

**Quando** o monitoramento identificar a indisponibilidade

**Então** o sistema deve registrar a ocorrência e seu respectivo período.

#### Cenário 3 - Monitoramento de desempenho

**Dado que** o sistema está recebendo requisições e processando dados

**Quando** o monitoramento de desempenho for executado

**Então** o sistema deve registrar informações relacionadas ao tempo de resposta e utilização dos recursos.

#### Cenário 4 - Validação da capacidade do sistema

**Dado que** o sistema precisa suportar o crescimento da quantidade de estações e dados

**Quando** forem executados testes de carga

**Então** o sistema deve manter seu funcionamento dentro dos parâmetros de desempenho definidos.

#### Cenário 5 - Validação do SLA

**Dado que** o sistema possui um SLA de disponibilidade definido

**Quando** for analisado o período de funcionamento do sistema

**Então** a disponibilidade registrada deve atender ao percentual de 99% estabelecido no SLA.

---

### US07

**História de Usuário:** Como Gerente Agrícola, quero visualizar os dados meteorológicos atuais, para acompanhar as condições climáticas.

#### Cenário 1 - Visualização dos dados meteorológicos atuais

**Dado que** existem estações cadastradas e com dados disponíveis

**Quando** o Gerente Agrícola acessar a tela de dados meteorológicos atuais

**Então** o sistema deve exibir os dados mais recentes das estações e os respectivos parâmetros meteorológicos.

#### Cenário 2 - Identificação da última atualização

**Dado que** uma estação possui dados meteorológicos registrados

**Quando** o Gerente Agrícola consultar os dados da estação

**Então** o sistema deve exibir a data e hora da última atualização recebida.

#### Cenário 3 - Atualização dos dados meteorológicos

**Dado que** uma estação está enviando novas medições

**Quando** novos dados forem recebidos pelo sistema

**Então** o sistema deve atualizar os dados meteorológicos apresentados ao Gerente Agrícola.

---

### US08

**História de Usuário:** Como Gerente Agrícola, quero visualizar o histórico dos dados, para analisar períodos anteriores.

#### Cenário 1 - Consulta do histórico de dados

**Dado que** existem dados meteorológicos armazenados

**Quando** o Gerente Agrícola acessar a tela de histórico

**Então** o sistema deve exibir as medições registradas para as estações selecionadas.

#### Cenário 2 - Consulta por período

**Dado que** existem medições armazenadas em diferentes períodos

**Quando** o Gerente Agrícola informar uma data inicial e uma data final

**Então** o sistema deve exibir somente os dados correspondentes ao período informado.

#### Cenário 3 - Consulta de histórico sem registros

**Dado que** não existem medições registradas para o período selecionado

**Quando** o Gerente Agrícola realizar a consulta

**Então** o sistema deve informar que não existem dados disponíveis para o período informado.

---

### US09

**História de Usuário:** Como Administrador, quero identificar estações ou sensores com falhas ou dados inconsistentes, para facilitar a manutenção.

#### Cenário 1 - Identificação de estação sem comunicação

**Dado que** existe uma estação cadastrada e ativa

**Quando** a estação permanecer sem enviar dados pelo período configurado

**Então** o sistema deve identificar a estação como uma ocorrência de falha de comunicação.

#### Cenário 2 - Identificação de dados fora dos limites

**Dado que** existe um sensor com limites mínimos e máximos configurados

**Quando** for recebida uma medição fora dos limites definidos

**Então** o sistema deve identificar o dado como inconsistente e registrar uma ocorrência.

#### Cenário 3 - Consulta de estações ou sensores com falhas

**Dado que** existem falhas ou inconsistências registradas

**Quando** o Administrador acessar a tela de ocorrências

**Então** o sistema deve exibir as estações ou sensores afetados, o tipo da ocorrência, a data e o status.

---

### US10

**História de Usuário:** Como Administrador, quero gerenciar o acesso de usuários cadastrados no Sistema, para controlar os níveis de acesso.

#### Cenário 1 - Alteração do nível de acesso

**Dado que** existe um usuário cadastrado no sistema

**Quando** o Administrador alterar seu nível de acesso e confirmar a alteração

**Então** o sistema deve atualizar as permissões do usuário.

#### Cenário 2 - Bloqueio de acesso de usuário

**Dado que** existe um usuário ativo no sistema

**Quando** o Administrador desativar seu acesso

**Então** o sistema deve impedir que o usuário acesse as funcionalidades do sistema.

#### Cenário 3 - Tentativa de acesso a funcionalidade não autorizada

**Dado que** o usuário possui um nível de acesso definido

**Quando** tentar acessar uma funcionalidade que não está autorizada para seu perfil

**Então** o sistema deve impedir o acesso e informar que o usuário não possui permissão.

---

### US11

**História de Usuário:** Como Gerente Agrícola, quero visualizar estatísticas dos dados, para analisar o comportamento do clima e visualizar previsões futuras.

#### Cenário 1 - Visualização das estatísticas meteorológicas

**Dado que** existem dados meteorológicos armazenados

**Quando** o Gerente Agrícola acessar a tela de estatísticas

**Então** o sistema deve apresentar estatísticas dos parâmetros meteorológicos disponíveis.

#### Cenário 2 - Consulta de estatísticas por período

**Dado que** existem dados meteorológicos registrados em diferentes períodos

**Quando** o Gerente Agrícola selecionar um período para análise

**Então** o sistema deve apresentar as estatísticas correspondentes ao período selecionado.

#### Cenário 3 - Visualização de previsões futuras

**Dado que** existem informações de previsão meteorológica disponíveis

**Quando** o Gerente Agrícola acessar a área de previsões

**Então** o sistema deve apresentar as previsões futuras para a região ou estação selecionada.

---

### US12

**História de Usuário:** Como Gerente Agrícola, quero receber os dados tratados das estações, para centralizar as informações.

#### Cenário 1 - Recebimento de dados válidos

**Dado que** uma estação cadastrada está enviando dados meteorológicos

**Quando** o sistema receber as medições

**Então** o sistema deve validar, tratar e disponibilizar os dados para consulta.

#### Cenário 2 - Tratamento de dados inconsistentes

**Dado que** o sistema recebeu dados que apresentam inconsistências

**Quando** os dados forem processados

**Então** o sistema deve identificar a inconsistência e impedir que dados inválidos sejam disponibilizados como dados tratados.

#### Cenário 3 - Associação dos dados à estação e ao sensor

**Dado que** o sistema recebeu uma medição válida

**Quando** o dado for processado e armazenado

**Então** o sistema deve associar a medição à estação e ao sensor correspondente.

---

### US13

**História de Usuário:** Como Gerente Agrícola, quero cadastrar e gerenciar propriedades agrícolas, para associá-las às estações meteorológicas e organizar o monitoramento climático de cada propriedade.

#### Cenário 1 - Cadastro de propriedade agrícola

**Dado que** o Gerente Agrícola possui as informações necessárias da propriedade

**Quando** realizar o cadastro da propriedade

**Então** o sistema deve registrar a propriedade com suas informações de identificação e localização.

#### Cenário 2 - Consulta de propriedades cadastradas

**Dado que** existem propriedades agrícolas cadastradas

**Quando** o Gerente Agrícola acessar a tela de propriedades

**Então** o sistema deve exibir as propriedades cadastradas e suas respectivas informações.

#### Cenário 3 - Atualização dos dados da propriedade

**Dado que** existe uma propriedade cadastrada

**Quando** o Gerente Agrícola alterar seus dados e confirmar a alteração

**Então** o sistema deve atualizar as informações da propriedade.

#### Cenário 4 - Associação de estação à propriedade

**Dado que** existe uma propriedade cadastrada e uma estação meteorológica disponível

**Quando** o Gerente Agrícola associar a estação à propriedade

**Então** o sistema deve registrar a associação entre a propriedade e a estação meteorológica.

#### Cenário 5 - Exclusão ou desativação da propriedade

**Dado que** existe uma propriedade cadastrada

**Quando** o Gerente Agrícola solicitar sua exclusão ou desativação

**Então** o sistema deve realizar a operação respeitando as regras de integridade dos dados e os vínculos existentes.

---

### US16

**História de Usuário:** Como Cliente, quero que o sistema possua um pipeline de CI, para automação de testes e validações de código.

#### Cenário 1 - Execução automática do pipeline

**Dado que** uma alteração foi realizada no código do projeto

**Quando** a alteração for enviada ao repositório configurado

**Então** o pipeline de Integração Contínua deve ser executado automaticamente.

#### Cenário 2 - Execução dos testes automatizados

**Dado que** o pipeline foi iniciado

**Quando** a etapa de testes for executada

**Então** o sistema deve executar os testes automatizados configurados e registrar seus resultados.

#### Cenário 3 - Validação e build da aplicação

**Dado que** os testes automatizados foram executados

**Quando** a etapa de validação e build for iniciada

**Então** o pipeline deve validar e gerar o build da aplicação conforme as configurações do projeto.

#### Cenário 4 - Validação da qualidade do código

**Dado que** o pipeline está em execução

**Quando** a etapa de análise de qualidade for executada

**Então** o sistema deve realizar as verificações de qualidade e informar eventuais problemas encontrados.

#### Cenário 5 - Registro do resultado do pipeline

**Dado que** uma execução do pipeline foi finalizada

**Quando** todas as etapas forem concluídas

**Então** o sistema deve registrar e disponibilizar o resultado da execução, indicando se o pipeline foi aprovado ou apresentou falhas.
