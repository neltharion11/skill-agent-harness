# 决策树（第一层）

> **作用**：决定「用什么组合」
> **加载时机**：Step 1

---

## 快速决策

```
任务是什么类型？
│
├─ 简单问答？─── → 直接回答，不需要框架
│
├─ 需要收集需求？─── → Inversion（先问清楚）
│
├─ 需要生成格式内容？─── → Generator（直接生成）
│
├─ 需要审查/评分？─── → Reviewer（检查评估）
│
└─ 需要多步骤执行？
    │
    └─ 是 ──→ Pipeline + 具体 WORKFLOW
              │
              ├─ 研究任务？─── → + research
              ├─ 协调任务？─── → + subagent
              ├─ 压缩任务？─── → + context
              └─ 分析任务？─── → + analysis
```

---

## 决策表

| 任务 | 组合 | 说明 |
|------|------|------|
| 深度研究报告 | **Pipeline + research** | 多步骤研究流程 |
| 多 Agent 协作 | **Pipeline + subagent** | 分解+并行+汇聚 |
| 长任务压缩 | **Pipeline + context** | 上下文管理 |
| 竞品/多维度分析 | **Pipeline + analysis** | 对比评估 |
| 固定格式生成 | Generator | 直接填充模板 |
| 质量审查 | Reviewer | 检查评分 |
| 需求不明确 | Inversion | 先收集信息 |

---

## 决策案例

### 案例 1

**任务**：「研究 AI Agent 市场趋势」
```
决策过程：
1. 多步骤？→ Yes
2. 具体类型？→ 研究
3. 组合：Pipeline + research
```

### 案例 2

**任务**：「帮我同时分析三个产品的竞争格局」
```
决策过程：
1. 多步骤？→ Yes
2. 具体类型？→ 分析
3. 组合：Pipeline + analysis
```

### 案例 3

**任务**：「生成格式一致的周报」
```
决策过程：
1. 多步骤？→ No，格式固定
2. 需要生成？→ Yes
3. 组合：Generator（直接填充）
```

---

_最后更新：2026-04-07 by neltharion11 | https://github.com/neltharion11/skill-agent-harness_
