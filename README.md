# PPT 制作 Skill 综述

> 面向 AI Agent、Codex、Claude Code 与演示文稿自动化开发者的选型、上手和工程实践指南。

**调研快照：2026-07-13** ｜ **语言：中文** ｜ **范围：公开 GitHub 仓库** ｜ **许可：[CC BY 4.0](LICENSE)**

## 一分钟结论

GitHub 上的“PPT Skill”至少包含四种不同技术路线。选错路线，通常比选错具体仓库影响更大。

| 目标 | 优先考察 | 主要代价 |
|---|---|---|
| 交付可逐元素编辑的 `.pptx` | [Anthropic PPTX Skill](https://github.com/anthropics/skills/tree/main/skills/pptx)、[ppt-master](https://github.com/hugohe3/ppt-master)、[MiniMax PPTX Generator](https://github.com/MiniMax-AI/skills/tree/main/skills/pptx-generator) | 版式编程、渲染环境和 QA 成本较高 |
| 追求网页动效和视觉表现 | [Frontend Slides](https://github.com/zarazhangrui/frontend-slides)、[Huashu Design](https://github.com/alchaincyf/huashu-design)、[Guizang PPT Skill](https://github.com/op7418/guizang-ppt-skill) | HTML 源码可编辑不等于 PowerPoint 元素可编辑 |
| 追求最快的高视觉完成度 | [Codex PPT Skill](https://github.com/ningzimu/codex-ppt-skill) 等 image-first 工作流 | 常是整页图片，文字、图表难以在 PowerPoint 内修改 |
| 学术报告/答辩 | [Academic PPTX Skill](https://github.com/Gabberflast/academic-pptx-skill) + 原生 PPTX 渲染 Skill | 领域 Skill 多负责叙事规范，仍需底层生成器 |
| 咨询/管理汇报 | [MCK PPT Design Skill](https://github.com/likaku/Mck-ppt-design-skill)、[presentation-skill](https://github.com/siril9/presentation-skill) | 需要结构化输入和迭代校验 |
| 自建团队服务或 API | [Presenton](https://github.com/presenton/presenton)、[PPTAgent / DeepPresenter](https://github.com/icip-cas/PPTAgent) | 部署和模型依赖明显更重 |
| 只想快速筛选工具 | [Awesome AI PPT](https://github.com/ningzimu/awesome-ai-ppt) | 它是导航 Skill，不是生成引擎 |

**默认建议：** 若交付物必须在 PowerPoint 中继续修改，先选 PPTX-native；若交付物主要用于播放或传播，HTML-first 更灵活；若时间最紧且不要求逐元素编辑，才优先 image-first。

## 如何使用本综述

1. 先读 [技术版图与核心概念](docs/01-landscape.md)，确认你需要的是 Skill、应用、MCP 还是底层库。
2. 用 [选型指南](docs/02-selection-guide.md) 按交付格式、可编辑性、部署和合规要求缩小范围。
3. 阅读 [重点项目评测](docs/03-project-reviews.md)，了解每个项目的优势、限制与适用边界。
4. 跟随 [快速上手](docs/04-quickstart.md)，用一个最小任务验证环境和产物。
5. 团队引入前，按 [工程化与质量保障](docs/05-engineering-practice.md) 建立可重复的 QA 门禁。
6. 需要复核范围和评分依据时，查阅 [调研方法与来源](docs/06-methodology.md) 及 [项目数据表](data/projects.csv)。

## 核心认知

### 1. “能导出 PPTX”不等于“原生可编辑 PPTX”

- **原生可编辑**：文字、形状、图表等是 PowerPoint 对象。
- **部分可编辑**：背景可能是一张图，只叠加部分文字或结构化对象。
- **图片式**：每页主要是一张完整图片；可以换页，但很难改内容。
- **源码可编辑**：HTML/React/Markdown 可改，并不表示导出的 PPTX 可逐元素修改。

### 2. Skill 与生成引擎不是同一层

`SKILL.md` 主要规定何时触发、如何规划、调用哪些脚本以及怎样验收。真正写出文件的通常是 PptxGenJS、python-pptx、Office XML、浏览器渲染器或 PowerPoint COM/API。优秀方案往往是“领域 Skill + 生成器 + 渲染器 + QA”的组合，而不是单个提示词。

### 3. 视觉预览与回归检查是生产级分水岭

只验证“文件成功生成”远远不够。至少应完成：结构检查、渲染成图片、缩略图总览、溢出/重叠检查、字体与跨平台检查，以及一次修复后复验。

## 本综述的重点推荐

这里的“推荐”指在某一场景中值得优先试用，不是绝对排名。

| 项目 | 类型 | 最适合 | 关键判断 |
|---|---|---|---|
| [Anthropic PPTX Skill](https://github.com/anthropics/skills/tree/main/skills/pptx) | 通用 PPTX Skill | 学习复杂 Skill 的参考架构；创建、编辑、读取 PPTX | 工作流完整，但文档 Skill 为 source-available，须核对许可 |
| [MiniMax PPTX Generator](https://github.com/MiniMax-AI/skills/tree/main/skills/pptx-generator) | 通用 PPTX Skill | 需要 PPTX 创建、读取、XML 编辑的 Agent | 结构清晰，仓库支持多种 Agent；仍需逐文件核对许可证 |
| [ppt-master](https://github.com/hugohe3/ppt-master) | PPTX-native harness/Skill | 从文档、URL、Markdown 生成高可编辑 PPTX | 原生对象与可编辑性突出；模型质量和运行环境决定上限 |
| [presentation-skill](https://github.com/siril9/presentation-skill) | Codex/Agent Skill | 把 deck 当代码管理、强调可复现构建和 QA | source-first 与质量门禁强；生态体量较小 |
| [Frontend Slides](https://github.com/zarazhangrui/frontend-slides) | HTML-first Skill | 单文件网页演示、强视觉、PPT 转 Web | 上手轻、无构建依赖；不是原生 PPTX 生产线 |
| [Huashu Design](https://github.com/alchaincyf/huashu-design) | HTML-native 设计 Skill | 幻灯片、原型、动画、视频的统一视觉生产 | 设计系统丰富；范围大，学习和依赖成本高于单用途 Skill |
| [Guizang PPT Skill](https://github.com/op7418/guizang-ppt-skill) | HTML-first Skill | 中文叙事型分享、杂志/瑞士风网页 PPT | 风格鲜明、清单扎实；AGPL-3.0 对集成方式有约束 |
| [Codex PPT Skill](https://github.com/ningzimu/codex-ppt-skill) | Image-first Skill | 快速生成高视觉完成度的整页图片式 PPT | 流程成熟、安装清晰；不适合重编辑和数据审计 |
| [Academic PPTX Skill](https://github.com/Gabberflast/academic-pptx-skill) | 领域叙事 Skill | 会议报告、答辩、学术研讨 | 行动标题、论证、引文规范好；应与渲染 Skill 配合 |
| [MCK PPT Design Skill](https://github.com/likaku/Mck-ppt-design-skill) | 咨询风 PPTX Skill | 管理汇报、咨询风分析 deck | 布局与 QA 体系明确；风格专门化，不适合所有内容 |
| [Presenton](https://github.com/presenton/presenton) | 完整应用/API/MCP | 自托管、多人使用、模板与模型切换 | 产品化程度高；不是轻量 `SKILL.md` |
| [PPTAgent / DeepPresenter](https://github.com/icip-cas/PPTAgent) | 研究型 Agent 系统/MCP | 文档到演示、反思式生成、研究与私有部署 | 能力面广；部署复杂，不适合作为第一个轻量 Skill |

## 仓库结构

```text
ppt-skill-survey/
├── README.md
├── CONTRIBUTING.md
├── docs/
│   ├── 01-landscape.md
│   ├── 02-selection-guide.md
│   ├── 03-project-reviews.md
│   ├── 04-quickstart.md
│   ├── 05-engineering-practice.md
│   └── 06-methodology.md
└── data/
    └── projects.csv
```

## 重要说明

- Star、功能、安装方式和许可证会变化；表内数据是调研日快照，不应替代对上游仓库的复核。
- 父仓库 Star 不能直接代表其中某个子 Skill 的成熟度，例如 `anthropics/skills` 和 `MiniMax-AI/skills`。
- 本综述没有对全部项目运行统一端到端基准；未实测的判断依据 README、`SKILL.md`、目录结构、许可证和公开示例，已在方法论中明确区分。
- “开源”“source-available”“免费使用”不是同义词。生产采用前请阅读具体 LICENSE、模型条款、字体和素材许可。

## 维护

欢迎通过 PR 更新项目状态、补充复现实验或纠正描述。贡献前请阅读 [CONTRIBUTING.md](CONTRIBUTING.md)。
