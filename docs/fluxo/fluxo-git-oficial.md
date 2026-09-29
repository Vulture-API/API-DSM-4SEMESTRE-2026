# Fluxo Git Oficial

**Equipe Vulture - Projeto AgroClima 360**  
**Projeto:** AgroClima 360 - API DSM 4º Semestre 2026  
**Equipe:** Vulture  
**Repositório oficial:** `Vulture-API/API-DSM-4SEMESTRE-2026`  
**Branches permanentes:** `dev` e `main`  
**Base do processo:** Fluxo Jira + GitHub validado pela equipe e estratégia oficial definida para as Sprints.

---

## 1. Objetivo

Definir o fluxo Git oficial utilizado pela Equipe Vulture durante o desenvolvimento do AgroClima 360, padronizando criação de branches, commits, Pull Requests, Code Review, integração na branch `dev` e promoção de incrementos estáveis para `main`.

O objetivo é preservar rastreabilidade, reduzir conflitos e impedir alterações diretas nas branches protegidas.

---

## 2. Princípios do fluxo

- Todo trabalho de desenvolvimento deve ocorrer em branch própria da atividade.
- As branches de trabalho devem partir da `dev` durante as Sprints.
- Nenhum Developer deve desenvolver diretamente em `dev` ou `main`.
- A integração de uma atividade deve ocorrer por Pull Request para `dev`.
- A `main` representa a versão estável e recebe apenas incrementos previamente integrados e validados em `dev`.
- Toda Pull Request deve passar por Code Review de pelo menos um Developer diferente do autor.
- Quando a atividade possuir Work Item no Jira, a chave `SCRUM-XX` deve ser preservada na branch, nos commits e na Pull Request para manter a rastreabilidade.

---

## 3. Papel das branches

| Branch | Tipo | Função | Recebe merge de |
|---|---|---|---|
| `main` | Permanente | Versão estável do projeto. Deve conter somente incrementos integrados e validados. | `dev` |
| `dev` | Permanente | Branch de integração das funcionalidades em andamento durante a Sprint. | `feature/*`, `docs/*`, `fix/*` e demais branches de trabalho aprovadas |
| `feature/*` | Temporária | Desenvolvimento de funcionalidade. | Não recebe integração direta; nasce da `dev`. |
| `docs/*` | Temporária | Alterações e criação de documentação versionada. | Não recebe integração direta; nasce da `dev`. |
| `fix/*` | Temporária | Correções de defeitos ou ajustes. | Não recebe integração direta; nasce da `dev`. |

---

## 4. Fluxo oficial durante as Sprints

```text
Atividade
   ↓
Branch a partir da dev
   ↓
Desenvolvimento
   ↓
Commit
   ↓
Push
   ↓
PR para dev
   ↓
Code Review
   ↓
Aprovação
   ↓
Merge na dev
```

Após a integração na `dev`, a funcionalidade passa a compor o ambiente integrado do projeto e pode ser submetida às validações e testes pertinentes.

---

## 5. Criação da branch de trabalho

Quando existir uma Task/Work Item no Jira, a branch deverá preferencialmente ser criada a partir do próprio Jira, vinculando-a ao item correspondente.

A branch de origem deverá ser `dev`.

### Padrões

```text
feature/SCRUM-XX-descricao
docs/SCRUM-XX-descricao
fix/SCRUM-XX-descricao
```

O nome deve ser curto, descritivo e manter a chave do Jira quando aplicável.

> O exemplo da Sprint 0 utilizou `main` apenas para validar a integração. Esse não é o fluxo oficial das Sprints.

---

## 6. Trabalho local e atualização da branch

- Atualizar o repositório local antes de iniciar o trabalho.
- Fazer checkout da branch correta da atividade.
- Confirmar que o trabalho não está sendo realizado diretamente em `dev` ou `main`.
- Manter a branch de trabalho sincronizada quando necessário para reduzir conflitos.
- Utilizar GitHub Desktop, terminal ou IDE conforme preferência do Developer, sem alterar as regras de integração.

---

## 7. Commits e rastreabilidade

Os commits devem ser claros e representar alterações coerentes.

Quando houver Work Item no Jira, a mensagem deve conter a chave `SCRUM-XX` para permitir associação automática pelo painel **Development**.

| Tipo | Exemplo |
|---|---|
| Funcionalidade | `feat(SCRUM-123): implementa cadastro de estação` |
| Correção | `fix(SCRUM-123): corrige validação do código da estação` |
| Documentação | `docs(SCRUM-123): documenta contrato de estações` |
| Teste | `test(SCRUM-123): adiciona testes do cadastro de estação` |
| Manutenção | `chore(SCRUM-123): ajusta configuração do projeto` |

