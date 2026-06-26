---
title: Problem Formulation Framework
purpose: Defines the Adoption Maximizer criteria, 6-tier structure, and critique rubrics used by bi-problem-formulator to generate and evaluate business problems.
---

# Problem Formulation Framework

This document defines the reasoning framework, tier structure, and evaluation rubrics that govern how the `bi-problem-formulator` skill generates, critiques, and refines business problems for BI/BA adoption.

---

## 1. The Adoption Maximizer Principle

BI adoption in a small-to-medium business is driven by three forces. Every candidate problem must satisfy **all three** to be viable:

### Force 1: Felt Daily
The person who opens the dashboard needs it **today**, not quarterly. The problem must create a daily or weekly habit of checking the system. If the user can ignore the dashboard for a week without consequences, the problem is too weak.

**Test question**: *"Would the Store Manager / Owner / Buyer open this dashboard every morning or evening without being told to?"*

### Force 2: Data Already Exists
The data to solve the problem must already exist in some form — even if messy (POS receipts, bank transfer alerts, WhatsApp threads, handwritten notebooks, Excel sheets). Problems that require significant new data infrastructure investment (IoT sensors, GPS fleet tracking, custom apps) before a single dashboard can go live are **adoption killers**. The business owner will wait weeks for setup, lose interest, and the project stalls.

**Test question**: *"Can we build the first version of this dashboard using data the business already generates today — even if we need to digitize it?"*

### Force 3: Replaces Something They Already Hate Doing
The problem must map to an existing manual process that causes real pain — manual cash counting, mental arithmetic, chasing debtors in a notebook, guessing procurement quantities. The dashboard must be **faster and easier** than the current method. If the dashboard adds work rather than replacing it, adoption fails.

**Test question**: *"What specific manual task does this dashboard eliminate? Can the user name it?"*

---

## 2. The 6-Tier Problem Structure

Every engagement produces exactly **6 problems**, structured into 4 tiers. The tiers are sequential — each tier builds on the data infrastructure and organizational habits created by the previous tier.

### Tier 1–3: Foundation Problems (The Daily Habit Layer)

**Goal**: Create a daily rhythm of dashboard usage using data that already exists.

**Quantity**: Exactly 3 problems.

**Selection Criteria**:
- All three Adoption Maximizer forces must be satisfied (felt daily, data exists, replaces manual work)
- Together, the 3 problems should form a natural **daily operating rhythm** (e.g., morning procurement check, evening cash reconciliation, weekly debt review)
- Each problem should capture a different **data dimension** of the business (e.g., revenue/sales, costs/procurement, customers/credit)
- Time-to-first-dashboard must be **days to 1–2 weeks**, not months

**Anti-patterns to reject**:
- Problems requiring new hardware (sensors, GPS, tablets) before any dashboard can go live
- Problems that sound impressive but are checked monthly, not daily
- Problems where the primary user is hypothetical ("the data analyst we'll hire someday")

**Analytics type**: Descriptive + Comparative ("What happened today? How does it compare?")

---

### Tier 4: Compound Value Problem (The Diagnostic Leap)

**Goal**: Demonstrate that solving Problems 1–3 has quietly built a data foundation that makes a 4th, more powerful capability almost free to unlock.

**Quantity**: Exactly 1 problem.

**Selection Criteria**:
- Must consume data from **at least 2** of the 3 foundation problem pipelines
- Must require exactly **1 small additional data capture investment** (e.g., a tablet at the cold room, a daily stock count, a simple form) — not zero (that would make it feel trivial) and not many (that would break the "hand's breadth away" narrative)
- Must produce a **"wow" insight** that was previously invisible — something the owner thought they knew but discover they were wrong about
- Must answer a question that connects previously siloed data (e.g., "Am I actually making money on this product after accounting for cost + credit + waste?")

**The narrative frame**: *"You already have 3 of the 4 inputs flowing. Adding one simple data point completes the picture and reveals something you've never seen before."*

**Analytics type**: Diagnostic ("Why is this happening? Where are we really making/losing money?")

