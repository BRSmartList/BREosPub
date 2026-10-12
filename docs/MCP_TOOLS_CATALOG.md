# BREoS Canonical MCP Tools Catalog

> **Protocolo:** Model Context Protocol (MCP)  
> **Runtime:** Go 1.22 (`github.com/BRSmartList/BREoS/runtime`)  
> **Paridade de Descoberta:** Garantida por construção via `GATE-03` / `TestDiscovery_Parity`  
> **Ponto Único de Despacho:** `COR-DIS-001` (`dispatchTool`)

---

## 1. Visão Geral das 27 Ferramentas Canônicas

O servidor MCP do BREoS expõe 27 ferramentas canônicas organizadas em 6 domínios operacionais:

```text
┌─────────────────────────────────────────────────────────────┐
│                   BREoS MCP SERVER (Go 1.22)                │
└──────────────────────────────┬──────────────────────────────┘
                               │
       ┌───────────────────────┼───────────────────────┐
       │                       │                       │
       ▼                       ▼                       ▼
┌──────────────┐        ┌──────────────┐        ┌──────────────┐
│  Discovery   │        │   Planning   │        │  Execution   │
│  & Analysis  │        │  & Guidance  │        │  & Lifecycle │
└──────────────┘        └──────────────┘        └──────────────┘
       │                       │                       │
       ▼                       ▼                       ▼
┌──────────────┐        ┌──────────────┐        ┌──────────────┐
│  Governance  │        │  Adaptive    │        │  Platform    │
│  & RFC Gates │        │  & Learning  │        │  & Workspace │
└──────────────┘        └──────────────┘        └──────────────┘
```

---

## 2. Catálogo Detalhado por Domínio

### 2.1 Descoberta & Análise de Arquitetura (Discovery & Analysis)

| Ferramenta | Descrição Canônica | Entrada Chave | Saída Principal |
|:---|:---|:---|:---|
| `breos_discover` | Executa o pipeline de descoberta tecnológica no repositório. Detecta linguagens, frameworks, padrões arquiteturais e constrói o Digital Twin. | `path` (opcional) | Grafo do Digital Twin em formato estruturado. |
| `breos_analyze` | Análise profunda de aspectos específicos: arquitetura, dependências, riscos, débitos técnicos e documentação. | `aspect`, `target` | Relatório de insights e árvore de riscos. |
| `breos_health` | Exibe indicadores de saúde e conformidade da base de código com base no Digital Twin. | `detailed` (bool) | Health score e débitos detectados. |
| `breos_explain` | Explica adaptativamente um padrão detectado, decisão arquitetural ou módulo do sistema. | `topic`, `target` | Explicação contextualizada para o nível do usuário. |

---

### 2.2 Planejamento & Roteamento de Intenção (Planning & Guidance)

| Ferramenta | Descrição Canônica | Entrada Chave | Saída Principal |
|:---|:---|:---|:---|
| `breos_guide` | Roteador de intenção para comandos (*Goal First, Commands Second*). Converte objetivos em linguagem natural nas ferramentas ideais. | `goal` (string) | Plano de ação e recomendações de ferramentas. |
| `breos_plan` | Motor de planejamento que gera um Execution Plan (EPS-compliant) a partir de um objetivo, considerando restrições de contexto. | `goal`, `constraints` | Grafo de execução determinístico (EPS). |
| `breos_next` | Sugere as próximas tarefas prioritárias com base nas lacunas do Digital Twin (testes, docs, refactoring). | `focus` (opcional) | Lista priorizada de ações recomendadas. |
| `breos_roadmap` | Gera roadmap priorizado de evolução tecnológica com horizontes temporais. | `horizon`, `focus` | Visualização de marcos e evolução. |

---

### 2.3 Execução & Ciclo de Vida de Engenharia (Execution & Lifecycle)

| Ferramenta | Descrição Canônica | Entrada Chave | Saída Principal |
|:---|:---|:---|:---|
| `breos_execute` | Executa um plano através do ciclo completo: Loading $\to$ Execution $\to$ Validation $\to$ Documentation $\to$ Metrics $\to$ Audit $\to$ Feedback. | `plan_id` / `plan` | Log de execução e auditoria de cada fase. |
| `breos_bootstrap` | Executa ciclo bootstrap recursivo: varre ADRs, ingere estratégias, detecta gaps e gera RFCs automaticamente. | `mode` | Relatório do ciclo e RFCs geradas. |
| `breos_publish` | Publica o conhecimento técnico derivado do Digital Twin na documentação oficial e contexto para IAs. | `target`, `format` | Documentos sincronizados e catalogados. |
| `breos_intelligence`| Analisa telemetria de execuções anteriores, calcula KPIs e gera insights de melhoria contínua. | `period` | Relatório analítico de eficiência. |

