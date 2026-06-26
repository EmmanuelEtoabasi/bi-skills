---
title: Output Template
purpose: Defines the 4 required output artifacts that bi-problem-formulator must produce before handing off to bi-solution-architect.
---

# Output Template — bi-problem-formulator

This document defines the exact output structure the skill must produce after all 6 problems are locked. The output is consumed by `bi-solution-architect` to populate `path-definition.md` and drive the 15-deliverable architecture builds per layer.

---

## Output 1: Problem Registry

Produce one block per problem using this template. All 6 problems must be documented.

```markdown
## Problem [N]: [Problem Title]

**Tier**: [Foundation / Compound / Near-Future / Long-Term]
**Primary Layer**: [Operational / Analytical / Strategic]

### Operational Component
<!-- Daily monitoring, SLA tracking, exception alerts, transactional logging -->

### Analytical Component
<!-- Diagnostic analysis, correlations, root-cause investigation, pattern discovery -->

### Strategic Component
<!-- Forecasting, scenario simulation, capital planning, growth modeling -->

### Simulated Data Markers
| Field Name | Data Type | Description |
|------------|-----------|-------------|
| | | |

### BI Adoption Value
<!-- One paragraph: Why would the target user open this dashboard? What pain does it eliminate? -->

### "Aha!" Moment
<!-- The specific insight or number that makes the owner say "I didn't know that." Include a concrete example with plausible numbers. -->

### Additional Investment Required
<!-- What new data capture, hardware, API, or process is needed beyond what prior problems already built? Write "None — uses existing pipelines" if applicable. -->

### Cross-Problem Dependencies
<!-- Which prior problems' data pipelines does this problem consume? -->
```

---

## Output 2: Cumulative Data Infrastructure Map

Produce a Mermaid diagram showing the data pipelines each problem builds and how later problems consume earlier pipelines. Use this structure:

```markdown
## Cumulative Data Infrastructure Map

<!-- Mermaid diagram showing:
  - Each problem as a node
  - Data streams flowing between problems
  - New data capture points highlighted
  - The dependency chain from Problem 1 through Problem 6
-->

### Data Assets Created Per Problem

| Problem | New Data Assets Created | New Data Capture Required |
|---------|------------------------|---------------------------|
| P1 | e.g., Daily transaction log, payment method split | POS digitization |
| P2 | e.g., Purchase cost log, supplier delivery records | Receipt logging |
| P3 | e.g., Customer ledger, aging brackets | Sales ledger digitization |
| P4 | e.g., Inventory lifecycle, waste records | 1 new capture point (specify) |
| P5 | e.g., Cash flow model, forecast dataset | Bank balance feed, fixed costs |
| P6 | e.g., External signals, autonomous decision log | External APIs, automation tools |
```

---

## Output 3: Layer Decomposition Table

Produce a table mapping all 6 problems to the 3 build layers. Clearly indicate which problems are split across layers.

```markdown
## Layer Decomposition

### Build 1: Operational — "The Daily Heartbeat"

| Problem Assignment | Component Description | Operational KPIs Created |
|--------------------|----------------------|--------------------------|
| P[N] (full / P[N]-OP) | | KPI-OP-XX: ... |

**Primary Users**: [roles]
**Cadence**: [daily/weekly]

---

### Build 2: Analytical — "The Diagnostic Engine"

| Problem Assignment | Component Description | Analytical KPIs Created | Cross-Horizon References |
|--------------------|----------------------|-------------------------|--------------------------|
| P[N] (full / P[N]-ANA) | | KPI-ANA-XX: ... | References KPI-OP-XX from Build 1 |

**Primary Users**: [roles]
**Cadence**: [weekly diagnostic reviews]

---

### Build 3: Strategic — "The Forward-Looking Intelligence"

| Problem Assignment | Component Description | Strategic KPIs Created | Cross-Horizon References |
|--------------------|----------------------|------------------------|--------------------------|
| P[N] (full) | | KPI-STR-XX: ... | References KPI-ANA-XX from Build 2 |

**Primary Users**: [roles]
**Cadence**: [continuous + weekly strategic review]

---

### Cross-Horizon Data Flow Summary

<!-- Mermaid diagram or table showing:
  Operational KPIs → feed into → Analytical Engines → feed into → Strategic Models
-->
```

---

## Output 4: Analytics Maturity Staircase

Produce a summary table showing the progression across all 6 problems.

```markdown
## Analytics Maturity Staircase

| # | Problem | Analytics Type | Owner's Role | Time Orientation | Layer |
|---|---------|---------------|--------------|------------------|-------|
| 1 | [Title] | Descriptive | Reads dashboard | Past | Operational |
| 2 | [Title] | Comparative | Reads + compares | Past | Operational |
| 3 | [Title] | Diagnostic (light) | Decides + acts | Present | Operational |
| 4 | [Title] | Diagnostic (deep) | Discovers insights | Present | Analytical |
| 5 | [Title] | Predictive + Prescriptive | Reviews + approves | Future | Strategic |
| 6 | [Title] | Autonomous + Adaptive | Oversees + overrides | Continuous | Strategic |
```

---

## Assembly Format for Handoff

Once all 4 outputs are complete, assemble them into a single document and present to the user for final approval. Upon approval, pass the complete output to `bi-solution-architect` as input context using this handoff format:

```markdown
# Problem Formulation Complete — Handoff to bi-solution-architect

## Business Profile Summary
<!-- Repeat the key fields from bi-prompt-builder: Company, Industry, Operating Model, Scale, Stack -->

## Approved Problems (6)
<!-- Include full Output 1: Problem Registry -->

## Data Infrastructure Map
<!-- Include full Output 2 -->

## Layer Decomposition
<!-- Include full Output 3 -->

## Maturity Staircase
<!-- Include full Output 4 -->

## Path Selection
*   **Pathway**: [Path A or Path B as determined during bi-prompt-builder]
*   **First Active Build**: [Operational / Strategic — based on path]

## Instructions for bi-solution-architect
Write the 6 approved problems and their layer assignments into `docs/agent_docs/architecture_docs/path-definition.md`. Then begin the first active build using the problems assigned to its layer as the driving use cases.
```
