# 视觉质量系统 / Visual Quality System

> 用途：约束 `$video-auto-edit` 的视频包装质感，重点解决字体普通、卡片廉价、层级不清、遮挡主体和动效过散的问题。  
> Purpose: constrain `$video-auto-edit` packaging quality, especially typography, card polish, hierarchy, subject safety, and motion consistency.

## 核心原则 / Core Principles

1. 先做“设计系统”，再做单个动效。所有包装都必须从字体、组件、颜色、层级和安全区出发。
2. 包装元素服务口播，不抢人物主体。短视频包装应该是“信息增强”，不是把画面做成海报。
3. 一条视频只允许 1 个主视觉方向、1 套字体组合、1-2 个强调色和 3-5 个组件类型。
4. 任何包装方案都必须写明：字体、字重、字号区间、组件类型、颜色、层级、安全区和退场方式。
5. Remotion 实现后必须做截图验收；发现字体 fallback、遮挡脸嘴、文字过大或卡片过密，要先修正再让用户看。
6. 如果用户没有提供更强的自定义风格，默认使用 `card-style-library.md` 中的 `Neon Analytics HUD`，再按字幕语义选择具体报告、雷达、表格、评分、分流、终端等组件。

## 字体系统 / Typography System

| 角色 | 中文优先 | 英文/数字优先 | 用途 |
|---|---|---|---|
| 主标题 | YouSheBiaoTiHei, HarmonyOS Sans SC Black, Source Han Sans Heavy | Anton, Bebas Neue, DIN Condensed, Inter Black | 章节标题、强观点、封面式大字 |
| 关键词 | Source Han Sans Heavy, PingFang SC Heavy, HarmonyOS Sans SC Bold | Inter ExtraBold, DIN Alternate Bold | 关键词弹出、敲章、描边、标签 |
| 正文小字 | PingFang SC Semibold, Source Han Sans Medium | Inter SemiBold, IBM Plex Sans SemiBold | 卡片说明、步骤短句 |
| 代码/命令 | SF Mono, JetBrains Mono, Menlo | JetBrains Mono, SF Mono | prompt、命令、终端卡 |

### 字体硬规则 / Typography Rules

- 不要裸用浏览器默认字体；Remotion 里必须显式设置 `fontFamily`。
- 中文标题必须使用 Heavy/Black 级别字重；普通 `font-weight: 400` 禁止用于包装主视觉。
- 关键词最多 2 行，每行不超过 8 个中文字符或 4 个英文词。
- 小字说明每行不超过 12 个中文字符或 5 个英文词。
- 字距不要用负值；英文 HUD 标签可以使用 `letter-spacing: 0.08em-0.18em`。
- 标题行高控制在 `0.9-1.08`；卡片正文行高控制在 `1.15-1.35`。
- 如果本机没有推荐字体，使用已安装的同类字体，但必须在设计稿和实现说明里写出 fallback。

## 字号与层级 / Size and Hierarchy

| 层级 | 1080x1920 竖屏建议 | 1920x1080 横屏建议 | 使用限制 |
|---|---:|---:|---|
| Hero 标题 | 56-92px | 72-128px | 只用于开头钩子或章节，不常驻 |
| 关键词 | 38-68px | 44-84px | 1-4 个字最佳，出现后快速收束 |
| 卡片标题 | 28-42px | 30-48px | 必须比正文明显粗 |
| 卡片正文 | 22-30px | 22-34px | 不写长段落 |
| HUD 标签 | 18-26px | 18-28px | 全大写或短中文标签 |

包装视觉权重从高到低：人物脸部/主体 > 当前口播关键词 > 说明卡片 > HUD 标签 > 装饰线条。任何装饰线条不能比关键词更抢眼。

## 组件库 / Component Library

动效方案和 Remotion 实现优先从这些组件中选，不要每段重新发明样式。

