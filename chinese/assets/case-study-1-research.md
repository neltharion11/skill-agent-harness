# 场景一：深度研究任务

## 触发词
「研究 AI Agent 市场趋势」

## 执行流程

```
Step 1 ──→ Step 2 ──→ Step 3 ──→ Step 4 ──→ Step 5
   │           │           │           │           │
   ▼           ▼           ▼           ▼           ▼
01-DECISION  02-PIPELINE 03-WORKFLOW 04-TEMPLATE 05-QUALITY
  决策        执行框架     research    报告模板    质量检查
```

---

### Step 1 — 决策树

**读取**：`references/01-DECISION.md`

**判断**：
```
任务 = 研究任务？
↓
是
↓
Pipeline + research
```

**输出**：
```
最终判定: Pipeline + WORKFLOWS/research
```

---

### Step 2 — 执行框架

**读取**：`references/02-PIPELINE.md`

**理解**：通用的 4 步执行流程

```
Pipeline = 烹饪方法（不管做什么菜都是：备→炒→装→尝）

Step 1: 计划
Step 2: 执行
Step 3: 汇总
Step 4: 检查
```

---

### Step 3 — 具体工作流

**读取**：`references/03-WORKFLOWS/research.md`

**执行**：
```
Pipeline Step 1（计划）──→ research Step 1：任务分解
                    │
                    ├── 识别主题：AI Agent 市场趋势
                    ├── 拆解维度：技术/商业/竞争/趋势
                    └── 输出：研究规划

Pipeline Step 2（执行）──→ research Step 2：多角度研究
                    │
                    ├── 技术维度：搜索 + 收集
                    ├── 商业维度：搜索 + 收集
                    └── ...

Pipeline Step 3（汇总）──→ research Step 3：信息综合
                    │
                    ├── 去重验证
                    ├── 提取事实
                    └── 识别缺口

Pipeline Step 4（检查）──→ research Step 4：报告输出
                    │
                    └── 对照检查清单
```

---

### Step 4 — 输出模板

**读取**：`references/04-TEMPLATES/research-report.md`

**填充**：
```markdown
# 研究报告：AI Agent 市场趋势

**日期**：2026-04-07

## 执行摘要
{3-5 句话的核心发现}

## 研究发现
### 关键事实
- {事实} [来源: {url}]

### 洞察推断
- {推断} [置信度: 高]

## 参考来源
| # | 来源 | 可靠性 |
|---|------|--------|
| 1 | {url} | 高 |

## 下一步建议
- {建议}
```

---

### Step 5 — 质量检查

**读取**：`references/05-QUALITY.md`

**检查**：
- [ ] 执行摘要完整
- [ ] 每个发现有来源
- [ ] 置信度已标注
- [ ] 知识缺口已识别

---

## 完整对话示例

```
用户：研究 AI Agent 市场趋势

Agent：
[执行前检查]
Q1: 多步骤？→ Yes
Q2: 研究任务？→ Yes
最终判定: Pipeline + WORKFLOWS/research

[Step 1] 加载 01-DECISION.md
→ 确定组合：Pipeline + research

[Step 2] 加载 02-PIPELINE.md
→ 理解 4 步执行框架

[Step 3] 加载 03-WORKFLOWS/research.md
→ 开始执行研究流程...

[Step 4] 加载 04-TEMPLATES/research-report.md
→ 按模板输出报告

[Step 5] 加载 05-QUALITY.md
→ 质量检查通过
```

