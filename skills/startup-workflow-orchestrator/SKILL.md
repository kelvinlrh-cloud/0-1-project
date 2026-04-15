---
name: startup-workflow-orchestrator
description: Use when the user wants to start, continue, or manage a staged product initiation workflow that moves from idea to MVP feature list. Coordinates the workflow state, initializes project files under docs/product-workflow, routes to the correct stage skill, and enforces stop-and-confirm behavior after each stage.
---

# Startup Workflow Orchestrator

## Overview

Use this skill as the control plane for the startup initiation workflow. It manages state, keeps stage outputs in the current project workspace, and ensures the product manager confirms each stage before the workflow advances.

Load these references before acting:

- `references/workflow-overview.md`
- `references/stage-contracts.md`
- `references/file-conventions.md`

This skill has two startup modes:

- `existing-workflow mode`: the user explicitly asks to continue, resume, inspect status, or manage an existing workflow
- `fresh-idea mode`: the user gives a new idea or brief concept without explicitly pointing to existing local materials

## When To Use

Use this skill when the user asks to:

- start a new product initiation workflow
- continue a paused workflow
- run an AI consultant-style initiation process
- move an idea toward an MVP through staged review
- inspect current workflow status or decide the next stage

Do not use this skill when the user only wants a single stage review. In that case, use the relevant stage skill directly.

## Core Responsibilities

This skill does exactly six things:

1. Decide whether the request is `existing-workflow mode` or `fresh-idea mode`.
2. In `existing-workflow mode`, check whether `docs/product-workflow/` already exists in the current workspace.
3. If the user explicitly wants a new workflow and none exists for that idea, initialize the workflow directory, status file, stage files, and summary files using the conventions in `references/file-conventions.md`.
4. Read `docs/product-workflow/00-workflow-status.md` only when the user is managing an existing workflow, or after the user has explicitly agreed to create or reuse a local workflow for the new idea.
5. Determine the current stage, next recommended stage, and rollback target.
6. Tell the product manager what the active stage must accomplish, what inputs it needs, and what output it must produce.
7. After a stage completes, update the workflow status and stop for confirmation.

## Context Access Policy

- In `fresh-idea mode`, start from the user's message only.
- Do not automatically read product notes, research files, analysis files, or existing workflow files just because they happen to exist in the workspace.
- If local materials may be relevant, say so explicitly and ask whether to use them before reading them.
- If the user gives only a short idea such as a one-line concept, default to discussing or framing the idea from scratch, using labeled assumptions where needed.
- Only enter `existing-workflow mode` without asking when the user clearly signals continuity, for example: "continue", "resume", "看下当前进度", "这个 workflow 到哪了", or when they explicitly point to an existing file or folder.
- If `docs/product-workflow/` exists but the user has not asked to manage that workflow, do not assume it belongs to the current idea.

## Operating Procedure

### 1. Startup Or Resume

- First classify the request:
  - if the user clearly wants to continue or inspect an existing workflow, use `existing-workflow mode`
  - otherwise use `fresh-idea mode`
- In `fresh-idea mode`, do not inspect workspace business files before briefing the user on that choice.
- In `existing-workflow mode`, if a workflow exists, read the status file first.
- Never assume stage order from memory; when a workflow is in use, always trust the current status file.

### 2. Identify The Active Stage

Pick the active stage using this order:

1. `current_stage` if it is `in_progress`
2. `next_recommended_stage` if present
3. the first stage whose status is `pending`
4. if a stage is `revise`, route to the rollback or rerun target

### 3. Brief The Product Manager

Before the stage runs, tell the user:

- what the stage is for
- whether you are using only the user prompt or also specific local files
- what files it reads
- what file it will write
- what a passing result looks like
- what decisions are possible: `go`, `revise`, `stop`

### 4. Enforce Gatekeeping

After a stage skill finishes:

- record the stage result in the status file
- set `next_recommended_stage` only if the result is `go`
- set `rollback_target` if the result is `revise`
- set `overall_status` to `stopped` if the result is `stop`
- stop and wait for explicit product manager confirmation

Never auto-run the next stage.

## Guardrails

- Do not replace a stage skill's analytical work with your own summary.
- Do not skip a stage because the answer "seems obvious."
- Do not reinterpret `revise` as `go`.
- Do not keep advancing after a stage result; always stop for confirmation.
- If a stage was rerun directly and downstream outputs are now stale, say so explicitly and recommend which later stages must be rerun.
- Do not silently import context from unrelated workspace files when the user has only provided a fresh idea.
- Do not treat the mere existence of `docs/product-workflow/` as permission to reuse it for a new project.

## Language Rule

- If the user is primarily communicating in Chinese, write all workflow Markdown files, research artifacts, and user-facing explanatory text in Chinese by default.
- Keep machine-stable identifiers such as stage ids, YAML keys, file names, and status enums unchanged when needed for workflow compatibility.
- Only switch workflow artifacts to another language if the user explicitly asks.

## User-Facing Output Pattern

When orchestrating, keep the message short and structured:

- `Current Stage`
- `Why This Stage`
- `Required Inputs`
- `Expected Output`
- `Pass Condition`
- `Possible Decisions`

## Completion Rule

The workflow completes only when:

- `mvp-scope-planner` returns `go`
- the MVP feature list is present in `07-mvp-scope-planner.md`
- `overall_status` is updated to `completed`

If `mvp-scope-planner` returns `revise` or `stop`, the workflow is not complete.
