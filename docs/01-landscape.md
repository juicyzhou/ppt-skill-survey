# 技术版图与核心概念

## 1. 生态分层

一个完整的 AI PPT 流程通常包含五层：

```text
领域规则/品牌规范
        ↓
Agent Skill（触发、规划、编排、验收）
        ↓
生成与编辑引擎（PptxGenJS / python-pptx / HTML / Office API）
        ↓
渲染与检查（PowerPoint / LibreOffice / Chromium / 缩略图）
        ↓
交付物（PPTX / PDF / HTML / PNG / 视频）
```

| 层次 | 典型项目 | 作用 | 常见误区 |
|---|---|---|---|
| Agent Skill | Anthropic PPTX、Frontend Slides、Codex PPT | 把经验写成可复用工作流 | 把一份长提示词误认为完整工具链 |
| 领域 Skill | Academic PPTX、MCK PPT | 约束叙事、版式和验收 | 单独使用时可能没有生成能力 |
| 完整系统 | Presenton、PPTAgent | UI/API/MCP、模型、资产和导出一体化 | 部署成本被低估 |
| 生成库 | PptxGenJS、python-pptx | 创建或修改 PPTX 对象 | 库本身不会自动做出好设计 |
| 自动化接口 | OfficeCLI、PowerPoint MCP/COM | 控制、检查、预览 Office 文件 | 常有系统平台或 Office 安装限制 |

## 2. 四条主要生产路线

### 2.1 PPTX-native

直接创建 PowerPoint 对象。常见实现包括 PptxGenJS、python-pptx、Office Open XML、Office/COM API。

**优势**：文字和形状可编辑；适合企业模板、翻译、数据更新、长期维护。  
**限制**：复杂排版、字体度量、图表兼容和跨软件渲染需要大量工程处理。  
**适用**：正式商务交付、咨询报告、学术答辩、团队协作修改。

### 2.2 HTML-first

先生成 HTML/CSS/JS 或 React/Vue 演示，再用浏览器播放，或导出 PDF、图片、PPTX。

**优势**：现代布局、动画、交互和响应式设计能力强；Agent 熟悉前端代码。  
**限制**：CSS 到 PPTX 的语义映射有限；导出 PPTX 可能只是图片或部分可编辑。  
**适用**：发布会、线上演示、网页分享、需要动画或互动的内容。

### 2.3 Image-first

用图像模型生成完整幻灯片图，再组装成 PPTX/PDF/视频。

**优势**：快速获得高视觉完成度，复杂插画和艺术风格成本低。  
**限制**：内容校对、细粒度修改、图表数据追溯、文字可访问性最弱；图像模型还可能生成错字。  
**适用**：概念提案、视觉叙事、一次性播放、时间非常紧的草案。

### 2.4 Template/edit-first

分析既有模板或参考 deck，复用母版、布局、风格和页面结构，再替换内容或执行编辑动作。

**优势**：品牌一致性和版式稳定性通常优于从零生成。  
**限制**：模板质量决定上限；复杂占位符、图表和 OOXML 编辑容易产生兼容问题。  
**适用**：企业品牌模板、周期性报告、同系列 deck、批量更新。

## 3. 可编辑性的严格定义

| 等级 | 判定 | 示例 |
|---|---|---|
| E3 原生可编辑 | 主要文字、形状、图片、表格/图表是独立 PowerPoint 对象 | PptxGenJS/python-pptx 输出，或 Office API 操作 |
| E2 部分可编辑 | 文字可编辑，但视觉背景/复杂图表是图片；或大部分对象可改但语义丢失 | HTML 转 PPTX、OCR 重建、背景图 + 文本层 |
| E1 图片式 | 每页主体是单张图片，PowerPoint 只承载页面 | image-first deck |
| E0 非 PPTX | HTML/PDF/视频是最终交付物 | 网页演示、Beamer PDF |

评估时至少检查：文本是否可选择、图表能否改数据、对象是否分组合理、母版是否保留、备注是否存在、导入 PowerPoint/Keynote/LibreOffice 是否一致。

## 4. 什么才算优秀的 PPT Skill

成熟 Skill 不仅能“生成文件”，还应覆盖以下闭环：

1. **触发准确**：描述清楚何时使用、何时不使用。
2. **需求澄清**：受众、场景、时长、页数、品牌、交付格式。
3. **内容规划**：故事线、行动标题、证据、引用、备注。
4. **视觉系统**：色彩、字体、网格、版式多样性、图表纪律。
5. **资产管理**：模板、图片、图标、数据、版权和来源。
6. **确定性构建**：源文件可版本控制，生成可重复。
7. **视觉 QA**：渲染、接触表、溢出/重叠、对比度、占位符检查。
8. **兼容与交付**：PPTX/PDF/HTML 输出、字体降级、跨平台复核。
9. **安全与许可**：脚本审查、外部 API、素材和模型条款透明。

## 5. 当前趋势

- Skill 正从单个 `SKILL.md` 向“说明 + 脚本 + references + assets + QA”演化。
- 原生 PPTX 与 HTML-first 正通过 HTML-to-PPTX、DOM-to-PPTX 和浏览器渲染靠拢，但可编辑性仍需逐项目验证。
- 高质量项目越来越强调 source-first、可重复构建、接触表和修复后复验。
- MCP/CLI 让演示能力更容易被不同 Agent 调用，但同时扩大了部署和安全审查面。
- 垂直领域 Skill（学术、咨询、答辩、医学）往往比通用 Skill 更擅长叙事与验收，但通常需要搭配底层渲染 Skill。

