---
name: bi-problem-formulator
description: >-
  Generate exactly 6 adoption-optimized, multi-horizon business problems
  from a compiled business profile. Uses a 6-tier structure
  (3 foundation, 1 compound, 1 near-future, 1 long-term) with
  interactive per-tier critique and user approval. Output feeds directly
  into the bi-solution-architect skill for layered architecting.
---

# BI Problem Formulator

## Overview

This skill takes a compiled business profile (from `bi-prompt-builder`) and produces exactly **6 business problems** structured into a 4-tier adoption hierarchy. Each problem is designed to maximize BI/BA adoption by creating daily dashboard habits, proving compounding data value, and demonstrating progressive analytics maturity — from descriptive monitoring through autonomous intelligence.

The output is consumed by `bi-solution-architect` to populate the path registry and drive the 15-deliverable architecture builds per decision horizon layer.

## Dependencies

| Skill | Relationship | Purpose |
|-------|-------------|---------|
| `bi-prompt-builder` | **Upstream** | Provides the compiled business profile: company name, industry, operating model, revenue mix, scale, data sources, target stack, decision makers, adoption goals. If the profile is missing or incomplete, invoke this skill first. |
| `bi-solution-architect` | **Downstream** | Consumes the 6-problem output, layer decomposition, and data markers. Writes them into `path-definition.md` and uses them to drive architecture builds. |

## Quick Start

This skill is invoked automatically by `bi-solution-architect` during Phase 1 (Business Context Definition) when the user has not explicitly defined business problems. It can also be invoked directly:

```
/bi-problem-formulator

Business Profile:
- Company: [Name]
- Industry: [Sector]
- Operating Model: [Description]
- Revenue Mix: [Breakdown]
- Scale: [Size]
- Data Sources: [List]
- Target Stack: [Technologies]
- Decision Makers: [Roles]
- Adoption Goals: [Goals]
```

## Workflow

### Phase 0: Input Validation

1. Check if the business profile contains all required fields:
   - Company Name & Industry
   - Operating Model
   - Revenue Mix
   - Scale (employees, locations)
   - Data Sources (current systems)
   - Target Analytics Stack
   - Decision Makers (by level)
   - Adoption Goals
2. **If any field is missing**: Invoke `bi-prompt-builder` to gather the missing context before proceeding.
3. **If all fields are present**: Proceed to Phase 1.

---

### Phase 1: Foundation Problems (Tier 1–3)

**Objective**: Generate 3 problems that create a daily dashboard habit using data that already exists in the business.

#### Step 1.1: Generate Candidates

Analyze the business profile and generate 3 candidate foundation problems. Apply the **Adoption Maximizer Principle** from [FRAMEWORK.md](FRAMEWORK.md) as a generation filter:

1. **Felt daily** — the person who opens the dashboard needs it today, not quarterly.
2. **Data already exists** — even if messy (POS receipts, bank alerts, WhatsApp threads, notebooks). It must NOT require significant data infrastructure investment before a single dashboard can go live — otherwise the business owner will wait weeks for sensors and apps to be set up, lose interest, and the project stalls.
3. **Replaces something they already hate doing** — manual cash counting, mental arithmetic, chasing debtors.

Each problem should capture a different **data dimension** of the business. Together, the 3 problems should form a natural **daily operating rhythm** (e.g., morning check, evening reconciliation, weekly review).

#### Step 1.2: Critique Candidates

Evaluate each candidate against the **Foundation Critique Rubric** from [FRAMEWORK.md](FRAMEWORK.md):

| Criterion | Test |
|-----------|------|
| Data readiness | Works with data that exists today? |
| Daily usage pull | Primary user would check every day? |
| Time to first dashboard | Days to 1–2 weeks (not months)? |
| Emotional impact | "We're losing money RIGHT NOW" (not "we should track this")? |
| Who opens it | A real person who already exists in the business? |
| Replaces manual work | Eliminates a specific named manual process? |

If any candidate fails a mandatory criterion, replace it and re-critique.

#### Step 1.3: Present with Critique Results

Present the 3 foundation problems to the user. For each problem, show:
- Problem title and description
- Which data sources it uses (must already exist)
- The daily/weekly rhythm it creates
- The critique rubric results (all green)
- A side-by-side comparison table if "obvious" problems were rejected:

