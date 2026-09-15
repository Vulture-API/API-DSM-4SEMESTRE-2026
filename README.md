  # 🌦️ AgroClima 360 — API DSM 4º Semestre 2026

  <h2 align="center">Vulture API</h2>

  <p align="center">
  Solução IoT para monitoramento meteorológico desenvolvida pela Equipe Vulture.
  </p>

  > **Status do Projeto:** Sprint 1 em andamento  
  > **Jira:** https://vultureapi.atlassian.net/jira/software/projects/SCRUM/boards/1/backlog  
  > **Confluence:** https://vultureapi.atlassian.net/wiki/x/AYA7

  ---

  # 🎯 Descrição do Desafio

  ## 🏢 Cliente / Parceiro

  A **Tecsus** é a empresa cliente do projeto AgroClima 360.

  O projeto está sendo desenvolvido com foco na expansão do portfólio de soluções IoT da empresa, por meio da criação de uma solução de monitoramento meteorológico capaz de coletar, processar, armazenar e disponibilizar dados ambientais.

  ## 😢 Dor do Cliente

  A Tecsus busca expandir seu portfólio de soluções IoT para o segmento de monitoramento ambiental.

  A empresa necessita validar uma solução baseada em estação meteorológica que possua uma estrutura básica de software capaz de:

  - receber dados provenientes de uma estação meteorológica;
  - processar e tratar essas informações;
  - armazenar os dados de forma persistente;
  - disponibilizar as informações por meio de uma aplicação web;
  - permitir evolução futura para múltiplas estações, sensores e cenários de monitoramento.

  A dor principal é **validar uma nova solução tecnológica que possa futuramente integrar o portfólio da empresa**.

  ## 🏅 Desafio

  Construir uma solução de monitoramento meteorológico capaz de demonstrar, de forma simples e funcional, a proposta tecnológica da Tecsus.

  Para a primeira entrega, a equipe prioriza:

  - arquitetura definida;
  - banco de dados operacional;
  - CRUD funcional;
  - front-end integrado.

  ## 💡 Solução

  O **AgroClima 360** propõe uma solução modular capaz de receber, processar, armazenar e disponibilizar dados ambientais por meio de uma aplicação web.

  A proposta contempla:

  - estações meteorológicas e sensores;
  - comunicação entre componentes;
  - armazenamento temporário;
  - tratamento e validação dos dados;
  - persistência definitiva;
  - APIs;
  - front-end;
  - testes, monitoramento e integração contínua.

  Enquanto o hardware físico não estiver disponível, poderão ser utilizados **dados simulados**.

  ---

  # 📋 Backlog do Produto

  O Product Backlog é mantido e refinado continuamente no Jira e no Confluence.

  > **Jira e Confluence são as fontes oficiais e mais atualizadas do backlog.**

  | ID | Prioridade | User Story | Planning Poker | Sprint |
  | :--: | :--: | --- | :--: | :--: |
  | US1 | Alta | Cadastrar e gerenciar estações meteorológicas. | 8 | 1 |
  | US2 | Alta | Cadastrar sensores e parâmetros. | 8 | 1 |
  | US3 | Alta | Cadastrar e gerenciar usuários. | 8 | 1 |
  | US4 | Alta | Visualizar o status das estações. | 5 | 1 |
  | US5 | Alta | Cadastrar e configurar alertas meteorológicos. | 5 | 1 |
  | US6 | Alta | Garantir disponibilidade e escalabilidade do sistema. | 13 | 1 |
  | US7 | Alta | Visualizar dados meteorológicos atuais. | 8 | 2 |
  | US8 | Alta | Visualizar histórico dos dados. | 8 | 2 |
  | US9 | Média | Identificar estações/sensores com falhas ou dados inconsistentes. | 13 | 2 |
  | US10 | Média | Gerenciar níveis de acesso dos usuários. | 8 | 2 |
  | US11 | Média | Visualizar estatísticas e previsões. | 13 | 2 |
  | US12 | Média | Receber dados tratados das estações. | 8 | 2 |
  | US13 | Baixa | Gerar relatórios meteorológicos. | 5 | 3 |
  | US14 | Baixa | Visualizar dados meteorológicos como Cliente. | 8 | 3 |
  | US15 | Baixa | Possuir pipeline de integração contínua. | 13 | 3 |
  | US16 | Baixa | Configurar datalogger e coleta dos dados. | 13 | 3 |

  **Totais:** Sprint 1 = 47 pontos • Sprint 2 = 58 pontos • Sprint 3 = 39 pontos.

  ---

  # 🏗️ Arquitetura do Projeto

  ![alt text](<Arquitetura Projeto.png>)

  # 📈 Cronograma de Evolução

  ```mermaid
  flowchart LR
      S1["Sprint 1<br/>07/09/2026 a 27/09/2026<br/>Arquitetura + Banco + CRUD + Front"]
      S2["Sprint 2<br/>Período a definir<br/>Evolução funcional"]
      S3["Sprint 3<br/>Período a definir<br/>Integração final, CI e hardware"]
      S1 --> S2 --> S3
  ```

  ---

  # 🗓️ Sprints

  | Sprint | Período | Documentação da Sprint | Vídeo do Incremento |
  | :---: | --- | --- | --- |
  | Sprint 1 | 07/09/2026 a 27/09/2026 | [Documentação](docs/) | A adicionar |
  | Sprint 2 | A definir | A adicionar | A adicionar |
  | Sprint 3 | A definir | A adicionar | A adicionar |

  ---

  ## 💻 Tecnologias <a id="tecnologias"></a>

