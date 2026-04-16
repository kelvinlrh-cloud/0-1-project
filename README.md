# 0-1 Project Workflow

0-1 Project Workflow is a staged product-initiation workflow for AI agents. It helps teams move from a rough idea to a reviewable MVP scope through a gated process instead of jumping straight into a PRD, prototype, or feature list.

This repository is not Codex-only. The workflow logic is written as portable Markdown-based skills, while the repository also includes a Codex-friendly packaging layout and a repo-local plugin under `plugins/startup-workflow/`.

## 中文说明

`0-1 Project Workflow` 是一个面向 AI agent / AI 助手的产品立项工作流仓库。它的目标不是让 AI 直接替你拍结论，而是把一个模糊产品想法拆成一组可评审、可回滚、可暂停的阶段化判断，最终收敛到清晰的 MVP 范围。

这个仓库适合以下场景：

- 你有一个 0-1 产品想法，但还不够清晰
- 你想让 AI 参与产品立项，而不是直接生成一份空泛 PRD
- 你需要一套能暂停、回滚、复用的产品判断流程
- 你想在团队里复用一套一致的 AI-assisted product workflow

### 仓库定位

这个仓库有两层内容：

- `workflow logic`
  阶段定义、阶段契约、状态推进规则，以及每个阶段该如何判断
- `packaging format`
  这些 workflow 如何被 Codex 或其他 AI 工具加载和触发

因此，它不是“只能给 Codex 用的仓库”。

你可以把它当成：

- 一套直接可用的 Codex skills
- 一个 repo-local Codex plugin
- 一套可以迁移到 Cursor、Claude Code、Gemini CLI、OpenCode 或自定义 agent framework 的 Markdown workflow

### 角色与分工

这套 workflow 里主要有三类角色：

- `Product Manager`
  负责给出背景、补充信息、审查阶段输出，并在每个阶段结束时决定 `go`、`revise` 或 `stop`
- `startup-workflow-orchestrator`
  作为控制平面，负责读取状态、判断当前阶段、说明本阶段输入输出，并在每阶段结束后停下等待确认
- `Stage Skills`
  负责完成具体分析任务，每个阶段只做自己该做的判断，不越权跳到后续阶段

### 工作流程

整个 workflow 分为 7 个阶段：

1. `opportunity-framer`
   把模糊想法收敛成一个可测试的机会定义，明确目标用户、问题、场景和边界。
2. `user-research-planner`
   设计用户研究方案，决定该访谈谁、怎么问、怎么记录、怎么判断结果。
3. `evidence-and-insight-reviewer`
   审查研究和观察结果，区分证据、推断和未验证假设。
4. `ai-fit-and-experience-reviewer`
   判断 AI 在这个产品体验里是否真的必要，避免为 AI 而 AI。
5. `market-and-strategy-reviewer`
   审查市场逻辑、竞争环境、why now 和战略成立条件。
6. `business-and-risk-reviewer`
   审查获客、留存、成本、商业模式和关键失败风险。
7. `mvp-scope-planner`
   把通过前面审查的方向收敛成第一版 MVP 范围、must-have、non-goals 和验证计划。

这套 workflow 的推进规则很明确：

- 每个阶段结束后只能得到 `go`、`revise` 或 `stop`
- 编排器负责更新状态并强制停下
- 不允许自动跳过阶段，也不允许直接从 idea 跳到 MVP

### 产出物

当这套 workflow 在某个项目里运行时，通常会把产出写到 `docs/product-workflow/` 下，主要包括：

- `00-workflow-status.md`
  工作流状态文件，记录当前阶段、阶段状态、下一推荐阶段和阻塞问题
- `01-...md` 到 `07-...md`
  每个阶段各自的结构化 Markdown 输出
- `research/`
  用户研究阶段产生的筛选表、访谈提纲、笔记模板和结果模板
- `summaries/`
  每个阶段的 YAML 摘要，供后续阶段继续读取

这些文件是 workflow 在用户项目里的运行产物，不是这个仓库本身必须预先提交的内容。

### 如何使用

最常见的使用方式如下：

