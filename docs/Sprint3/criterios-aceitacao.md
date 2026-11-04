# Critérios de aceitação da Sprint 3

**Sprint 3 · 02/11/2026 a 22/11/2026**

[Backlog](backlog-sprint-3.md) · [Cenários](cenarios-sprint-3.md) · [Critérios de aceitação](criterios-aceitacao.md) · [Tasks](tasks-sprint-3.md)

Os critérios abaixo sintetizam as tarefas de cada história. Na US18, a numeração CA1–CA8 segue a registrada no Jira.

## US15

**História de usuário:** Como Gerente Agrícola, quero gerar três tipos de relatórios meteorológicos, para consultar os dados coletados. [SCRUM-554](https://vultureapi.atlassian.net/browse/SCRUM-554)

- **Geração dos relatórios.** Quando o gerente solicita cada um dos três tipos de relatório, o serviço organiza os dados conforme o tipo selecionado. [SCRUM-558](https://vultureapi.atlassian.net/browse/SCRUM-558)
- **Filtros combinados.** Quando o gerente seleciona uma estação e um intervalo, o relatório contém somente as medições correspondentes aos dois filtros. [SCRUM-562](https://vultureapi.atlassian.net/browse/SCRUM-562)
- **Exportação.** Quando o gerente solicita sua exportação, o arquivo contém os dados do relatório selecionado. [SCRUM-566](https://vultureapi.atlassian.net/browse/SCRUM-566)

## US16

**História de usuário:** Como Cliente, quero visualizar os dados meteorológicos disponibilizados, para acompanhar as condições climáticas. [SCRUM-555](https://vultureapi.atlassian.net/browse/SCRUM-555)

- **Consulta filtrada.** Quando o cliente consulta uma estação e um período, a interface apresenta as medições correspondentes. [SCRUM-570](https://vultureapi.atlassian.net/browse/SCRUM-570)
- **Última atualização.** Quando a interface atualiza os dados, o horário exibido corresponde à última atualização. [SCRUM-572](https://vultureapi.atlassian.net/browse/SCRUM-572)
- **Consulta sem dados.** Quando o serviço processa a consulta, o resultado indica ausência de dados para a seleção. [SCRUM-568](https://vultureapi.atlassian.net/browse/SCRUM-568)

## US17

**História de usuário:** Como Cliente, quero que o sistema possua um pipeline de CI, para automação de testes e validações de código. [SCRUM-556](https://vultureapi.atlassian.net/browse/SCRUM-556)

- **Etapas de teste.** Quando o workflow executa a validação, é possível distinguir a execução e o resultado dos testes unitários e de integração. [SCRUM-596](https://vultureapi.atlassian.net/browse/SCRUM-596)
- **Falha em verificação obrigatória.** Quando uma verificação obrigatória falha, o merge permanece bloqueado. [SCRUM-577](https://vultureapi.atlassian.net/browse/SCRUM-577)
- **Publicação da versão.** Quando o deploy termina e a equipe consulta a interface publicada, a consulta à API funciona e a versão testada fica identificada. [SCRUM-593](https://vultureapi.atlassian.net/browse/SCRUM-593)

## US18

**História de usuário:** Como Administrador, quero configurar o datalogger e a coleta dos dados, para permitir o funcionamento da estação meteorológica. [SCRUM-557](https://vultureapi.atlassian.net/browse/SCRUM-557)

- CA1 — A estação meteorológica deve possuir ESP32 e os sensores necessários para realizar a coleta dos dados meteorológicos. [SCRUM-579](https://vultureapi.atlassian.net/browse/SCRUM-579)
- CA2 — Os sensores devem estar conectados e configurados corretamente no ESP32, permitindo a leitura dos parâmetros meteorológicos definidos. [SCRUM-580](https://vultureapi.atlassian.net/browse/SCRUM-580)
- CA3 — O datalogger deve permitir configurar a frequência de coleta dos dados meteorológicos. [SCRUM-583](https://vultureapi.atlassian.net/browse/SCRUM-583)
- CA4 — O sistema deve receber os dados coletados pelo ESP32 por meio da comunicação configurada. [SCRUM-584](https://vultureapi.atlassian.net/browse/SCRUM-584)
- CA5 — O sistema deve validar os dados coletados antes de realizar o envio. [SCRUM-585](https://vultureapi.atlassian.net/browse/SCRUM-585)
- CA6 — O sistema deve registrar o status da coleta e identificar falhas de comunicação ou de leitura dos sensores. [SCRUM-586](https://vultureapi.atlassian.net/browse/SCRUM-586)
- CA7 — O Administrador deve conseguir acompanhar o funcionamento da coleta e configurar os parâmetros disponibilizados pelo sistema. [SCRUM-589](https://vultureapi.atlassian.net/browse/SCRUM-589)
- CA8 — O funcionamento completo da estação meteorológica deve ser validado, incluindo a comunicação entre ESP32, sensores e sistema. [SCRUM-591](https://vultureapi.atlassian.net/browse/SCRUM-591)

## US06 — Monitoramento na versão integrada

- O monitoramento permite verificar separadamente a disponibilidade e o tempo de resposta da aplicação e o horário da última medição da estação.
- A equipe registra evidências do envio normal, da interrupção e da retomada, com indicação de onde consultar o monitoramento. [SCRUM-592](https://vultureapi.atlassian.net/browse/SCRUM-592)