| Criteria | Rejected Problems | Proposed Problems |
|----------|------------------|-------------------|
| Data readiness | Requires new infrastructure | Works with existing data |
| Daily usage pull | Medium | Very high |
| Time to first dashboard | Weeks to months | Days to 1–2 weeks |
| Emotional impact | "We should track this" | "We're losing money RIGHT NOW" |

#### Step 1.4: Discuss & Lock

Allow the user to accept, edit, or replace any of the 3 problems. Once confirmed, lock Tier 1–3 and proceed.

---

### Phase 2: Compound Value Problem (Tier 4)

**Objective**: Identify a 4th problem that becomes trivially solvable because Problems 1–3 built the data pipes — requiring only one small additional data capture investment.

#### Step 2.1: Map Existing Data Infrastructure

Analyze what data pipelines Problems 1–3 have created. Produce a table:

| Problem | Data Assets Now Flowing |
|---------|------------------------|
| P1 | [e.g., daily revenue by product, payment methods] |
| P2 | [e.g., procurement costs by supplier, delivery records] |
| P3 | [e.g., customer ledger, payment history, aging] |

#### Step 2.2: Identify the Gap

Find the single missing data dimension that, when added, connects all three data streams into a new diagnostic capability. The gap should be:
- **One data capture point** — not zero (too easy) and not many (too hard)
- **Cheap to implement** — a tablet, a form, a daily count
- **Connecting previously siloed data** — revenue + cost + credit + [gap] = complete picture

#### Step 2.3: Generate the Problem

Frame the problem using the **"hand's breadth away"** narrative:
- Show what data already flows (from P1–P3)
- Show the single missing input
- Show the powerful insight that becomes possible when the gap is filled
- Include a concrete "aha!" example with plausible numbers (a table showing the surprising result)

#### Step 2.4: Critique Against Tier 4 Rubric

Evaluate against the **Compound Value Critique Rubric** from [FRAMEWORK.md](FRAMEWORK.md):
- Uses ≥2 prior data streams? ✅
- Requires exactly 1 new data capture point? ✅
- Produces a "wow" insight the owner was wrong about? ✅
- Connects previously separate data dimensions? ✅

#### Step 2.5: Present → Discuss → Lock

Present with:
- The data infrastructure map (what's built vs. what's new)
- The "aha!" moment with example numbers
- A "what's needed" checklist (mostly ✅, one ❌)

---

### Phase 3: Near-Future Problem (Tier 5)

**Objective**: Propose a predictive + prescriptive problem that moves from "what happened" to "what will happen and what should I do."

#### Step 3.1: Map the Complete Data Model

Show the full data model built by Problems 1–4:
- Revenue data (P1)
- Cost data (P2)
- Customer/credit data (P3)
- Inventory/waste data (P4)

#### Step 3.2: Identify the Owner's Deepest Anxiety

The near-future problem should solve the single most emotionally charged question the owner faces. For most small businesses, this is a cash flow question: *"Will I have enough money to pay my obligations?"*

Analyze the business profile to identify this question. Consider:
- Fixed obligations (rent, salaries, supplier payments)
- Variable income (fluctuating daily sales)
- Credit exposure (receivables timing uncertainty)

#### Step 3.3: Generate the Problem

The problem must:
- **Look forward in time** (14-day projection minimum)
- **Consume data from ALL prior problems** (P1–P4)
- **Generate prescriptive actions** — each action must reference a specific prior problem's data
- **Include a novel delivery mechanism** (WhatsApp briefing, SMS, automated notification)
- **Include a composite score** summarizing business health in one number
- **Include a "what-if" element** for scenario simulation

#### Step 3.4: Critique Against Tier 5 Rubric

Evaluate against the **Near-Future Critique Rubric** from [FRAMEWORK.md](FRAMEWORK.md).

#### Step 3.5: Present → Discuss → Lock

Present with:
- Data flow diagram showing all prior problems feeding into the prediction
- Example prescriptive actions (each citing a specific prior problem)
- Mock-up of the delivery mechanism (e.g., WhatsApp message format)
- The health score formula with component weights

---

### Phase 4: Long-Term Vision Problem (Tier 6)

**Objective**: Demonstrate the medium-to-long-term transformative potential of BI/BA — the system begins to sense, decide, and act.

