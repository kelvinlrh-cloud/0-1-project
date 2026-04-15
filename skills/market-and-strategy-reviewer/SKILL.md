---
name: market-and-strategy-reviewer
description: Use when the user needs a company-level view on whether an opportunity is strategically worth pursuing. Best for reviewing market size, timing, competitive logic, why-now, why-us, and whether the current wedge can grow into a meaningful business.
---

# Market And Strategy Reviewer

## Overview

Use this skill to move from “users may have this problem” to “this is worth company attention.” This stage is about strategic judgment, not just user empathy.

## When To Use

Use this skill when the user asks to:

- review market logic or strategic fit
- assess whether the opportunity is worth pursuing
- test why now and why us
- examine competitive dynamics
- run stage 4 of the startup workflow

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

Write to:

- `docs/product-workflow/05-market-and-strategy-reviewer.md`
- `docs/product-workflow/summaries/05-market-and-strategy-reviewer.yaml`

## Workflow

1. Read the upstream opportunity, evidence, and AI-fit decisions.
2. Evaluate the size and durability of the opportunity.
3. Test whether timing is favorable.
4. Analyze competitive structure and wedge quality.
5. Evaluate `why now`, `why us`, and strategic fit.
6. Produce the stage document and summary.
7. Set one final decision and update workflow status.
8. Stop and wait for confirmation.

## What This Stage Must Answer

- Is the market worth pursuing?
- Why now?
- Why us?
- What is the competitive landscape?
- Is this a credible wedge or just a feature?
- Does it fit the company's strengths or channels?
- Can this grow beyond a narrow utility?

## Review Lens

Prefer explicit judgment on:

- market depth
- timing quality
- differentiation logic
- execution advantage
- expansion potential

If the opportunity depends on advantages the team does not have, say so.

## Markdown Output Contract

The stage Markdown should contain:

- `Inherited Context`
- `This Stage Judgment`
- `Market Assessment`
- `Timing Assessment`
- `Competitive Landscape`
- `Why Now`
- `Why Us`
- `Strategic Fit`
- `Growth Potential`
- `Key Risks`
- `Decision`
- `Next Action`

Prepend this frontmatter:

```yaml
stage: market-and-strategy-reviewer
version: 1
depends_on:
  - 01-opportunity-framer.md
  - 02-user-research-planner.md
  - 03-evidence-and-insight-reviewer.md
  - 04-ai-fit-and-experience-reviewer.md
status: go|revise|stop
last_updated: YYYY-MM-DD
```

## YAML Summary Contract

```yaml
stage: market-and-strategy-reviewer
decision: go|revise|stop
market_size_assessment: ""
timing_assessment: ""
competitive_landscape: []
why_now: []
why_us: []
strategic_fit: []
growth_potential: ""
key_risks: []
revision_advice: []
```

## Decision Rules

- `go`: the opportunity is strategically credible enough to test business viability
- `revise`: the wedge may work, but timing, market logic, or strategic fit is still weak
- `stop`: the opportunity lacks sufficient strategic value or team advantage

## Guardrails

- Do not let “interesting market” substitute for a credible entry wedge.
- Do not claim `why us` unless there is a real capability, channel, asset, or insight advantage.
- Do not assume a user pain point automatically implies strategic attractiveness.
