# Regras de Gerenciamento de Estações Meteorológicas

## SCRUM-266

### Objetivo

Documentar o contrato e as regras iniciais para o gerenciamento de estações meteorológicas.

## Dados da estação

Uma estação meteorológica deverá possuir inicialmente:

- Código
- Nome
- Localização
- Status
- Data de criação
- Data de atualização

O código da estação deverá ser único no sistema.

## Regras de cadastro

- Código, nome e localização são obrigatórios.
- Não será permitido cadastrar duas estações com o mesmo código.
- Os campos obrigatórios devem ser validados antes da persistência.
- A estação deverá possuir um estado que permita identificar se está ativa ou inativa.

## Regras de atualização

- Uma estação cadastrada poderá ter seus dados atualizados.
- O código deverá permanecer único.
- A atualização não deverá alterar a identificação da estação de forma inconsistente.

## Contrato inicial

Exemplo inicial de representação de uma estação:

    {
      "codigo": "EST-001",
      "nome": "Estacao Fazenda 01",
      "localizacao": "Area 01",
      "ativa": true
    }

## Decisão pendente

### Exclusão física ou desativação

Ainda não foi definido se a remoção de uma estação deverá ocorrer por:

1. exclusão física do registro no banco de dados; ou
2. desativação lógica da estação, preservando seu histórico.

Essa decisão deverá ser acordada antes da implementação do endpoint de remoção.

Enquanto a decisão não estiver definida, a implementação não deverá assumir exclusão física definitiva.

## Dependências

Este documento servirá de base para:

- modelagem do banco de dados;
- implementação do backend;
- interface de gerenciamento de estações;
- associação de sensores;
- testes da funcionalidade.
