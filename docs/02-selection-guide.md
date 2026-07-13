# 选型指南

## 1. 先回答六个问题

1. 最终必须交付 `.pptx` 吗，还是 HTML/PDF/视频也可以？
2. 是否要求逐元素编辑、修改图表数据和复用母版？
3. 演示是商务汇报、学术报告、发布会、课程还是社媒传播？
4. 是否有企业模板、字体、品牌资产和既有 deck？
5. 数据是否敏感，能否调用云端 LLM、搜索或图像 API？
6. 团队能否维护 Node/Python/LibreOffice/Chromium/Docker 环境？

## 2. 决策树

```text
必须原生可编辑 PPTX？
├─ 是
│  ├─ 有固定企业模板 → template/edit-first + PPTX-native
│  ├─ 学术内容 → Academic PPTX + 通用 PPTX Skill
│  ├─ 咨询/管理汇报 → MCK / presentation-skill / ppt-master
│  └─ 要部署服务 → Presenton / PPTAgent / 自建 API
└─ 否
   ├─ 要网页动画或交互 → Frontend Slides / Huashu / Guizang
   ├─ 要最快视觉草案 → Codex PPT 等 image-first
   └─ 要 Markdown 可维护 → Marp/Slidev 类工作流
```

## 3. 按场景推荐组合

### 企业周报/季度汇报

优先：模板编辑 + PPTX-native + 确定性图表 + PDF 交付副本。  
建议：Anthropic PPTX 或 MiniMax PPTX 作为通用工作流，结合组织自己的品牌 Skill；长期项目可参考 presentation-skill 的 source-first 工作区。

### 咨询或董事会 deck

优先：行动标题、证据链、原生图表、严格版式和人工终审。  
建议：MCK PPT Design Skill 或 presentation-skill；若从大量文档生成，可试 ppt-master。不要用整页图片承载需要审计的数据。

### 学术会议/答辩

优先：论证结构、图表可读性、引用、公式、备注和 Q&A。  
建议：Academic PPTX Skill 负责叙事纪律，通用 PPTX Skill 负责生成；LaTeX 重度场景另考察 Beamer Skill。务必检查引用、公式字体和投影可读性。

### 产品发布/品牌演示

优先：视觉冲击、动效、品牌一致性和播放稳定。  
建议：Frontend Slides、Huashu Design 或 Guizang PPT；若必须交 PowerPoint，先做一页导出测试，确认不是不可接受的图片式结果。

### 一次性概念提案

优先：速度和画面。  
建议：Codex PPT 等 image-first；在生成前锁定大纲，在生成后 OCR/人工核对全部文字，并保留可替换的原始图像。

### 团队自托管服务

优先：权限、模型路由、模板管理、队列、审计和成本。  
建议：Presenton 更接近产品/API；PPTAgent/DeepPresenter 更偏 Agent/研究型工作流。先用 3–5 页最小任务验证，再评估部署。

## 4. 选择 Skill 时的红旗

- README 只展示截图，没有可下载样例或生成源文件。
- 声称“可编辑 PPTX”，但没有解释对象级可编辑还是仅文本层可编辑。
- 没有渲染检查、溢出检查或修复循环。
- 强依赖外部模型/API，却没有列出数据流、密钥和成本。
- 仓库没有许可证，或 Skill 子目录与父仓库许可证关系不清。
- 安装命令执行远程脚本，但没有版本固定与代码审查建议。
- 用父级大仓库 Star 直接证明单个 PPT Skill 成熟。
- 模板、字体、图片来源和商用授权不清楚。

## 5. 建议的试用评分表

每项 0–5 分，在同一输入、同一模板和同一模型条件下比较。

| 维度 | 权重建议 | 关键问题 |
|---|---:|---|
| 内容与叙事 | 20% | 结论是否明确、证据是否匹配、结构是否连贯 |
| 视觉设计 | 20% | 层级、留白、对齐、版式多样性是否专业 |
| 可编辑性 | 15% | 文本、形状、图表、母版能否继续修改 |
| 可靠性与 QA | 15% | 是否检测溢出、重叠、占位符和渲染差异 |
| 模板/品牌能力 | 10% | 是否能复用母版、字体、色板和资产 |
| 上手与维护 | 10% | 安装、依赖、文档、可复现性如何 |
| 隐私与许可 | 10% | 数据是否外发、许可证是否适配业务 |

不要把 Star 计入质量分；Star 只作为社区关注度信号。

