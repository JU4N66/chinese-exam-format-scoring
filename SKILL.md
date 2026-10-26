---
name: chinese-exam-format-scoring
description: Score the question-type dimension of Chinese-language entrance-exam papers on a strict 0–2 scale. Use when evaluating a Chinese exam paper against a regional senior- or junior-high entrance-exam question-type baseline, including checks for required question types, question quantity, score allocation, and confused question-type organization.
---

# Chinese Exam Format Scoring

Evaluate only the paper's **question-type dimension**. Return exactly one score: `0`, `1`, or `2`.

## Inputs

1. Obtain the paper to evaluate.
2. Identify its applicable regional exam baseline and read the corresponding Markdown file in `references/`.
3. If the named region has no baseline file, or the baseline is still a placeholder, state that scoring cannot be completed; do not invent a regional standard.

## Evaluation procedure

1. Compare the paper with the baseline for required question types, question count, score allocation, and the organization of question types.
2. Determine the base score using the strict rules below.
3. If question types are confused, subtract `1` from that base score, with a minimum of `0`.
4. Give the final score in the required comparison-table format, with checkable evidence for every deduction.

## Base-score rules

Start from the following mutually exclusive outcome:

| Finding | Base score |
| --- | --- |
| The paper is not set as required and is clearly unreasonable, such as missing required multiple-choice questions or constructed-response questions. | `0` |
| The question count is slightly too high or too low. | `1` |
| The score allocation contains an error or is unreasonable. | `1` |
| None of the above problems exist. | `2` |

Apply these rules strictly:

- A paper that meets the first rule is `0`; do not raise its score because other parts are acceptable.
- If either or both of the two `1`-point conditions occur, the base score is `1`, not a cumulative deduction.
- “Slightly” must be judged against the applicable baseline. Record the expected and actual counts.
- Treat a score-allocation problem as an error or unreasonable distribution in the light of the baseline; record the affected question type and expected versus actual score where the baseline supplies it.
- Do not deduct for content quality, language, answer quality, typography, or other dimensions outside question types.

## Question-type confusion adjustment

After assigning the base score, determine whether question types are confused. Confusion includes inconsistent or unclear type grouping, labeling, ordering, or attribution that makes the paper's question-type structure not correspond to the baseline.

If confusion is present, calculate `max(base score - 1, 0)`. Never deduct more than one point for this adjustment and never go below `0`.

## Required response format

Present every evaluation in Chinese and use tables. Do not replace the comparison tables with prose-only conclusions.

```markdown
题型维度得分：X/2（可用性：不可用 / 有缺陷 / 无问题）

| 项目 | 结论 |
| --- | --- |
| 地区与考试 | …… |
| 对照基准 | …… |

| 检查项 | 地区题型基准 | 待评试卷实际情况 | 判定 | 对得分的影响 |
| --- | --- | --- | --- | --- |
| 大题结构／题号组织 | …… | …… | 符合／不符 | …… |
| 必设选择题 | …… | …… | 符合／缺失／不符 | …… |
| 必设主观或解答题 | …… | …… | 符合／缺失／不符 | …… |
| 题目数量 | …… | …… | 符合／略多／略少／明显不符 | …… |
| 分值设置 | …… | …… | 合理／错误／不合理 | …… |
| 其他地区特定题型 | …… | …… | 符合／缺失／不符 | …… |
| 题型混乱 | …… | …… | 无／有 | …… |

| 计分步骤 | 分数 | 说明 |
| --- | ---: | --- |
| 基准分 | X | …… |
| 题型混乱调整 | 0 / -1 | 无；或“有，扣 1 分” |
| 最终得分 | X/2 | 不可用／有缺陷／无问题 |
```

Apply the table as follows:

- Include every material discrepancy as a separate row; add rows when the regional baseline contains additional required types or fixed item-level score rules.
- State exact expected and actual counts and scores whenever they are available. State “试卷未标明，无法核验” rather than infer an unprinted score.
- Mark the effect on score explicitly: “触发 0 分规则”、“基准分为 1 分”、“不扣分” or “题型混乱扣 1 分”.
- Write a short prose sentence only when needed to clarify evidence that does not fit in a table; never omit the two tables.

Map the final score exactly: `0 = 不可用`、`1 = 有缺陷`、`2 = 无问题`.

## Regional baselines

- Anhui junior-high entrance exam: read `references/anhui-zhongkao.md`.
- Beijing senior-high entrance exam: read `references/beijing-gaokao.md`.

When a user supplies updated baseline content, replace the matching placeholder file while preserving its Markdown structure. Do not alter the scoring rules unless the user explicitly changes them.
