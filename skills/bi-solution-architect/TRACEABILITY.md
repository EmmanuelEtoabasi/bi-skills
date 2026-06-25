# Traceability Chain & Cross-Horizon Validation

Every architecture must trace back through the decision horizon value chain to ensure there are no isolated elements or untraced objectives.

---

## Suffix Tagging Model

Standardized suffixes are mandatory to identify the decision horizon of each element:
*   `SO-STR-00x` or `BC-STR-00x` (Strategic Objectives)
*   `SO-OP-00x` or `BC-OP-00x` (Operational Objectives)
*   `SO-ANA-00x` or `BC-ANA-00x` (Analytical Objectives)

Similarly for use cases (`UC-STR-`), narratives (`NR-STR-`), KPIs (`KPI-STR-`), engines (`ENG-STR-`), and deliverables (`DEL-STR-`).

---

## Cross-Horizon Linking Rules (Serial Builds)

When building layers sequentially under **Path A** or **Path B**:

1.  **Upstream Referencing**:
    If a prior build subdirectory exists (e.g. `operational/` is complete, and the current build is `analytical/`), the new build deliverables **MUST** reference KPIs, Data Assets, or Engine outputs from the prior build where applicable.
2.  **Traceability Mapping**:
    The Deliverable Traceability Matrix (`11-deliverable-traceability-matrix.md`) in the current build folder must contain a dedicated section **Cross-Horizon Connections** mapping how this layer links to the adjacent completed layer:
    *   *Example*: Mapping how Operational Alert `KPI-OP-001` triggers Analytical Engine `ENG-ANA-001`.
3.  **Path Definition Registration**:
    The Orchestrator must register the completed status of each layer in `docs/agent_docs/architecture_docs/path-definition.md` upon final Gate sign-off.

---

## QA Validation Checklist

The Quality Assurance Agent runs this checklist at the end of each Parallelization Gate:

### 1. Horizon Separation Check
- [ ] **Zero Blending**: Deliberables in the `operational/` folder contain no strategic scenario planning or analytical modeling (regressions/correlations) unless explicitly labeled as cross-horizon inputs.
- [ ] All elements (objectives, KPIs, engines, visuals) are strictly tagged with their matching suffix (`-STR-`, `-OP-`, or `-ANA-`).

### 2. Traceability Alignment
- [ ] Every deliverable (KPI, engine, narrative, visual) traces back to at least one of the 3 multi-horizon problems registered in `path-definition.md`.
- [ ] Every KPI has a valid formula and traces back to a data source (`DA-`) and objective (`BC-`).
- [ ] Every analytical engine (`ENG-`) consumes at least one KPI and supports a documented decision area.
- [ ] Every visualization (`VIZ-`) maps to a deliverable (`DEL-`) and chart type appropriate to the chosen horizon (KPI Cards for Strategic, Alert Cards for Operational, Scatter/Decomposition for Analytical).

### 3. Cross-Horizon Integration & Simulation Prep
- [ ] If a prior build exists, the current traceability matrix contains at least one active connection mapping inputs/outputs between the folders.
- [ ] The simulated data markers (fields, variances) declared in `path-definition.md` are correctly mapped as source attributes in `04-data-asset-inventory.md` and referenced in calculation formulas in `07-analytics-foundation-architecture.md`.
- [ ] The `path-definition.md` file is complete, accurately lists the statuses of all completed and active directories, and maintains the consistent 3 problems.