<h4 align="center">

  <a href="https://developer.mozilla.org/pt-BR/docs/Web/HTML">
    <img src="https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white"/>
  </a>

  <a href="https://developer.mozilla.org/pt-BR/docs/Web/CSS">
    <img src="https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white"/>
  </a>

  <a href="https://developer.mozilla.org/pt-BR/docs/Web/JavaScript">
    <img src="https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black"/>
  </a>

  <a href="https://nodejs.org/">
    <img src="https://img.shields.io/badge/Node.js-339933?style=for-the-badge&logo=nodedotjs&logoColor=white"/>
  </a>

  <a href="https://react.dev/">
    <img src="https://img.shields.io/badge/React-087EA4?style=for-the-badge&logo=react&logoColor=white"/>
  </a>

  <a href="https://nextjs.org/">
    <img src="https://img.shields.io/badge/Next.js-000000?style=for-the-badge&logo=nextdotjs&logoColor=white"/>
  </a>

  <a href="https://www.typescriptlang.org/">
    <img src="https://img.shields.io/badge/TypeScript-3178C6?style=for-the-badge&logo=typescript&logoColor=white"/>
  </a>

  <a href="https://www.python.org/">
    <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  </a>

  <a href="https://isocpp.org/">
    <img src="https://img.shields.io/badge/C++-00599C?style=for-the-badge&logo=cplusplus&logoColor=white"/>
  </a>

  <a href="https://www.c-language.org/">
    <img src="https://img.shields.io/badge/C-A8B9CC?style=for-the-badge&logo=c&logoColor=black"/>
  </a>

  <a href="https://www.arduino.cc/">
    <img src="https://img.shields.io/badge/Arduino-00878F?style=for-the-badge&logo=arduino&logoColor=white"/>
  </a>

  <a href="https://tailwindcss.com/">
    <img src="https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=for-the-badge&logo=tailwindcss&logoColor=white"/>
  </a>

  <a href="https://www.postgresql.org/">
    <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=for-the-badge&logo=postgresql&logoColor=white"/>
  </a>

  <a href="https://mosquitto.org/">
    <img src="https://img.shields.io/badge/Eclipse_Mosquitto-3C5280?style=for-the-badge&logo=eclipsemosquitto&logoColor=white"/>
  </a>

  <a href="https://redis.io/">
    <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white"/>
  </a>

  <a href="https://www.docker.com/">
    <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white"/>
  </a>

