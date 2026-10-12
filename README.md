<div align="center">

# 🌐 BREoS — Engineering Intelligence Platform
### Public Architecture Showcase & Systems Engineering Portfolio

[![Go Version](https://img.shields.io/badge/Go-1.22-00ADD8?style=flat&logo=go)](https://go.dev/)
[![Protocol](https://img.shields.io/badge/Protocol-Model_Context_Protocol_(MCP)-8A2BE2?style=flat)](https://modelcontextprotocol.io/)
[![Architecture Level](https://img.shields.io/badge/Architecture-Level_5_(Optimized)-4BC51D?style=flat)](#scorecard-de-engenharia-nível-5)
[![Context Waste](https://img.shields.io/badge/Context_Waste-0.00%25_(M3)-success?style=flat)](#context-budgeting--zero-waste)
[![Knowledge Retrieval](https://img.shields.io/badge/Retrieval_NDCG@5-1.000_(M11)-success?style=flat)](#digital-twin--busca-semântica)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

<br/>

> **Build. Understand. Navigate. Evolve.**  
> *"Reduzindo a distância entre a vontade de criar software e a capacidade de realizá-lo."*

<br/>

[💼 Ler Case Study Completo (Staff Level)](./PORTFOLIO_CASE_STUDY.md) • [🌐 Web Showcase (GitHub Pages)](./docs/index.html) • [🛠️ Catálogo das 27 MCP Tools](./docs/MCP_TOOLS_CATALOG.md) • [📐 Deep Dive de Arquitetura](./docs/ARCHITECTURE.md)

</div>

---

## 📌 Sobre Este Repositório Público

Este repositório (`BREosPub`) é o **showcase público oficial de arquitetura e portfólio de engenharia** do **BREoS**. Ele foi estruturado para demonstrar as decisões de design de sistemas, os trade-offs arquiteturais, a implementação canônica em Go do servidor **Model Context Protocol (MCP)** e os resultados empíricos alcançados pelo projeto.

> 🔒 **Nota de Transparência:** O núcleo de execução proprietário e dados internos corporativos operam em ambiente privado. Todas as especificações, métricas de CI, designs de protocolo e modelos conceituais estão abertos e documentados aqui.

---

## 💡 O que é o BREoS?

O **BREoS** é uma **Engineering Intelligence Platform** — uma meta-arquitetura viva que integra runtime determinístico, conhecimento semântico e cognição artificial para viabilizar a colaboração entre desenvolvedores humanos e agentes de IA autônomos.

Diferente de assistentes convencionais que apenas geram blocos de código sem memória:
1. **Preserva contexto transversal** entre sessões sem poluir a janela de contexto de LLMs.
2. **Constrói um Digital Twin da base de código** para navegação semântica em tempo real.
3. **Controla o orçamento de contexto (*Context Budgeting*)**, eliminando o desperdício de tokens ($M3 = 0.00\%$).
4. **Impõe governança constitucional** com portões de aprovação humana de Nível 2 para ações de alto impacto.

---

## 🏛️ Topologia Arquitetural

A plataforma estrutura-se sob uma cadeia de composição rigorosa:

$$\text{Components} \to \text{Capabilities} \to \text{Domains} \to \text{Platform} \to \text{Experiences} \to \text{Intelligence}$$

```text
                           BREoS PLATFORM
                                 │
                     Experience Layer (XE)
               (Cross-Cutting Meta Architecture)
                                 │
    ┌────────────────────────────┼────────────────────────────┐
    │                            │                            │
    ▼                            ▼                            ▼
┌──────────────────────┐ ┌──────────────────────┐ ┌──────────────────────┐
│ COGNITIVE DOMAIN     │ │ KNOWLEDGE DOMAIN     │ │ RUNTIME DOMAIN       │
│                      │ │                      │ │                      │
│ • Brain (Reasoning)  │ │ • Knowledge Platf.   │ │ • Go 1.22 Runtime    │
│ • Assistant          │ │ • Knowledge Nav.     │ │ • Canonical MCP      │
│ • Goal Resolver      │ │ • Digital Twin       │ │ • Lifecycle Engine   │
│ • Intent Routing     │ │ • Mission Catalog    │ │ • Governance Store   │
└──────────────────────┘ └──────────────────────┘ └──────────────────────┘
```

### O Papel da Experience Layer (ADR-0114)
Classificada como **Cross-Cutting Meta Architecture**:
- **O que faz:** Orquestra jornadas entre domínios, preserva contexto e adapta a experiência ao perfil do desenvolvedor (Beginner, Intermediate, Staff).
- **O que NÃO faz:** Não implementa capacidades funcionais e não executa lógica de negócio, garantindo zero acoplamento indesejado com frameworks ou LLMs específicos.

---

## ⚡ Runtime em Go & 27 Canonical MCP Tools

A camada de runtime do BREoS foi desenvolvida em **Go 1.22**, expondo um servidor canônico que implementa o protocolo **Model Context Protocol (MCP)** via JSON-RPC 2.0.

### Destaques do Servidor MCP:
- **Ponto Único de Despacho (`COR-DIS-001`):** Todas as 27 ferramentas passam pelo interceptor central `dispatchTool` em Go.
- **Paridade por Construção (`GATE-03`):** Suítes de teste unitário verificam em tempo de CI se todas as ferramentas anunciadas em `tools/list` possuem handlers ativos e documentados em `tools/call`.
- **Human-in-the-Loop Obrigatório:** Ferramentas destrutivas ou de governança requerem aprovação humana explícita persistida em `.breos/approvals/<id>.json`.

### Resumo das 27 Ferramentas:
| Categoria | Quantidade | Exemplos Principais |
|:---|:---:|:---|
| **Discovery & Health** | 5 | `breos_discover`, `breos_analyze`, `breos_health`, `breos_explain` |
| **Planning & Intent** | 6 | `breos_guide`, `breos_plan` (EPS Engine), `breos_next`, `breos_roadmap` |
| **Execution & Lifecycle** | 6 | `breos_execute` (7-stage cycle), `breos_bootstrap`, `breos_publish` |
| **Governance & RFCs** | 6 | `breos_propose`, `breos_approval_list`, `breos_approve`, `breos_validate` |
| **Adaptive & Learning** | 2 | `breos_adaptive` (missões adaptativas), `breos_learn` |
| **Platform & Workspace** | 2 | `breos_workspace`, `breos_init`, `breos_status`, `breos_welcome` |

👉 *Consulte o catálogo completo com parâmetros e schemas no [MCP Tools Catalog](./docs/MCP_TOOLS_CATALOG.md).*

---

## 📊 Scorecard de Engenharia (Nível 5 Optimized)

O BREoS segue uma diretriz inegociável de **honestidade empírica**: *nenhuma métrica existe sem fórmula, limiar (threshold), owner instrumentado, ação esperada e evidência verificável*.

```text
┌─────────────────────────────────────────────────────────────────────────────┐
│                       EVIDÊNCIAS DE ENGENHARIA MEDIDAS                      │
├─────────────────────────┬───────────────────┬───────────────┬───────────────┤
│ Métrica                 │ Target Mandatório │ Valor Medido  │ Status        │
├─────────────────────────┼───────────────────┼───────────────┼───────────────┤
│ M2 — Context Cost       │ ≤ 5,000 tokens    │ 2,597 tokens  │ ✅ Aprovado   │
│ M3 — Context Waste      │ ≤ 30.00%          │ 0.00%         │ ✅ Hard Gate  │
│ M10 — ADR Debt          │ ≤ 10 pendentes    │ 9 ADRs        │ ✅ No Limite  │
│ M11 — Retrieval NDCG@5  │ ≥ 0.80            │ 1.000         │ ✅ Perfeito   │
│ GATE-03 — Tool Parity   │ 100% Paridade     │ 27 / 27 tools │ ✅ Compilação │
└─────────────────────────┴───────────────────┴───────────────┴───────────────┘
```

### Context Budgeting & Zero Waste
Ao contrário de agentes que sobrecarregam prompts com dezenas de milhares de tokens irrelevantes (*prompt dumping*), o BREoS introduziu uma injeção cirúrgica baseada em **utilidade marginal**. O resultado é **0.00% de Context Waste** e um custo estável de apenas **2.597 tokens por missão**.

---

## 🔒 Ciclo de Governança Constitucional

O BREoS integra um ciclo formal de evolução de software diretamente acoplado ao servidor MCP:

```text
   [Intenção Arquitetural]
              │
              ▼
        breos_propose       ──► Criação de RFC formal
              │
              ▼
        Revisão Humana      ──► RFC classificada como Level 2 (Crítica)
              │
              ▼
        breos_approve       ──► Decisão humana persistida em disco
              │
              ▼
      breos_generate_spec   ──► Geração de Especificação Técnica com critérios
              │
              ▼
        breos_implement     ──► Orquestração de tarefas de implementação
              │
              ▼
        breos_validate      ──► Execução de testes de conformidade e certificação
```

---

## 📂 Estrutura do Showcase

```text
BREosPub/
├── docs/
│   ├── index.html                # Showcase Web Interativo (GitHub Pages)
│   ├── ARCHITECTURE.md           # Deep Dive de Topologia e Contratos
│   ├── MCP_TOOLS_CATALOG.md      # Catálogo com as 27 Ferramentas MCP
│   ├── LEVEL_5_SCORECARD.md      # Scorecard de Métricas e Instrumentação
│   └── NORTH_STAR.md             # Filosofia e Princípios da Plataforma
├── PORTFOLIO_CASE_STUDY.md       # Case Study Completo para Staff/Principal Engineers
├── README.md                     # Entrada Principal do Portfólio
└── LICENSE                       # Licença MIT
```

---

## 🚀 Como Explorar

- **Leitura Executiva / Staff Engineer:** Leia o [PORTFOLIO_CASE_STUDY.md](./PORTFOLIO_CASE_STUDY.md) para entender os trade-offs, decisões de ADRs e arquitetura de concorrência e memória.
- **Visualização Interativa:** Abra [`docs/index.html`](./docs/index.html) no navegador para interagir com o explorador visual de ferramentas MCP e simulador de Context Budget.
- **Referência do Protocolo:** Consulte [`docs/MCP_TOOLS_CATALOG.md`](./docs/MCP_TOOLS_CATALOG.md) para detalhes técnicos de cada ferramenta despachada pelo runtime.

---

## 📜 Licença

Este projeto está licenciado sob os termos da licença [MIT](./LICENSE).  
Copyright (c) 2026 BRSmartList.