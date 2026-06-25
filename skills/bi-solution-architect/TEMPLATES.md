# Templates — Business Analytics Solution Architect

All deliverables are saved in the respective subdirectory under `./docs/agent_docs/architecture_docs/[strategic|operational|analytical]/` based on the selected decision horizon.

## ID Suffix Reference

Use these suffix markers consistently across every deliverable to maintain cross-horizon traceability:
*   `-STR-` for Strategic Layer assets.
*   `-OP-` for Operational Layer assets.
*   `-ANA-` for Analytical Layer assets.

---

## 1. Business Context Analysis
**Filename:** `01-business-context-analysis.md`
```markdown
# Business Context Analysis

## Selected Decision Horizon
<!-- Specify: Strategic, Operational, or Analytical. Blend solutions are prohibited. -->

## Executive Summary
<!-- 3-5 sentence overview of the business, its market position, and the analytics opportunity identified. -->

## Business Model
<!-- Describe how the organisation creates, delivers, and captures value. -->

## Core Focus Areas (Layer-Specific)
<!--
  - For Strategic: Long-term market forces, corporate targets, investment constraints.
  - For Operational: Daily key processes, cycle bottlenecks, SLA commitments.
  - For Analytical: Performance variance patterns, diagnostic questions, data relationships.
-->

## Strategic Objectives
| ID | Objective | Priority | Decision Area | Success Criteria | Owner | Time Horizon |
|----|-----------|----------|---------------|------------------|-------|--------------|
| BC-STR-00x / BC-OP-00x / BC-ANA-00x | | | | | | |

## Decision-Making Structure
<!-- Detail who makes which decisions (Business Owner, Managers, or Analysts), their cadence, and their information needs. -->

## Business Capability Map
<!-- Map functional capabilities and rate their current maturity (1-5) and analytics relevance (1-5). -->
```

---

## 2. Use Case Definition
**Filename:** `02-use-case-definition.md`
```markdown
# Use Case Definition

## Candidate Use Cases Catalogue (Ranked by Change Impact)
| Use Case ID | Use Case Title | Linked Objective | Difficulty | Organizational Change Level | Must-Have Justification | Change Impact Description |
|-------------|----------------|------------------|------------|-----------------------------|-------------------------|---------------------------|
| UC-STR-00x / UC-OP-00x / UC-ANA-00x | | | Low/Med/High | Very Low to Very High | <!-- active vs passive justification --> | |

## Selected Use Case(s)
<!-- Detail the use case(s) selected by the user for full architecting. Repeat the block below. -->

### UC-00x: [Title]
*   **Business Objective Statement**: "Enable [BC-00x] by providing [analytics capability]."
*   **Problem Statement**: "[Role] cannot [do what] because [root cause], resulting in [business consequence]."
*   **Must-Have vs. Nice-to-Have Justification**: <!-- Define why active prescriptive/foresight analytics is necessary and the cost of inaction. -->
*   **Success Criteria**: Metric | Target | Measurement Method.
*   **Expected Business Impact**: Quantified financial or operational value.
*   **Decision Areas Affected**: Grouped by role.
```

---

## 3. Executive Narrative Library
**Filename:** `03-executive-narrative-library.md`
```markdown
# Executive Narrative Library

## Narrative Index
| ID | Type | Management Question | Business Value |
|----|------|---------------------|----------------|
| NR-STR-00x / NR-OP-00x / NR-ANA-00x | Executive / Diagnostic / Predictive / Prescriptive | | |

## NR-00x: [Narrative Title]
*   **Management Question**: The exact question a decision-maker would ask.
*   **Analytics Discovery**: Data-driven finding answering the question (referencing specific KPI- IDs).
*   **Executive Insight**: Business meaning of the finding (jargon-free).
*   **Recommended Action**: Specific action with owner, timeline, and dependencies.
*   **Business Value**: Quantified value serving a BC- objective.
```

---

## 4. Data Asset Inventory
**Filename:** `04-data-asset-inventory.md`
```markdown
# Data Asset Inventory

## Data Source Registry
| Source ID | System | Type | Owner | Refresh Frequency | Key Entities | Quality Rating |
|-----------|--------|------|-------|--------------------|--------------|----------------|
| DA-00x | | | | | | |

## Data Dictionary
| Field | Source (DA-) | Type | Business Meaning | Quality Notes |
|-------|--------------|------|------------------|---------------|

## Source Mapping Diagram
<!-- Mermaid diagram showing join keys and database schemas. -->
```

---

