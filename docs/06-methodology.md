# 调研方法与来源

## 1. 调研问题

本综述试图回答：

- GitHub 上哪些项目是真正可由 Agent 使用的 PPT Skill？
- 哪些是完整应用、MCP 或底层库，不能与 Skill 直接比较？
- 不同路线在可编辑性、视觉、部署、QA 和许可上有什么权衡？
- 新用户怎样用最少成本做出可靠的技术选型？

## 2. 检索范围

- 快照日期：2026-07-13。
- 数据源：公开 GitHub 仓库、README、`SKILL.md`、目录结构、LICENSE、公开样例与论文/项目说明。
- 关键词包括：PPT/PPTX、PowerPoint、slides、presentation、`SKILL.md`、Agent Skill、PptxGenJS、python-pptx、HTML-to-PPTX、image-first、MCP。
- 重要二级入口：[Awesome AI PPT](https://github.com/ningzimu/awesome-ai-ppt)，用于扩大候选范围；所有重点结论尽量回到上游仓库复核。

## 3. 纳入标准

重点项目满足至少一项：

1. 提供可安装或可读取的 `SKILL.md`，直接处理演示文稿；
2. 是具代表性的完整 AI 演示系统、MCP 或 Agent 框架；
3. 是多个 PPT Skill 明确依赖的关键生成/编辑基础设施；
4. 在某个专业场景（学术、咨询、品牌、图片生成）有明显方法论价值。

排除纯模板市场、没有公开技术工作流的 SaaS、泛图像工具、已归档/空仓库，以及只在文章中声称能力但无代码或 Skill 的项目。

## 4. 评估维度

| 维度 | 观察点 |
|---|---|
| 类型真实性 | 是 Skill、领域规则、应用、MCP、Agent 框架还是库 |
| 交付能力 | PPTX/PDF/HTML/图片/视频，原生或转换 |
| 可编辑性 | E0–E3，是否有对象级说明或样例 |
| 工作流完整性 | brief、规划、资产、生成、编辑、交付 |
| 设计方法 | 网格、字体、色彩、版式、叙事和领域规则 |
| QA | 结构、几何、视觉、内容、兼容和修复循环 |
| 上手成本 | 安装、依赖、示例、跨 Agent 支持 |
| 运维与隐私 | 本地/云端、Docker/API、数据外发 |
| 许可 | 根许可证、子目录条款、第三方资产和模型依赖 |
| 社区信号 | Star、提交、Issue、文档；只作辅助信号 |

## 5. 证据等级

- **A：直接证据**——上游 `SKILL.md`、LICENSE、代码、可下载产物或官方文档明确说明。
- **B：项目自述**——README/演示说明，但未在统一环境复现。
- **C：分析推断**——根据技术路线和目录结构判断；应以 PoC 验证。

本综述的项目功能描述多为 A/B，跨项目质量判断主要为 B/C。没有宣称完成统一模型、统一输入和统一环境的实测排名。

## 6. Star 数据的解释

Star 是时间敏感的关注度信号，不是质量分。尤其注意：

- 大型多 Skill 仓库的 Star 无法归因到 PPT 子目录。
- 短期传播可使 Star 激增，但文档、测试与兼容性未必同步。
- 小而专门的领域 Skill 可能比大项目更适合特定场景。
- `data/projects.csv` 中的近似值仅帮助理解生态热度，采用时应打开上游仓库查看实时数据。

## 7. 主要来源

- [Anthropic Skills](https://github.com/anthropics/skills)：Agent Skills 参考仓库及 PPTX 文档 Skill。
- [MiniMax Skills](https://github.com/MiniMax-AI/skills)：跨 Agent Skills 与 PPTX Generator。
- [Awesome AI PPT](https://github.com/ningzimu/awesome-ai-ppt)：分类目录和候选项目入口。
- [PPTAgent / DeepPresenter](https://github.com/icip-cas/PPTAgent)：反思式演示 Agent 与评估研究。
- [Presenton](https://github.com/presenton/presenton)：自托管 AI 演示产品/API/MCP。
- 各重点项目的 README、`SKILL.md`、LICENSE 和示例目录，链接见项目评测。

## 8. 局限与后续工作

- 尚未在统一 OS、模型、字体、模板和 PowerPoint 版本下跑完整基准。
- GitHub 页面展示的 Star、功能和许可证可能在调研后变化。
- 中文字体、Keynote/LibreOffice 兼容、复杂图表和母版保持需要专项测试。
- 后续最有价值的贡献是：提交固定 brief 的产物、接触表、环境信息、耗时/成本和失败记录，而不是只增加链接。

