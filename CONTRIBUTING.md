# 贡献说明

感谢你希望改进这套 Codex workflow skills。

## 贡献范围

欢迎以下类型的贡献：

- 修正 skill 描述中的歧义或不一致
- 补充 `references/` 中的说明文档
- 改进某一阶段的输出结构与判断标准
- 增加更清晰的安装说明、示例和最佳实践
- 修复工作流阶段之间的依赖问题

## 提交修改前的建议

在修改前，请先明确你改动的是哪一类内容：

- 编排逻辑：`startup-workflow-orchestrator`
- 单阶段分析能力：对应阶段 skill
- 参考材料：各 skill 下的 `references/`
- 代理配置：各 skill 下的 `agents/`

不要把“编排器职责”和“阶段分析职责”混在一起。

`startup-workflow-orchestrator` 负责：

- 判断当前阶段
- 维护 workflow 状态
- 控制阶段推进与暂停

单阶段 skill 负责：

- 执行该阶段的分析
- 产出该阶段的 Markdown 与摘要
- 给出 `go`、`revise`、`stop`

## 修改原则

- 保持阶段职责清晰，不要跨阶段偷读未来文件
- 不要让编排器自动跳过人工确认
- 不要把 `revise` 等同于 `go`
- 任何新增说明都应尽量具体，避免空泛表述
- 如果新增依赖文件，请确保 `README.md` 中的安装与目录说明仍然成立

## 推荐提交流程

```bash
git checkout -b feat/your-change-name
git add .
git commit -m "Describe your change"
git push origin feat/your-change-name
```

然后提交 Pull Request，并在说明中写清楚：

- 改动的是哪个 skill
- 改动动机是什么
- 是否影响现有 workflow 阶段顺序
- 是否需要使用者同步更新本地 skill

## 对使用者兼容性的要求

如果你的改动会影响已有使用方式，请在 PR 说明中明确标注：

- 是否破坏兼容
- 旧 workflow 是否需要重跑
- 旧的输出文件是否会失效

## 文档语言

当前仓库优先使用中文文档；如果补充英文说明，请保持中英文边界清晰，不要混杂成难以维护的双语段落。
