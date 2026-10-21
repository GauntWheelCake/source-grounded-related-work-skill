# Source-Grounded Related Work

版本：v0.1.0。

[下载单技能ZIP](https://github.com/GauntWheelCake/source-grounded-related-work-skill/releases/tag/v0.1.0)

逐句溯源撰写论文的Related Work：从核心论文Introduction提取1–3句压缩成背景，
补齐至少6篇高质量引用；每篇代表性工作从Abstract/Introduction选1–2句缩写为一句；
最后用1–2句归纳有依据的research gap。

这是一份纯文本Agent Skill，不绑定特定模型、浏览器、API或MCP。联网查文献、读取PDF等能力由使用它的环境提供。
默认中文解释、英文正文、在会话中逐句交付；本次用户要求可以覆盖默认设置。

## 文件结构

```text
skills/source-grounded-related-work/
  SKILL.md
  LICENSE
  references/
    citation-verification.md
    worked-example.md
tests/
  cases.md
  fixtures.md
  results.md
```

`skills/source-grounded-related-work/`是安装单元。`tests/`用于维护和验收，不需要安装。
核心文件只使用标准`name`、`description`元数据；引用相对路径，不包含作者电脑路径或真实论文全文。
技能目录和ZIP同时包含许可证，方便完整复制和再分发。

## 使用示例

```text
使用 source-grounded-related-work，帮我写“Serverless Workflow Orchestration”的背景第一句。
先从我提供的几篇核心论文Introduction选原句，再压缩综合；只在会话中输出。
```

```text
继续处理AQUATOPE：从Abstract和Introduction选1–2句自身方法介绍，
缩写为一句，给出原文定位、取舍说明和LaTeX。保留现有citation key。
```

Codex支持显式调用时可写`$source-grounded-related-work`；其他客户端使用其技能选择入口或直接点名。
需要补充文献时提供研究方向、核心论文和现有参考文献库；联网不可用时会如实保留缺项。

## 安装与移植

复制完整的`source-grounded-related-work`文件夹，而不是只复制SKILL.md。
随附的单技能ZIP用于分发；桌面导入接受的格式以当前客户端为准，尚未实际验证。

当前安装位置和产品差异请以对应官方文档为准：

- Codex：项目的`.agents/skills/`或个人的`~/.agents/skills/`。
- Claude Code：项目或个人的`.claude/skills/`。
- WorkBuddy代码开发项目：按官方项目文档使用`.codebuddy/skills/`；桌面可使用技能上传入口。
- Claude网页：按技能上传入口导入包含完整技能目录的ZIP。

ZIP解压结构应为：

```text
source-grounded-related-work/
  SKILL.md
  references/...
```

WorkBuddy市场提交可能需要额外字段；这份通用包不等于已通过市场审核的发布包。
发布到GitHub时可保留仓库结构，并将单技能ZIP作为下载附件。

## 验证与已知限制

格式检查及背景改写、方法缩写、固定正文补引用、候选gap、来源缺失处理、请求范围控制六类行为场景通过，
具体测试结果见[验证记录](tests/results.md)。这些测试只覆盖本环境；
Claude Code、Claude网页和WorkBuddy的实际导入及执行尚待各端实测。
技能不会凭空提供论文访问权限或分区数据库，也不会将检索摘要当作已读全文。

## 维护依据

- [Agent Skills开放规范](https://agentskills.io/specification)：通用文件格式与资源组织。
- [Anthropic编写最佳实践](https://platform.claude.com/docs/en/agents-and-tools/agent-skills/best-practices)：明确触发条件、按需加载与可观察验收。
- [Claude Code Skills](https://code.claude.com/docs/en/skills)：Claude Code安装与调用。
- [Codex Skills](https://learn.chatgpt.com/docs/build-skills)：Codex安装与发现。
- [WorkBuddy技能说明](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Skills-Market)：桌面技能入口。
- [WorkBuddy项目配置](https://www.codebuddy.cn/docs/workbuddy/From-Beginner-to-Expert-Guide/Function-Description/Project)：代码开发项目的技能目录。
- [WorkBuddy开放平台](https://open.workbuddy.cn/docs/skill)：市场提交的独立要求。

这些链接用于维护与核对产品差异，不是运行时依赖。

## 许可

本技能以[MIT许可证](LICENSE)发布。
