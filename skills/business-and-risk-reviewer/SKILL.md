---
name: business-and-risk-reviewer
description: Use when the user needs to decide whether an opportunity deserves investment rather than further admiration. Best for reviewing retention logic, acquisition paths, migration friction, cost structure, monetization possibilities, key risks, and clear kill criteria.
---

# Business And Risk Reviewer

## Overview

Use this skill to judge whether the opportunity is investable. This stage turns product and strategy logic into a harder economic and risk conversation.

## When To Use

Use this skill when the user asks to:

- review business viability
- test retention, growth, or monetization logic
- identify fatal risks or kill criteria
- decide whether the opportunity deserves real investment
- run stage 5 of the startup workflow

## Required Inputs

Read:

- `docs/product-workflow/00-workflow-status.md`
- `docs/product-workflow/01-opportunity-framer.md`
- `docs/product-workflow/summaries/01-opportunity-framer.yaml`
- `docs/product-workflow/02-user-research-planner.md`
- `docs/product-workflow/summaries/02-user-research-planner.yaml`
- `docs/product-workflow/03-evidence-and-insight-reviewer.md`
- `docs/product-workflow/summaries/03-evidence-and-insight-reviewer.yaml`
- `docs/product-workflow/04-ai-fit-and-experience-reviewer.md`
- `docs/product-workflow/summaries/04-ai-fit-and-experience-reviewer.yaml`
- `docs/product-workflow/05-market-and-strategy-reviewer.md`
- `docs/product-workflow/summaries/05-market-and-strategy-reviewer.yaml`

Write to:

- `docs/product-workflow/06-business-and-risk-reviewer.md`
- `docs/product-workflow/summaries/06-business-and-risk-reviewer.yaml`

## Workflow

1. Read all upstream stage outputs.
2. Test retention logic first.
3. Test acquisition and migration friction.
4. Evaluate cost structure and operational burden.
5. Identify monetization options and their plausibility.
6. Name the top risks and explicit kill criteria.
7. Produce the stage document and summary.
8. Set one final decision and update workflow status.
9. Stop and wait for confirmation.

## What This Stage Must Answer

- Why would users come back?
- How could users be acquired?
- What migration costs exist?
- Is the cost structure acceptable?
- Is there a plausible monetization path?
- What are the key operational, product, or trust risks?
- What kill criteria should stop the effort?

## Review Lens

Be explicit about:

- retention mechanism
- acquisition logic
- cost drivers
- monetization realism
- downside scenarios

If the concept only works under optimistic assumptions, say so.

## Markdown Output Contract

The stage Markdown should contain:

- `Inherited Context`
- `This Stage Judgment`
- `Retention Hypothesis`
- `Acquisition Hypothesis`
- `Migration Costs`
- `Cost Structure`
- `Monetization Options`
- `Key Risks`
- `Kill Criteria`
- `Recommended Decision`
- `Decision`
- `Next Action`

Prepend this frontmatter:

```yaml
stage: business-and-risk-reviewer
version: 1
depends_on:
  - 01-opportunity-framer.md
  - 02-user-research-planner.md
  - 03-evidence-and-insight-reviewer.md
  - 04-ai-fit-and-experience-reviewer.md
  - 05-market-and-strategy-reviewer.md
status: go|revise|stop
last_updated: YYYY-MM-DD
```

## YAML Summary Contract

```yaml
stage: business-and-risk-reviewer
decision: go|revise|stop
retention_hypothesis: ""
acquisition_hypothesis: ""
migration_costs: []
cost_structure: []
monetization_options: []
key_risks: []
kill_criteria: []
recommended_decision: go|validate_more|pivot|stop
revision_advice: []
```

## Decision Rules

- `go`: the opportunity has a believable enough business case to scope an MVP
- `revise`: the direction may still work, but the economics or risk posture are too unclear
- `stop`: the opportunity does not justify investment under current assumptions

## Guardrails

- Do not confuse “could be monetized someday” with an actual monetization path.
- Do not ignore model or human-ops costs in AI-heavy products.
- Do not pass this stage without explicit kill criteria.