#### Step 4.1: Map the Analytics Maturity Achieved

Show the progression: Descriptive → Diagnostic → Predictive. The 6th problem must land on the next rung: **Autonomous + Adaptive**.

#### Step 4.2: Identify Relevant External Signals

Analyze the business profile and industry to identify external data sources that would give the system "peripheral vision":
- Weather (impacts foot traffic, delivery, spoilage)
- Cultural/religious calendar (demand spikes)
- Local events (university calendars, market days)
- Market price feeds (supplier pricing intelligence)
- Infrastructure status (power grid, road conditions)

#### Step 4.3: Generate the Problem

The problem must include:
- **External signal integration** table (source, insight, impact)
- **Two tiers of autonomy**: fully autonomous (low stakes) and human-approved (high stakes) with concrete examples of each
- **A learning loop** diagram (Sense → Predict → Decide → Act → Measure → feedback)
- **A side-by-side demo scenario** showing the same business event handled with vs. without the system
- **An investment timeline** table (what, cost, when)

#### Step 4.4: Critique Against Tier 6 Rubric

Evaluate against the **Long-Term Vision Critique Rubric** from [FRAMEWORK.md](FRAMEWORK.md).

#### Step 4.5: Present → Discuss → Lock

Present with the side-by-side scenario as the headline — this is the "bold demo moment."

---

### Phase 5: Layer Decomposition & Output Assembly

**Objective**: Decompose all 6 problems into the 3 decision horizon layers and produce the 4 required output artifacts.

#### Step 5.1: Layer Decomposition

Assign each problem (or problem-component) to its primary build layer using the **Layer Decomposition Rules** from [FRAMEWORK.md](FRAMEWORK.md):

| Layer | Core Question | Typical Problems |
|-------|---------------|-----------------|
| **Operational** | "How are we performing today?" | Foundation P1–P3 (data capture + monitoring) |
| **Analytical** | "Why is this happening?" | Compound P4 + analytical components of P2, P3 |
| **Strategic** | "Where should we go?" | Near-Future P5 + Long-Term P6 |

Where a problem spans two layers, split it explicitly:
- `P[N]-OP` = Operational component (data capture, daily monitoring)
- `P[N]-ANA` = Analytical component (diagnostics, scoring, comparison)

#### Step 5.2: Assemble All 4 Output Artifacts

Produce all outputs defined in [OUTPUT-TEMPLATE.md](OUTPUT-TEMPLATE.md):

1. **Problem Registry** — Full details for all 6 problems
2. **Cumulative Data Infrastructure Map** — Mermaid diagram + data assets table
3. **Layer Decomposition Table** — 3-build assignment with KPIs and cross-horizon references
4. **Analytics Maturity Staircase** — Progression summary table

#### Step 5.3: Final User Approval

Present the complete assembled output to the user. Upon approval, format the output using the **Handoff Format** from [OUTPUT-TEMPLATE.md](OUTPUT-TEMPLATE.md) and pass to `bi-solution-architect`.

---

## Common Mistakes

1. **Proposing problems that need new infrastructure for foundation tier** — The most common error. Foundation problems MUST work with data that already exists. If the problem requires buying sensors, building apps, or installing GPS trackers before a dashboard can go live, it will kill adoption. Always validate against Force 2 of the Adoption Maximizer.

2. **Generating all 6 problems in isolation** — Each tier must explicitly build on the data infrastructure created by previous tiers. Problem 4 must consume data from P1–P3. Problem 5 must consume data from P1–P4. If a problem doesn't reference prior problems, it's not demonstrating the compounding value of BI investment.

3. **Making the "aha!" moments abstract** — Every "aha!" moment must include **concrete numbers** in the business's local currency and context. "Margins are lower than expected" is weak. "I keep only ₦51K on ₦480K of chicken sales after spoilage and unpaid credit" is powerful. Always use plausible, industry-appropriate example numbers.

## Reference Files

* [FRAMEWORK.md](FRAMEWORK.md) — Adoption Maximizer criteria, tier definitions, and critique rubrics.
* [OUTPUT-TEMPLATE.md](OUTPUT-TEMPLATE.md) — Required output structure and handoff format for `bi-solution-architect`.
* [EXAMPLES.md](EXAMPLES.md) — Complete worked example (Farmborg Foods, Ibadan, Nigeria).
