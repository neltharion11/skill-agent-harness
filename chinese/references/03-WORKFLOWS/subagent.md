# Subagent Workflow（子 Agent 协调工作流）

> **作用**：Pipeline 的「具体工作内容」层
> **适用场景**：任务分解、多 Agent、并行执行、协调
> **加载时机**：Pipeline Step 2 执行时
> **组合**：Pipeline + subagent

---

## 关系说明

```
Pipeline（方法）         subagent（内容）
────────────────────────────────────────
Step 1: 计划      ←→  任务分析
Step 2: 执行      ←→  启动子 Agent
Step 3: 汇总      ←→  结果汇聚
Step 4: 检查      ←→  质量验证
```

---

## 4 步协调流程

### Step 1 — 任务分析（对应 Pipeline 计划）

**问题**：任务能分解吗？

**分析维度**：
1. 复杂度：>5 步骤？
2. 并行性：可独立执行？
3. 专业性：需多领域？

**决策**：单 Agent 执行 vs 多 Agent 协调

---

### Step 2 — 任务分解（对应 Pipeline 执行）

**问题**：怎么分解？

**分解原则**：
| 原则 | 说明 |
|------|------|
| **独立性** | 子任务无依赖，可独立运行 |
| **完整性** | 覆盖全部范围 |
| **粒度** | 不过细（Agent 开销），不过粗（失去并行价值） |

**输出**：
```markdown
## 任务分解

### 主任务
{主任务}

### 子任务
1. **[Agent-A]**：{描述} → 输出：{格式}
2. **[Agent-B]**：{描述} → 输出：{格式}
3. **[Agent-C]**：{描述} → 输出：{格式}
```

---

### Step 3 — 并行执行（对应 Pipeline 汇总）

**问题**：怎么协调多个子 Agent？

**OpenClaw API**：
```markdown
启动子 Agent：
sessions_spawn({
  task: "{任务描述}",
  runtime: "subagent",
  mode: "run",
  cleanup: "delete"   // 用完即删，保持会话干净
})

等待结果：
sessions_yield()   // 暂停，等待子 Agent 推送结果
                  // 每个子 Agent 完成都会触发一次事件推送
                  // 可以多次 yield，等完所有子 Agent
```

**执行示例**（3 个子 Agent 并行）：
```markdown
1. sessions_spawn → Agent-A
2. sessions_spawn → Agent-B
3. sessions_spawn → Agent-C
4. sessions_yield → 等待推送
   ← Agent-A 结果回来
5. sessions_yield → 继续等待
   ← Agent-B 结果回来
6. sessions_yield → 继续等待
   ← Agent-C 结果回来
（所有子 Agent 完成）
```

**⚠️ 推送机制**：
- 子 Agent **不需要**调用 sessions_send 推送结果
- OpenClaw 内置 `subagent_announce` 机制：子 Agent 完成后自动通过 completion 事件推送
- 每个子 Agent 完成都会触发一次事件推送给父会话

---

### Step 4 — 结果汇聚（对应 Pipeline 检查）

**问题**：如何合并结果？

**汇聚策略**：
| 策略 | 适用场景 |
|------|----------|
| 顺序合并 | 时间线任务 |
| 分类聚合 | 多维度任务（取各维度结果拼接） |
| 综合判断 | 选择类任务（汇总各视角结论） |

**输出**：
```markdown
## 结果汇聚

### 子任务结果
- Agent-A：{结果}
- Agent-B：{结果}
- Agent-C：{结果}

### 综合结论
{最终输出}
```

---

## 快速执行清单

```
subagent 快速执行清单：
□ 加载 03-WORKFLOWS/subagent.md
□ 确认任务可分解且值得分解
□ 分解为 2-N 个独立子任务
□ 为每个子任务调用 sessions_spawn
□ 调用 sessions_yield 等待结果（可多次）
□ 收集所有结果，汇聚输出
□ 执行 Pipeline Step 4（模板）+ Step 5（质量检查）
```

---

## ⚠️ 完整输出方案（重要工程发现）

**问题**：completion 事件推送的内容会被 OpenClaw 格式化层截短/摘要化，用户看不到子 Agent 的完整原始输出。

**推荐方案：子 Agent 写文件 + 父 Agent 通知**

```markdown
子 Agent prompt 设计：
1. 执行任务（研究/分析/代码等）
2. 将完整输出保存到文件：{用户工作目录}/subagent_reports/{任务名}_{时间戳}.md
3. sessions_send 通知父 Agent「报告已保存，文件路径：xxx」
   （如果 sessions_send 失败则忽略，不影响主流程）
4. 用 sessions_yield 结束

父 Agent 收到通知后：
- 确认文件存在
- 在对话中告知用户文件路径
- 用户自行读取完整文件
```

**文件路径规范**：
```
{用户配置的工作目录}/subagent_reports/
├── {任务名}_{YYYYMMDD_HHMM}.md
├── AI_Agent_研究方向_20260407_2156.md
└── ...
```

> 实际路径由用户在 TOOLS.md 中配置（如 `D:/subagent_reports/` 或其他目录）

**为什么不用 sessions_send**：
- 子 Agent 调用 sessions_send 有时不成功（工具调用限制）
- 父 Agent 读 history 会额外消耗 token
- 写文件方案最稳定，用户可随时读取

---

## 测试验证记录

| 测试 | 结果 | 说明 |
|------|------|------|
| 并行 3 子 Agent | ✅ 成功 | 各自独立完成，推送正常 |
| sessions_yield 多次唤醒 | ✅ 成功 | 每完成一个子 Agent 触发一次事件 |
| 推送机制 | ✅ 走 subagent_announce 内置事件 | 不需要子 Agent 自己调用 sessions_send |
| 写文件 + sessions_send | ✅ 成功 | 完整报告写入文件，sessions_send 可选 |
| runTimeoutSeconds=0 | ✅ 有效 | 无时间限制，子 Agent 跑完为止 |
| session 模式 + thread=true | ❌ 飞书不支持 | channel plugin 未注册相关 hook |

---

_最后更新：2026-04-07 by neltharion11 | https://github.com/neltharion11/skill-agent-harness_
