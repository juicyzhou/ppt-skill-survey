# 重点项目评测

> 本章基于截至 2026-07-13 的公开仓库资料进行案头评估。Star 是动态快照；“未统一实测”不代表质量结论，只表示尚未在相同环境完成端到端基准。

## A. 通用与原生 PPTX Skill

### 1. Anthropic PPTX Skill

- 仓库：[anthropics/skills/skills/pptx](https://github.com/anthropics/skills/tree/main/skills/pptx)
- 定位：覆盖读取、创建、编辑、模板复用、拆分/合并和 QA 的通用 PPTX Skill。
- 技术路线：MarkItDown 提取、缩略图、Office XML 解包/打包、模板编辑、PptxGenJS 从零生成。
- 优势：触发范围完整；把创建与模板编辑分流；强调接触表、溢出检查和视觉修复，是复杂文档 Skill 的重要参考架构。
- 限制：Anthropic 明确说明 PPTX 等文档 Skill 是 source-available，而非普通开源许可；依赖脚本与运行环境较多。父仓库的高 Star 不能等同于此子 Skill 的独立采用度。
- 适合：研究生产级 PPT Skill 结构、在兼容环境中处理多种 PPTX 任务。
- 不适合：未完成许可证审查就直接再分发或嵌入商业产品。
- 结论：**参考架构首选；采用前先审许可。**

### 2. MiniMax PPTX Generator

- 仓库：[MiniMax-AI/skills/skills/pptx-generator](https://github.com/MiniMax-AI/skills/tree/main/skills/pptx-generator)
- 定位：面向多种 Coding Agent 的 PPTX 创建、读取和编辑 Skill。
- 技术路线：PptxGenJS 生成、MarkItDown 读取、XML 工作流编辑；按页生成可运行 JS 并预览。
- 优势：仓库同时提供 Claude、Codex、Cursor 等接入结构；创建/读取/编辑边界清楚；适合研究跨 Agent 打包。
- 限制：项目处于活跃 Beta；仓库含 `LICENSES/`，采用时应核对具体 Skill 和第三方资产条款，不应只看根目录 MIT 标签。
- 适合：希望在不同编码 Agent 中复用同一 PPTX 工作流的团队。
- 结论：**跨 Agent 与结构化生成值得优先试用。**

### 3. ppt-master

- 仓库：[hugohe3/ppt-master](https://github.com/hugohe3/ppt-master)
- 定位：从 PDF、DOCX、URL 或 Markdown 生成原生可编辑 PowerPoint 的本地工作流/harness。
- 技术路线：内容分析、视觉设计、SVG/图表生成、PPTX 导出；强调真实文本框、形状、图表和动画，而不是整页图片。
- 优势：可编辑性目标明确；输入类型广；展示了较丰富的视觉样例；本地优先理念适合敏感材料。
- 限制：作者明确称其为 harness 而非完整 Agent；最终质量高度依赖模型、素材生成和环境配置。复杂功能仍要通过样例 deck 验证。
- 适合：需要从长文档快速形成可继续编辑的 PPTX。
- 结论：**当前原生可编辑路线中最值得做 PoC 的项目之一。**

### 4. presentation-skill

- 仓库：[siril9/presentation-skill](https://github.com/siril9/presentation-skill)
- 许可证：MIT。
- 定位：把 deck 当作代码管理的 Codex/Agent Skill。
- 技术路线：`outline.json` 等结构化源文件 → PptxGenJS 渲染 → 几何、视觉、内容三类 QA；支持可重建 workspace。
- 优势：source-first、确定性构建、工作区模式、占位符检查和修复后复验思路完整；适合团队版本控制。
- 限制：社区规模小于头部项目；预设与渲染器能力需按企业模板验证。
- 适合：周期性 deck、审计要求高、希望持续维护源文件的团队。
- 结论：**工程化思路突出，尤其适合借鉴 QA 和 workspace 设计。**

## B. HTML-first 视觉型 Skill

### 5. Frontend Slides

- 仓库：[zarazhangrui/frontend-slides](https://github.com/zarazhangrui/frontend-slides)
- 许可证：MIT；调研日约 25.4k Star。
- 定位：用 Coding Agent 生成单文件 HTML 演示，也支持 PPT 转网页演示。
- 技术路线：内联 HTML/CSS/JS，固定 16:9；先生成多个风格预览再选择；可提取 PPT 文本、图片和备注。
- 优势：零 npm/构建依赖；入门视频和跨 Agent 说明完整；视觉选择过程对非设计用户友好；源码可直接修改。
- 限制：核心交付是网页演示；不能把“HTML 源码可编辑”当成“PowerPoint 对象可编辑”。
- 适合：线上分享、开发者演讲、需要视觉和动效但不强求 `.pptx` 的场景。
- 结论：**HTML-first 新手首选。**

### 6. Huashu Design

- 仓库：[alchaincyf/huashu-design](https://github.com/alchaincyf/huashu-design)
- 许可证：MIT；调研日约 21.3k Star。
- 定位：覆盖高保真原型、幻灯片、动画和视频导出的 HTML-native 设计 Skill。
- 优势：视觉哲学、评审维度、风格库和品牌资产输入比单用途 Skill 更丰富；Agent-agnostic。
- 限制：能力范围大，依赖和学习面更宽；“可编辑 PPT”的具体对象级表现要按导出路径验证。
- 适合：一个团队希望用统一设计系统生产多种视觉资产。
- 结论：**综合设计能力强，适合有设计生产需求的团队。**

### 7. Guizang PPT Skill

- 仓库：[op7418/guizang-ppt-skill](https://github.com/op7418/guizang-ppt-skill)
- 许可证：AGPL-3.0；调研日约 21.1k Star。
- 定位：面向 Claude Code、Codex 等 Agent 的单文件 HTML 横向翻页 PPT、配图和封面 Skill。
- 优势：电子杂志与瑞士国际主义两套鲜明视觉系统；中文说明友好；把实际踩坑沉淀为 checklist；兼顾 WebGL 与低功耗运行。
- 限制：原生 PowerPoint 编辑不是主目标；AGPL-3.0 对网络服务和衍生集成的合规影响需专业评估。
- 适合：中文内容分享、观点型演讲、网页播放和社媒衍生资产。
- 结论：**中文视觉叙事很强，采用时重点看交付格式与许可证。**

## C. Image-first Skill

### 8. Codex PPT Skill

- 仓库：[ningzimu/codex-ppt-skill](https://github.com/ningzimu/codex-ppt-skill)
- 许可证：MIT；调研日约 3.5k Star。
- 定位：把文章、报告、论文或课程笔记转成整页图片式 PowerPoint。
- 技术路线：规划大纲和风格 → 调用图像模型逐页生成 → 本地脚本组装 `.pptx`。
- 优势：Codex 原生使用路径明确，也兼容支持 `SKILL.md` 的 Agent；流程文档、变更记录和素材结构较完整；适合快速做高视觉草案。
- 限制：整页图片意味着 E1 可编辑性；文字错误、数据图表真实性、无障碍和打印清晰度要额外检查；通常需要图像 API。
- 适合：概念方案、视觉故事、一次性演示。
- 结论：**image-first 代表项目；不要用于需要逐元素修改或严格数据审计的最终稿。**

## D. 垂直领域 Skill

### 9. Academic PPTX Skill

- 仓库：[Gabberflast/academic-pptx-skill](https://github.com/Gabberflast/academic-pptx-skill)
- 定位：会议报告、研讨会、答辩和基金汇报的内容与设计规范 Skill。
- 优势：要求行动标题、完整论证线、ghost deck 测试、一页一个核心 exhibit、图内标注、逐图引用和结论页驻留；规则很适合学术沟通。
- 限制：仓库没有明显根许可证信息，使用/再分发前必须确认；它更像领域指导层，需配合通用 PPTX 生成能力。
- 适合：已有论文和图表，需要把“论文结构”改造成“演讲结构”的用户。
- 结论：**学术叙事规范优秀，最佳用法是叠加到通用 PPTX Skill。**

### 10. MCK PPT Design Skill

- 仓库：[likaku/Mck-ppt-design-skill](https://github.com/likaku/Mck-ppt-design-skill)
- 许可证：Apache-2.0；调研日约 213 Star。
- 定位：咨询公司风格的原生 PPTX 设计系统。
- 技术路线：python-pptx、数十种布局、图表语法、脚本与 QA pipeline。
- 优势：布局库、扁平化设计和质量检查面向管理汇报；仓库有示例、references、经验文档和测试入口，工程资料较全。
- 限制：强风格定向；“咨询风”不适合品牌发布或强叙事艺术演示。名称与视觉模仿也不代表任何咨询公司的官方认可。
- 适合：战略分析、经营复盘、结构化高密度商务页面。
- 结论：**咨询风原生 PPTX 的实用专项选择。**

## E. 完整系统与导航

### 11. Presenton

- 仓库：[presenton/presenton](https://github.com/presenton/presenton)
- 许可证：Apache-2.0；提供桌面端、Docker、自托管 API 与 MCP。
- 定位：开源 AI 演示生成产品，支持多模型、模板、文件输入、编辑、PPTX/PDF 导出。
- 优势：产品与 API 完整度高；BYOK、Ollama、本地/自托管、模板和多模型路由适合团队服务。
- 限制：不是轻量 Skill；系统部署、安全、认证、模型费用和导出兼容性都要评估。
- 结论：**需要产品化服务时优先 PoC。**

### 12. PPTAgent / DeepPresenter

- 仓库：[icip-cas/PPTAgent](https://github.com/icip-cas/PPTAgent)
- 定位：研究型、反思式演示生成 Agent 框架，提供 CLI、WebUI、MCP、离线与 PPTX 导出。
- 优势：参考 deck 分析、规划、生成、反思和评估形成完整 Agent 研究路线；公开论文与 PPTEval 便于理解内容、设计、连贯性三维评价。
- 限制：依赖面较重，可能涉及 Docker、Playwright、模型、检索、解析和图像服务；Windows 通常依赖 WSL。
- 结论：**研究和复杂私有部署价值高，不是最轻量的入门 Skill。**

### 13. Awesome AI PPT

- 仓库：[ningzimu/awesome-ai-ppt](https://github.com/ningzimu/awesome-ai-ppt)
- 许可证：CC0；自身提供可安装的推荐型 Skill。
- 定位：按 HTML-first、image-first、PPTX-native 与基础设施分类的精选目录。
- 优势：覆盖面广、分类明确、含可编辑性和 Skill/MCP 标签；适合持续发现项目。
- 限制：导航清单不是生成器；Star 和项目描述仍需回到上游验证。
- 结论：**作为持续跟踪入口很有价值，本综述则更强调方法、边界和专业采用。**

## F. 必须认识的底层基础设施

### PptxGenJS

[gitbrent/PptxGenJS](https://github.com/gitbrent/PptxGenJS) 是大量 JavaScript PPT Skill 的底层生成库。优势是对象模型、图表和 Node 生态；挑战是文本度量、布局抽象和视觉 QA。

### python-pptx

[scanny/python-pptx](https://github.com/scanny/python-pptx) 是 Python 生态的主流 PPTX 创建/修改库。适合数据、科研和自动化管线；复杂动画、部分高级 OOXML 能力需额外处理。

### OfficeCLI

[iOfficeAI/OfficeCLI](https://github.com/iOfficeAI/OfficeCLI) 面向 Agent 提供本地 Office 创建、检查、编辑和预览能力，可作为 Skill 的执行基础设施。采用时要验证当前版本、许可证、平台支持和渲染一致性。

