# Critérios de Aceitação

## Sprint 2

### US06

**História de Usuário:** Como Cliente, quero contar com a disponibilidade e escalabilidade do sistema, para suportar o crescimento das estações e atender ao SLA definido.

**CA1:** O sistema deve permanecer disponível conforme o percentual de disponibilidade definido no SLA.

**CA2:** O sistema deve monitorar e registrar o tempo de disponibilidade e indisponibilidade da aplicação.

**CA3:** O sistema deve monitorar o desempenho e o consumo de recursos da aplicação.

**CA4:** O sistema deve suportar o aumento da quantidade de estações e dados sem comprometer o funcionamento do sistema.

**CA5:** O sistema deve permitir identificar períodos de indisponibilidade e falhas de desempenho.

---

### US07

**História de Usuário:** Como Gerente Agrícola, quero visualizar os dados meteorológicos atuais, para acompanhar as condições climáticas.

**CA1:** O sistema deve exibir os dados meteorológicos atuais das estações cadastradas.

**CA2:** O sistema deve apresentar os valores dos parâmetros meteorológicos monitorados.

**CA3:** O sistema deve exibir a data e hora da última atualização dos dados.

**CA4:** O sistema deve identificar a estação relacionada a cada conjunto de dados apresentado.

**CA5:** O sistema deve atualizar os dados conforme novas medições forem recebidas.

---

### US08

**História de Usuário:** Como Gerente Agrícola, quero visualizar o histórico dos dados, para analisar períodos anteriores.

**CA1:** O sistema deve permitir consultar dados meteorológicos históricos.

**CA2:** O sistema deve permitir selecionar um período para consulta.

**CA3:** O sistema deve permitir selecionar a estação desejada.

**CA4:** O sistema deve apresentar os dados históricos de forma organizada e compreensível.

**CA5:** O sistema deve informar a data e hora de cada medição apresentada.

---

### US09

**História de Usuário:** Como Administrador, quero identificar estações ou sensores com falhas ou dados inconsistentes, para facilitar a manutenção.

**CA1:** O sistema deve identificar estações sem comunicação dentro do período configurado.

**CA2:** O sistema deve identificar sensores que apresentem dados fora dos limites configurados.

**CA3:** O sistema deve identificar dados ausentes ou inconsistentes.

**CA4:** O sistema deve apresentar a estação ou sensor relacionado à falha identificada.

**CA5:** O sistema deve permitir consultar o histórico de ocorrências identificadas.

---

### US10

**História de Usuário:** Como Administrador, quero gerenciar o acesso de usuários cadastrados no Sistema, para controlar os níveis de acesso.

**CA1:** O sistema deve permitir consultar os usuários cadastrados.

**CA2:** O sistema deve permitir atribuir níveis de acesso aos usuários.

**CA3:** O sistema deve permitir alterar o nível de acesso de um usuário.

**CA4:** O sistema deve impedir que usuários acessem funcionalidades não autorizadas para seu nível de acesso.

**CA5:** O sistema deve permitir ativar e desativar o acesso dos usuários.

---

### US11

**História de Usuário:** Como Gerente Agrícola, quero visualizar estatísticas dos dados, para analisar o comportamento do clima e visualizar previsões futuras.

**CA1:** O sistema deve apresentar estatísticas dos dados meteorológicos coletados.

**CA2:** O sistema deve permitir selecionar o período utilizado para geração das estatísticas.

**CA3:** O sistema deve apresentar medidas estatísticas relevantes para os parâmetros meteorológicos monitorados.

**CA4:** O sistema deve apresentar gráficos ou indicadores para facilitar a análise dos dados.

**CA5:** O sistema deve disponibilizar previsões futuras quando houver dados ou serviço de previsão disponível.

---

### US12

**História de Usuário:** Como Gerente Agrícola, quero receber os dados tratados das estações, para centralizar as informações.

**CA1:** O sistema deve receber os dados enviados pelas estações meteorológicas.

**CA2:** O sistema deve validar os dados recebidos antes de armazená-los.

**CA3:** O sistema deve tratar dados inválidos ou inconsistentes conforme as regras definidas.

**CA4:** O sistema deve associar os dados tratados à estação e ao sensor correspondente.

**CA5:** O sistema deve disponibilizar os dados tratados para consulta no sistema.

---

### US13

**História de Usuário:** Como Gerente Agrícola, quero cadastrar e gerenciar propriedades agrícolas, para associá-las às estações meteorológicas e organizar o monitoramento climático de cada propriedade.

**CA1:** O sistema deve permitir cadastrar uma propriedade agrícola com suas informações de identificação e localização.

**CA2:** O sistema deve permitir consultar as propriedades agrícolas cadastradas.

**CA3:** O sistema deve permitir editar e atualizar os dados de uma propriedade cadastrada.

**CA4:** O sistema deve permitir associar uma ou mais estações meteorológicas a uma propriedade.

**CA5:** O sistema deve permitir excluir ou desativar uma propriedade cadastrada, respeitando as regras de integridade dos dados.

---

### US16

**História de Usuário:** Como Cliente, quero que o sistema possua um pipeline de CI, para automação de testes e validações de código.

**CA1:** O sistema deve executar automaticamente o pipeline de Integração Contínua após alterações no código.

**CA2:** O pipeline deve executar os testes automatizados configurados para o projeto.

**CA3:** O pipeline deve realizar a validação e o build da aplicação.

**CA4:** O pipeline deve realizar as verificações de qualidade e validação do código configuradas no projeto.

**CA5:** O sistema deve registrar e disponibilizar o resultado de cada execução do pipeline.
