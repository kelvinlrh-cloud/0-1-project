---
name: ai-fit-and-experience-reviewer
description: Use when the user needs to decide whether AI is truly justified in a product experience. Best for judging AI necessity, defining the right AI role, surfacing user acceptance boundaries, and identifying privacy, trust, latency, and cost risks before the workflow advances.
---

# AI Fit And Experience Reviewer

## Overview

Use this skill to test whether AI belongs in the product at all, and if so, what job it should perform. This stage is intentionally skeptical.

## When To Use

Use this skill when the user asks to:

- evaluate whether AI is necessary
- define the role AI should play in the experience
- assess user willingness to interact with AI
- identify AI-related risks and boundaries
- run stage 3 of the startup workflow

## Required Inputs

Read:

- `docs/product-workflow/00-workflow-status.md`
- `docs/product-workflow/01-opportunity-framer.md`
- `docs/product-workflow/summaries/01-opportunity-framer.yaml`
- `docs/product-workflow/02-user-research-planner.md`
- `docs/product-workflow/summaries/02-user-research-planner.yaml`
- `docs/product-workflow/research/02-results-template.md`
- `docs/product-workflow/03-evidence-and-insight-reviewer.md`
- `docs/product-workflow/summaries/03-evidence-and-insight-reviewer.yaml`

Write to:

- `docs/product-workflow/04-ai-fit-and-experience-reviewer.md`
- `docs/product-workflow/summaries/04-ai-fit-and-experience-reviewer.yaml`

## Workflow

1. Read the inherited opportunity and evidence.
2. Test the non-AI baseline first.
3. Identify what specific experience value AI adds, if any.
4. Evaluate user acceptance and rejection boundaries.
5. Evaluate privacy, trust, latency, and cost boundaries.
6. Produce the stage document and summary.
7. Set one final decision and update workflow status.
8. Stop and wait for confirmation.

## What This Stage Must Answer

- Can this be solved without AI?
- What does AI improve in the experience?
- Is AI required, merely helpful, or unnecessary?
- What AI role fits the experience?
- What would users refuse to trust AI with?
- What are the privacy, trust, latency, and cost boundaries?
- What is the fallback non-AI option?

## Review Lens

Interrogate AI on five dimensions:

- necessity
- acceptance
- trust
- operational viability
- downside if AI underperforms

If a conventional product design can solve the same problem well enough, say so.

## Markdown Output Contract

The stage Markdown should contain:

- `Inherited Context`
- `This Stage Judgment`
- `AI Necessity`
- `AI Role`
- `Experience Value`
- `Acceptance Boundaries`
- `Rejection Reasons`
- `Risk Boundaries`
- `Fallback Non-AI Option`
- `Decision`
- `Next Action`

Prepend this frontmatter:

```yaml
stage: ai-fit-and-experience-reviewer
version: 1
depends_on:
  - 01-opportunity-framer.md
  - 02-user-research-planner.md
  - 03-evidence-and-insight-reviewer.md
status: go|revise|stop
last_updated: YYYY-MM-DD
```

## YAML Summary Contract

```yaml
stage: ai-fit-and-experience-reviewer
decision: go|revise|stop
ai_necessity: required|helpful_not_required|not_needed
ai_role: tool|assistant|companion|decision_support|other
experience_value: []
acceptance_boundaries: []
rejection_reasons: []
risk_boundaries:
  privacy: []
  trust: []
  latency: []
  cost: []
fallback_non_ai_option: ""
revision_advice: []
```

## Decision Rules

- `go`: AI has a justified role with understood boundaries
- `revise`: the opportunity may still work, but the AI role or risk posture is unclear
- `stop`: AI is not justified or creates a trust/risk profile that breaks the concept

## Guardrails

- Do not rubber-stamp AI just because the product is AI-native in spirit.
- Do not ignore model latency or cost if the core scenario is time-sensitive.
- Do not bury trust concerns inside vague “future improvements.”
