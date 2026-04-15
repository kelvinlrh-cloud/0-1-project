# Stage Contracts

Every stage follows the same contract.

Required reads:

- `docs/product-workflow/00-workflow-status.md`
- required upstream stage Markdown files
- required upstream stage YAML summaries

Required outputs:

- one stage Markdown file under `docs/product-workflow/`
- one YAML summary file under `docs/product-workflow/summaries/`

Required distinctions:

- evidence
- inference
- unresolved questions

Required final decision:

- `go`
- `revise`
- `stop`

Required user-facing sections in stage Markdown:

- `Inherited Context`
- `This Stage Judgment`
- `Gaps`
- `Decision`
- `Next Action`

Required behavior:

- do not read future stage files
- do not auto-advance
- do update `00-workflow-status.md`
- do stop and wait after the stage finishes
