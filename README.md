# Startup Workflow Skills for AI Agents

一个面向 AI agent / AI 助手的产品立项工作流技能包，用来把一个模糊想法推进成清晰的 MVP 范围。

This repository is a product initiation workflow for AI agents and AI assistants. It helps turn a rough idea into a clear MVP scope through a staged, reviewable process.

## What This Is / 这是什么

这不是一个只给 Codex 用的仓库。

它当前以 Codex 的技能目录结构发布，但核心内容是可迁移的 Markdown workflow skills。只要你的 AI 工具支持以下任意一种能力，就可以使用或适配这套 workflow：

- reusable prompts
- local instruction files
- skills / plugins / extensions
- agent memory or task-specific playbooks

This is not Codex-only.

The repository is currently packaged in a Codex-friendly skill layout, but the core content is portable Markdown-based workflow skills. You can use or adapt it in any AI tool that supports:

- reusable prompts
- local instruction files
- skills, plugins, or extensions
- agent memory or task-specific playbooks

## How It Works / 工作流如何运作

这套 workflow 的目标不是让 AI 直接替你“拍脑袋给结论”，而是把产品立项拆成一组阶段化判断：

1. 定义机会
2. 设计用户研究
3. 审查证据与洞察
4. 判断 AI 是否适配体验
5. 审查市场与战略逻辑
6. 审查商业模式与关键风险
7. 收敛到 MVP 范围

编排器 `startup-workflow-orchestrator` 负责控制节奏、维护状态、阻止自动跳阶段。

每个阶段结束后只能得到三种结果：

- `go`
- `revise`
- `stop`

The workflow is designed to prevent shallow AI output.

Instead of jumping straight to a PRD or prototype, it breaks product initiation into gated stages:

1. frame the opportunity
2. plan user research
3. review evidence and insights
4. evaluate whether AI truly fits the experience
5. review market and strategy
6. review business model and key risks
7. define MVP scope

The `startup-workflow-orchestrator` skill manages flow control, workflow state, and stage gating.

Each stage ends with exactly one decision:

- `go`
- `revise`
- `stop`

## Compatibility / 兼容方式

这套仓库分成两层：

- workflow logic：阶段定义、阶段契约、状态推进规则
- packaging format：某个具体工具如何加载这些 skill

当前仓库的 packaging format 偏向 Codex，但 workflow logic 本身可以用于其他工具。

The repository has two layers:

- workflow logic: stage definitions, stage contracts, and state transitions
- packaging format: how a specific AI tool loads and runs the skills

The current packaging is Codex-oriented, but the workflow logic is tool-agnostic.

### Codex

Codex 可以直接使用当前目录结构。

Codex can use the current directory structure directly.

### Other AI Tools

其他 AI 工具通常有三种接入方式：

1. 作为本地 skills / plugins / extensions 导入
2. 作为可复用 prompt files 保存
3. 作为项目级 agent instructions 或 playbook 接入

如果你的工具没有“skills”概念，也仍然可以使用：

- 把各个 `SKILL.md` 作为阶段模板
- 把 `references/` 中的规则作为附加上下文
- 把 `startup-workflow-orchestrator` 作为总控提示词

Most non-Codex tools can adopt this workflow in one of three ways:

1. import the files as local skills, plugins, or extensions
2. store them as reusable prompt files
3. use them as project-level agent instructions or playbooks

If your tool does not have a formal skill system, you can still use the repo by:

- treating each `SKILL.md` as a stage prompt
- using files in `references/` as supporting context
- using `startup-workflow-orchestrator` as the control-plane prompt

## Installation / 安装方式

### Codex

```bash
git clone https://github.com/kelvinlrh-cloud/codex-startup-workflow.git
mkdir -p ~/.codex/skills
cp -R codex-startup-workflow/skills/* ~/.codex/skills/
```

### Other AI Tools

如果你使用的是 Claude Code、Cursor、Gemini CLI、OpenCode、Copilot CLI 或自定义 agent framework，这个仓库更适合按“内容迁移”的方式使用，而不是假设存在统一安装命令。

推荐步骤：

