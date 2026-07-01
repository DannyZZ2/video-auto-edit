# 默认包装风格 / Default Packaging Style

## 风格名称 / Style Name

**Neon Analytics HUD / 霓虹数据分析 HUD**

这是 `$video-auto-edit` 的默认视觉包装风格。它不是普通科技卡片，而是“AI 分析仪表盘 + 语音关键词解释层”：深色实拍或暗色背景上，叠加蓝色 HUD 标题、数据报告面板、雷达图、合规表、替换词卡、分流连线、终端步骤和纵向自动化报告。

This is the default visual packaging style for `$video-auto-edit`: an AI analytics dashboard and spoken-keyword explanation layer over dark footage, using blue HUD titles, report panels, radar charts, compliance tables, replacement chips, branch lines, terminal steps, and vertical automation reports.

## 核心气质 / Core Feel

- 深色、冷静、专业，像 AI 正在分析视频内容。
- 信息密度高，但每个模块只解释一个当前关键词。
- 蓝色是主视觉；绿色表示正确/完成，红色表示错误/违规，黄色表示分数/风险/重点。
- 卡片、图表和连线都要有轻微发光、暗玻璃底和清晰层级。
- 不做整条视频顶部/底部全局进度条。

- Dark, calm, and analytical, as if an AI system is reading the content.
- Dense but controlled: each module explains one active spoken keyword.
- Blue is primary; green means correct/done, red means error/non-compliant, yellow means score/risk/emphasis.
- Cards, charts, and connectors use subtle glow, dark glass surfaces, and clear hierarchy.
- Do not generate global top or bottom video progress bars.

## 默认组件 / Default Components

### 1. HUD Section Label / 左上 HUD 章节标题

结构：

- 左侧 3-5px 发光竖线。
- 英文大写标签，蓝色、宽字距，例如 `WHAT IT DOES`、`TRAFFIC SCORE`、`COMPLIANCE CHECK`。
- 下方一行中文副标题，白色粗体。

动效：

- 竖线从 0 高度生长。
- 英文标签逐字或整体轻微滑入，蓝色弱发光。
- 中文副标题延迟 3-6 帧淡入。

### 2. AI Report Panel / AI 报告面板

适用：

- 总结某个工具能做什么。
- 展示 2-3 个分析结果、建议或指标。

结构：

- 大型深色玻璃面板，1px 蓝色描边，圆角 10-14px。
- 顶部标题栏：英文报告名 + 中文标题 + 右侧状态点，如 `SCANNING`。
- 左侧编号模块：1/2/3 圆点 + 线性图标 + 英文标签 + 中文关键词。
- 右侧用横向条形图、短线条或完成勾展示信息，不写长段落。

动效：

- 面板先从左/下轻滑入并绘制边框。
- 状态点闪烁 1-2 次后进入弱呼吸。
- 编号模块按关键词落点逐条进入。
- 横向条从 0 宽度增长；每条延迟 3-5 帧。

### 3. Radar Score / 雷达评分图

适用：

- 多维度评分、能力维度、内容诊断。

结构：

- 中心五边形雷达图，外框蓝色发光，内部 3-5 层弱线。
- 标签卡必须贴在最外侧五边形顶点附近，不放到图内部。
- 每个标签卡包含线性图标、英文短词和中文短词。

动效：

- 五边形外框先绘制，内部网格依次淡入。
- 当前维度顶点有一个小光点沿边线循环移动。
- 标签卡从对应顶点外侧吸附进入。
- 雷达填充面根据关键词逐点展开。

### 4. Keyword Aura / 人物关键词光环

适用：

- 需要围绕人物强调一个核心概念或情绪词。

结构：

- 人物/主体下方保留在底层，文字在主体后方或左右避让，不挡脸和嘴。
- 主体周围半圆或圆形蓝色刻度环，外圈点状轨道。
- 中心只放 1 个短关键词，文字必须居中对齐。

动效：

- 光环按弧线绘制，刻度短线错峰出现。
- 关键词轻微放大进入，随后保持 2%-4% 的弱呼吸。
- 如果人物在中间，文字层必须放在人物后方或安全侧边。

### 5. Compliance Table / 合规检查表

适用：

- 错误 -> 正确、违规 -> 合规、旧词 -> 新词、问题 -> 修复。

结构：

- 暗色表格面板，顶部列名：类别、严重度、怎么改。
- 每行左侧是问题项，中间是严重度点，右侧是红色错误词和绿色替换词。
- 红绿词卡之间用短连接线和箭头，长度根据两个词卡边缘计算。

动效：

