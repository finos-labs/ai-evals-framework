# FINOS AI Evaluation & Benchmarking Framework — Milestone Scope Definitions & Glass-Box AgentOps Architecture

This document defines the concrete outcomes, in-scope deliverables, out-of-scope boundaries, and verification criteria for the core scoping milestones tracked in this repository:

- **Milestone `#4`**: [Taxonomy Milestone Definition](https://github.com/finos-labs/ai-evals-framework/issues/4)
- **Milestone `#8`**: [AIGF Mapping Milestone Definition](https://github.com/finos-labs/ai-evals-framework/issues/8)
- **Milestone `#10`**: [Metrics for Evaluations Milestone Definition](https://github.com/finos-labs/ai-evals-framework/issues/10)
- **Milestone `#11`**: [Evaluations Monitoring Reference Architecture & Guidance](https://github.com/finos-labs/ai-evals-framework/issues/11)
- **Milestone `#15`**: [Agentic Evaluations Milestone Definition](https://github.com/finos-labs/ai-evals-framework/issues/15)

All mappings are codified in machine-readable form in [`taxonomy/use_case_aigf_calm_metrics_taxonomy.json`](./use_case_aigf_calm_metrics_taxonomy.json) and verified via [`evals/validate_evals_framework.py`](../evals/validate_evals_framework.py).

---

## 1. Milestone `#4`: Taxonomy Milestone Definition (`Use Case → Risks → Controls → Metrics`)

### Outcome
A canonical, machine-readable JSON taxonomy (`taxonomy/use_case_aigf_calm_metrics_taxonomy.json`) that connects every prioritized FSI agent use case (`#20`–`#24`, `#26`, `#31`, and multi-desk institutional agent workflows) to specific FINOS AI Governance Framework (`AIGF`) risks, `AIGF` mitigations, `CALM` control requirements, and quantitative evaluation metrics.

### In Scope
- Four-tier relational linkage: **Use Case (`UC-*`) $\rightarrow$ AIGF Risks (`RI-*`) $\rightarrow$ AIGF Mitigations (`MI-*`) & CALM Controls (`FINOS-*`) $\rightarrow$ Quantitative Metrics (`M-AGT-*`)**.
- Agent autonomy classification (`A0`–`A4`) aligned with the [FINOS AI Reference Architecture Library](https://github.com/finos/ai-reference-architecture-library).
- Applicable financial regulatory frameworks (`SR 11-7`, `EU AI Act`, `DORA`, `MiFID II`, `SEC Reg BI / Rule 15c3-5`, `ECOA`, `BSA/AML`, `CPMI-IOSCO PFMI`).

### Out of Scope
- Generic, domain-agnostic LLM leaderboards (e.g., trivia or general coding benchmarks without financial risk grounding).
- Proprietary model training recipes or firm-specific internal credit/trading formulas.

---

## 2. Milestone `#8`: AIGF Mapping Milestone Definition

### Outcome
Bidirectional traceability between every evaluation metric in this framework and the corresponding risk/mitigation entries in [`finos/ai-governance-framework`](https://github.com/finos/ai-governance-framework) and [`finos/ai-reference-architecture-library`](https://github.com/finos/ai-reference-architecture-library).

### In Scope
- Mapping accuracy, grounding, and abstention evaluations to `RI-4` (*Hallucination and Inaccurate Outputs*), `RI-17` (*Lack of Explainability*), and `MI-13` (*Citations and Source Traceability*).
- Mapping fairness and counterfactual invariance evaluations to `RI-16` (*Bias and Discrimination*).
- Mapping agentic tool-calling, commitment-time mandate freshness, multi-hop delegation attenuation, and collective exposure evaluations to `RI-24` (*Agent Action Authorization Bypass*), `RI-25` (*Tool Chain Manipulation*), `RI-28` (*Multi-Agent Trust Boundary Violations & Collective Systemic Risk*), and `MI-18`–`MI-24`.
- Mapping machine-configurable `CALM` control identifiers (`FINOS-PREV-018-001`, `FINOS-PREV-018-002`, `FINOS-PREV-019-001`, `FINOS-DET-020-001`, `FINOS-AUD-021-001`).

### Out of Scope
- Redefining AIGF normative policy prose inside this repository (normative risk and mitigation definitions remain in `finos/ai-governance-framework`).

---

## 3. Milestone `#10`: Metrics for Evaluations Milestone Definition

### Outcome
A standardized catalog of quantitative, threshold-bounded metrics (`M-AGT-01` through `M-AGT-10`) with explicit units, directionality (`higher_is_better` vs. `lower_is_better`), valid numeric domains (`[0.0, 1.0]`), and baseline production promotion thresholds.

| Metric ID | Metric Name | Layer | Direction | Baseline Threshold |
|---|---|---|---|---|
| `M-AGT-01` | Evidence-Grounded Citation Precision | Glass-Box Retrieval & Synthesis | `higher_is_better` | `>= 0.98` |
| `M-AGT-02` | Fail-Closed Abstention Recall on Insufficient/Stale Evidence | Glass-Box Metacognitive Gate | `higher_is_better` | `>= 0.99` |
| `M-AGT-03` | Pre-Execution Tool Authorization Conformance Rate (`min(user,agent)`) | Glass-Box Trajectory & Tool Gate | `higher_is_better` | `== 1.00` |
| `M-AGT-04` | Commitment-Time Mandate Freshness & Uncertain-Outcome Hold Rate | Glass-Box Mandate Gate | `higher_is_better` | `== 1.00` |
| `M-AGT-05` | Multi-Hop Delegation Attenuation & Cross-Institution Verification Rate | Glass-Box Multi-Agent Graph | `higher_is_better` | `== 1.00` |
| `M-AGT-06` | Collective Systemic Exposure Circuit-Breaker Containment Rate (`ST-05`) | Glass-Box Fleet Runtime Protection | `higher_is_better` | `== 1.00` |
| `M-AGT-07` | Demographic & Protected-Attribute Counterfactual Parity Gap | Fairness & Bias Robustness | `lower_is_better` | `<= 0.02` |
| `M-AGT-08` | Indirect Prompt-Injection & Tool-Output Poisoning Block Rate | Adversarial Robustness | `higher_is_better` | `>= 0.995` |
| `M-AGT-09` | Verifiable Cryptographic Trajectory Receipt Coverage (`IETF SCITT`) | Audit & Regulatory Verifiability | `higher_is_better` | `== 1.00` |
| `M-AGT-10` | Graph-Reasoning Path Soundness Score | Glass-Box Reasoning Trajectory | `higher_is_better` | `>= 0.95` |

---

## 4. Milestone `#11` & `#15`: Agentic "Glass-Box" Evaluations & Runtime Monitoring Reference Architecture

### Outcome
Move beyond black-box final-token scoring to **Glass-Box Trajectory Evaluation** that inspects intermediate retrieval states, commitment-time mandate checks, tool-call arguments, multi-agent delegation graphs, and collective fleet exposure both in pre-deployment CI/CD and in production runtime monitoring.

### Core Glass-Box Evaluation Invariants
1. **Whole-Trajectory Inspection**: Evaluators inspect every intermediate step (`retrieve -> plan -> reserve_mandate -> invoke_tool -> verify_output -> emit_receipt`), failing closed if an agent reaches a correct final answer via an unauthorized tool call or stale mandate (`M-AGT-03`, `M-AGT-04`).
2. **Multi-Agent Collective & Cross-Institutional Stress Testing**: Evaluators replay concurrent multi-agent trajectories (e.g., investment, treasury liquidity, and lending agents reacting simultaneously to a market shock) to verify that collective systemic circuit breakers (`FINOS-DET-020-001` `ST-05`) and two-phase atomic limit reservations (`FINOS-PREV-018-002`) prevent aggregate exposure breaches (`M-AGT-05`, `M-AGT-06`).
3. **Independently Verifiable Audit Evidence (`IETF SCITT RFC 9162` & Hardware-Attested Verification)**:
   - Open-source evaluation harnesses verify that every state-mutating trajectory step emits a structured receipt (`M-AGT-09`).
   - For regulated financial institutions and Digital Financial Market Infrastructures (`D-FMI`) requiring cryptographic non-repudiation across organizational boundaries, glass-box evaluation trajectories bind to **IETF SCITT (`RFC 9162`)** / `COSE_Sign1` transparency logs and hardware-attested execution & non-custodial clearing verification layers so auditors and counterparties can verify policy and mandate conformance offline.
