![badge-labs](https://user-images.githubusercontent.com/327285/230928932-7c75f8ed-e57b-41db-9fb7-a292a13a1e58.svg)
# AI Evaluation and Benchmarking Framework

A [FINOS Labs](https://www.finos.org/blog/updated-finos-project-lifecycle) initiative for building a taxonomy, datasets, and tooling for **system-level** evaluation of AI (including agentic workflows) in financial services.

## Motivation

AI systems are non-deterministic and financial tasks rarely have a single “correct” answer. General-purpose, model-only benchmarks miss domain-specific correctness, operational risk, and compliance needs.

This project anchors evaluations in financial **use cases**, with a taxonomy that links:

**Use Cases → Risks → Metrics**

That bridges technical benchmarking with business and regulatory reality—supporting trust, comparability, and safer deployment—not a generic leaderboard.

## Role in the FINOS AI ecosystem

This work is part of the broader FINOS AI agenda: it supplies the **evaluation and benchmarking** layer that turns governance intent into measurable evidence.

- **AI Governance Framework (AIGF):** What to govern (policies, risks, guardrails).
- **Common Architecture Language Model (CALM) and related specs:** Machine-readable expression of those requirements where applicable.
- **This framework:** Datasets, metrics, reference architectures, and methods (including LLM-as-a-judge patterns) to **test** whether systems and agents behave acceptably in real workflows.
- **FINOS Common Cloud Controls (CCC) and firm controls:** Infrastructure and organizational requirements that sit alongside technical evaluation.

Together, these pieces support a transparent, finance-aware path from requirements to verified behavior—not a model factory or a substitute for internal compliance programs.

## What this repository is (and is not)

**It is:** a taxonomy and methodology hub; a place for evaluation datasets and synthetic-data strategies; reference architectures and implementation patterns for RAG and agentic stacks; task benchmarks and guardrail concepts; and adapters/patterns that map open evaluation tooling to FSI contexts.

**It is not:** an orchestration platform or LLM factory; a generic public leaderboard; or a replacement for firm-specific policies and sign-off.

Evaluation here emphasizes **whole-system** behavior (retrieval, tools, routing, traces, policies), not final-token accuracy alone.

## From use case proposal to dedicated Labs work

Community **use cases** are the main intake for prioritizing agents, datasets, and evaluation design. The structured form captures description, business value, risks, proposed metrics, and likely system components (LLM, RAG, tools, etc.).

**Suggested path:**

1. **Propose** — Open a [Financial Agent Use Case](https://github.com/finos-labs/ai-evals-framework/issues/new?template=Use_case.yml) issue ([form source](https://github.com/finos-labs/ai-evals-framework/blob/main/.github/ISSUE_TEMPLATE/Use_case.yml)). This creates a shared, reviewable record under the `use-case` workflow.
2. **Prioritize and align** — Maintainers and contributors discuss and prioritize proposals against framework milestones (taxonomy, metrics, reference stacks, synthetic-data pipelines, RAG/agentic evaluation tracks). [Open issues](https://github.com/finos-labs/ai-evals-framework/issues) in this repository track those themes.
3. **Implement in dedicated repositories** — For agreed priorities, **reference agent implementations** and **evaluation harnesses** (datasets, scenarios, thresholds, reproducible runs) typically live in **separate FINOS Labs repositories**, implemented **in line with approved reference architectures and patterns** published or agreed here. That keeps this repo focused on taxonomy, standards, and cross-cutting assets while allowing each agent/eval program to iterate quickly with clear scope.
4. **Lifecycle** — New or incubated work generally enters the ecosystem under the [updated FINOS Project Lifecycle](https://www.finos.org/blog/updated-finos-project-lifecycle): **Labs** for exploratory, neutral collaboration with clear baseline expectations; optional **Forming** for time-bound setup; **Incubating** for governance, roadmap discipline, and repeatable open-source practices; **Graduated** for high maturity, adoption, and sustainability; **Archived** when maintenance ends but history remains valuable. Security and operational expectations scale with stage (aligned with OpenSSF baselines as described in that post). Broader FINOS project proposals and stage transitions are coordinated through the foundation’s community processes (including issue-based workflows described on [FINOS](https://www.finos.org/)).

## Deliverables

For each financial use case, the framework aims to provide:

- Test datasets and synthetic data generation approaches
- Reference architectures and implementation strategies for evaluation
- Metrics, thresholds, and evaluation guidelines
- Monitoring and “glass-box” / trajectory-oriented evaluation guidance where agentic systems are in scope

Associated assets may include open datasets (for example CDM-oriented synthetic scenarios), patterns for observability-backed evaluation, and integration notes for open evaluators adapted to financial tasks.

## Roadmap

High-level phases (see workshop summary in the PDF below and [milestones as GitHub issues](https://github.com/finos-labs/ai-evals-framework/issues)):

- Gather workshop and techsprint artefacts (Sept 2025) → [PDF summary](https://github.com/finos-labs/ai-evals-framework/blob/main/202509%20-%20FINOS%20AI%20Evals.pdf)
- Literature review, infrastructure, repository launch; taxonomy and milestone definitions advanced on GitHub (2025–2026)
- Use-case intake via the issue template; prioritized work feeding dedicated Labs implementation and evaluation repos
- Template repositories and reference examples aligned to agreed architectures
- Pilot engagement with financial institutions
- Expand shared taxonomy and reusable assets across industry participants

### OSFF 2026: contributors, use-case prioritization, and showcase

The evaluation stream is on the agenda of the FINOS **[AI Governance Framework Training Workshop — OSFF Toronto](https://www.finos.org/hosted-events/2026-04-13-ai-governance-framework-training-workshop)** (13 April 2026, Toronto). After sessions on AIGF leader training and the AI Reference Architecture Library (including how that library intersects with AIGF and CALM), the workshop includes **“Beyond the Black Box: Operationalizing AgentOps and glass-box evaluations for financial AI”**—a practical segment on moving from traditional MLOps to AgentOps and on mapping real-world financial **use cases** to rigorous, quantitative **evaluation metrics**, grounded in ongoing work in **this FINOS AI Evaluation & Benchmarking framework**. That session is a primary moment to **recruit contributors** and **prioritize use cases** with governance, risk, and engineering practitioners in the room.

Aim to **showcase** a selection of those prioritized use cases and evaluation progress at **[Open Source in Finance Forum London](https://events.linuxfoundation.org/open-source-finance-forum-london/)** (25 June 2026). If you plan to propose or champion a use case, filing a [Financial Agent Use Case](https://github.com/finos-labs/ai-evals-framework/issues/new?template=Use_case.yml) issue ahead of Toronto helps the community prepare for discussion and follow-up.

## Milestones

Each milestone in the diagram below is tracked as a GitHub issue in this repository (search issues for “milestone definition” and use-case proposals for active agent threads).

![202509 - FINOS AI Evals](https://github.com/user-attachments/assets/94f3e390-655f-432c-bf27-3fbade4fb35d)

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) and the [FINOS Community Code of Conduct](CODE_OF_CONDUCT.md). Use the [Financial Agent Use Case](https://github.com/finos-labs/ai-evals-framework/issues/new?template=Use_case.yml) template for new evaluation scenarios; use the other issue templates for bugs, features, and support questions.

## License

Copyright 2025 FINOS

Distributed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0).

SPDX-License-Identifier: [Apache-2.0](https://spdx.org/licenses/Apache-2.0)
