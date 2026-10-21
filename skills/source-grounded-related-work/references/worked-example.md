# 从原句到一句介绍：缩写示范

以下论文名、引用键、原文和方法均为教学虚构，不能用于真实论文或参考文献库。

用户请求：只介绍示例论文 Cedar，一句英文，输出 LaTeX。

## 已提供的原文

示例论文 Cedar，Abstract 第2–3句：

> We introduce Cedar, a scheduler that coordinates stage execution with model residency.
> Cedar uses predicted stage demand to preload models while respecting a fixed accelerator-memory budget.

## 选择和缩写

保留三个核心信息：协调 stage execution 与 model residency；依据 predicted stage demand 预加载；
受固定 accelerator-memory budget 约束。删去重复的系统名和“We introduce”等作者叙述。
原文没有说明 GPU 间迁移、零冷启动或公平性，不增加这些能力。

## 可交付的句子

```latex
Cedar~\cite{cedar-example} coordinates stage execution with model residency and uses predicted stage demand to preload models within a fixed accelerator-memory budget.
```

`cedar-example` 只是教学键，不生成真实 BibTeX。

## 举例之后的 gap 如何判断

不能据此写“现有工作没有考虑模型预加载或显存约束”，因为所选原文已明确描述两者。
应检查用户论文真正研究的关系，以及 Cedar 全文在该关系上的实际范围；
若只有这两句材料，只能提出待核查的 gap 方向，不能宣布某项能力不存在。