---

### 2.4 Governança & Portões de Decisão Humana (Governance & RFC Gates)

| Ferramenta | Descrição Canônica | Entrada Chave | Saída Principal |
|:---|:---|:---|:---|
| `breos_propose` | Cria uma nova RFC (Request for Comments) para uma mudança arquitetural ou técnica. | `title`, `rationale` | RFC formal versionada em disco. |
| `breos_approval_list` | Lista RFCs ou ações de Nível 2 que aguardam aprovação e decisão humana obrigatória. | - | Lista de approvals pendentes com IDs. |
| `breos_approve` | Registra a aprovação ou rejeição humana de uma ação Level 2 (`approved` ou `rejected`). | `approval_id`, `status` | Token de autorização em `.breos/approvals/`. |
| `breos_generate_spec`| Gera uma Especificação Técnica formal a partir de uma ADR aprovada. | `adr_id` | Especificação técnica com critérios de aceite. |
| `breos_implement` | Decompõe os critérios de aceite de uma Especificação em tarefas ordenadas de implementação. | `spec_id` | Estrutura de tarefas em `tasks/<spec>/`. |
| `breos_validate` | Valida uma implementação contra sua Especificação, executando testes e verificando conformidade. | `spec_id` | Relatório de certificação e conformidade. |
| `breos_evolve` | Analisa e orquestra a evolução contínua da plataforma pós-certificação (analyze, approve, reject, backlog). | `action`, `target` | Registro no backlog de evolução contínua. |

---

### 2.5 Aprendizado Adaptativo (Adaptive & Learning)

| Ferramenta | Descrição Canônica | Entrada Chave | Saída Principal |
|:---|:---|:---|:---|
| `breos_adaptive` | Execução adaptativa de missões que se ajustam ao perfil do desenvolvedor e ao progresso acumulado. | `action` (start, next...) | Passo adaptativo da jornada. |
| `breos_learn` | Modo de aprendizado interativo para explorar a arquitetura e padrões técnicos sem atrito. | `topic` | Lição contextualizada e interativa. |

---

### 2.6 Plataforma, Workspace & Suporte (Platform & Workspace)

| Ferramenta | Descrição Canônica | Entrada Chave | Saída Principal |
|:---|:---|:---|:---|
| `breos_init` | Inicializador passo a passo de projetos com templates de engenharia em português. | `project_name` | Estrutura inicial do projeto. |
| `breos_workspace` | Detecta o contexto de execução atual: plataforma, projeto consumidor ou workspace externo. | - | Metadados do kernel e perfis ativos. |
| `breos_status` | Status do runtime: versão de release, componentes ativos, uptime e telemetria de sessão. | - | Status consolidado do runtime. |
| `breos_list` | Lista os componentes registrados na plataforma por tipo (`command`, `profile`, `capability`). | `type` (opcional) | Catálogo de componentes disponíveis. |
| `breos_welcome` | Experiência de primeiro uso (*First Run Experience*), detecta estado inicial e apresenta guia. | - | Banner e direcionamentos iniciais. |
| `breos_help` | Central de ajuda sobre comandos, terminologias e conceitos do BREoS. | `query` (opcional) | Ajuda e exemplos de uso. |

---

## 3. Garantias de Segurança & Governança no MCP

Toda e qualquer invocação no servidor MCP do BREoS segue três leis universais:

1. **Paridade Absoluta (`GATE-03`):** Se uma ferramenta está no `tools/list`, ela possui implementação ativa e coberta por testes unitários.
2. **Autorização Centralizada (`GATE-05`):** `dispatchTool` é o único ponto de entrada para execução; nenhuma ferramenta pode contornar os gates de segurança.
3. **Persistência de Decisão Humana:** Ações críticas de Nível 2 necessitam que um token assinado exista em `.breos/approvals/<id>.json` antes de qualquer alteração destrutiva ou de governança.