## 5. Analytics Capability Assessment
**Filename:** `05-analytics-capability-assessment.md`
```markdown
# Analytics Capability Assessment

## Analytics Capability Matrix
| Capability | Feasibility | Data Readiness | Gap | Priority |
|------------|-------------|----------------|-----|----------|

## KPI Feasibility Matrix
| KPI (KPI-) | Required Data | Available (DA-) | Gap | Feasibility Rating |
|------------|---------------|-----------------|-----|--------------------|

## Supported & Unsupported Analyses
<!-- Enumerate which analyses can proceed and which are blocked by data gaps. -->
```

---

## 6. KPI Catalogue
**Filename:** `06-kpi-catalogue.md`
```markdown
# KPI Catalogue

## KPI Index
| KPI ID | Name | Family | Priority |
|--------|------|--------|----------|
| KPI-STR-00x / KPI-OP-00x / KPI-ANA-00x | | | |

<!--
  - For Strategic: NPV, LTV, CAGR, Market Share, ROI.
  - For Operational: Cycle times, SLA breach rates, Inventory Turns, Logistics counts.
  - For Analytical: Variance rates, correlation coefficients, cluster sizes.
-->
```

---

## 7. Analytics Foundation Architecture
**Filename:** `07-analytics-foundation-architecture.md`
```markdown
# Analytics Foundation Architecture

## Architecture Overview
<!-- Transform pattern description (ELT, DuckDB model, dbt layer). -->

## Metric Calculation Logic
<!-- Pseudocode, SQL, or DAX expressions for calculated KPIs. Detail input fields, filters, and edge cases. -->
```

---

## 8. Analytics Engine Architecture
**Filename:** `08-analytics-engine-architecture.md`
```markdown
# Analytics Engine Architecture

## Engine Index
| Engine ID | Name | Type | Priority |
|-----------|------|------|----------|
| ENG-STR-00x / ENG-OP-00x / ENG-ANA-00x | | | |

<!--
  - Strategic: Time-series forecasting (Holt-Winters), Scenario simulation, Risk modeling.
  - Operational: Threshold monitoring, Anomaly detection, Workflow bottleneck mining.
  - Analytical: Regression predictors, K-means clustering, Correlation segmentations.
-->
```

---

## 9. Intelligence Layer Architecture
**Filename:** `09-intelligence-layer-architecture.md`
```markdown
# Intelligence Layer Architecture

## RCA & Recommendation Framework
<!-- Describe the diagnostic root cause rules and recommendation prioritization rules (Impact x Feasibility). -->

## Automated Insight Templates
| Rule ID | Pattern | Insight Template | Severity |
|---------|---------|------------------|----------|
```

---

## 10. Management Deliverables Catalogue
**Filename:** `10-management-deliverables-catalogue.md`
```markdown
# Management Deliverables Catalogue

## Deliverable Index
| ID | Name | Type | Audience | Frequency |
|----|------|------|----------|-----------|
| DEL-STR-00x / DEL-OP-00x / DEL-ANA-00x | | Dashboard / Report / Exception Queue | | |
```

---

## 11. Deliverable Traceability Matrix
**Filename:** `11-deliverable-traceability-matrix.md`
```markdown
# Deliverable Traceability Matrix

## Full Traceability Matrix
| Deliverable (DEL-) | KPIs Consumed (KPI-) | Analytics Foundations | Analytics Engines (ENG-) | Intelligence Components (INT-) | Executive Outputs (NR-) | Decisions Enabled | Business Objectives (BC-) |
|--------------------|---------------------|---------------------|------------------------|-------------------------------|------------------------|-------------------|--------------------------|

## Cross-Horizon Connections (If serial build)
<!-- List references linking this build back to prior completed subdirectories. -->
```

---

## 12. Visualization Architecture
**Filename:** `12-visualization-architecture.md`
```markdown
# Visualization Architecture

## Dashboard Wireframes
<!-- ASCII Wireframe layouts strictly matching the chosen horizon:
  - Strategic: Quadrant matrix, forecast curves, maps.
  - Operational: Horizontal comparison bar charts, SLA card indicators, alert card feeds.
  - Analytical: Scatter plots with regression lines, bubble charts, decomposition trees.
-->
```

---

## 13. Solution Architecture Blueprint
**Filename:** `13-solution-architecture-blueprint.md`
```markdown
# Solution Architecture Blueprint

## Technical Blueprints
<!-- Data layer, pipelines (batch/streaming), SQL storage layers, API endpoints, and frontend dashboard platforms. -->
```

---

## 14. Development Roadmap
**Filename:** `14-development-roadmap.md`
```markdown
# Development Roadmap

## Roadmap Overview
<!-- 5-phase rollout schedule detailing milestones, durations, technical tasks, and critical risks. -->
```

---

## 15. Management Adoption Story
**Filename:** `15-management-adoption-story.md`
```markdown
# Management Adoption Story

## Business Storytelling
<!-- Before vs. After transition story, executive ROI case, change management, and quick wins. -->
```
