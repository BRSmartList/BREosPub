# BREoS Level 5 Scorecard (Optimized)

> **Padrão de Maturidade:** CMMI Level 5 (Optimized Architecture)  
> **Filosofia de Honestidade Empírica:** *Nenhuma métrica existe sem fórmula matemática, limiar (threshold), owner instrumentado, ação corretiva e evidência reproduzível no CI.*

---

## 1. Tabela Consolidada de Métricas

| ID | Métrica | Definição / Fórmula | Target Mandatório | Medição Atual | Evidência / Instrumentação |
|:---|:---|:---|:---:|:---:|:---|
| **M1** | Time-to-Resolution | Duração média fim-a-fim de uma missão executada | $\downarrow \ge 10\%$ vs baseline | *Instrumentado* | `TelemetryEngine.RecordMethodCall` |
| **M2** | Context Cost | Média de tokens de entrada injetados por execução | $\le 5.000$ tokens | **2.597 tokens/exec** | `ContextLoader.ExportMetrics` via `L5-OPTIMIZE-01` |
| **M3** | Context Waste | Proporção de tokens carregados descartados | $\le 30\%$ | **0.00%** | Hard gate atingido sem desperdício de tokens |
| **M4** | Execution Failure Rate | Taxa de falhas de execução no runtime | $\downarrow \ge 50\%$ vs baseline | *Instrumentado* | `TelemetryEngine` error stream |
| **M10** | ADR Technical Debt | Número de decisões arquiteturais pendentes | $\le 10$ ADRs | **9 ADRs** | `docs/governance/adr/` registry |
| **M11** | Knowledge Retrieval | Qualidade de ranking na busca semântica (NDCG@5) | $\ge 0.80$ | **1.000 (Perfeito)** | Avaliação offline com 12/12 queries canônicas |

---

## 2. Quality Gates Mandatórios do CI

O pipeline de Continuous Integration do BREoS impede regressões arquiteturais por meio de cinco portões automáticos:

1. **`GATE-01` — Sintaxe & Integridade Estrutural:** Validação estática de contratos e esquemas de configuração.
2. **`GATE-02` — Contratos de Dependência Unidirecional:** Proíbe que a Experience Layer dependa de implementações específicas ou que o Core dependa de adapters externos.
3. **`GATE-03` — Paridade MCP por Construção:** Testes unitários (`TestDiscovery_Parity`) garantem paridade de $100\%$ entre o que o MCP anuncia em `tools/list` e o que o despachante aceita em `tools/call`.
4. **`GATE-04` — Orçamento Estrito de Contexto:** Bloqueia a execução se a taxa de *Context Waste* exceder o teto estrito de $30\%$.
5. **`GATE-05` — Interceptação de Autorização & Decisões Level 2:** Obriga que toda mutação crítica tenha sido explicitamente aprovada por um humano via token persistido em `.breos/approvals/<id>.json`.
