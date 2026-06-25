# BI Skills Suite

A monorepo containing a suite of business intelligence agent skills designed to facilitate and orchestrate the design of modern, structured, and traceable analytics architectures.

---

## 🚀 Installation

To install skills from this suite directly into your AI agent workspace, run:

```bash
npx skills@latest add EmmanuelEtoabasi/bi-skills
```

Running this command will scan the repository and present you with an interactive selection list where you can select one or both skills to install:

```text
? Select skills to install:
❯ [ ] bi-prompt-builder - Conversational onboarding wizard...
  [ ] bi-solution-architect - Transform business context...
```

---

## 🧩 Included Skills

### 1. `bi-prompt-builder`
An interactive onboarding wizard that interviews users step-by-step to gather context about their business profile, operating model, data infrastructure, and adoption targets. It outputs a fully constructed structural prompt for the Solution Architect.
- **Key Files**: `SKILL.md`, `DEFAULTS.md`
- **Recommended use**: Run this first when starting a new workspace design to generate rich, industry-specific configurations without manual drafting.

### 2. `bi-solution-architect`
A path-based agentic designer that translates a business context prompt into a complete multi-horizon analytics architecture across 13 design phases and 5 parallel gates.
- **Key Files**: `SKILL.md`, `AGENTS.md`, `PHASES.md`, `TEMPLATES.md`, `TRACEABILITY.md`, `VISUALIZATION-GUIDE.md`
- **Recommended use**: Run this next to generate 15 detailed architectural files across your chosen decision horizon (**Strategic**, **Operational**, or **Analytical**).

---

## 🧠 Usage Workflow

For the most cohesive results, we recommend using both skills sequentially:

1. **Step 1 (Prompt Builder)**: Invoke `bi-prompt-builder` to run through the 5-step conversational profile wizard and generate your structured context prompt.
2. **Step 2 (Horizon Architecture)**: Copy the generated prompt output and supply it as input to `bi-solution-architect`.
3. **Step 3 (Deployment)**: Follow the suggested sequence (Path A for Bottom-Up, Path B for Top-Down) and construct each decision horizon one at a time.