> Os prefixos acima formalizam um padrão recomendado para a equipe. O requisito essencial já validado no fluxo é que a mensagem seja clara e contenha a chave do Jira quando houver item associado.

---

## 8. Pull Request da atividade para `dev`

Ao concluir a implementação da atividade, a Pull Request deverá utilizar:

- **base:** `dev`
- **compare:** branch da atividade (`feature/*`, `docs/*` ou `fix/*`)
- título contendo `SCRUM-XX` quando a atividade estiver vinculada ao Jira
- descrição com resumo da alteração, testes realizados e observações relevantes

---

## 9. Code Review e aprovação

- A Pull Request deve ser revisada por pelo menos um Developer diferente do autor.
- Comentários e solicitações de ajuste devem ser resolvidos antes do merge.
- Os testes pertinentes devem ser executados antes da aprovação final.
- Quando os checks automatizados do GitHub Actions estiverem configurados, o pipeline deverá estar aprovado antes do merge.
- A aprovação não elimina a responsabilidade coletiva pela qualidade do incremento.

---

## 10. Merge na `dev`

Após Code Review, aprovação e validações pertinentes, a branch da atividade poderá ser integrada à `dev`.

A `dev` funciona como ponto de integração das entregas da Sprint.

A branch temporária poderá ser removida após a confirmação do merge, desde que não exista trabalho pendente nela.

---

## 11. Promoção de `dev` para `main`

```text
dev
 ↓
Integração e testes
 ↓
Pull Request
 ↓
Revisão / validação
 ↓
main
```

A `main` não deve receber diretamente as Tasks individuais.

Ela recebe incrementos que já passaram pela integração em `dev`.

A promoção deverá ocorrer por Pull Request, respeitando as proteções configuradas para a `main`.

---

## 12. Proteção das branches permanentes

As branches `dev` e `main` estão protegidas por rulesets.

O processo documentado pela equipe utiliza, no mínimo:

- Pull Request obrigatório para integração;
- mínimo de 1 aprovação;
- resolução das conversas antes do merge;
- bloqueio de force push;
- proteção contra exclusão das branches permanentes.

Checks obrigatórios de CI/CD poderão ser adicionados ao ruleset quando o pipeline automatizado estiver configurado.

---

## 13. Relação com Jira e rastreabilidade

A integração Jira + GitHub permite acompanhar os eventos de desenvolvimento associados ao Work Item.

O fluxo foi validado pela equipe com branch, commit e Pull Request vinculados à chave do Jira.

| Elemento | Exemplo | Rastreabilidade |
|---|---|---|
| Work Item | `SCRUM-266` | Origem da atividade |
| Branch | `docs/SCRUM-266-regras-estacoes-meteorologicas` | Associação da implementação |
| Commit | `docs(SCRUM-266): documenta regras e contrato de estações` | Registro da alteração |
| Pull Request | `SCRUM-266 \| Documenta regras e contrato de estações` | Review, aprovação e merge |

---

## 14. Situações que devem ser evitadas

- Commit ou desenvolvimento direto em `dev` ou `main`.
- Criar branch de Sprint a partir da `main`.
- Fazer merge local direto da branch de trabalho para `dev`, ignorando Pull Request.
- Abrir PR de uma Task individual diretamente para `main`.
- Aprovar e integrar PR sem os testes pertinentes.
- Remover a chave `SCRUM-XX` de branch/commit/PR quando a atividade estiver vinculada ao Jira.
- Utilizar o repositório antigo em vez do repositório oficial da organização Vulture-API.

---

## 15. Fluxo resumido

```text
Jira / Atividade
      ↓
     dev
      ↓
feature | docs | fix
      ↓
Desenvolvimento + commits
      ↓
     Push
      ↓
 PR para dev
      ↓
Code Review + testes
      ↓
   Aprovação
      ↓
 Merge na dev
      ↓
Integração / validação
      ↓
 PR dev → main
      ↓
 main estável
```

---

## 16. Observação sobre a Sprint 0

Os primeiros testes de integração Jira + GitHub foram realizados durante a Sprint 0 utilizando a `main` como origem/destino para fins de validação e documentação do processo.

A partir das Sprints de desenvolvimento do produto, o fluxo oficial adotado pela equipe é:

```text
branch de trabalho → dev → main
```

---

## 17. Revisão do documento

Este fluxo deverá ser revisado caso a equipe altere:

- a estratégia de branches;
- as regras de proteção;
- os requisitos de Code Review;
- os checks obrigatórios do pipeline CI/CD.

Mudanças relevantes devem ser registradas no documento de **Mudanças e Decisões** da equipe.
