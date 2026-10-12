# BREoS Architecture Deep Dive

> **Classificação:** Engineering Intelligence Meta-Architecture  
> **Referência Constitucional:** ADR-0003, ADR-0113, ADR-0114, ADR-0857  
> **Status:** Level 5 Optimized Architecture

---

## 1. Topologia da Meta-Arquitetura

O BREoS rompe com o modelo tradicional de monólitos de ferramentas de desenvolvimento através de uma separação estrita de responsabilidades:

```text
                                  BREoS PLATFORM
                                        │
                            Experience Layer (XE)
                      (Cross-Cutting Meta Architecture)
                                        │
        ┌───────────────────────────────┼───────────────────────────────┐
        │                               │                               │
        ▼                               ▼                               ▼
┌───────────────────────┐   ┌───────────────────────┐   ┌───────────────────────┐
│   COGNITIVE DOMAIN    │   │   KNOWLEDGE DOMAIN    │   │    RUNTIME DOMAIN     │
│                       │   │                       │   │                       │
│  Brain (Reasoning)    │   │  Knowledge Platform   │   │  Go MCP Server        │
│  Assistant            │   │  Knowledge Navigation │   │  Lifecycle Engine     │
│  Goal Resolver        │   │  Digital Twin Engine  │   │  Context Loader       │
│  Adaptive Planner     │   │  Mission Catalog      │   │  Governance Store     │
└───────────────────────┘   └───────────────────────┘   └───────────────────────┘
```

---

## 2. As Quatro Dimensões Arquiteturais

### 2.1 Experience Layer (Meta-Arquitetura Transversal)
Diferente de domínios funcionais tradicionais, a **Experience Layer** não executa lógica de negócio nem manipula arquivos diretamente.

- **Responsabilidade:** Orquestrar a jornada dos usuários e agentes de IA, preservar contexto cognitivo entre sessões consecutivas e adaptar o tom e profundidade das respostas ao perfil do operador (Beginner, Intermediate, Staff).
- **Invariante Constitucional (ADR-0114):** Permanece agnóstica a tecnologias ou fornecedores específicos de LLM, mantendo contratos unidirecionais com os domínios inferiores.

---

### 2.2 Cognitive Domain (Motor de Raciocínio & Intenção)
Responsável por transformar linguagem natural ou objetivos ambíguos em especificações executáveis e determinísticas:

- **Intent Recognition:** Mapeia a intenção declarada do desenvolvedor ("Quero validar o modelo de concorrência do runtime") para o conjunto exato de capacidades necessárias.
- **EPS (Execution Plan Specification):** Constrói um Grafo Acíclico Dirigido (DAG) contendo tarefas ordenadas com validações intermediárias.

---

### 2.3 Knowledge Domain & Digital Twin
O cérebro documental e semântico do ecossistema:

- **Digital Twin:** Uma representação viva e atualizada da base de código, contendo métricas de coesão, acoplamento, dependências externas e conformidade arquitetural.
- **Semantic Retrieval com NDCG@5 = 1.000:** Algoritmos refinados de busca vetorial e lexical que garantem que apenas a documentação relevante seja recuperada, evitando alucinações.

---

### 2.4 Runtime Domain (Motor de Execução em Go)
O coração operacional do BREoS:

- **Servidor MCP Nativo:** Implementado em Go 1.22, comunica-se via JSON-RPC 2.0 padrão com clientes como Claude Desktop, IDEs, Cursor e terminais.
- **Context Budget Manager:** Mede e impõe limites estritos de tokens em tempo de execução, garantindo desperdício zero de contexto ($M3 = 0.00\%$).
- **Lifecycle Engine:** Controla as fases de execução:
  $$\text{Loading} \to \text{Execution} \to \text{Validation} \to \text{Documentation} \to \text{Metrics} \to \text{Audit} \to \text{Feedback}$$

---

## 3. Fluxo de Vida de uma Solicitação

O diagrama abaixo ilustra a passagem de uma intenção até sua execução segura:

```text
Engenheiro / Agente IA
         │
         │ (1) Envia intenção em linguagem natural
         ▼
┌──────────────────┐
│   breos_guide    │ ──► Determina meta e ferramentas necessárias
└────────┬─────────┘
         │
         │ (2) Intenção contextualizada
         ▼
┌──────────────────┐
│    breos_plan    │ ──► Gera Execution Plan (EPS)
└────────┬─────────┘
         │
         │ (3) Plano gerado
         ▼
┌──────────────────┐
│  Context Budget  │ ──► Filtra contexto marginalmente relevante (M2: 2597 tokens)
└────────┬─────────┘
         │
         │ (4) Execução
         ▼
┌──────────────────┐
│  breos_execute   │ ──► Dispara tarefas do plano
└────────┬─────────┘
         │
         ├─── Se ação crítica ──► Bloqueia até breos_approve (Level 2)
         │
         │ (5) Conclusão
         ▼
┌──────────────────┐
│  breos_validate  │ ──► Valida contra critérios de aceite e certifica
└──────────────────┘
```

---

## 4. Garantias Constitucionais & Anti-Regressão

A integridade do BREoS é salvaguardada por 5 Gates mandatórios:

- **GATE-01:** Verificação de formatação e integridade léxica.
- **GATE-02:** Verificação de contratos de dependência arquitetural unidirecional.
- **GATE-03:** Paridade de compilação entre ferramentas anunciadas e despacháveis no MCP.
- **GATE-04:** Context Budget Enforcement (bloqueia execuções com desperdício de tokens $> 30\%$).
- **GATE-05:** Interceptação mandatória de autorização e aprovação humana de Nível 2.