**Required output elements**:
- A clear diagram showing which data streams from Problems 1–3 feed into Problem 4
- The single new data capture point required
- The exact "aha!" calculation or insight with a concrete example using plausible numbers
- A "what's needed" table showing what's already built vs. what's new

---

### Tier 5: Near-Future Problem (The Predictive Leap)

**Goal**: Demonstrate BI's ability to look forward, not just backward. This is the first time the system predicts the future.

**Quantity**: Exactly 1 problem.

**Selection Criteria**:
- Must cross the boundary from descriptive/diagnostic analytics into **predictive + prescriptive** analytics
- Must use data from **all prior problems** (1–4) simultaneously, proving that the investment compounds
- Must solve the owner's **most emotionally charged anxiety** — the thing they worry about lying in bed at night (typically: "Will I have enough cash to pay suppliers and salaries?")
- Must require a **modest additional investment** (e.g., bank balance feed, fixed cost schedule) that is clearly smaller than the value it unlocks
- Must include a **novel delivery mechanism** that meets the user where they already are (e.g., WhatsApp morning briefing, SMS alert) — not just another dashboard to log into
- Must contain a **"what-if" element** — the ability to simulate scenarios (e.g., "What if Customer X pays this week?")

**The narrative frame**: *"Problems 1–4 told you what happened and why. Problem 5 tells you what WILL happen — and what to do about it."*

**Analytics type**: Predictive + Prescriptive ("What will happen? What should I do?")