- 行按关键词落点进入，不一次性全亮。
- 红色错误词先出现并轻微震动。
- 连接线从红卡边缘绘制到绿卡边缘。
- 连接线上必须有柔和光晕点循环移动，显性表现替换/传输。
- 绿色替换词在光点到达时 pop 进入。

### 6. Minimal Edit / 最小改动替换卡

适用：

- 只替换关键词、不改变整体语气。

结构：

- 大玻璃面板内放一组短词替换：原词、红色错误词、箭头、绿色新词。
- 新词必须位于箭头指向的目标位置，不能偏到边缘或底部。
- 下方可放 1-2 条弱化的保留原则卡片。

动效：

- 原词变暗，红词先贴上。
- 箭头短促绘制，新词在箭头目标处弹入。
- 不要让新词卡压到面板边缘。

### 7. Gauge Score / 环形评分表

适用：

- 流量潜力、完成度、风险分、质量分。

结构：

- 半圆或环形粗线仪表盘。
- 数字居中，例如 `82/100`；中文指标在下方。
- 底部可放 1-2 个小指标卡。

动效：

- 当数值为 0 时，不显示右侧彩色进度端点。
- 进度从 0 增长到目标分，末端光晕跟随进度移动。
- 数字用计数动画增长，末尾轻微 settle。

### 8. Branch Flow / 分流连线图

适用：

- 一个来源分出 2-3 个去向、工具路径、部署方式、内容流转。

结构：

- 左侧源节点卡，右侧三张目标卡。
- 曲线从源节点边缘连接到每张目标卡左边缘，长度根据目标卡位置和宽度计算。
- 三条线颜色可为蓝、绿、黄。

动效：

- 源节点先出现，三条路径按关键词逐条绘制。
- 每条线上都有一个柔和发光点沿曲线循环运动。
- 光点必须沿线移动，不停在终点。
- 目标卡在光点接近时点亮。

### 9. Terminal Steps / 终端步骤面板

适用：

- 命令、部署、调用、工具执行步骤。

结构：

- 深色终端窗口，左上红黄绿小点。
- 顶部命令栏使用短命令，例如 `>_ codex code`。
- 内部用 01/02/03 步骤，不写长代码块。
- 每步包含图标、英文动作和中文短词。

动效：

- 命令栏短打字机进入。
- 步骤逐条亮起，当前步骤边框或图标发光。
- 不做持续 glitch；只允许 4-6 帧局部抖动作为强调。

### 10. Auto Report / 纵向自动化报告

适用：

- 自动抓取、审查、输出、流水线。

结构：

- 左侧纵向节点链，节点之间用蓝/绿发光线连接。
- 右侧对应每个节点放横向说明卡。
- 当前节点亮，其它节点降亮。

动效：

- 节点从上到下依次点亮。
- 连接线上有柔和光点向下循环移动。
- 右侧说明卡与节点同步滑入。

## 字体 / Typography

```text
英文 HUD 标签：DIN Condensed / Avenir Next Condensed / Bebas Neue / Inter Black，ALL CAPS，letter-spacing 0.12em-0.22em。
中文关键词：Source Han Sans Heavy / HarmonyOS Sans SC Black / PingFang SC Heavy，白色粗体，短词优先。
卡片正文：PingFang SC Semibold / Source Han Sans Medium，避免长句。
代码命令：JetBrains Mono / SF Mono / Menlo。
```

规则：

- 必须显式设置 `fontFamily`，不能依赖默认字体。
- 中文关键词最多 2 行，每行不超过 8 个字。
- 英文标签只做识别符，不写完整句子。
- 字距不能为负值。

## 颜色 / Color

```text
background: #020812 / #06111f / rgba(0,0,0,0.45-0.68)
primary blue: #109BFF / #1EA7FF
cyan: #20E2D2
green: #2FE36B
red: #FF4D5B
yellow: #FFD32A
white: #F4F8FF
panel fill: rgba(2, 8, 18, 0.62-0.82)
```

## 安全区 / Safe Zones

- 人脸、嘴部、手势优先级高于包装元素。
- 中下方字幕安全区默认不放大卡片。
- 卡片优先放左侧、右侧或上半区。
- 如果必须在画面中间做图表，人物必须抠在上层，动画放在人物下方或后方。

## 禁用 / Do Not

- 不生成整条视频的顶部/底部进度条。
- 不生成大面积扫光、闪白或强转场光效。
- 不让卡片遮挡脸、嘴、字幕。
- 不用纯色扁平矩形代替玻璃面板。
- 不用完整口播句子当大字卡。
- 不把所有图表一次性全部出现，必须按语音关键词落点触发。
