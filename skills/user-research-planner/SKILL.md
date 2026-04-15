---
name: user-research-planner
description: Use when the user needs to design a user research plan for validating a product opportunity before evidence review. Best for choosing interview and survey methods, defining recruitment and screeners, writing interview guides, and creating note/result templates that the evidence review stage can consume.
---

# User Research Planner

## Overview

Use this skill to turn an opportunity definition into an executable research plan. This stage sits between opportunity framing and evidence review so the product manager can collect fit-for-purpose evidence instead of ad hoc notes.

## When To Use

Use this skill when the user asks to:

- design a user interview plan
- create a screener or interview guide
- decide research methods for validating an opportunity
- prepare a survey, note template, or results template
- run stage 2 of the startup workflow

## Required Inputs

Read:

- `docs/product-workflow/00-workflow-status.md`
- `docs/product-workflow/01-opportunity-framer.md`
- `docs/product-workflow/summaries/01-opportunity-framer.yaml`

Write to:

- `docs/product-workflow/02-user-research-planner.md`
- `docs/product-workflow/summaries/02-user-research-planner.yaml`
- `docs/product-workflow/research/02-screener.md`
- `docs/product-workflow/research/02-interview-guide.md`
- `docs/product-workflow/research/02-note-template.md`
- `docs/product-workflow/research/02-results-template.md`

Load these references before acting:

- `references/planner-lens.md`
- `references/output-template.md`

## Workflow

1. Read the opportunity definition and extract the claims that still need validation.
2. Convert those claims into explicit research hypotheses.
3. Choose the minimum useful method mix, such as interviews, a lightweight survey, and desk research.
4. Define who is in scope, who is out of scope, and how to screen participants.
5. Write the interview guide with concrete behavioral questions and follow-up probes.
6. Create a note template and results template that preserve evidence quality for the next stage.
7. Produce the stage document and summary.
8. Set one final decision and update workflow status.
9. Stop and wait for confirmation.

## What This Stage Must Answer

- What exactly needs to be validated?
- Which methods are appropriate right now?
- Who should be recruited and screened out?
- Which interview questions are mandatory?
- What answers would count as support or counter-evidence?
- How should results be captured so evidence review can assess them?

## Planning Rules

- Default to the smallest research plan that can resolve the main uncertainty.
- Prefer recent real behavior over speculative opinions.
- Keep screeners strict enough that weak samples do not contaminate evidence review.
- Make every interview question serve a validation purpose.
- Explicitly define what would disprove the opportunity.

## Markdown Output Contract

The stage Markdown should contain:

- `Inherited Context`
- `This Stage Judgment`
- `Research Objective`
- `Validation Hypotheses`
- `Method Mix`
- `Sample Plan`
- `Channels`
- `Interview Topics`
- `Success Signals`
- `Counter Signals`
- `Artifacts To Produce`
- `Decision`
- `Next Action`

Prepend this frontmatter:

```yaml
stage: user-research-planner
version: 1
depends_on:
  - 01-opportunity-framer.md
status: go|revise|stop
last_updated: YYYY-MM-DD
```

## YAML Summary Contract

```yaml
stage: user-research-planner
decision: go|revise|stop
research_objective: ""
validation_hypotheses: []
methods: []
sample_plan:
  in_scope: []
  out_of_scope: []
  target_count: ""
channels: []
interview_topics: []
success_signals: []
counter_signals: []
required_artifacts: []
revision_advice: []
```

## Artifact Requirements

### `02-screener.md`

Must include:

- participant inclusion criteria
- exclusion criteria
- screening questions
- pass / fail logic

### `02-interview-guide.md`

Must include:

- interview goal
- opening script
- core behavioral questions
- mandatory follow-up prompts
- closing questions

### `02-note-template.md`

Must include fields for:

- participant basics
- recent scenario reconstruction
- trigger
- actions taken
- alternatives used
- pain points
- direct quotes
- preliminary interpretation

### `02-results-template.md`

Must include sections for:

- sample overview
- repeated patterns
- counter-evidence
- supported claims
- unsupported claims
- raw quote snippets
- remaining gaps

## Decision Rules

- `go`: the research plan is concrete enough to execute and later feed evidence review
- `revise`: the plan is directionally right, but the methods, sample, or questions are still weak
- `stop`: the opportunity is not clear enough to justify planning research yet

## Guardrails

- Do not treat this stage as evidence review.
- Do not write generic interview questions like “What features do you want?”
- Do not let the sample definition drift away from the opportunity definition.
- Do not proceed without explicit success and counter signals.
