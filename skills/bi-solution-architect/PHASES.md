# Analytical Solution Design Phases

This file defines the 13 sequential phases of the solution design workflow, grouped into **5 Parallelization Gates** to enable concurrent agentic processing.

Every phase specifies how the inputs, responsibilities, and outputs adapt based on the selected decision layer: **Strategic**, **Operational**, or **Analytical**.

---

## Gate 1: Strategic Scope (Sequential)

### Phase 1: Business Context Definition
*   **Objective**: Understand the business scope, organizational roles, and target decision area.
*   **Problem Discovery Scan**:
    *   Assess if the user has provided explicit business problems to solve.
    *   **If undefined/vague**: Deep-dive into the index business model, industry sector, and operational layers. Brainstorm and select a **minimum of 3 highly relevant business problems** that present the highest potential for proving the value of BI/BA and driving adoption.
    *   For each selected problem, define its three components and simulation criteria:
        *   *Operational Component*: Daily transaction monitoring, SLA metrics, and operational exception alerts.
        *   *Analytical Component*: Diagnostic analyses, regression variables, and predictive model targets.
        *   *Strategic Component*: Portfolio-level rollups, long-term trends, scenario forecasts, and capital allocation impact.
        *   *Simulated Data Markers*: Transaction variables, labels, and variance factors (e.g. `actual_cost`, `waste_ratio`, `project_delay_days`) to guide demo data generation.
        *   *BI Adoption Value*: The specific value proposition that convinces stakeholders at each organizational level.
*   **Layer-Specific Responsibilities (for the active build)**:
    *   *Strategic*: Identify long-term market forces, corporate objectives, macro-economic conditions, and board-level decision rights.
    *   *Operational*: Map daily key operational workflows, process managers' decision areas, and immediate cost/time pain points.
    *   *Analytical*: Catalog diagnostic performance indicators, pattern-discovery goals, and explanatory questions (the "why" behind the numbers).
*   **Outputs**: `01-business-context-analysis.md` containing the business model description, objectives, and capability mapping.

### Phase 2: Use Case Definition & Interactive Verification Gate
*   **Objective**: Brainstorm candidate use cases, map them to the 3 target problems, and select the primary target for full design.
*   **Outputs**: `02-use-case-definition.md` containing the ranked use cases catalogue and selected usecase specifications.
*   **Interactive Verification Gate (Orchestrator)**:
    *   At the end of Phase 2, if this is the first build, the Orchestrator **MUST** halt execution and present the drafted 3 multi-horizon problems and simulation markers to the user.
    *   Prompt the user to choose:
        1.  **Accept**: Writes the path choice and the 3 detailed problems to `docs/agent_docs/architecture_docs/path-definition.md` and triggers the next Gate.
        2.  **Edit**: Allows the user to modify any layer's component or simulation marker before storing.
        3.  **Regenerate**: Instructs the Context Analyst to propose alternative business problems.
    *   This gate blocks all downstream parallel subagents until approval is received.

---

## Gate 2: Content Discovery (Parallel)

### Phase 3: Executive Narrative Design (Subagent A)
*   **Objective**: Create the core management narratives that frame the analytics findings.
*   **Layer-Specific Responsibilities**:
    *   *Strategic*: Write long-term market trend projections and capital return narratives (`NR-STR-`).
    *   *Operational*: Write daily SLA breach alerts, immediate stockout warnings, and process bottleneck alerts (`NR-OP-`).
    *   *Analytical*: Write diagnostic margin contribution findings and customer profile insights (`NR-ANA-`).
*   **Outputs**: `03-executive-narrative-library.md`.

### Phase 4: Data Asset Discovery (Subagent B)
*   **Objective**: Register internal and external data sources supporting the use cases.
*   **Layer-Specific Responsibilities**:
    *   *Strategic*: Focus on high-level financial ledgers, competitor intelligence reports, and macro API feeds.
    *   *Operational*: Focus on transactional databases, POS logs, site supervisor sheets, and real-time event logs.
    *   *Analytical*: Focus on granular checkout records, customer profiles, and marketing databases.
*   **Outputs**: `04-data-asset-inventory.md`.

---

## Gate 3: Analytics Foundations (Sequential)

### Phase 5: Analytical Possibility Assessment
*   **Objective**: Evaluate data gaps and metric feasibility against the chosen layer.
*   **Outputs**: `05-analytics-capability-assessment.md` (identifies feasibility green/amber/red levels and gap remediations).

