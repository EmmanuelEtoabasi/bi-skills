---
name: bi-prompt-builder
description: Conversational onboarding wizard that dynamically generates industry-specific business and technology defaults to help users compile a rich-context BI solution architecture prompt.
---

# BI Solution Architect Prompt Builder

This skill provides an interactive onboarding wizard to collect user context. Instead of requiring the user to fill out a large configuration manually, this skill interviews the user step-by-step, generating smart, industry-specific defaults that adapt dynamically as they provide incremental inputs.

---

## Startup Protocol (Dynamic Inference Engine)

When called, the agent executes the following 5-step conversation wizard, presenting pre-filled defaults at each step based on the accumulated context.

### Step 1: Industry Seed Lookup
*   **Prompt**: *"Welcome to the BI Solution Architect wizard! To help us design a tailored analytics solution, let's start with your company profile. What is your **Company Name** and **Industry Sector** (e.g., Renewable Energy, Retail, Logistics, SaaS)?"*
*   **Action**: Once the user replies, scan [DEFAULTS.md](DEFAULTS.md) for a matching sector. If no match is found, fallback to the *Generic / Default Template*.

### Step 2: Profile & Operating Model Defaults
*   **Logic**: Read the matched template's **Operating Model**, **Revenue Mix**, and **Scale**.
*   **Prompt**: 
    *"Thanks! Based on the [Industry] sector, I have drafted these defaults for your business profile:
    
    *   **Operating Model**: [Template's Operating Model]
    *   **Revenue Mix**: [Template's Revenue Mix]
    *   **Scale**: [Template's Scale]
    
    Type **'ok'** to accept these, or specify any adjustments (e.g., 'our revenue mix is 50% retail and 50% services')."*

### Step 3: Path & Horizon Directives
*   **Logic**: Read the template's **Path Choice** and **Active Horizon Build**.
*   **Prompt**:
    *"Great. Next, let's define our development path and the starting point for this build. Based on your profile, I recommend:
    
    *   **Path Choice**: [Template's Path Choice]
    *   **Active Horizon Build**: [Template's Active Horizon Build]
    
    Would you like to proceed with this sequence? (Type **'ok'** to proceed, or specify if you want to switch pathways or start with a different horizon)."*

### Step 4: Infrastructure & Tech Stack Defaults
*   **Logic**: Read the template's **Data Sources** and **Target Analytics Stack**.
*   **Prompt**:
    *"Now, let's map your data systems and target technologies. I suggest the following:
    
    *   **Data Sources**: [Template's Data Sources]
    *   **Target Analytics Stack**: [Template's Target Analytics Stack]
    
    Type **'ok'** to accept, or list your active data sources and preferred stack."*

### Step 5: Audience & Adoption Goals
*   **Logic**: Read the template's **Decision Makers** and **Adoption Goals**.
*   **Prompt**:
    *"Finally, who will be using the dashboards, and what are the main adoption goals?
    
    *   **Decision Makers**: [Template's Decision Makers]
    *   **Adoption Goals**: [Template's Adoption Goals]
    
    Type **'ok'** to accept, or customize the roles and goals."*

---

## Assembly & Return Protocol

Once all 5 steps are completed, the agent must compile the answers into the structured model prompt format shown below and return it to the parent `/bi-solution-architect` Orchestrator to start the design loop:

```markdown
/bi-solution-architect

I want to build a complete analytics solution architecture. Here is my business context and requirements:

### 1. Business Profile & Operating Model
*   **Company Name & Industry**: [User's Company Name] - [User's Industry]
*   **Operating Model**: [Confirmed Operating Model]
*   **Revenue Mix**: [Confirmed Revenue Mix]
*   **Scale**: [Confirmed Scale]

### 2. Path & Horizon Directives
*   **Path Choice**: [Confirmed Path Choice]
*   **Active Horizon Build**: [Confirmed Active Horizon Build]
*   **Serial Integration**: Set up the global `path-definition.md` registry.

### 3. Data & Technology Infrastructure
*   **Data Sources**: [Confirmed Data Sources]
*   **Target Analytics Stack**: [Confirmed Target Analytics Stack]

### 4. Target Audience & Key Roles
*   **Decision Makers**: [Confirmed Decision Makers]
*   **Adoption Goals**: [Confirmed Adoption Goals]

### 5. Core Business Problems
*   **Problems**: I have not defined the index business problems. Please analyze my business profile and select a minimum of 3 highly relevant multi-horizon business problems with operational, analytical, and strategic components and simulated data markers.
*   **Verification Gate**: Present these 3 problems for my approval before starting parallel writing.
```
