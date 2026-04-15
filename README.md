# Codex Startup Workflow Skills

一套用于 Codex 的产品立项工作流技能包，帮助你把一个模糊想法逐步推进到可执行的 MVP 功能范围。

## 这个技能包是干什么的

这套技能包的目标，不是直接替代产品经理做判断，而是提供一套结构化、可暂停、可回滚的工作流，让你用统一的方法完成以下过程：

1. 把一个初始想法定义清楚
2. 设计用户研究和验证方式
3. 判断证据是否足够支持这个机会
4. 判断 AI 是否真的适合放进这个产品体验
5. 评估市场和战略层面是否值得做
6. 评估商业模式与关键风险是否成立
7. 收敛出一版清晰、克制的 MVP 功能范围

它适合以下场景：

- 你有一个新产品想法，但还比较模糊
- 你希望用阶段化方式推进产品立项
- 你希望每一阶段都有明确输入、输出和决策
- 你希望在团队内复用同一套产品判断流程

## 这套工作流怎么运作

整个 workflow 由 1 个编排器技能和 7 个阶段技能组成。

阶段顺序如下：

1. `opportunity-framer`
2. `user-research-planner`
3. `evidence-and-insight-reviewer`
4. `ai-fit-and-experience-reviewer`
5. `market-and-strategy-reviewer`
6. `business-and-risk-reviewer`
7. `mvp-scope-planner`

其中：

- `startup-workflow-orchestrator` 负责判断当前处于哪个阶段、应该读写哪些文件、阶段结束后如何更新状态
- 其余 7 个 skills 负责各自阶段的分析和产出

每个阶段结束后，只会得到三种决策结果：

- `go`：进入下一阶段
- `revise`：当前阶段或更早阶段需要重做
- `stop`：结束这一轮 workflow

编排器不会自动跑完整套流程。每完成一阶段，它都会停下来，等待你确认是否继续。

## 包含的技能

请保持以下目录完整，不要只复制单个 `SKILL.md` 文件：

- `startup-workflow-orchestrator`
- `opportunity-framer`
- `user-research-planner`
- `evidence-and-insight-reviewer`
- `ai-fit-and-experience-reviewer`
- `market-and-strategy-reviewer`
- `business-and-risk-reviewer`
- `mvp-scope-planner`

这些 skill 目录中的 `references/`、`agents/` 等配套文件也是工作流的一部分。

## 推荐目录结构

建议将仓库组织成如下结构：

```text
codex-startup-workflow/
  README.md
  LICENSE
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

## 安装方法

如果你是通过 GitHub 获取这个仓库，安装步骤如下：

```bash
git clone <your-repo-url>
mkdir -p ~/.codex/skills
cp -R codex-startup-workflow/skills/* ~/.codex/skills/
```

如果你是通过压缩包获取，也可以直接将 `skills/` 目录下的内容复制到：

```bash
~/.codex/skills/
```

## 快速开始

安装完成后，进入你自己的项目目录，直接对 Codex 发送类似下面的指令：

```text
[$startup-workflow-orchestrator](~/.codex/skills/startup-workflow-orchestrator/SKILL.md)
我想从一个新 idea 开始，启动产品立项 workflow：……
```

如果你已经在项目中跑过这套流程，也可以直接说：

```text
继续当前 workflow
```

或者：

```text
看下当前 workflow 的进度
```

## 使用方法

### 1. 启动一个新 workflow

进入你自己的项目目录后，对 Codex 说类似这样的话：

```text
[$startup-workflow-orchestrator](~/.codex/skills/startup-workflow-orchestrator/SKILL.md)
我想为一个新的产品想法启动 workflow：……
```

如果你只是给一个简短 idea，编排器会默认从这个想法本身开始，不会自动读取你项目里的其他资料。

### 2. 继续已有 workflow

如果你已经跑过一部分，可以说：

```text
继续当前 workflow
```

或者：

```text
看下当前 workflow 到哪一步了
```

这时编排器会读取项目内的：

```text
docs/product-workflow/00-workflow-status.md
```

并判断当前阶段、下一推荐阶段、是否需要回滚。

### 3. 在每一阶段完成后做决策

每个阶段结束后，你需要明确给出下一步判断：

- `go`
- `revise`
- `stop`

这一步是工作流的关键。它确保流程不是一股脑往前跑，而是按你的判断推进。

## 运行后会生成什么

当编排器在你的项目中启动 workflow 后，通常会在项目里创建：

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

这些文件属于使用者自己的项目产物，不属于本技能包本身。

## 发布到 GitHub

如果你想像普通开源项目一样把这套技能包发布到 GitHub，建议按以下步骤操作：

```bash
cd codex-startup-workflow
git init
git add README.md LICENSE .gitignore skills
git commit -m "Initial commit"
git branch -M main
git remote add origin <your-repo-url>
git push -u origin main
```

建议仓库名保持直观，例如：

- `codex-startup-workflow`
- `codex-product-initiation-workflow`
- `codex-startup-skills`

## 使用建议

- 用它来推进“一个具体产品机会”，不要同时混入多个无关 idea
- 不要跳过中间阶段，否则后续判断会失去依据
- 如果阶段结论是 `revise`，就按建议回滚，不要把 `revise` 当成 `go`
- 如果只是想单独做某一类分析，直接调用对应阶段 skill，不一定非要走完整个 orchestrator

## 适合谁

这套技能包更适合以下角色：

- 独立产品探索者
- AI 产品经理
- 创业团队中的 0 到 1 负责人
- 需要把产品判断流程标准化的小团队

## License

建议为该仓库补充一个明确的 `LICENSE` 文件，例如 `MIT`。否则别人虽然能看到仓库内容，但复用边界不清晰。
