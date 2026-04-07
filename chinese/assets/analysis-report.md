# 分析报告模板

> 用于 WORKFLOWS/analysis 的标准化报告输出

---

# {{TOPIC}} 分析报告

**分析日期**：{{DATE}}
**分析维度**：{{DIMENSIONS}}
**分析方法**：{{METHOD}}

---

## 核心结论

{{CORE_CONCLUSIONS}}

> 1-3 句话的核心发现

---

## 分析维度

{{DIMENSIONS_DESCRIPTION}}

> 维度的定义和评估标准

---

## 评分矩阵

| 对象 | {{DIM_A}} | {{DIM_B}} | {{DIM_C}} | 总分 |
|------|-----------|-----------|-----------|------|
| {{SUBJECT_1}} | {{SCORE_A1}} | {{SCORE_B1}} | {{SCORE_C1}} | {{TOTAL_1}} |
| {{SUBJECT_2}} | {{SCORE_A2}} | {{SCORE_B2}} | {{SCORE_C2}} | {{TOTAL_2}} |
| {{SUBJECT_3}} | {{SCORE_A3}} | {{SCORE_B3}} | {{SCORE_C3}} | {{TOTAL_3}} |

---

## 详细分析

### {{DIM_A}} 分析

{{ANALYSIS_DIM_A}}

### {{DIM_B}} 分析

{{ANALYSIS_DIM_B}}

### {{DIM_C}} 分析

{{ANALYSIS_DIM_C}}

---

## 对比总结

### 优势对比

| 对象 | 主要优势 |
|------|----------|
| {{SUBJECT_1}} | {{ADVANTAGES_1}} |
| {{SUBJECT_2}} | {{ADVANTAGES_2}} |

### 劣势对比

| 对象 | 主要劣势 |
|------|----------|
| {{SUBJECT_1}} | {{DISADVANTAGES_1}} |
| {{SUBJECT_2}} | {{DISADVANTAGES_2}} |

---

## 可操作建议

1. **{建议1}**：{{RECOMMENDATION_1}}
2. **{建议2}**：{{RECOMMENDATION_2}}
3. **{建议3}**：{{RECOMMENDATION_3}}

---

## 置信度与不确定性

### 置信度评估
- 结论置信度：{{CONFIDENCE}}
- 主要依据：{{BASIS}}

### 主要不确定性
- {{UNCERTAINTY_1}}
- {{UNCERTAINTY_2}}

---

_报告生成时间：{{TIMESTAMP}}_
_使用 agent-harness skill 生成 | by neltharion11 | https://github.com/neltharion11/skill-agent-harness_
