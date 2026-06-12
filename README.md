# Academic Image PPT

`academic-image-ppt` 是一个 Codex Skill，用于把论文、毕业论文、开题/答辩材料、研究报告或学术手稿整理成图片版学术 PPT。它的核心路线是：先生成一张张完整的 16:9 slide 图片，再把图片全页嵌入 PPTX。

它适合需要高质量视觉表达、严格遵守论文事实、并愿意先确认大纲和样页再批量生成的学术汇报场景。

![Academic Image PPT reference gallery - black white navy](skills/academic-image-ppt/assets/reference-thumbnails/参考图1（黑白+藏蓝）.png)

![Academic Image PPT reference gallery - navy burgundy accent](skills/academic-image-ppt/assets/reference-thumbnails/参考图2（黑白+藏蓝+重点酒红）.png)

> From academic source material to source-faithful image-based defense/report decks.

## 它解决什么问题？

很多学术 PPT 的难点不是“做几页漂亮模板”，而是把论文内容变成一套能讲清楚研究问题、方法、实验和结论的学术表达：

- 从 PDF、DOCX、论文正文或研究报告中提炼汇报结构。
- 把论文信息转成页级 `governing message` 和证据角色。
- 在生成图片前先确认 alignment、deck blueprint、缩略图风格和样页。
- 对中文、指标、公式、学校/作者信息、图表数值做高风险 QA。
- 最终交付 PNG 页面和每页一张全幅图片的 image-only PPTX。

## 30 秒开始

把 skill 目录复制到你的 Codex skills 目录：

```powershell
# Windows PowerShell
New-Item -ItemType Directory -Force "$env:USERPROFILE\.codex\skills\academic-image-ppt" | Out-Null
Copy-Item -Recurse -Force .\skills\academic-image-ppt\* "$env:USERPROFILE\.codex\skills\academic-image-ppt"
```

```bash
# macOS / Linux
mkdir -p ~/.codex/skills/academic-image-ppt
cp -R ./skills/academic-image-ppt/. ~/.codex/skills/academic-image-ppt/
```

然后在 Codex 里这样触发：

```text
请使用 academic-image-ppt，把我上传的论文生成一套中文毕业答辩图片版 PPT。

目标受众：答辩委员会老师
汇报时长：15 分钟
学校/专业/导师/日期：按我提供的信息填写
风格：正式学术答辩，白底，蓝色为主色
输出格式：PNG + image-only PPTX

请先做目标对齐和 Deck Blueprint，不要直接生成图片。
```

## 工作流

1. 目标对齐：确认论文文件、汇报场景、受众、页数或时长、学校信息、作者信息、导师、日期、输出格式和风格偏好。
2. 内容抽取：从论文或报告中整理 `Academic Input Pack`，保证中文文本没有乱码。
3. 蓝图设计：生成页级 `Deck Blueprint`，包含标题、主信息、证据角色、视觉机会、来源证据和 QA 风险。
4. 蓝图确认：等待用户确认或逐页修改，不确认不进入设计阶段。
5. 风格缩略图：生成 3 个 thumbnail style variants，让用户选择视觉系统。
6. 样页确认：生成 1-2 页全尺寸样页，确认文字、图表、密度和风格继承。
7. 批量生成：按已确认的蓝图和视觉 contract 逐页生成完整 slide 图片。
8. 质量检查：制作 contact sheet，检查中文、数字、图表、页码、学校/作者信息和整体一致性。
9. PPTX 打包：把每张 PNG 作为单页全幅图片嵌入 PPTX，并验证页数和图片数量。

## 输出物

默认输出通常包含：

```text
image_pages/
  slide_01.png
  slide_02.png
qa/
  alignment-summary.md
  deck-blueprint.md
  thumbnail-style-contract.md
  contact-sheet.png
output/
  academic-image-ppt-image-only.pptx
```

PPTX 中每页是一张完整图片。它可以用于放映、替换整页图片或重新生成，但默认不能逐字编辑文本框。

## 适合 / 不适合

适合：

- 毕业答辩、开题答辩、中期检查、课程汇报、学术讲座。
- 从论文、报告、PDF、DOCX 或手稿生成图片版学术 PPT。
- 需要先确认大纲、风格缩略图和样页，再批量生成。
- 对中文、公式、学校信息、指标含义和图表数值要求较高的汇报。

不适合：

- 需要整套全对象原生可编辑 PPTX 的任务。
- 只想简单套模板或快速美化已有 PPT。
- 不愿意经过 alignment、blueprint、thumbnail、sample gate 的批量生成任务。
- 需要模型凭空补实验数据、引用、指标或学校信息的任务。

## 目录结构

```text
academic-image-ppt/
  README.md
  LICENSE
  skills/
    academic-image-ppt/
      SKILL.md
      agents/
      assets/
      references/
```

## FAQ

### 生成的 PPTX 能逐字修改吗？

默认不能。这个 skill 的交付路线是 image-only PPTX：每页是一张完整图片。需要改字、改数字或改图表时，建议回到蓝图、样页或单页 prompt 层重新生成。

### 为什么不能直接批量生成？

学术 PPT 对事实、术语、指标和图表含义很敏感。先确认蓝图、风格缩略图和样页，可以避免整套 deck 在结构、风格或文字质量上跑偏。

### 可以只输出 PNG 吗？

可以。PPTX 只是把已确认的 PNG 机械打包成演示文件；如果不需要演示文件，可以只交付 PNG。

### 可以用于英文论文吗？

可以。默认规则强调中文学术答辩 QA，但英文论文同样适用：仍然需要先确认目标、蓝图、风格和样页，并严格遵守原文事实。