### Phase 6: Analytics Foundation Design (KPIs)
*   **Objective**: Design the KPI Catalogue and metrics dictionary.
*   **Layer-Specific Responsibilities**:
    *   *Strategic*: Define metrics like Net Present Value (NPV), Customer Lifetime Value (LTV), and Compound Annual Growth Rate (CAGR).
    *   *Operational*: Define metrics like cycle times, SLA breach ratios, inventory turnover days, and logistics variances.
    *   *Analytical*: Define statistical metrics like regression variables, correlation margins, and cluster boundaries.
*   **Outputs**: `06-kpi-catalogue.md` and `07-analytics-foundation-architecture.md`.

### Phase 7: Analytics Engine Design
*   **Objective**: Detail processing models (`ENG-`) and detection rules.
*   **Layer-Specific Responsibilities**:
    *   *Strategic*: Specify Holt-Winters forecasting engines, scenario simulators, and risk index estimators.
    *   *Operational*: Specify threshold-based alert engines, process bottleneck monitors, and real-time exception logs.
    *   *Analytical*: Specify K-means clustering engines, regression predictors, and correlation analyzers.
*   **Outputs**: `08-analytics-engine-architecture.md`.

### Phase 8: Intelligence Layer Design
*   **Objective**: Map analytical outputs to priority recommendation matrices and automated text insights.
*   **Outputs**: `09-intelligence-layer-architecture.md`.

### Phase 8B: Data Simulation Design
*   **Objective**: Synthesize data schemas, date ranges, inflection points, and math requirements into a single data generation specification.
*   **Responsibilities**:
    *   Invoke the **`bi-data-simulator-designer`** skill under the hood to write the data simulation specification.
    *   Consume all prior deliverables (`01` through `09` and `path-definition.md`).
    *   Map out target date ranges and record frequencies matching the target horizon (Strategic: 3+ years, Analytical: 1+ year, Operational: 3 months).
    *   Inject specific **Points of Inflection** (anomalies, spikes, structural breaks) that match the qualitative storylines in `03-executive-narrative-library.md`.
    *   Define generation rules and mathematical formulas (e.g. noise distributions, sine waves) that produce data within the bounds required by the KPI catalogue (`07-analytics-foundation-architecture.md`) and the analytics engines (`08-analytics-engine-architecture.md`).
*   **Outputs**: `16-data-simulation-specification.md`.

---

## Gate 4: Frontend Design (Parallel)

### Phase 9 & 10: Management Deliverable Definition (Subagent A)
*   **Objective**: Define deliverables (`DEL-`) and build the end-to-end traceability matrix.
*   **Layer-Specific Responsibilities**:
    *   *Strategic*: Specify executive scorecards, strategic opportunity boards, and investment briefings.
    *   *Operational*: Specify operational dashboards, exception queues, and real-time alert logs.
    *   *Analytical*: Specify interactive exploratory reports, diagnostic summaries, and customer segmentation matrices.
*   **Outputs**: `10-management-deliverables-catalogue.md` and `11-deliverable-traceability-matrix.md`.

### Phase 11: Visualization Architecture (Subagent B)
*   **Objective**: Design wireframes (`VIZ-`) based on visual cognitive guides.
*   **Layer-Specific Responsibilities**:
    *   *Strategic*: Design quadrant matrices, forecast trend charts with confidence intervals, and maps.
    *   *Operational*: Design horizontal comparison bar charts, SLA card indicators, and alert cards.
    *   *Analytical*: Design scatter plots with regression lines, bubble charts, and decomposition trees.
*   **Outputs**: `12-visualization-architecture.md`.

---

## Gate 5: Roadmaps & Storytelling (Parallel)

### Phase 12: Development Architecture (Subagent A & B)
*   **Objective**: Outline technology blueprints and rollout roadmaps.
*   **Layer-Specific Responsibilities**:
    *   *Strategic*: Detail long-term cloud storage layers, data integration gateways, and a 3-year corporate roadmap.
    *   *Operational*: Detail high-frequency CDC ingestion (Kafka, streaming), local database pipelines, and a quick-wins roadmap.
    *   *Analytical*: Detail python data science feature environments (Jupyter, sklearn), model registry nodes, and training schedules.
*   **Outputs**: `13-solution-architecture-blueprint.md` and `14-development-roadmap.md`.

### Phase 13: Management Storytelling (Subagent C)
*   **Objective**: Draft the before/after narrative presentation and corporate ROI case.
*   **Outputs**: `15-management-adoption-story.md`.