1. clone 这个仓库
2. 选择你需要的 skill 目录
3. 把 `SKILL.md` 和对应的 `references/` 一起迁移到你的工具
4. 把编排器 skill 设为主入口
5. 用你所在工具支持的 prompt / skill / extension 机制触发它

For Claude Code, Cursor, Gemini CLI, OpenCode, Copilot CLI, or a custom agent framework, the recommended approach is content portability rather than assuming a single universal installer.

Recommended steps:

1. clone this repository
2. select the skills you want
3. copy each `SKILL.md` together with its related `references/`
4. use the orchestrator as the entry point
5. trigger it through your tool's prompt, skill, plugin, or extension mechanism

## Quick Start / 快速开始

### Chinese

把 `startup-workflow-orchestrator` 交给你的 AI agent，然后发出类似请求：

```text
我想从一个新 idea 开始，启动产品立项 workflow：……
```

如果你已经跑过一部分，也可以说：

```text
继续当前 workflow
```

### English

Give your AI agent the `startup-workflow-orchestrator` skill, then start with a prompt like:

```text
I want to start a product initiation workflow from a new idea: ...
```

If the workflow already exists, you can say:

```text
Continue the current workflow.
```

## Workflow Stages / 工作流阶段

1. `opportunity-framer`
2. `user-research-planner`
3. `evidence-and-insight-reviewer`
4. `ai-fit-and-experience-reviewer`
5. `market-and-strategy-reviewer`
6. `business-and-risk-reviewer`
7. `mvp-scope-planner`

其中：

- `startup-workflow-orchestrator` 负责判断当前阶段、读写状态、控制推进
- 其余 skill 负责具体阶段分析和输出

In this system:

- `startup-workflow-orchestrator` handles stage selection, workflow state, and progression control
- the remaining skills do the stage-specific analysis and output

## What's Inside / 仓库包含什么

```text
skills/
  startup-workflow-orchestrator/
  opportunity-framer/
  user-research-planner/
  evidence-and-insight-reviewer/
  ai-fit-and-experience-reviewer/
  market-and-strategy-reviewer/
  business-and-risk-reviewer/
  mvp-scope-planner/
```

请不要只复制单个 `SKILL.md`。

很多 skill 还依赖：

- `references/`
- `agents/`

Do not copy only the top-level `SKILL.md`.

Many skills also depend on:

- `references/`
- `agents/`

## Output Artifacts / 会产出什么

当某个 agent 按照这套 workflow 在项目中执行时，通常会在项目内生成：

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
  summaries/
```

这些是 workflow 运行产物，不是仓库本身必须提前提交的内容。

When an agent runs this workflow inside a project, it will typically generate:

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
  summaries/
```

These are workflow outputs inside the user's project, not files that must exist in this repository ahead of time.

## When To Use It / 适合什么场景

- 你有一个还不够清晰的新产品想法
- 你想让 AI 参与产品立项，但不想要空泛结论
- 你需要一套可回滚、可暂停、可复用的产品判断流程
- 你想在团队内复用同一套 AI-assisted workflow

- You have an early-stage product idea that is still fuzzy
- You want AI assistance without shallow hand-wavy output
- You need a workflow that is reviewable, pausable, and reversible
- You want a reusable AI-assisted initiation process across a team

## Design Principles / 设计原则

- gated progression over auto-advance
- evidence over unsupported claims
- structured review over one-shot generation
- explicit rollback over silent drift
- PRD-quality output over flashy prototype defaults

- 先过关再推进，不自动跳阶段
- 证据优先，不接受无依据判断
- 结构化评审优先，不鼓励一把梭生成
- 可以明确回滚，不允许悄悄漂移
- 在进入定义和交付阶段时，默认优先输出结构化 PRD，而不是自动给原型

## Contributing / 贡献

Skills live directly in this repository.

如果你要贡献新的 stage、reference 或 workflow rule，请先看 [CONTRIBUTING.md](./CONTRIBUTING.md)。

If you want to contribute new stages, references, or workflow rules, read [CONTRIBUTING.md](./CONTRIBUTING.md) first.

## License

MIT License. See [LICENSE](./LICENSE).
