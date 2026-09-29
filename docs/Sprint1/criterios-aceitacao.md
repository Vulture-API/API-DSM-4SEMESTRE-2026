# Critérios de Aceitação para Cadastro de Estações Meteorológicas, Sensores e Usuários

## US01

- **CA1:** Permitir cadastrar uma estação meteorológica.
- **CA2:** Código, Nome e Localização devem ser obrigatórios.
- **CA3:** Não permitir códigos duplicados.
- **CA4:** Permitir editar os dados da estação.
- **CA5:** Permitir ativar e desativar estações.
- **CA6:** Exibir mensagem de sucesso após cadastro ou alteração.

## US02

- **CA1:** Permitir cadastrar sensores vinculados a uma estação.
- **CA2:** Nome, Tipo de Medição e Unidade de Medida devem ser obrigatórios.
- **CA3:** Permitir definir limites mínimos e máximos.
- **CA4:** Permitir editar sensores cadastrados.
- **CA5:** Não permitir sensores sem associação a uma estação.
- **CA6:** Exibir mensagem de sucesso após cadastro ou alteração.

## US03

- **CA1:** Permitir cadastrar usuários.
- **CA2:** Validar os campos obrigatórios.
- **CA3:** Não permitir usuários duplicados.
- **CA4:** Permitir editar usuários cadastrados.
- **CA5:** Permitir ativar e desativar usuários.
- **CA6:** Exibir mensagem de sucesso após cadastro ou alteração.

## US04

- **CA1:** Exibir todas as estações cadastradas.
- **CA2:** Apresentar o status: Online, Offline ou Com Alerta.
- **CA3:** Exibir data e hora da última comunicação.
- **CA4:** Atualizar automaticamente o status conforme o envio de dados.
- **CA5:** Permitir filtrar estações por status.

## US05

- **CA1:** Permitir cadastrar alertas meteorológicos.
- **CA2:** Permitir selecionar o parâmetro que acionará o alerta.
- **CA3:** Permitir definir limites para acionamento do alerta.
- **CA4:** Permitir ativar e desativar alertas cadastrados.
- **CA5:** O sistema deve notificar o Gerente Agrícola quando uma condição configurada for atingida.

## US06

- **CA1:** O sistema deve permanecer disponível durante a operação das estações.
- **CA2:** O sistema deve suportar o crescimento da quantidade de estações cadastradas.
- **CA3:** O sistema deve suportar o crescimento da quantidade de dados recebidos.
- **CA4:** O sistema deve monitorar sua disponibilidade.
- **CA5:** O sistema deve atender ao nível de disponibilidade definido no SLA.
