---
name: opportunity-framer
description: Use when the user needs to turn a vague product idea into a testable opportunity definition for the first stage of the startup initiation workflow. Best for clarifying target users, scenarios, problems, current alternatives, opportunity hypotheses, and boundaries before deeper evidence or strategy review.
---

# Opportunity Framer

## Overview

Use this skill to convert a rough product idea into a disciplined opportunity definition. The output is not a feature plan. It is a problem-space handoff that later stages can test.

## When To Use

Use this skill when the user asks to:

- frame or narrow a product idea
- define the target user or core scenario
- clarify the real problem behind an idea
- turn a concept into a testable opportunity
- start stage 1 of the startup workflow

## Required Inputs

Read these files first if they exist:

- `docs/product-workflow/00-workflow-status.md`
- any existing notes the user points to

Write to:

- `docs/product-workflow/01-opportunity-framer.md`
- `docs/product-workflow/summaries/01-opportunity-framer.yaml`

## Workflow

1. Read the current workflow status.
2. Gather only the missing context required to define the opportunity.
3. Push the user away from features and toward users, scenarios, problems, and alternatives.
4. Distinguish explicit evidence from assumptions.
5. Produce the stage document and summary.
6. Set one final decision: `go`, `revise`, or `stop`.
7. Update the status file and stop.

## What This Stage Must Answer

- Who is the primary target user?
- How can that user be screened in the real world?
- What is the recurring scenario?
- What trigger starts the scenario?
- What is the user's real problem?
- What alternatives exist today?
- What is the opportunity hypothesis?
- What is explicitly out of scope?

## Questioning Style

- Ask only for missing information.
- Prefer concrete prompts over abstract brainstorming.
- Pull toward recent behavior, not generic preferences.
- If the user is underspecified, make labeled assumptions rather than blocking.

## Markdown Output Contract

The stage Markdown should contain:

- `Inherited Context`
- `This Stage Judgment`
- `Target User`
- `Core Scenario`
- `Problem Statement`
- `Alternatives`
- `Opportunity Hypothesis`
- `Non-Goals`
- `Open Questions`
- `Decision`
- `Next Action`

Prepend a short YAML frontmatter block:

```yaml
stage: opportunity-framer
version: 1
depends_on: []
status: go|revise|stop
last_updated: YYYY-MM-DD
```

## YAML Summary Contract

Write this shape to `01-opportunity-framer.yaml`:

```yaml
stage: opportunity-framer
decision: go|revise|stop
target_user:
  primary: ""
  screening_criteria: []
scenario:
  name: ""
  trigger: ""
  frequency_assumption: ""
problem_statement: ""
alternatives: []
opportunity_hypothesis: ""
non_goals: []
open_questions: []
revision_advice: []
```

## Decision Rules

- `go`: the opportunity is specific enough for evidence review
- `revise`: the opportunity may work, but the user, scenario, or problem is still too fuzzy
- `stop`: the idea is currently too incoherent or solution-led to justify continuing

## Guardrails

- Do not generate an MVP or feature list here.
- Do not accept vague labels like “young people” or “AI users” as target users.
- Do not confuse emotional states with concrete product problems.
- Do not write feature concepts as the opportunity hypothesis.