**Required output elements**:
- Clear mapping of how every prior problem's data feeds into the prediction model
- The specific prescriptive actions the system generates (each referencing a specific prior problem's data)
- The delivery mechanism design (e.g., WhatsApp briefing format)
- A composite score or index that summarizes business health in a single number

---

### Tier 6: Long-Term Vision Problem (The Autonomous Leap)

**Goal**: Demonstrate the medium-to-long-term transformative potential of BI/BA — the system begins to act on its own.

**Quantity**: Exactly 1 problem.

**Selection Criteria**:
- Must introduce **external data signals** for the first time — the system looks outside the business (weather, calendar events, market prices, population movements, competitor signals)
- Must include **decision autonomy** — the system is allowed to act (not just advise) on low-stakes decisions, while requesting approval for high-stakes ones
- Must include a **learning loop** — the system tracks the accuracy of its own predictions and improves over time
- Must clearly define **two tiers of autonomy**: fully autonomous (low stakes) and human-approved (high stakes), with concrete examples of each
- Must demonstrate how the owner's role evolves from **operator** to **governor** — they oversee the system rather than doing the work
- Must include a compelling **side-by-side demo scenario** showing the same business event handled with vs. without the system

**The narrative frame**: *"The business handles routine disruptions on its own, freeing the owner to think about growth instead of daily firefighting."*

**Analytics type**: Autonomous + Adaptive ("The system senses, decides, acts, and learns.")

**Required output elements**:
- External signals table (source, what it tells the system, business impact)
- Tier 1 autonomous actions (low stakes — system acts)
- Tier 2 human-approved actions (high stakes — system recommends, owner approves)
- Learning loop diagram (Sense → Predict → Decide → Act → Measure → feedback)
- Side-by-side scenario comparison (with vs. without the system)
- Additional investment table (what, when, estimated cost)

---

## 3. Critique Rubric

After generating candidate problems at each tier, evaluate them against this rubric. A problem must score **green on all mandatory criteria** to pass.

### Foundation Problems (Tiers 1–3)

| Criterion | 🟢 Pass | 🔴 Fail | Mandatory? |
|-----------|---------|---------|------------|
| **Data readiness** | Works with data that exists today (receipts, bank alerts, notebooks) | Requires new infrastructure (sensors, GPS, apps) before any dashboard | ✅ Yes |
| **Daily usage pull** | Primary user would check this every day/evening | Checked monthly or quarterly | ✅ Yes |
| **Time to first dashboard** | Days to 1–2 weeks | Weeks to months (data capture setup needed) | ✅ Yes |
| **Emotional impact** | "We're losing money RIGHT NOW" | "We should track this someday" | ✅ Yes |
| **Who opens it** | A real person who already exists in the business | A hypothetical future hire | ✅ Yes |
| **Replaces manual work** | Eliminates a specific named manual process | Adds a new process on top of existing ones | ✅ Yes |

### Compound Value Problem (Tier 4)

| Criterion | 🟢 Pass | 🔴 Fail | Mandatory? |
|-----------|---------|---------|------------|
| **Uses prior pipelines** | Consumes data from ≥2 foundation problems | Only uses data from 1 prior problem | ✅ Yes |
| **Single new investment** | Requires exactly 1 new, small data capture point | Requires zero (too easy) or many (too hard) new inputs | ✅ Yes |
| **"Wow" insight** | Reveals something the owner thought they knew but were wrong about | Confirms what they already suspected | ✅ Yes |
| **Connects silos** | Joins previously separate data dimensions | Deepens analysis within one dimension | ✅ Yes |

### Near-Future Problem (Tier 5)

| Criterion | 🟢 Pass | 🔴 Fail | Mandatory? |
|-----------|---------|---------|------------|
| **Predictive** | Looks forward in time (forecasts, projections) | Only looks backward (historical analysis) | ✅ Yes |
| **Uses all prior data** | Consumes data from all Problems 1–4 | Only uses a subset of prior data | ✅ Yes |
| **Emotional resonance** | Solves the owner's deepest daily anxiety | Solves a nice-to-have optimization | ✅ Yes |
| **Novel delivery** | Meets the user where they already are (WhatsApp, SMS) | Requires logging into a new platform | ⬜ Recommended |
| **Scenario simulation** | Includes "what-if" capability | Only shows a single forecast | ⬜ Recommended |

### Long-Term Vision Problem (Tier 6)

| Criterion | 🟢 Pass | 🔴 Fail | Mandatory? |
|-----------|---------|---------|------------|
| **External signals** | Integrates data from outside the business | Only uses internal data | ✅ Yes |
| **Decision autonomy** | System can act on low-stakes decisions without human input | System only advises | ✅ Yes |
| **Learning loop** | System tracks and improves its own prediction accuracy | Static rules that never improve | ✅ Yes |
| **Two-tier autonomy** | Clearly separates autonomous vs. human-approved decisions | All-or-nothing autonomy | ✅ Yes |
| **Compelling demo** | Side-by-side scenario showing with vs. without the system | Abstract description only | ✅ Yes |

---

## 4. Layer Decomposition Rules

After all 6 problems are locked, decompose them into the 3 decision horizon layers for the `bi-solution-architect`:

### Layer Definitions

| Layer | Core Question | Time Horizon | Primary Users | KPI Suffix |
|-------|--------------|--------------|---------------|------------|
| **Operational** | "How are we performing today?" | Short-term (daily) | Managers, Operations Teams | `-OP-` |
| **Analytical** | "Why is this happening?" | Any horizon (diagnostic) | Analysts, Managers | `-ANA-` |
| **Strategic** | "Where should we go?" | Long-term (forward-looking) | Executives, Owner | `-STR-` |

### Decomposition Protocol

1. **Identify the primary layer** for each problem based on its centre of gravity.
2. **Split problems across layers** where necessary — a problem's data capture may be Operational while its diagnostic analysis is Analytical.
3. **Map cross-horizon data flows** — show exactly which operational KPIs feed into analytical engines, and which analytical findings feed into strategic models.
4. **Verify upward data flow** — data must flow strictly upward: Operational (captures) → Analytical (diagnoses) → Strategic (predicts + acts). No layer should duplicate another layer's work.

### Expected Mapping Pattern

The 6-tier structure typically maps to layers as follows (adapt based on industry):

| Tier | Problems | Typical Primary Layer |
|------|----------|----------------------|
| Foundation (1–3) | Daily monitoring & tracking | **Operational** (data capture + daily dashboards) |
| Compound (4) | Diagnostic "why" analysis | **Analytical** (connects operational data streams) |
| Near-Future (5) | Predictive forecasting | **Strategic** (forward-looking projections) |
| Long-Term (6) | Autonomous intelligence | **Strategic** (adaptive decision-making) |

Note: Foundation problems 2 and 3 often **split** across Operational (data capture) and Analytical (comparative/diagnostic analysis). This is expected and should be documented clearly in the layer decomposition table.
