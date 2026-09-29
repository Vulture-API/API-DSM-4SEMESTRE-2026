# Cenários

## US01

**História de Usuário:** Como Administrador, quero cadastrar e gerenciar estações meteorológicas, para controlar as estações instaladas.

### Cenário 1 - Cadastro de estação bem-sucedido

**Dado que** o Administrador está na tela de cadastro de estações  
**Quando** informar Código, Nome e Localização válidos e confirmar o cadastro  
**Então** o sistema deve registrar a estação e exibir uma mensagem de sucesso.

### Cenário 2 - Tentativa de cadastro com código duplicado

**Dado que** já existe uma estação cadastrada com determinado código  
**Quando** o Administrador tentar cadastrar outra estação utilizando o mesmo código  
**Então** o sistema deve impedir o cadastro e informar que o código já está sendo utilizado.

### Cenário 3 - Atualização de dados da estação

**Dado que** existe uma estação cadastrada  
**Quando** o Administrador alterar seus dados e confirmar a atualização  
**Então** o sistema deve salvar as alterações e exibir uma mensagem de sucesso.

---

## US02

**História de Usuário:** Como Administrador, quero cadastrar sensores e parâmetros, para permitir diferentes tipos de medições.

### Cenário 1 - Cadastro de sensor bem-sucedido

**Dado que** existe uma estação cadastrada  
**Quando** o Administrador informar os dados obrigatórios do sensor e confirmar o cadastro  
**Então** o sistema deve registrar o sensor e associá-lo à estação selecionada.

### Cenário 2 - Tentativa de cadastro sem estação associada

**Dado que** o Administrador está cadastrando um sensor  
**Quando** tentar concluir o cadastro sem selecionar uma estação  
**Então** o sistema deve impedir o cadastro e informar que a associação a uma estação é obrigatória.

### Cenário 3 - Alteração dos parâmetros do sensor

**Dado que** existe um sensor cadastrado  
**Quando** o Administrador alterar seus parâmetros de medição e salvar as alterações  
**Então** o sistema deve atualizar as configurações do sensor.

---

## US03

**História de Usuário:** Como Administrador, quero identificar estações ou sensores com falhas ou dados inconsistentes, para facilitar a manutenção.

### Cenário 1 - Identificação de estação sem comunicação

**Dado que** existe uma estação cadastrada e ativa  
**Quando** a estação permanecer sem enviar dados por período superior ao configurado  
**Então** o sistema deve registrar uma ocorrência de falha de comunicação.

### Cenário 2 - Identificação de dados inconsistentes

**Dado que** existe um sensor com limites configurados  
**Quando** for recebida uma medição fora dos limites definidos  
**Então** o sistema deve registrar uma inconsistência e gerar um alerta.

### Cenário 3 - Consulta de falhas registradas

**Dado que** existem falhas registradas no sistema  
**Quando** o Administrador acessar a lista de ocorrências  
**Então** o sistema deve exibir data, hora, tipo e status de cada ocorrência.

---

## US04

**História de Usuário:** Como Gerente Agrícola, quero visualizar o status das estações, para identificar problemas de comunicação.

### Cenário 1 - Visualização das estações cadastradas

**Dado que** existem estações cadastradas  
**Quando** o Gerente Agrícola acessar a tela de monitoramento  
**Então** o sistema deve exibir todas as estações e seus respectivos status.

### Cenário 2 - Visualização da última comunicação

**Dado que** uma estação possui registros de comunicação  
**Quando** o Gerente consultar seus detalhes  
**Então** o sistema deve exibir a data e hora da última comunicação.

### Cenário 3 - Filtragem por status

**Dado que** existem estações com diferentes status  
**Quando** o Gerente selecionar um filtro  
**Então** o sistema deve exibir somente as estações correspondentes.

---

## US05

**História de Usuário:** Como Desenvolvedor, quero disponibilizar uma API para receber os dados das estações, para centralizar as informações.

### Cenário 1 - Recebimento de dados válido

**Dado que** a estação está cadastrada  
**Quando** enviar uma requisição válida para a API  
**Então** a API deve receber os dados e retornar confirmação de sucesso.

### Cenário 2 - Recebimento de estação inválida

**Dado que** a API está disponível  
**Quando** receber requisição associada a uma estação inexistente  
**Então** a API deve rejeitar a requisição e retornar erro.

### Cenário 3 - Recebimento em formato inválido

**Dado que** a API está disponível  
**Quando** receber dados fora do formato JSON esperado  
**Então** a API deve rejeitar a requisição e informar o erro encontrado.

---

## US06

**História de Usuário:** Como Desenvolvedor, quero validar e armazenar os dados recebidos, para evitar informações inconsistentes e permitir consultas históricas.

### Cenário 1 - Armazenamento de dados válidos

**Dado que** a API recebeu dados válidos  
**Quando** os dados forem processados  
**Então** o sistema deve validar e armazenar as medições.

### Cenário 2 - Rejeição de dados inconsistentes

**Dado que** a API recebeu dados fora dos parâmetros  
**Quando** os dados forem processados  
**Então** o sistema deve impedir o armazenamento.

### Cenário 3 - Disponibilização do histórico

**Dado que** existem medições armazenadas  
**Quando** uma consulta ao histórico for realizada  
**Então** o sistema deve retornar as medições correspondentes.

---

## US07

**História de Usuário:** Como Cliente, quero visualizar os dados meteorológicos disponibilizados, para acompanhar as condições climáticas.

### Cenário 1 - Visualização bem-sucedida dos dados meteorológicos

**Dado que** o Cliente está na tela de consulta de dados meteorológicos  
**Quando** selecionar uma estação disponível  
**Então** o sistema deve exibir os dados meteorológicos mais recentes da estação, incluindo os parâmetros medidos pelos sensores.

### Cenário 2 - Tentativa de edição dos dados pelo Cliente

**Dado que** o Cliente está visualizando os dados de uma estação  
**Quando** tentar editar ou excluir algum dado meteorológico  
**Então** o sistema deve impedir a ação, pois o Cliente possui apenas permissão de visualização.

### Cenário 3 - Estação sem dados recentes disponíveis

**Dado que** uma estação selecionada não possui dados coletados recentemente  
**Quando** o Cliente tentar visualizar seus dados  
**Então** o sistema deve informar que não há dados disponíveis no momento.
