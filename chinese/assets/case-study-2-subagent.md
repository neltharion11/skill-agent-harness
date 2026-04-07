# 场景二：多 Agent 协调任务

## 触发词
「帮我同时分析三个产品的竞争格局」
「任务分解」「多 Agent」「并行执行」

## 执行流程

```
Step 1 ──→ Step 2 ──→ Step 3 ──→ Step 4 ──→ Step 5
   │           │           │           │           │
   ▼           ▼           ▼           ▼           ▼
01-DECISION  02-PIPELINE 03-WORKFLOW 04-TEMPLATE 05-QUALITY
  决策        执行框架     subagent    汇总模板    质量检查
```

---

## 详细步骤

### Step 1 — 决策树

**判断**：
```
任务 = 多步骤？→ 是
任务类型 = 协调（多 Agent）？
↓
是
↓
Pipeline + subagent
```

---

### Step 2 — 执行框架

**读取**：`references/02-PIPELINE.md`

```
Pipeline = 烹饪方法

Step 1: 计划 ──→ 今天做三道菜
Step 2: 执行 ──→ 三口锅同时炒
Step 3: 汇总 ──→ 三道菜放一起
Step 4: 检查 ──→ 试吃评分
```

---

### Step 3 — 具体工作流

**读取**：`references/03-WORKFLOWS/subagent.md`

```
Pipeline Step 1（计划）──→ subagent Step 1：任务分析
                    │
                    ├── 复杂度：3 个产品，>5 步骤 → 需分解
                    ├── 并行性：3 个分析可并行 → 适合多 Agent
                    └── 决策：启动多 Agent 协调

Pipeline Step 2（执行）──→ subagent Step 2-3：分解 + 并行
                    │
                    ├── 创建子任务 A：分析产品 A
                    ├── 创建子任务 B：分析产品 B
                    ├── 创建子任务 C：分析产品 C
                    │
                    ├── 启动 Sub-A（独立 session）
                    ├── 启动 Sub-B（独立 session）
                    ├── 启动 Sub-C（独立 session）
                    │
                    └── 等待所有完成

Pipeline Step 3（汇总）──→ subagent Step 4：结果汇聚
                    │
                    ├── 收集 Sub-A 结果
                    ├── 收集 Sub-B 结果
                    ├── 收集 Sub-C 结果
                    │
                    ├── 横向对比
                    ├── 识别差异
                    └── 生成综合报告
```

---

### Step 4 — 输出模板

**加载**：`references/04-TEMPLATES/analysis-report.md`

---

## 完整对话示例

```
用户：帮我同时分析产品 A、B、C 的竞争格局

Agent：
[执行前检查]
Q1: 多步骤？→ Yes
Q2: 协调任务？→ Yes
最终判定: Pipeline + WORKFLOWS/subagent

[Step 1] 确定组合：Pipeline + subagent

[Step 2] 加载 02-PIPELINE.md
→ 理解：计划→分解→并行→汇聚

[Step 3] 加载 03-WORKFLOWS/subagent.md
→ 开始执行...

[Step 3.1] 任务分析
→ 决定分解为 3 个子任务

[Step 3.2] 启动 3 个子 Agent 并行执行
→ Sub-A：分析产品 A
→ Sub-B：分析产品 B
→ Sub-C：分析产品 C

[Step 3.3] 等待完成，汇聚结果
→ 综合结论：{竞品格局分析}

[Step 4] 按模板输出

[Step 5] 质量检查
```

---

## 与研究任务的区别

| 维度 | 研究任务 | 协调任务 |
|------|----------|----------|
| WORKFLOW | research | subagent |
| Step 2 | 多角度信息收集 | 启动多个子 Agent |
| 子任务 | 并行搜索不同维度 | 并行分析不同产品 |
| 汇聚 | 信息综合 | 结果合并 |

