# 美赛摘要写作 Skill

根据完整论文撰写、压缩、润色和排版 MCM/ICM、HiMCM/MidMCM 摘要。仓库由早期的分段式提示词升级为可复用的 `mcm-summary-writing` skill，将内容依据、段落句式、学术表达和一页版面检查纳入同一流程。

## 文件入口

| 文件 | 用途 |
| --- | --- |
| [SKILL.md](skills/mcm-summary-writing/SKILL.md) | 技能入口、使用范围、写作流程与交付检查 |
| [写作要求与沿革](skills/mcm-summary-writing/references/requirements-and-examples.md) | 原始提示词与后续要求的完整对照、句子角色和中英文示例 |
| [模板与版面检查](skills/mcm-summary-writing/references/latex-layout.md) | LaTeX 原位编辑、首行缩进、加粗、字体兼容与一页检查 |
| [中文摘要示例](examples/2025-himcm-a-16390/summary.zh.md) | 2025 HiMCM A 题、16390 队论文的摘要重写测试 |
| [英文 LaTeX 示例](examples/2025-himcm-a-16390/summary.tex) | 已完成一页试排的英文摘要与可编辑源文件 |

## 核心要求

1. **先读完整论文。** 摘要中的方法、数值、单位、条件、验证和模型联系均应有正文依据，不为满足段落模板补造结果。
2. **每个核心段按问题开头。** 第一整句以加粗的“针对问题几，”或“For Problem N,”开头，说明该问题的研究目标；第二句明确说明建立了什么模型。
3. **专业命名。** 模型名称准确反映研究对象和方法，使用通行术语或清楚的描述性名称，避免修饰语堆叠和生造词。
4. **表达平实、严谨、克制。** 不使用夸张修辞，不滥用 `not ... but ...`、`rather than`、引号、冒号、破折号或增补式解释。
5. **保留内容层次。** 开篇交代背景、目标和总体方法，核心段说明数据、方法和结果，结尾提供已有验证与适用边界。段落数量服从实际问题，不强凑三个模型。
6. **突出重点。** 完整加粗逐题引导语，并有选择地加粗模型名、核心方法、主要结果与验证指标；正文第一段也应首行缩进。
7. **在一页内合理充实。** 超页时删冗余，留白时补有依据的重要内容；以实际模板编译结果检查容量，不用固定词数保证一页，不靠缩小字号或页边距挤入内容。
8. **保持任务范围。** 要求中文就输出中文；要求模板试排时再制作英文或指定语言版本。已有 LaTeX 文档在原文件中修改并编译检查。

这些是本技能采用的写作规范。赛事格式仍应按对应比赛、年份和指定模板核对；逐题句式与加粗偏好不是赛事官方规定。

## 使用方法

将整个 [`skills/mcm-summary-writing`](skills/mcm-summary-writing) 目录放入所用工具的技能目录。对于本地 Codex，默认目录为 `~/.codex/skills/`；设置了 `CODEX_HOME` 时使用其下的 `skills/`。需要保留 `agents/` 和 `references/`，不能只复制 `SKILL.md`。

提供完整论文、题目，以及需要使用的模板。可以这样调用：

```text
使用 $mcm-summary-writing，根据这篇完整论文撰写中文摘要，直接在聊天中输出。
```

```text
使用 $mcm-summary-writing，将已确认的摘要译成英文，放入当前打开的 HiMCM LaTeX 模板。
保留逐问题开头、第二句说明模型、首行缩进和重点加粗。
摘要必须完整留在第一页，并合理利用页面空间。
```

## 示例与验证范围

本次示例依据 2025 HiMCM A 题 *Emergency Evacuation Sweeps*、16390 队论文正文重新组织，保留原题问题二至四的建模任务编号。论文来源可通过 [COMAP 赛题资源页](https://www.comap.org/membership/member-resources/item/emergency-evacuation-sweeps) 和 [历年比赛页面](https://www.contest.comap.com/highschool/contests/himcm/previous%20problems.html) 查询。

- 阅读了赛题与论文全文，并核对核心结果表；正文中没有依据的效果与最优性不补写。
- 英文摘要约 476 词，已通过 Codex 内置 LaTeX 编译及一页容量检查。该词数只描述此示例，不是通用长度标准。
- 字号、行距和页边距沿用本次试排模板；保留第一段缩进以及模型、方法和结果的加粗。
- 尚未通过工具完成 PDF 预览的截图目检，也没有独立复现原论文的仿真。

英文示例为适配版面补充了正文已有的方法细节，不能视为中文稿的逐句直译。它是摘要写作与排版测试，不是原参赛摘要；所用 LaTeX 模板是根据 Word 样式适配的本地版本，不是 COMAP 官方 LaTeX 模板。复用示例时应更新队号、题号、年份和论文内容。

## 原始提示词

原有提示词采用“完整论文 → 分段生成 → 压缩 → 英文润色”的流程。本版本保留这一基础，并补充固定句式、证据核对、克制文风和真实模板检查。原始内容仍保留在 [历史版本](https://github.com/ranranrannervous/MathModeling-LLM-Prompts/blob/4abb6708e399234745b8642786e581dee6dee194/README.md) 中。

仓库沿用现有 [MIT License](LICENSE)。示例所依据的参赛论文未随仓库分发，其原文权利归相应权利人。
