---
name: agent-harness
description: |
  Agent 工作框架。统一入口的思考框架 + 工作流 Skill。
  
  触发词（思考模式）：
  研究、规划、设计、思考、模式、流程、步骤、审查、评分、分析、评估、对比、调研、方案、可行性、总结
  
  触发词（工作流）：
  深度研究、调研报告、任务分解、多 Agent、并行执行、上下文压缩、长任务规划
---

# Agent Harness

> **一句话总结**：先想清楚「用什么组合」，再按层级执行。
> 
> **核心关系**：
> ```
> 决策树 → 选择「Pipeline + 哪个 WORKFLOWS」
> Pipeline = 执行框架（通用）
> WORKFLOWS = 工作内容（具体）
> ```

---

## ⚠️ 执行前检查（必须逐项确认）

```
收到任务后，先回答以下问题：

1. [ ] 任务核心是什么？（多步骤/单步）
2. [ ] 需求是否明确？（明确 → 下一步 / 不明确 → 加载 06-INVERSION.md）
3. [ ] 需要多步骤执行吗？（是 → Pipeline + 其他）
4. [ ] 具体做什么内容？（对应 WORKFLOWS 中的哪一个）
```

**回答格式**：
```
[执行前检查]
Q1: xxx → 结论
Q2: xxx → 结论
...
最终判定: Pipeline + WORKFLOWS/{name}
或：最终判定: Inversion（独立模式）
```

---

## 层级关系图（核心理解）

```
┌─────────────────────────────────────────────────────────────┐
│                     层级执行顺序                              │
│                                                             │
│  Step 1 ──→ Step 2 ──→ Step 3 ──→ Step 4                  │
│     │           │           │           │                  │
│     ▼           ▼           ▼           ▼                  │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐              │
│  │决策树   │→│Pipeline │→│WORKFLOW│→│ 模板   │              │
│  │01-     │ │02-      │ │03-     │ │04-     │              │
│  │DECISION│ │PIPELINE │ │WORKFLOWS│ │TEMPLATE│              │
│  └────────┘ └────────┘ └────────┘ └────────┘              │
│                                                             │
│  决策树决定「用哪个组合」，Pipeline 决定「通用执行流程」，     │
│  WORKFLOWS 决定「具体做什么内容」                           │
└─────────────────────────────────────────────────────────────┘
```

### 类比理解

```
烹饪场景：
- 决策树 = 客人点菜（今天想吃辣的）
- Pipeline = 烹饪方法（不管炒什么，先热锅）
- WORKFLOWS = 具体菜谱（鱼香肉丝的做法）
- 模板 = 摆盘方式（盘子怎么放）

软件场景：
- 决策树 = 任务分类（这是研究任务）
- Pipeline = 执行流程（不管研究什么，先分解）
- WORKFLOWS = 研究方法（DeerFlow 的 4 步法）
- 模板 = 报告格式（标题-摘要-正文-结论）
```

---

## 执行流程

### Step 1 — 决策（加载 01-DECISION.md）

```
[Step 1] 读取 references/01-DECISION.md
         决定：Pipeline + 哪个 WORKFLOWS

常见组合：
- Pipeline + research    → 研究任务
- Pipeline + subagent   → 协调任务  
- Pipeline + context    → 压缩任务
- Pipeline + analysis    → 分析任务
```

### Step 2 — 执行框架（加载 02-PIPELINE.md）

```
[Step 2] 读取 references/02-PIPELINE.md
         理解：通用的 4 步执行流程

Pipeline 步骤：
Step 1: 做计划
Step 2: 执行
Step 3: 汇总
Step 4: 检查
```

### Step 3 — 具体内容（加载 03-WORKFLOWS/{name}.md）

```
[Step 3] 读取 references/03-WORKFLOWS/{对应工作流}.md
         执行：具体的工作内容

research = 4 步研究法（分解→研究→综合→报告）
subagent = 4 步协调法（分析→分解→并行→汇聚）
context  = 4 步压缩法（评估→策略→执行→验证）
analysis = 4 步分析法（拆解→收集→对比→结论）
```

### Step 4 — 输出模板（加载 04-TEMPLATES/{name}.md）

```
[Step 4] 读取 references/04-TEMPLATES/{对应模板}.md
         生成：结构化的最终输出
```

### Step 5 — 质量检查（加载 05-QUALITY.md）

```
[Step 5] 读取 references/05-QUALITY.md
         验证：输出质量是否达标
```

---

## 常用组合速查

| 任务类型 | 组合 | 说明 |
|----------|------|------|
| 深度研究报告 | Pipeline + **research** | 多步骤研究流程 |
| 多 Agent 协作 | Pipeline + **subagent** | 任务分解+并行+汇聚 |
| 长任务压缩 | Pipeline + **context** | 上下文管理策略 |
| 竞品分析 | Pipeline + **analysis** | 多维度对比 |
| 需求不明确 | **Inversion**（独立模式） | 先收集需求再决定下一步 |

---

## 禁止行为

- ❌ **跳步**：未完成 Step 1 就跳到 Step 3
- ❌ **混淆层级**：把 Pipeline 和 WORKFLOWS 当成同类东西
- ❌ **缺模板**：输出了内容但格式混乱
- ❌ **缺检查**：没有质量验证就结束

---

## 完成标志

```
[agent-harness 执行完毕]
✓ 已完成 Step 1-5
✓ 组合：Pipeline + WORKFLOWS/{name}
✓ 禁止行为检查：通过
```

---

## 文件索引

| 文件 | 作用 | 加载时机 |
|------|------|----------|
| `SKILL.md` | 入口 + 层级说明 | 触发时 |
| `references/01-DECISION.md` | 决策树 | Step 1 |
| `references/02-PIPELINE.md` | 执行框架 | Step 2 |
| `references/03-WORKFLOWS/research.md` | 研究内容 | Step 3 |
| `references/03-WORKFLOWS/subagent.md` | 协调内容 | Step 3 |
| `references/03-WORKFLOWS/context.md` | 压缩内容 | Step 3 |
| `references/03-WORKFLOWS/analysis.md` | 分析内容 | Step 3 |
| `references/04-TEMPLATES/research-report.md` | 研究模板 | Step 4 |
| `references/04-TEMPLATES/analysis-report.md` | 分析模板 | Step 4 |
| `references/06-INVERSION.md` | 需求澄清（Inversion） | 需求不明确时 |
| `references/05-QUALITY.md` | 质量检查 | Pipeline Step 4 |

---

_最后更新：2026-04-07 by neltharion11 | https://github.com/neltharion11/skill-agent-harness_
