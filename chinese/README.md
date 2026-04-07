# 🎯 Agent Harness

> **统一入口的思考框架 + 工作流 Skill**
> 让 Agent 执行复杂任务时，先想清楚「用什么组合」，再按层级执行。

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## ✨ 核心特性

| 特性 | 说明 |
|------|------|
| 🧠 **两种模式** | Pipeline（多步骤框架）/ Inversion（需求澄清） |
| 📦 **模块化设计** | 决策树 → Pipeline → WORKFLOWS → 模板 → 质量检查，层层递进 |
| 🔄 **可复用** | 任何复杂任务都可以分解为固定组合 |
| 📖 **开箱即用** | 附带完整 Templates、Quality Checklist、Case Studies |
| 🌏 **跨 Agent** | 适用于所有 OpenClaw Agent |

---

## 🏗️ 架构概览

```
Step 1 ──→ Step 2 ──→ Step 3 ──→ Step 4 ──→ Step 5
   │           │           │           │           │
   ▼           ▼           ▼           ▼           ▼
01-DECISION  02-PIPELINE 03-WORKFLOWS 04-TEMPLATE 05-QUALITY
  决策        执行框架     工作内容     输出模板     质量检查
```

### 类比理解

```
🍳 烹饪场景：
- 决策树 = 客人点菜（今天想吃辣的）
- Pipeline = 烹饪方法（不管炒什么，先热锅）
- WORKFLOWS = 具体菜谱（鱼香肉丝的做法）
- 模板 = 摆盘方式（盘子怎么放）
```

---

## 🚀 快速开始

### 安装

```bash
# via ClawHub
clawhub install agent-harness

# via SkillHub
skillhub install agent-harness
```

### 触发词（自动激活 Skill）

```
研究、规划、设计、思考、模式、流程、步骤、审查、评分、分析、
评估、对比、调研、方案、可行性、总结、深度研究、调研报告、
任务分解、多 Agent、并行执行、上下文压缩、长任务规划
```

### 工作流程

```
收到任务
    ↓
触发 agent-harness skill
    ↓
[Step 1] 决策树 → 确定组合
[Step 2] Pipeline → 4步执行
[Step 3] WORKFLOW → 具体内容
[Step 4] 模板 → 结构化输出
[Step 5] 质量检查 → 验证
```

---

## 📁 目录结构

```
chinese/
├── SKILL.md                      # 入口 + 层级说明
└── references/
    ├── 01-DECISION.md           # 决策树
    ├── 02-PIPELINE.md            # 执行框架（4步）
    ├── 03-WORKFLOWS/            # 工作内容
    │   ├── research.md          # 研究模式
    │   ├── subagent.md         # 协调模式
    │   ├── context.md          # 压缩模式
    │   └── analysis.md         # 分析模式
    ├── 04-TEMPLATES/            # 输出模板
    │   ├── research-report.md
    │   └── analysis-report.md
    ├── 05-QUALITY.md           # 质量检查
    └── 06-INVERSION.md          # 需求澄清（独立模式）
```

---

## 🎯 模式说明

| 模式 | 说明 | 使用场景 |
|------|------|---------|
| **Pipeline** | 多步骤任务执行框架 | 研究、规划、分析等多步骤任务 |
| **Inversion** | 需求澄清 | 需求模糊时先收集信息再执行 |

### 常用组合

| 任务类型 | 组合 | 说明 |
|----------|------|------|
| 📝 深度研究报告 | `Pipeline + research` | 多步骤研究流程 |
| 🤖 多 Agent 协作 | `Pipeline + subagent` | 任务分解+并行+汇聚 |
| 📦 长任务压缩 | `Pipeline + context` | 上下文管理策略 |
| ⚖️ 竞品分析 | `Pipeline + analysis` | 多维度对比 |
| ❓ 需求不明确 | `Inversion`（独立模式） | 先收集需求再决定 |

---

## ⚙️ Pipeline 4 步执行流程

```
Step 1: 做计划     → 理解目标，分解任务
Step 2: 执行       → 按计划行动，记录结果
Step 3: 汇总       → 整理产出，合并信息
Step 4: 检查       → 质量验证，不合格则返工
```

---

## 🧪 Case Studies

<details>
<summary><strong>📄 Case Study 1: 研究模式</strong></summary>

```
输入：研究嵌入式Linux学习路线
触发：Pipeline + research
执行：
  1. 分解子主题
  2. 并行搜索收集
  3. 汇总成报告
输出：完整研究报告
```
</details>

<details>
<summary><strong>🤖 Case Study 2: 子 Agent 协调</strong></summary>

```
输入：招聘后端工程师
触发：Pipeline + subagent
执行：
  1. 分析需求
  2. 分解子任务
  3. 并行执行
  4. 汇聚结果
输出：候选人推荐列表
```
</details>

---

## 🤝 贡献

欢迎提交 Issue 和 PR！

---

## 📄 License

MIT License

---

_最后更新：2026-04-07 by neltharion11 | https://github.com/neltharion11/skill-agent-harness_
