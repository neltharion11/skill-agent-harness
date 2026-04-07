# 🎯 Agent Harness

> **Unified Thinking Framework + Workflow Skill for Agents**
> When executing complex tasks, an Agent should first decide "what combination to use", then execute layer by layer.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

---

## ✨ Key Features

| Feature | Description |
|---------|-------------|
| 🧠 **Two Modes** | Pipeline (multi-step framework) / Inversion (requirements clarification) |
| 📦 **Modular Design** | Decision Tree → Pipeline → WORKFLOWS → Templates → Quality Check |
| 🔄 **Reusable** | Any complex task can be decomposed into fixed combinations |
| 📖 **Ready to Use** | Includes complete Templates, Quality Checklist, Case Studies |
| 🌏 **Cross-Agent** | Works with all OpenClaw Agents |

---

## 🏗️ Architecture Overview

```
Step 1 ──→ Step 2 ──→ Step 3 ──→ Step 4 ──→ Step 5
   │           │           │           │           │
   ▼           ▼           ▼           ▼           ▼
01-DECISION  02-PIPELINE 03-WORKFLOWS 04-TEMPLATE 05-QUALITY
  Decision    Framework    Workflow    Template    Quality Check
```

### Analogy

```
🍳 Cooking Scenario:
- Decision Tree = Customer orders ("I want something spicy today")
- Pipeline = Cooking method (no matter what you cook, first heat the pan)
- WORKFLOWS = Specific recipes (how to make fish-flavored shredded pork)
- Template = Plating style (how to arrange the plate)
```

---

## 🚀 Quick Start

### Install

```bash
# via ClawHub
clawhub install agent-harness

# via SkillHub
skillhub install agent-harness
```

### Trigger Words (Auto-activate Skill)

```
research, plan, design, think, pattern, process, step, review, score, analyze,
evaluate, compare, survey, solution, feasibility, summary, deep research,
research report, task decomposition, multi-agent, parallel execution,
context compression, long-task planning
```

### Workflow

```
Receive Task
    ↓
Trigger agent-harness skill
    ↓
[Step 1] Decision Tree → Determine Combination
[Step 2] Pipeline → 4-Step Execution
[Step 3] WORKFLOW → Specific Content
[Step 4] Template → Structured Output
[Step 5] Quality Check → Verification
```

---

## 📁 Directory Structure

```
english/
├── SKILL.md                      # Entry + Layer Description
└── references/
    ├── 01-DECISION.md           # Decision Tree
    ├── 02-PIPELINE.md            # Execution Framework (4 steps)
    ├── 03-WORKFLOWS/            # Workflow Content
    │   ├── research.md          # Research Mode
    │   ├── subagent.md         # Coordination Mode
    │   ├── context.md          # Compression Mode
    │   └── analysis.md         # Analysis Mode
    ├── 04-TEMPLATES/            # Output Templates
    │   ├── research-report.md
    │   └── analysis-report.md
    ├── 05-QUALITY.md           # Quality Check
    └── 06-INVERSION.md          # Requirements Clarification (Standalone Mode)
```

---

## 🎯 Mode Description

| Mode | Description | Use Case |
|------|-------------|----------|
| **Pipeline** | Multi-step task execution framework | Research, planning, analysis tasks |
| **Inversion** | Requirements clarification | Gather requirements before execution |

### Common Combinations

| Task Type | Combination | Description |
|-----------|-------------|-------------|
| 📝 Deep Research Report | `Pipeline + research` | Multi-step research flow |
| 🤖 Multi-Agent Coordination | `Pipeline + subagent` | Task decomposition + parallel + merge |
| 📦 Long-Task Compression | `Pipeline + context` | Context management strategy |
| ⚖️ Competitive Analysis | `Pipeline + analysis` | Multi-dimensional comparison |
| ❓ Unclear Requirements | `Inversion` (standalone) | Gather requirements first |

---

## ⚙️ Pipeline 4-Step Execution Flow

```
Step 1: Plan      → Understand goals, decompose tasks
Step 2: Execute   → Act according to plan, record results
Step 3: Summarize → Organize outputs, merge information
Step 4: Check     → Quality verification, iterate if needed
```

---

## 🧪 Case Studies

<details>
<summary><strong>📄 Case Study 1: Research Mode</strong></summary>

```
Input: Research embedded Linux learning path
Trigger: Pipeline + research
Execute:
  1. Decompose sub-topics
  2. Parallel search & collect
  3. Summarize into report
Output: Complete research report
```
</details>

<details>
<summary><strong>🤖 Case Study 2: Sub-Agent Coordination</strong></summary>

```
Input: Recruit backend engineer
Trigger: Pipeline + subagent
Execute:
  1. Analyze requirements
  2. Decompose sub-tasks
  3. Parallel execution
  4. Merge results
Output: Candidate recommendation list
```
</details>

---

## 🤝 Contributing

Issues and PRs are welcome!

---

## 📄 License

MIT License

---

_Last updated: 2026-04-07 by neltharion11 | https://github.com/neltharion11/skill-agent-harness_