1. 安装这套 workflow 的 skills，或启用 `plugins/startup-workflow/` 下的本地 plugin
2. 在你的 AI 工具里调用 `startup-workflow-orchestrator`
3. 用一句话或几段话描述你要评估的产品想法
4. 让 orchestrator 初始化或恢复 `docs/product-workflow/`
5. 按阶段推进，并在每个阶段结束后人工决定 `go`、`revise` 或 `stop`
6. 最终在 `07-mvp-scope-planner.md` 中得到第一版 MVP 范围

推荐的启动方式示例：

- “用 `startup-workflow-orchestrator` 帮我启动一个新的 0-1 产品 workflow，方向是 AI 面试陪练。”
- “继续当前的 product workflow，并告诉我下一阶段应该做什么。”
- “检查 `docs/product-workflow/` 的状态，判断是否可以进入 MVP scope 规划。”

### 兼容与安装

如果你使用的是 Codex，这个仓库提供两种接入方式：

- 直接使用 `skills/` 下的 skill 目录
- 使用 `plugins/startup-workflow/` 作为 repo-local plugin

相关目录：

```text
skills/
plugins/startup-workflow/
.agents/plugins/marketplace.json
```

如果你使用的是其他 AI 工具，一般推荐按“内容迁移”的方式使用：

1. clone 这个仓库
2. 选择你需要的 skill 目录
3. 把 `SKILL.md` 和对应的 `references/`、`agents/` 一起迁移
4. 把 `startup-workflow-orchestrator` 作为总控入口
5. 用所在工具支持的 prompt / skill / extension 机制触发它

不要只复制单个 `SKILL.md`，因为很多阶段还依赖 `references/` 和 `agents/`。

### 与 Track Workflow 的区别

`0-1 Project Workflow` 关注的是“从一个具体产品机会出发，逐步验证并收敛到 MVP 范围”。

它和 `Track Workflow` 的区别是：

- `0-1 Project Workflow`
  从具体 idea 或机会出发，输出写入 `docs/product-workflow/`
- `Track Workflow`
  从赛道进入问题出发，先判断市场结构、切口和进入策略，输出写入 `docs/track-workflow/`

如果你当前面对的问题是“这个产品机会到底值不值得做、AI 是否适配、第一版 MVP 应该是什么”，用 `0-1 Project Workflow`。
如果你当前面对的问题是“这个市场值不值得进、从哪一刀切进去”，应该用 `Track Workflow`。

## What It Includes

- `startup-workflow-orchestrator` as the control-plane skill
- seven stage skills from opportunity framing to MVP scope definition
- direct skill packaging under `skills/`
- a repo-local Codex plugin under `plugins/startup-workflow/`
- plugin metadata, branding assets, and marketplace registration for local plugin use

## Included Skills

- `startup-workflow-orchestrator`
- `opportunity-framer`
- `user-research-planner`
- `evidence-and-insight-reviewer`
- `ai-fit-and-experience-reviewer`
- `market-and-strategy-reviewer`
- `business-and-risk-reviewer`
- `mvp-scope-planner`

## Workflow Stages

1. Opportunity framing
2. User research planning
3. Evidence and insight review
4. AI fit and experience review
5. Market and strategy review
6. Business and risk review
7. MVP scope planning

## Workspace Output

When this workflow runs inside a project, it typically writes artifacts under `docs/product-workflow/`, including:

- `00-workflow-status.md`
- one Markdown file per stage from `01-...md` to `07-...md`
- research artifacts under `docs/product-workflow/research/`
- YAML summaries under `docs/product-workflow/summaries/`

## Install Or Reuse

For Codex, you can either:

1. use the direct skills under `skills/`
2. use the repo-local plugin under `plugins/startup-workflow/`

For other AI tools, the recommended pattern is content portability:

1. clone the repository
2. copy the stage `SKILL.md` files together with related `references/` and `agents/`
3. use `startup-workflow-orchestrator` as the entry point
4. trigger the workflow through your tool's prompt, skill, plugin, or extension mechanism

## Design Principles

- gated progression over auto-advance
- evidence over unsupported claims
- structured review over one-shot generation
- explicit rollback over silent drift
- reviewable MVP scope over flashy output

## Contributing

If you want to contribute new stages, references, or workflow rules, read [CONTRIBUTING.md](./CONTRIBUTING.md) first.

## License

MIT License. See [LICENSE](./LICENSE).
