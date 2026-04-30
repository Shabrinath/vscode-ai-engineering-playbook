# VS Code AI Capabilities Guide

## Table of Contents

- [copilot-instructions.md](#1-copilot-instructionsmd)
- [Prompt Files](#2-prompt-files)
- [Skills](#3-skills)
- [Custom Agent](#4-custom-agent)
- [Recommended Folder Structure](#recommended-folder-structure)
- [Beginner Workflow (Simple)](#beginner-workflow-simple)
- [Skill vs Agent (Cost and Benefit)](#skill-vs-agent-cost-and-benefit)
- [Quick Checklist: Finding the Cheapest Reliable Model](#quick-checklist-finding-the-cheapest-reliable-model)
- [Decision Matrix: Prompt File vs Skill vs Agent](#decision-matrix-prompt-file-vs-skill-vs-agent)
  
## Purpose of This Guide

This document explains practical AI capabilities you can use inside VS Code and related coding-agent workflows:

1. `copilot-instructions.md`
2. Prompt files
3. Skills
4. Custom agents

For each capability, you will learn:

- What it is
- How to use it
- Why teams use it

---

## 1) `copilot-instructions.md`

### What it is

A repository-level instruction file (commonly in `.github/copilot-instructions.md`) that defines how AI should behave for this specific project.

### How it is used
 
1. Add project standards, workflow rules, and quality expectations.
2. Define tool or command protocols (for example, skill invocation rules).
3. Keep instructions version-controlled so everyone uses the same AI behavior.

### Why it is used

- Creates consistent AI output across team members.
- Reduces repetitive prompting.
- Enforces project-specific practices (naming, testing, templates, approval steps).

---

## 2) Prompt Files

### What it is

Reusable, task-focused prompt templates stored in files (for example in `.github/prompts/` or `docs/prompts/`).

### How it is used

1. Create prompts for repeatable tasks (bug fix, SQL template generation, test writing, code review).
2. Include clear sections: objective, inputs, constraints, output format.
3. Reuse the same prompt template across issues and contributors.

### Why it is used

- Improves repeatability and quality of AI responses.
- Makes onboarding easier for beginners.
- Saves time by avoiding ad-hoc prompt writing.

---

## 3) Skills

### What it is

A structured automation layer where each skill has its own folder and `SKILL.md` instructions (example: `.github/skills/<skill-name>/SKILL.md`).

### How it is used

1. Define a skill for a specific job (example: generate view templates).
2. Document exact steps, required parameters, and expected output.
3. Invoke the skill by name/command so AI follows the predefined process.

### Why it is used

- Standardizes complex workflows.
- Reduces human error for repetitive engineering tasks.
- Enables scalable process reuse across repositories.

---

## 4) Custom Agent

### What it is

A specialized AI setup (instructions + tools + constraints) tuned for your team’s domain, stack, and governance model.

### How it is used

1. Define role and boundaries (example: data engineering agent, frontend agent, release agent).
2. Connect to approved tools/workflows (lint, tests, templates, CI checks).
3. Enforce quality gates before final output.

### Why it is used

- Produces domain-relevant, higher-precision outcomes.
- Aligns AI behavior with enterprise compliance and standards.
- Improves delivery speed while preserving quality.

---

## Recommended Folder Structure

```text
.github/
  copilot-instructions.md
  prompts/
    generate-sql-template.md
    code-review-checklist.md
  skills/
    generate-view-template/
      SKILL.md
docs/
  VSCode-AI-Capabilities-Guide.md
```

---

## Beginner Workflow (Simple)

1. Start with `copilot-instructions.md` for global rules.
2. Use a prompt file for the specific task.
3. Invoke a skill when the task is standardized.
4. Use a custom agent when domain specialization is needed.

---


## Skill vs Agent (Cost and Benefit)

### Why Skills Are Often More Cost-Effective

- Narrow scope and predefined steps reduce token usage.
- Less back-and-forth interaction is needed.
- Output format is consistent, so less rework is required.

### When Agents Are Better

- Task is complex and changes while executing.
- Multi-step orchestration is needed across files/tools.
- Strong reasoning and adaptation are required.

### Sample Example

**Use Skill (Best Choice):**  
Task: Create a new SQL view YAML + SQL file in your standard template format.  
Why: This is repetitive and rule-based. A skill can enforce exact folder path, naming convention, and template blocks every time.

**Use Agent (Best Choice):**  
Task: Investigate failed deployment pipeline, trace root cause across workflow YAML, SQL files, and test outputs, then propose and implement a fix.  
Why: This requires iterative reasoning, context switching, and adaptive decisions.

### Practical Rule

- If task is repeatable and standardized -> use a **skill**.
- If task is exploratory, cross-functional, or ambiguous -> use an **agent**.

---

## Quick Checklist: Finding the Cheapest Reliable Model

1. Start with a low-cost model for repetitive skill tasks.
2. Validate output using checks (format, schema, lint/tests).
3. Measure first-pass success rate, token usage, and retries.
4. Escalate only failing/complex task types to a stronger model.
5. Keep simple tasks on cheaper models for steady cost savings.
6. Recheck pricing and performance regularly.

---
## Decision Matrix: Prompt File vs Skill vs Agent

| Criteria | Prompt File | Skill | Agent |
|---|---|---|---|
| Best for | Reusable instruction templates | Standardized repeatable workflows | Complex, adaptive, multi-step tasks |
| Task complexity | Low to medium | Low to medium | Medium to high |
| Cost efficiency | High | Very high | Medium to low |
| Speed | Fast | Very fast | Slower |
| Consistency of output | Medium (depends on usage) | High (enforced structure) | Medium to high (depends on controls) |
| Setup effort | Low | Medium | High |
| Flexibility | High | Medium | Very high |
| Governance/control | Medium | High | High (with strong guardrails) |
| Beginner friendliness | High | High | Medium |
| Typical example | Code review prompt template | `/generate-view-template` scaffold generation | Root-cause analysis + fix across workflows/files |

### Recommended Choice by Situation

- Use **Prompt File** when you need lightweight reusable guidance.
- Use **Skill** when the workflow is repetitive and must be consistent.
- Use **Agent** when the task requires deep reasoning and adaptation.

### Mini Example

- `Generate standard SQL/view template` -> low-cost model.
- `Debug deployment failure across workflow + SQL + tests` -> stronger model.

