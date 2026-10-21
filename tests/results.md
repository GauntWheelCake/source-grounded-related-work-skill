# 验证记录

首次验证：2026-10-21。发布前补测：2026-10-22。

## 基线（未提供本skill）

独立新上下文代理收到案例A及其微型文献库的等价材料。实际输出：

> Workflow serving coordinates the execution of dependent model invocations across multiple inference stages~\cite{cachea2025,cacheb2026,cachec2025,cachee2024,cachef2026}.

观察到的差异：只引用5篇；未选出并定位核心论文Introduction的1–3句，也未展示原句到改写的对应。
这验证了“普通写作请求”本身不能可靠带出用户要求的完整流程。

## 使用skill后的测试

独立新上下文代理读取skill与模拟文献库，未读取案例的预期结果及本记录，未联网或写文件。

| 案例 | 实际行为 | 结果 |
|---|---|---|
| A 背景首句 | 选出A/B Introduction三句并定位；说明取舍；给一句英文及六个不同键，注明模拟等级 | 通过 |
| B 方法介绍 | 取A Abstract一句及Introduction一句；压缩为一句LaTeX，保留机制、目标和预算 | 通过 |
| C 固定正文补引用 | 保留给定文字，仅加入引用；判断只有五篇直接相关，拒绝将只谈显存的D用于凑数 | 通过 |
| D 比较性gap | 给两句英文候选判断，并说明片段不足以判断A/B是否处理该耦合，没有否认已有预加载 | 通过 |
| E 等级/原文缺失 | 2026-10-22补测：不联网且缺原文、会刊和分区资料时，报告0篇已核实引用，未编造六篇 | 通过 |
| F 非触发/只给最终正文 | 2026-10-22补测：普通邮件只给译文；已确认句子转LaTeX保持原文且不附解释 | 通过 |

C的人工验收标准已据实际材料澄清：保留原句优先，六篇必须相关；
不足时如实报告属于正确行为，不能为了满足数量而强行加入无关引用。

## 发布前补测的实际输出

新上下文评估者先实际响应E/F请求，再读取本记录核对，未联网或修改文件。

E（来源和等级缺失）输出要点：仅凭两篇论文标题和年份无法核对支撑与SCI分区；
已核实合格引用为0篇；说明需要背景句、原文段落、出版信息及分区体系和年份。

F（普通邮件）实际输出：

> Thank you for your feedback. I will send the revised draft on Friday.

F（只给确认句子的LaTeX）实际输出：

> Cedar coordinates stage execution with model residency.

这里没有需要额外转义的LaTeX字符，因此保持该行正文即满足请求。

本次是有限次数的人工场景测试，不代表统计可靠性评测，也不代表实际学术检索或多平台客户端验收。

## 格式与结构

- skill-creator自带quick_validate.py：通过（输出`Skill is valid!`）。
- SKILL.md为84行，标准frontmatter仅含name/description，名称与目录一致。
- 两个相对资源链接可解析，技能运行文件中无个人绝对路径或外部程序依赖。
- 单技能ZIP校验通过；发布包含技能根目录下的三个Markdown文件和MIT许可证，逐项内容与源文件一致。
- 已安装到个人skills目录，三个文件的SHA-256均与源文件一致；没有覆盖已有同名技能。

## 兼容性边界

格式检查和本环境的行为测试不等于Claude、WorkBuddy的客户端实际验收。
