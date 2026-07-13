# 贡献指南

感谢帮助维护这份 PPT Skill 综述。目标是提供可验证、可复现、对选型真正有用的信息，而不是扩大链接数量。

## 可接受的贡献

- 更新项目功能、许可证、安装方式或维护状态。
- 新增有明确 PPT/Slides 工作流的 Agent Skill、应用、MCP 或关键基础设施。
- 提交统一 brief 的复现实验、接触表、产物和失败分析。
- 修正文案、分类、可编辑性等级或专业术语。
- 补充中文字体、模板、PowerPoint/Keynote/LibreOffice 兼容测试。

## 新项目最少信息

PR 应包含：

1. GitHub 仓库与具体 Skill 路径（如有）。
2. 项目类别：Skill、领域 Skill、应用、Agent 框架、MCP 或库。
3. 主技术路线：PPTX-native、HTML-first、image-first 或 template/edit-first。
4. 主要输出和 E0–E3 可编辑性证据。
5. LICENSE 及第三方资产/模型依赖说明。
6. 至少一个公开样例、复现记录或明确的上游文档证据。
7. 优势、限制和不适用场景；不要只复制营销文案。

## 写作规范

- 区分事实、项目自述和分析判断。
- 不把 Star 当质量排名，不用父仓库 Star 代表子 Skill。
- 不把“可导出 PPTX”直接写成“原生可编辑”。
- 使用稳定、直达的 GitHub 链接；涉及时间变化的数据标注快照日期。
- 项目描述保持中性，说明边界、依赖和许可风险。

## 建议的复现附件

```text
benchmarks/<project>/<date>/
├── brief.md
├── environment.md
├── source/
├── output/
├── contact-sheet.png
└── review.md
```

请勿提交真实商业机密、无权再分发的模板/字体/图片、API 密钥或包含个人敏感信息的材料。

