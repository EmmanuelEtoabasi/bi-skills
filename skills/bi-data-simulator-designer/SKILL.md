---
name: bi-data-simulator-designer
description: Design data simulation specifications that map business problem nuances, trends, anomalies, and mathematical bounds across Strategic, Operational, and Analytical layers. Use when designing simulated datasets, writing mock data specifications, defining points of inflection/date ranges, or says "data simulator design", "simulate BI data", "mock data spec", "simulation rules".
---

# Business Analytics Data Simulation Designer

Design structured simulation rules that bake business logic, narratives, and mathematical patterns into synthetic datasets, enabling downstream analytics engines and dashboards to demonstrate BI value.

## Quick Start

Provide the skill with:
1. The **6 registered business problems** (with their Operational, Analytical, and Strategic layers) from `path-definition.md`.
2. The **Executive Narratives** (`03-executive-narrative-library.md`) representing the stories to tell.
3. The **Data Asset Inventory** (`04-data-asset-inventory.md`) defining the destination schemas.
4. The **KPIs & Engines** (`07-analytics-foundation-architecture.md`, `08-analytics-engine-architecture.md`) defining mathematical requirements.

Output: `16-data-simulation-specification.md` containing date ranges, inflection points, and generation formulas.

## Core Rules

1. **Uniform Temporal Bounds**: All generated tables MUST share identical start and end dates. The range is dictated by the longest horizon required in the path (e.g., if a Strategic horizon is planned, all tables must span 3–5 years). Staggered ranges are prohibited as they violate referential integrity when joining historical transactional tables.
2. **Inflection Point Injection**: Specifies the exact timestamps or cycles where anomalies, seasonal shifts, or operational failures occur, matching the storylines in the Executive Narratives.
3. **Layer Alignment**:
   - *Operational*: Daily noise, sensor bounds, and outlier spikes to trigger alerting systems.
   - *Analytical*: Explanatory trends, multi-variable correlations (e.g. weather driving sales), and regression relationships.
   - *Strategic*: Long-term growth cycles, baseline drift, and policy step-functions.
4. **Traceability**: Every simulation rule must reference the corresponding problem ID (`UC-CAN-xx`) and data source (`DA-xx`).

## Verification & QA Checklist

- [ ] Do all simulated transactional tables share the exact same start and end dates?
- [ ] Are all step-functions ($\mathbb{I}$) and spikes mapped to absolute calendar dates rather than relative day offsets?

## Reference Files

*   [FRAMEWORK.md](FRAMEWORK.md) — Mathematical methods, date range structures, and layer simulation rules.
*   [OUTPUT-TEMPLATE.md](OUTPUT-TEMPLATE.md) — Markdown template for the simulation specification deliverable.
*   [EXAMPLES.md](EXAMPLES.md) — Worked examples showing how to specify cyclical, random, and trend-based data.
