# Workflow Overview

This workflow moves a product manager from a rough idea to an MVP feature list through six gated stages:

1. `opportunity-framer`
2. `user-research-planner`
3. `evidence-and-insight-reviewer`
4. `ai-fit-and-experience-reviewer`
5. `market-and-strategy-reviewer`
6. `business-and-risk-reviewer`
7. `mvp-scope-planner`

State model:

- `go`: advance to the next stage after confirmation
- `revise`: rerun the current stage or roll back to an earlier stage
- `stop`: end the workflow round

Default operating pattern:

- the orchestrator initializes or resumes the workflow
- a stage skill produces the current stage output
- the orchestrator updates status and stops
- the product manager decides whether to continue

The workflow is optimized for AI-native products first, but it must still permit a non-AI outcome if the AI hypothesis fails.
