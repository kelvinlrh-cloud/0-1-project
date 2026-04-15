---
name: evidence-and-insight-reviewer
description: Use when the user needs to assess whether current interviews, desk research, observations, or behavioral signals actually support a product opportunity. Best for reviewing evidence quality, spotting evidence gaps, separating supported claims from assumptions, and deciding whether the workflow can advance.
---

# Evidence And Insight Reviewer

## Overview

Use this skill to audit whether the current opportunity is supported by real evidence. This stage protects the workflow from progressing on enthusiasm alone.

## When To Use

Use this skill when the user asks to:

- review whether evidence is strong enough
- audit user research or desk research
- identify missing evidence before strategy review
- run stage 2 of the startup workflow

## Required Inputs

Read:

- `docs/product-workflow/00-workflow-status.md`
- `docs/product-workflow/01-opportunity-framer.md`
- `docs/product-workflow/summaries/01-opportunity-framer.yaml`
- `docs/product-workflow/02-user-research-planner.md`
- `docs/product-workflow/summaries/02-user-research-planner.yaml`
- `docs/product-workflow/research/02-results-template.md`
- any completed interview notes, survey results, desk-research outputs, or raw research notes the user has supplied

Write to:

- `docs/product-workflow/03-evidence-and-insight-reviewer.md`
- `docs/product-workflow/summaries/03-evidence-and-insight-reviewer.yaml`

## Workflow

1. Read the inherited opportunity definition and research plan.
2. Inventory existing evidence and its sources.
3. Separate direct evidence from interpretation.
4. Check whether the evidence covers real behavior, real costs, and real alternatives.
5. Look for counter-evidence and missing proof.
6. Produce the stage document and summary.
7. Set one final decision and update workflow status.
8. Stop and wait for confirmation.

## What This Stage Must Answer

- What evidence exists today?
- Where did each piece of evidence come from?
- Does the evidence cover recent real behavior?
- Does it show time, money, effort, or social cost?
- What counter-evidence exists?
- What claims are supported?
- What claims are still unsupported?
- Is the evidence strong enough to continue?

## Evidence Lens

Prefer evidence in this order:

1. recent concrete user behavior
2. direct quotes tied to real scenarios
3. repeated patterns across users or channels
4. desk research and public signals
5. internal opinions and assumptions

If evidence is thin, say so explicitly.

## Markdown Output Contract

The stage Markdown should contain:

- `Inherited Context`
- `This Stage Judgment`
- `Evidence Inventory`
- `Behavioral Signals`
- `Counter-Evidence`
- `Supported Claims`
- `Unsupported Claims`
- `Key Gaps`
- `Recommended Research Actions`
- `Decision`
- `Next Action`

Prepend this frontmatter:

```yaml
stage: evidence-and-insight-reviewer
version: 1
depends_on:
  - 01-opportunity-framer.md
  - 02-user-research-planner.md
status: go|revise|stop
last_updated: YYYY-MM-DD
```

## YAML Summary Contract

```yaml
stage: evidence-and-insight-reviewer
decision: go|revise|stop
evidence_summary:
  desk_research: []
  interviews: []
  behavioral_signals: []
counter_evidence: []
confidence_level: high|medium|low
key_gaps: []
recommended_research_actions: []
supported_claims: []
unsupported_claims: []
revision_advice: []
```

## Decision Rules

- `go`: the evidence is strong enough that later stages can reason on it
- `revise`: the opportunity may still be valid, but critical evidence gaps remain
- `stop`: the current evidence materially undermines the opportunity

## Guardrails

- Do not let vivid anecdotes substitute for pattern strength.
- Do not treat user feature requests as problem proof.
- Do not pass this stage if the evidence does not clearly connect user behavior to cost or pain.
