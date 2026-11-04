# Cenários de teste da Sprint 3

**Sprint 3 · 02/11/2026 a 22/11/2026**

[Backlog](backlog-sprint-3.md) · [Cenários](cenarios-sprint-3.md) · [Critérios de aceitação](criterios-aceitacao.md) · [Tasks](tasks-sprint-3.md)

Cenários planejados para validação.

## US15

**História de usuário:** Como Gerente Agrícola, quero gerar três tipos de relatórios meteorológicos, para consultar os dados coletados. [SCRUM-554](https://vultureapi.atlassian.net/browse/SCRUM-554)

### Cenário 1 — Geração dos relatórios

**Dado que** há medições disponíveis,  
**quando** o gerente solicita cada um dos três tipos de relatório,  
**então** o serviço organiza os dados conforme o tipo selecionado. [SCRUM-558](https://vultureapi.atlassian.net/browse/SCRUM-558)

### Cenário 2 — Filtros combinados

**Dado que** existem medições de duas estações em períodos diferentes,  
**quando** o gerente seleciona uma estação e um intervalo,  
**então** o relatório contém somente as medições correspondentes aos dois filtros. [SCRUM-562](https://vultureapi.atlassian.net/browse/SCRUM-562)

### Cenário 3 — Exportação

**Dado que** um relatório foi gerado,  
**quando** o gerente solicita sua exportação,  
**então** o arquivo contém os dados do relatório selecionado. [SCRUM-566](https://vultureapi.atlassian.net/browse/SCRUM-566)

## US16

**História de usuário:** Como Cliente, quero visualizar os dados meteorológicos disponibilizados, para acompanhar as condições climáticas. [SCRUM-555](https://vultureapi.atlassian.net/browse/SCRUM-555)

### Cenário 1 — Consulta filtrada

**Dado que** existem medições de mais de uma estação,  
**quando** o cliente consulta uma estação e um período,  
**então** a interface apresenta as medições correspondentes. [SCRUM-570](https://vultureapi.atlassian.net/browse/SCRUM-570)

### Cenário 2 — Última atualização

**Dado que** uma nova medição foi disponibilizada,  
**quando** a interface atualiza os dados,  
**então** o horário exibido corresponde à última atualização. [SCRUM-572](https://vultureapi.atlassian.net/browse/SCRUM-572)

### Cenário 3 — Consulta sem dados

**Dado que** nenhuma medição corresponde ao filtro,  
**quando** o serviço processa a consulta,  
**então** o resultado indica ausência de dados para a seleção. [SCRUM-568](https://vultureapi.atlassian.net/browse/SCRUM-568)

## US17

**História de usuário:** Como Cliente, quero que o sistema possua um pipeline de CI, para automação de testes e validações de código. [SCRUM-556](https://vultureapi.atlassian.net/browse/SCRUM-556)

### Cenário 1 — Etapas de teste

**Dado que** um PR aciona o CI,  
**quando** o workflow executa a validação,  
**então** é possível distinguir a execução e o resultado dos testes unitários e de integração. [SCRUM-596](https://vultureapi.atlassian.net/browse/SCRUM-596)

### Cenário 2 — Falha em verificação obrigatória

**Dado que** um PR está aberto,  
**quando** uma verificação obrigatória falha,  
**então** o merge permanece bloqueado. [SCRUM-577](https://vultureapi.atlassian.net/browse/SCRUM-577)

### Cenário 3 — Publicação da versão

**Dado que** uma versão passou pelas verificações obrigatórias,  
**quando** o deploy termina e a equipe consulta a interface publicada,  
**então** a consulta à API funciona e a versão testada fica identificada. [SCRUM-593](https://vultureapi.atlassian.net/browse/SCRUM-593)

## US18

**História de usuário:** Como Administrador, quero configurar o datalogger e a coleta dos dados, para permitir o funcionamento da estação meteorológica. [SCRUM-557](https://vultureapi.atlassian.net/browse/SCRUM-557)

### Cenário 1 — Montagem

**Dado que** os componentes foram selecionados,  
**quando** a equipe liga a estação montada,  
**então** o ESP32 inicia com os sensores conectados. [SCRUM-579](https://vultureapi.atlassian.net/browse/SCRUM-579)

### Cenário 2 — Leitura

**Dado que** os sensores estão configurados,  
**quando** o firmware realiza uma coleta,  
**então** os sensores fornecem os parâmetros meteorológicos previstos. [SCRUM-580](https://vultureapi.atlassian.net/browse/SCRUM-580)

### Cenário 3 — Intervalo de coleta

**Dado que** o datalogger está em operação,  
**quando** o administrador configura uma frequência válida,  
**então** as próximas coletas seguem o intervalo definido. [SCRUM-583](https://vultureapi.atlassian.net/browse/SCRUM-583)

### Cenário 4 — Recepção MQTT

**Dado que** a estação produziu uma medição válida,  
**quando** o ESP32 publica a mensagem,  
**então** o serviço Python recebe a telemetria e a encaminha ao Redis. [SCRUM-584](https://vultureapi.atlassian.net/browse/SCRUM-584)

### Cenário 5 — Validação do payload

**Dado que** uma leitura é inválida,  
**quando** o firmware prepara a publicação,  
**então** a leitura inválida não é publicada como medição válida. [SCRUM-585](https://vultureapi.atlassian.net/browse/SCRUM-585)

### Cenário 6 — Falha de comunicação

**Dado que** a estação está coletando,  
**quando** a comunicação é interrompida,  
**então** o status permite identificar a falha. [SCRUM-586](https://vultureapi.atlassian.net/browse/SCRUM-586)

### Cenário 7 — Acompanhamento

**Dado que** a estação possui configuração disponível,  
**quando** o administrador consulta a interface,  
**então** ele consegue acompanhar a coleta e acessar os parâmetros configuráveis. [SCRUM-589](https://vultureapi.atlassian.net/browse/SCRUM-589)

### Cenário 8 — Validação ponta a ponta

**Dado que** a versão está publicada e a estação envia uma medição identificada,  
**quando** o QA consulta a estação na interface,  
**então** a estação e o valor exibidos correspondem à medição enviada. [SCRUM-594](https://vultureapi.atlassian.net/browse/SCRUM-594)

## US06 — Monitoramento na versão integrada

**Dado que** a aplicação está disponível e a estação transmite medições,  
**quando** a equipe interrompe apenas o envio do ESP32 e depois o retoma,  
**então** a aplicação continua respondendo, o horário da última medição permanece inalterado durante a interrupção e avança depois da retomada. Registrar evidências dos três momentos. [SCRUM-592](https://vultureapi.atlassian.net/browse/SCRUM-592)
