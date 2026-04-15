---
name: mvp-scope-planner
description: Use when the user needs to turn approved initiation findings into a narrow MVP feature list. Best for deciding what the MVP must solve, who it serves, what must be built first, what must not be built, and how the MVP will be validated after launch.
---

# MVP Scope Planner

## Overview

Use this skill to compress prior findings into a focused MVP. This stage is about subtraction, not expansion.

## When To Use

Use this skill when the user asks to:

- create an MVP feature list
- narrow scope after initiation review
- decide what the first version should and should not include
- define success metrics and first experiments
- run the final stage of the startup workflow

## Required Inputs

Read:

- `docs/product-workflow/00-workflow-status.md`
- all prior stage Markdown files
- all prior stage YAML summaries

Write to:

- `docs/product-workflow/07-mvp-scope-planner.md`
- `docs/product-workflow/summaries/07-mvp-scope-planner.yaml`

## Workflow

1. Read the entire upstream workflow.
2. Name the single core problem the MVP will solve.
3. Define in-scope users and out-of-scope users.
4. Derive a minimal must-have feature set.
5. Write a clear `should not build` list.
6. Define success metrics and first experiment steps.
7. Produce the stage document and summary.
8. Set one final decision and update workflow status.
9. Stop and wait for confirmation.

## What This Stage Must Answer

- What exact problem does the MVP solve?
- Who is in scope and out of scope?
- What must be built for v1?
- What should not be built yet?
- How will success be measured?
- What first experiment should follow launch?
- What options remain for phase 2?

## Scope Lens

Default toward the smallest useful scope that preserves the core hypothesis.

Prefer:

- one clear user
- one core scenario
- one primary job to be done
- a short must-have list

Reject ornamental features unless they are necessary for validation.

## Markdown Output Contract

The stage Markdown should contain:

- `Inherited Context`
- `This Stage Judgment`
- `MVP Goal`
- `Target User`
- `Core Scenario`
- `Core Problem`
- `Must-Have Features`
- `Should Not Build`
- `Success Metrics`
- `Experiment Plan`
- `Next Phase Options`
- `Decision`
- `Next Action`

Prepend this frontmatter:

```yaml
stage: mvp-scope-planner
version: 1
depends_on:
  - 01-opportunity-framer.md
  - 02-user-research-planner.md
  - 03-evidence-and-insight-reviewer.md
  - 04-ai-fit-and-experience-reviewer.md
  - 05-market-and-strategy-reviewer.md
  - 06-business-and-risk-reviewer.md
status: go|revise|stop
last_updated: YYYY-MM-DD
```

## YAML Summary Contract

```yaml
stage: mvp-scope-planner
decision: go|revise|stop
mvp_goal: ""
target_user: ""
core_scenario: ""
core_problem: ""
must_have_features: []
should_not_build: []
success_metrics: []
experiment_plan: []
next_phase_options: []
revision_advice: []
```

## Decision Rules

- `go`: the MVP is focused enough to build and test
- `revise`: the MVP still carries too much scope or unclear validation logic
- `stop`: the workflow has not produced a coherent MVP worth building

## Guardrails

- Do not sneak in phase 2 features.
- Do not produce a broad PRD here.
- Do not pass the stage without a concrete `should not build` list.
