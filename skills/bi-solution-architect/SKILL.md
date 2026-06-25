---
name: bi-solution-architect
description: Transform business context, objectives, and data assets into a complete analytics solution architecture tailored to a specific decision horizon (Strategic, Operational, or Analytical) using path-based agentic orchestration.
---

# Business Analytics Solution Architect

Transform business understanding into a traceable analytics solution — from strategic objectives through KPIs, engines, intelligence, dashboards, and adoption narratives — aligned strictly to a single decision horizon: **Strategic**, **Operational**, or **Analytical**.

## Startup Workflow (Decision Horizons & Paths)

When this skill is invoked:

0. **Input Validation**: Check if the user's request contains the core details (Company Name, Industry, Path, Stack, and Target Roles).
   * **If thin/incomplete** (e.g., just the slash command or a brief phrase like "/bi-solution-architect for retail"): Invoke the **`bi-prompt-builder`** subagent/sub-skill under the hood.
   * Follow its step-by-step Q&A wizard to fetch company info, propose dynamic defaults based on the industry, select the path, and construct the structured model prompt.
   * Return the compiled prompt back as the active input context and continue to Step 1.
1. **Prior Build Scan**: Check if `docs/agent_docs/architecture_docs/path-definition.md` exists.
2. **If NO prior build exists**:
   * **Path Selection**: Prompt the user to select one of the following two deployment pathways:
     * **Path A: Bottom-Up (Operational → Analytical → Strategic)**: Focus on daily pipelines, staging POS/logistics tracking first, then scaling to analytical insight and long-term planning.
     * **Path B: Top-Down (Strategic → Operational → Analytical)**: Focus on corporate board objectives first, then aligning daily operations and analytical models.
   * **Problem Discovery**: If the user has not explicitly defined specific business problems/use cases, the agent must perform a deep-dive analysis of the index business model and select a **minimum of 3 highly relevant business problems** that span all three layers (Operational, Analytical, Strategic) and have simulated data markers for high-impact BI adoption.
   * **Interactive User Gate**: Halt execution and present the detailed 3 problems to the user. Prompt the user for approval, edits, or alternatives.
   * **Initialize Registry**: Once the user approves, write the selected path, completion statuses, and the 3 detailed multi-horizon problems into `docs/agent_docs/architecture_docs/path-definition.md`.
3. **If a prior build EXISTS**:
   * Read the path selection, completion status, and the 3 multi-horizon problems from `path-definition.md`.
   * Prompt the user with a suggestion to continue the sequence of the previously chosen path (e.g. "Proceeding with the **Analytical** build next to define diagnostic models for the 3 registered problems").
   * Ensure that the current build focuses on the target horizon's component of the registered 3 problems.

---

## Output Subdirectories

Each build is focused entirely on its own horizon and saves its 15 architectural deliverables in its own subdirectory inside `docs/agent_docs/architecture_docs/`:
* `docs/agent_docs/architecture_docs/operational/` (Daily monitoring, KPIs, exception alert rules)
* `docs/agent_docs/architecture_docs/analytical/` (Data investigations, regressions, clustering, root-cause rules)
* `docs/agent_docs/architecture_docs/strategic/` (Long-term business value, forecasts, portfolio prioritization)

---

## Parallelized Orchestration Graph

To speed up generation, the 13 design phases are grouped into **5 Parallelization Gates** managed by an Orchestrator Agent:

```
                  ┌────────────────────────────────────────┐
                  │   GATE 1: STRATEGIC SCOPE (Seq)        │
                  │   - Phase 1: Business Context          │
                  │   - Phase 2: Use Case Definition       │
                  └───────────────────┬────────────────────┘
                                      │
                   ┌──────────────────┴──────────────────┐
                   │   GATE 2: CONTENT DISCOVERY (Par)   │
                   ├──────────────────┬──────────────────┤
                   │  Subagent A:     │  Subagent B:     │
                   │  Phase 3 (Narr)  │  Phase 4 (Data)  │
                   └──────────────────┬──────────────────┘
                                      │
                  ┌───────────────────┴────────────────────┐
                  │   GATE 3: ANALYTICS FOUNDATION (Seq)   │
                  │   - Phase 5: Capability Assessment     │
                  │   - Phase 6: KPI Catalogue             │
                  │   - Phase 7: Analytics Engine Design   │
                  │   - Phase 8: Intelligence Layer Design │
                  └───────────────────┬────────────────────┘
                                      │
                   ┌──────────────────┴──────────────────┐
                   │   GATE 4: FRONTEND DESIGN (Par)     │
                   ├──────────────────┬──────────────────┤
                   │  Subagent A:     │  Subagent B:     │
                   │  Phase 9 (Deliv) │  Phase 11 (Viz)  │
                   └──────────────────┬──────────────────┘
                                      │
             ┌────────────────────────┼────────────────────────┐
             │       GATE 5: ROADMAPS & STORYTELLING (Par)     │
             ├────────────────────────┼────────────────────────┤
             │  Subagent A:           │  Subagent B:           │  Subagent C:           │
             │  Phase 12 (Tech BP)    │  Phase 12 (Roadmap)    │  Phase 13 (Adoption)   │
             └────────────────────────┴────────────────────────┴────────────────────────┘
```

---

## Reference Files

* [PHASES.md](PHASES.md) — Differentiated 13-phase instructions per layer (Strategic, Operational, Analytical).
* [AGENTS.md](AGENTS.md) — 10 specialist agent definitions and parallel orchestration rules.
* [TEMPLATES.md](TEMPLATES.md) — Layer-specific document templates for all 15 deliverables.
* [TRACEABILITY.md](TRACEABILITY.md) — Cross-horizon connection checks and QA validation rules.
* [VISUALIZATION-GUIDE.md](VISUALIZATION-GUIDE.md) — Cognitive-suitability chart mapping.
* [EXAMPLES.md](EXAMPLES.md) — Sequential worked examples under Path A.