</h4>

  ---

  

  # ▶️ Como Executar, Usar e Testar

  > Esta seção será atualizada conforme os serviços executáveis forem disponibilizados.

  ## Pré-requisitos

  - Git
  - Node.js
  - npm
  - variáveis de ambiente necessárias

  ## Clonar o repositório

  ```bash
  git clone https://github.com/Vulture-API/API-DSM-4SEMESTRE-2026.git
  cd API-DSM-4SEMESTRE-2026
  ```

  ## Instalar dependências

  ```bash
  npm install
  ```

  ## Ambiente

  Credenciais, tokens e segredos deverão ser configurados localmente e **não deverão ser versionados**.

  ```text
  .env
  ```

  ## Execução e testes

  Os comandos específicos serão documentados em cada serviço à medida que forem disponibilizados.

  ---

  # 📚 Documentação

  - 📁 [Pasta de documentação](docs/)
  - 🔗 [Confluence](https://vultureapi.atlassian.net/wiki/x/AYA7)

  ## ✅ Checklist de DoR e DoD

  ### Definition of Ready — DoR

  Uma User Story ou Task estará pronta quando:

  - [ ] objetivo estiver claro;
  - [ ] estiver alinhada à Dor do Cliente;
  - [ ] critérios de aceite estiverem definidos;
  - [ ] regras de negócio principais estiverem documentadas;
  - [ ] dependências forem conhecidas;
  - [ ] impedimentos críticos tiverem tratamento;
  - [ ] puder ser estimada;
  - [ ] tiver sido refinada com os Developers;
  - [ ] prioridade e Sprint estiverem definidas;
  - [ ] puder ser decomposta em Tasks executáveis.

  ### Definition of Done — DoD

  Uma User Story ou Task estará concluída quando:

  - [ ] implementação estiver concluída;
  - [ ] critérios de aceite forem atendidos;
  - [ ] código estiver na branch correta;
  - [ ] commits seguirem o padrão;
  - [ ] PR estiver aberta para `dev`;
  - [ ] houver Code Review por outro Developer;
  - [ ] ajustes obrigatórios estiverem resolvidos;
  - [ ] testes pertinentes forem executados;
  - [ ] documentação necessária estiver atualizada;
  - [ ] não houver segredos versionados;
  - [ ] PR estiver aprovada e integrada à `dev`;
  - [ ] rastreabilidade Jira ↔ branch ↔ commit ↔ PR estiver preservada;
  - [ ] item estiver disponível para demonstração;
  - [ ] item estiver **Concluído** no Jira.

  > Os registros de DoR e DoD específicos de cada Sprint deverão ser mantidos na documentação da respectiva Sprint.

  ---

  ## 🌿 Estratégia de Branch

  A Equipe Vulture utiliza uma estratégia com `main` como versão estável e `dev` como branch de integração.

  ```text
  feature/docs/fix/test/chore
            ↓
          dev
            ↓
    integração e testes
            ↓
          main
  ```

  ### Regras

  - `main` representa a versão estável;
  - `dev` é a branch de integração;
  - branches de trabalho devem partir da `dev`;
  - não desenvolver diretamente em `main` ou `dev`;
  - toda integração ocorre por Pull Request;
  - PRs passam por Code Review;
  - sempre que possível, o autor não aprova o próprio PR.

  ### Exemplos

  ```text
  feature/SCRUM-123-cadastro-estacao
  fix/SCRUM-145-validacao-estacao
  docs/SCRUM-266-regras-estacoes
  test/SCRUM-205-testes-usuarios
  chore/configura-pipeline
  ```

  ---

  ## 📝 Padrão de Mensagens dos Commits

  Formato adotado conforme o guia da disciplina:

  ```text
  <tipo> (<id_demanda1>, <id_demanda2>, ..., <id_demandaN>): <descrição da entrega>
  ```

  | Tipo | Uso |
  | --- | --- |
  | `feat` | Nova funcionalidade |
  | `fix` | Correção de bug |
  | `docs` | Documentação |
  | `style` | Formatação sem impacto funcional |
  | `refactor` | Refatoração |
  | `test` | Testes |
  | `chore` | Configuração ou manutenção |

  Exemplos:

  ```text
  feat (SCRUM-101): implementa cadastro de estações
  docs (SCRUM-266): documenta regras de gerenciamento de estações
  fix (SCRUM-145): corrige validação do código da estação
  test (SCRUM-205): adiciona testes do cadastro de usuários
  ```

  ### Boas práticas de Git

  - utilizar `.gitignore`;
  - nunca realizar commit direto na `main`;
  - referenciar a demanda nos commits;
  - realizar commits pequenos e objetivos;
  - descrever a entrega com clareza;
  - utilizar Pull Requests;
  - descrever implementação e testes na PR;
  - aguardar Code Review antes do merge;
  - sempre que possível, não aprovar o próprio PR.

  ---

  ## 📘 Manual do Usuário

  Será produzido conforme as funcionalidades forem concluídas.

  ## 📖 Manual de Instalação

  Será atualizado conforme os serviços e dependências finais forem consolidados.

  ---

# 👥 Equipe <a id="equipe"></a>

| Integrante | Papel | GitHub | LinkedIn |
| :--- | :--- | :---: | :---: |
| **Aline Raquel Camargo de Oliveira** | Scrum Master / Developer | <a href="https://github.com/AlineRaquelC"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/aline-oliveira-60ab6265/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Ana Júlia Rubim** | Product Owner / Developer | <a href="https://github.com/anajrubim"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/ana-j%C3%BAlia-rubim/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Lucas Marins Santos** | Developer — CI/CD | <a href="https://github.com/lucasMarinsSantos"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/lucasmarinssantos/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Enrico de Chiara Germano** | Developer — Deploy / Ambientes | <a href="https://github.com/EnricoGermano"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/enrico-de-chiara-germano-022894204/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Leonardo da Silva Lopes** | Developer — Testes de Integração | <a href="https://github.com/leodaslb"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/leonardo-silva-lopes-aab435283/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Rafael Sette de Araújo** | Developer — Monitoramento / Observabilidade | <a href="https://github.com/Sette0o0"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/rafael-sette-de-araujo-229b88334/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |
| **Vinícius Leite** | Developer — Testes Unitários | <a href="https://github.com/vinislvleite"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/github/github-original.svg" width="30"></a> | <a href="https://www.linkedin.com/in/vin%C3%ADcius-leite-4792b02ba/"><img src="https://cdn.jsdelivr.net/gh/devicons/devicon@latest/icons/linkedin/linkedin-original.svg" width="30"></a> |

  ---

  # 📌 Status do Projeto

  **Fase atual:** Sprint 1 em andamento.

  A equipe está trabalhando na modelagem do banco, contratos de API, estrutura de microsserviços, rastreabilidade, testes e preparação do incremento funcional da primeira Sprint.

  Alterações relevantes de escopo, arquitetura ou processo são registradas no Jira, Confluence e na documentação versionada.
