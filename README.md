# BI Skills Suite

A monorepo containing a suite of business intelligence agent skills designed to facilitate and orchestrate the design of modern, structured, and traceable analytics architectures.

---

## 🚀 Installation

To install skills from this suite directly into your AI agent workspace, run:

```bash
npx skills@latest add EmmanuelEtoabasi/bi-skills
```

Running this command will scan the repository and present you with an interactive selection list where you can select one or more skills to install:

```text
? Select skills to install:
❯ [ ] bi-prompt-builder - Conversational onboarding wizard...
  [ ] bi-problem-formulator - Generate exactly 6 adoption-optimized...
  [ ] bi-data-simulator-designer - Design data simulation specs...
  [ ] bi-solution-architect - Transform business context...
```

---

## 🧩 Included Skills

### 1. `bi-prompt-builder`
An interactive onboarding wizard that interviews users step-by-step to gather context about their business profile, operating model, data infrastructure, and adoption targets. It outputs a fully constructed structural prompt for downstream skills.
- **Key Files**: `SKILL.md`, `DEFAULTS.md`
- **Recommended use**: Run this first when starting a new workspace design to generate rich, industry-specific configurations without manual drafting.

### 2. `bi-problem-formulator`
An analytical formulator that generates exactly 6 adoption-optimized, multi-horizon business problems structured in a 4-tier hierarchy. Evaluates each problem against a strict daily-usage and readiness rubric.
- **Key Files**: `SKILL.md`, `FRAMEWORK.md`, `OUTPUT-TEMPLATE.md`, `EXAMPLES.md`
- **Recommended use**: Use this to structure key business focus areas between context gathering and architectural design.

### 3. `bi-data-simulator-designer`
A simulator designer that designs structured data simulation rules, math formulations, date ranges, and inflection points representing business anomalies, seasonal trends, and operational failures.
- **Key Files**: `SKILL.md`, `FRAMEWORK.md`, `OUTPUT-TEMPLATE.md`, `EXAMPLES.md`
- **Recommended use**: Use this to map out simulated datasets and target schemas so downstream analytics engines and dashboards have reliable mock data metrics.

### 4. `bi-solution-architect`
A path-based agentic designer that translates a business context prompt and business problems into a complete multi-horizon analytics architecture across 13 design phases and 5 parallel gates.
- **Key Files**: `SKILL.md`, `AGENTS.md`, `PHASES.md`, `TEMPLATES.md`, `TRACEABILITY.md`, `VISUALIZATION-GUIDE.md`
- **Recommended use**: Run this to generate 15 detailed architectural files across your chosen decision horizon (**Strategic**, **Operational**, or **Analytical**).

---

## 🧠 Usage Workflow

For the most cohesive results, we recommend using these skills sequentially:

1. **Step 1 (Prompt Builder)**: Invoke `bi-prompt-builder` to run through the 5-step conversational profile wizard and generate your structured context profile.
2. **Step 2 (Problem Formulation)**: Pass the profile into `bi-problem-formulator` to generate exactly 6 highly prioritized business problems structured for maximum user adoption.
3. **Step 3 (Data Simulation Design)**: Use `bi-data-simulator-designer` to compile mock data generation specs, date ranges, and mathematical inflection formulas based on the problems and tech stack.
4. **Step 4 (Horizon Architecture)**: Supply the formulated profile, problems, and simulation rules to `bi-solution-architect` to build the comprehensive analytics architecture gate by gate.