| 组件 | 结构 | 适用 | 动效建议 |
|---|---|---|---|
| `HudTitleCard` | 左上/右上小标题条 + 主关键词 | 章节、主题切换 | 侧滑入，短线条延展，关键词 pop |
| `NeonAnalyticsHudPanel` | 左上 HUD 标题 + 暗玻璃报告/雷达/表格/评分/分流/终端模块 | 默认包装、视频诊断、流量评分、合规检查、关键词解释 | 竖线生长，面板绘制，关键词对应行/节点点亮，连线光点循环 |
| `KeywordChip` | 胶囊标签 + 轻描边 | 工具名、概念词、分类 | 弹出、变色、贴纸、吸附 |
| `TerminalCard` | 深色终端框 + mono 文本 | prompt、命令、工具状态 | 打字机、光标闪烁、局部加载 |
| `IconInfoCard` | 线性图标 + 英文标签 + 中文短说明 | 功能、模块、能力点 | 图标先入，文字后入，边框脉冲 |
| `StepListCard` | 1/2/3 或 checkbox 列表 | 教程步骤、执行过程 | 勾选、行内高亮、短进度 |
| `ComparisonCard` | 左右两卡或前后翻转 | 旧认知 vs 新结论 | 碰撞、翻转、擦除替换 |
| `MouseClickCallout` | 鼠标指针 + 点击光圈 + 高亮 | 操作演示、按钮、prompt | 移动、点击、光圈 6-10 帧 |
| `MagnetFlow` | 标签吸附 + 连线节点 | 工作流、Agent、自动化链路 | 错峰飞入、磁吸、连线生长 |
| `PremiumHudStatusCard` | 玻璃卡片 + 语义色描边 + 图标容器 + 英文标签 + 中文关键词 | 合规/不合规、问题/解决、旧方案/新方案 | 边框先亮，图标 pop，文字错峰进入 |
| `PremiumComparisonPair` | 左右两张高级 HUD 卡 + 中间箭头光线 | 对比、纠错、方案升级 | 旧卡暗下去，箭头绘制，新卡点亮 |
| `CodexAgentPackagePanel` | 左上 HUD 标题 + 角框大标题 + 三宫格能力卡 / 命令面板 / 工作流双卡 | AI 能力总览、Agent 工作流升级、视频生成链路 | 竖条生长，标题裁切揭示，能力卡错峰弹入，短箭头/连线带循环光晕点 |
| `HolographicGlassPanel` | 全息玻璃卡 + 双层蓝紫描边 + 状态 chip | prompt、命令、AI task、生成状态 | 角标绘制，面板滑入，chip pop，mono 打字 |
| `KineticStickerCard` | 深色贴纸卡 + 粗白描边 + 圆形主图标；不生成顶部/角落编号小方块 | 点击、拖拽、hook、修正动作 | 弹跳入场，点击光圈，拖拽标签 |
| `IsometricWorkflowModule` | 2.5D 模块卡 + 侧边厚度 + 发光连线 | Agent、自动化链路、步骤流转 | 模块错峰飞入，连线绘制，当前节点点亮 |
| `SoftClayNeumorphicCard` | 柔和 2.5D 圆角卡 + 凸起/内凹按钮 + 软阴影 | 友好教程、步骤提示、轻量设置 | 轻弹上浮，soft press，tile 磁吸 |
| `GlitchTerminalCard` | 终端卡 + 非对称框线 + 状态 LED + 命令短句 | 错误、修复、CLI、任务状态 | 4-8 帧 glitch，状态 chip 贴入，完成态点亮 |

组件半径优先 6-12px。除非参考风格明确要求，不要使用大圆角胶囊做所有卡片。

## 颜色与材质 / Color and Material

- 背景遮罩：`rgba(0,0,0,0.35-0.65)`，不要把人物压成死黑。
- 主文字：白色或接近白色，阴影克制。
- 主强调：青色/电光蓝二选一；辅助强调可用黄色或红色，但整条视频最多 2 个强调色。
- 卡片底：深蓝黑或黑色半透明，透明度 60%-88%。
- 描边：1-2px，发光只在边缘出现，不要大面积糊光。
- 禁止整屏渐变光斑、全屏扫光、顶部/底部整条视频进度条。

### 高级卡片材质 / Premium Card Material

默认卡片不要做成单层扁平矩形。参考 `card-style-library.md`，根据已启用风格明确卡片材质、描边、内外光影、字体和内容层。合规/正确用绿色，错误/不合规用红色，重点/hook 用蓝色，提醒/时间用灰白。发光只服务边框和图标，不要大面积糊光。

By default, cards must not be single-layer flat rectangles. Follow `card-style-library.md`: choose an active style and specify material, border, inner/outer lighting, typography, and content layers. Use green for compliant/correct, red for non-compliant/error, blue for emphasis/hook, and gray-white for time/reminders. Glow should support borders and icons only, not become a large blurry blob.

## 布局与安全区 / Layout and Safe Zones

- 口播人物视频默认保留脸部、嘴部、手势和下方中间字幕安全区。
- 卡片优先放左侧、右侧或上三分区；底部只放短标签或字幕，不放大卡片。
- 竖屏人物居中时，左右边缘可放窄卡；人物偏右时，左侧可放主卡。
- 单屏最多 1 张主卡 + 2 个标签；超过时要分批出现。
- 包装元素应在当前句子结束后退场，避免堆积。

## 动效质感 / Motion Quality

- 入场：180-360ms，`power2.out` 或 `back.out(1.2)`，弹跳幅度小。
- 强调：80-160ms，关键词 pop、描边点亮、局部高亮。
- 待机：只允许轻微呼吸、边框脉冲或光标闪烁，不要所有元素一直动。
- 退场：120-240ms，淡出或轻微位移，不做强转场闪烁。
- 错峰：同组元素间隔 3-8 帧，帮助观众分辨顺序。
- 任何抖动最多 2-3 次；不能让整条视频长期抖动。
- 高级 HUD 卡片入场拆成边框、主体、图标、文字 4 个错峰步骤，不要整卡一次性淡入。

## 包装方案必须包含 / Required In Packaging Plans

每个动效段落必须额外写清：

- 字体：具体 `fontFamily`、字重、字号区间。
- 组件：从组件库选择，如 `KeywordChip`、`TerminalCard`。
- 层级：在人物、字幕、卡片、装饰之间的前后关系。
- 质量风险：是否可能挡脸、挡嘴、挡字幕、字太小或卡片太密。

## Remotion 实现验收 / Remotion QA

打开 Studio 前必须至少检查一个桌面尺寸截图；如果是竖屏视频，也检查竖屏构图。验收项：

1. 字体加载成功，没有 fallback 成普通系统默认字。
2. 没有遮挡脸部、嘴部和字幕安全区。
3. 关键词不是整句字幕；只显示短词或短语。
4. 卡片数量、发光、描边和文字密度可读。
5. 没有整条视频的顶部/底部全局进度条。
6. 动效段落覆盖每个有意义句子或节奏点，而不是只做第一句。
7. Studio 预览不渲染导出，等用户确认后再导出。
8. 卡片不是扁平纯色矩形；至少能看到玻璃质感、内外光影、语义色描边和明确字体层级。
