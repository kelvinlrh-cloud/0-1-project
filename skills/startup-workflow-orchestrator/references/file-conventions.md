# File Conventions

Default workspace layout:

```text
docs/product-workflow/
  00-workflow-status.md
  01-opportunity-framer.md
  02-user-research-planner.md
  03-evidence-and-insight-reviewer.md
  04-ai-fit-and-experience-reviewer.md
  05-market-and-strategy-reviewer.md
  06-business-and-risk-reviewer.md
  07-mvp-scope-planner.md
  research/
    02-screener.md
    02-interview-guide.md
    02-note-template.md
    02-results-template.md
  summaries/
    01-opportunity-framer.yaml
    02-user-research-planner.yaml
    03-evidence-and-insight-reviewer.yaml
    04-ai-fit-and-experience-reviewer.yaml
    05-market-and-strategy-reviewer.yaml
    06-business-and-risk-reviewer.yaml
    07-mvp-scope-planner.yaml
```

Status file YAML block:

```yaml
workflow_name: ""
current_stage: ""
overall_status: active|paused|stopped|completed
stages:
  - stage: opportunity-framer
    status: pending|in_progress|go|revise|stop
  - stage: user-research-planner
    status: pending|in_progress|go|revise|stop
  - stage: evidence-and-insight-reviewer
    status: pending|in_progress|go|revise|stop
  - stage: ai-fit-and-experience-reviewer
    status: pending|in_progress|go|revise|stop
  - stage: market-and-strategy-reviewer
    status: pending|in_progress|go|revise|stop
  - stage: business-and-risk-reviewer
    status: pending|in_progress|go|revise|stop
  - stage: mvp-scope-planner
    status: pending|in_progress|go|revise|stop
next_recommended_stage: ""
rollback_target: ""
blocking_questions: []
```

Stage Markdown files should start with short YAML frontmatter:

```yaml
stage: stage-name
version: 1
depends_on: []
status: go|revise|stop
last_updated: YYYY-MM-DD
```

On rerun:

- overwrite the stage file and summary file
- preserve a short `revision_history` section in the Markdown if needed
- mark downstream stages for rerun if the new result invalidates them
