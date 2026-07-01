# 卡片风格库 / Card Style Library

> 用途：统一管理 `$video-auto-edit` 可选卡片风格，避免默认高级 HUD 和新增风格分散在多个文件中。  
> Purpose: manage all selectable card styles for `$video-auto-edit` in one reference.

## Reference Source / 参考来源

本库只保存可直接复用的文字化风格规则，不依赖图片资源。若项目本地另有参考图或 Remotion 样例，可用它们辅助观察质感，但上传 skill 时只保留必要 Markdown 和配置文件。

This library stores reusable text-based style rules only and does not depend on bundled image assets. If local reference images or Remotion demos exist, use them only as observation aids; upload only required Markdown and config files for the skill.

可参考项目中的 `CodexAgentPackaging` Remotion 合成提炼包装语言，但不要照搬其中的整条视频顶部进度条。

## 使用原则 / Usage Rules

1. 先根据字幕语义选风格，不要整条视频随机混用。
2. 一条视频最多使用 1 个主风格 + 1 个辅助风格。
3. 所有动效仍按字幕关键词落点触发。
4. 所有卡片必须避开脸部、嘴部和字幕安全区。
5. 风格图只是方向参考，最终必须用 Remotion + GSAP 可复刻的 div、CSS、SVG、clip-path、box-shadow、transform 实现。
6. `Neon Analytics HUD` 是基础默认风格；当前启用 6 种扩展风格。

1. Choose styles according to subtitle meaning; do not mix styles randomly.
2. Use at most one primary style plus one supporting style per video.
3. Trigger all animations from subtitle keyword cue points.
4. Keep all cards outside face, mouth, and subtitle-safe zones.
5. Reference images are visual direction only; final implementation must be reproducible with Remotion + GSAP using divs, CSS, SVG, clip-path, box-shadow, and transforms.
6. `Neon Analytics HUD` is the base default style; six extension styles are active.

## Active Styles / 已启用风格（共 7 种）

### Base. Neon Analytics HUD / 默认霓虹数据分析 HUD

适合：

- AI 工具讲解、视频诊断、流量评分、合规检查、关键词替换、Agent 流程报告。
- 需要“像 AI 正在分析内容”的默认包装片段。
- 口播每句话都要用对应图表或卡片解释，而不是只弹一个普通词卡。

视觉结构：

- 深色背景或压暗实拍画面上叠加数据分析 HUD。
- 左上角固定风格章节标题：蓝色发光竖线 + 英文大写标签 + 中文副标题。
- 组件优先使用 AI 报告面板、雷达评分图、关键词光环、合规检查表、最小改动替换卡、环形评分表、分流连线图、终端步骤面板、纵向自动化报告。
- 卡片是暗玻璃面板，1px-2px 蓝色/语义色描边，边缘弱发光，内部有清晰行列、图标和短标签。
- 语义色：蓝色为主视觉，绿色表示正确/完成，红色表示错误/违规，黄色表示分数/风险/重点。

字体：

```text
英文 HUD 标签：DIN Condensed / Avenir Next Condensed / Bebas Neue / Inter Black，ALL CAPS，letter-spacing 0.12em-0.22em，18-30px。
中文关键词：Source Han Sans Heavy / HarmonyOS Sans SC Black / PingFang SC Heavy，38-76px，line-height 0.92-1.05。
辅助说明：PingFang SC Semibold / Inter SemiBold，22-32px，line-height 1.18-1.32。
代码或命令：JetBrains Mono / SF Mono，22-30px。
```

Remotion 实现：

```text
section label: glowing vertical bar + uppercase blue label + Chinese subtitle
panel: dark glass card + semantic neon stroke + weak outer glow
chart: radar/gauge/table/branch/terminal built with SVG/CSS primitives
connector: SVG path with stroke draw + looping soft glow dot
motion: section label -> panel border draw -> rows/cards/charts by keyword cue
```

动效建议：

- 每句话按关键词选择一个匹配模块：报告、雷达、光环、表格、替换、评分、分流、终端或自动化报告。
- `cueFrame - 6`：左上 HUD 章节标题先入场，竖线生长。
- `cueFrame`：主面板边框绘制或图表骨架出现。
- `cueFrame + 4`：当前关键词对应行/节点/卡片点亮。
- 连线类动效必须有柔和光晕点沿线循环移动。
- 待机只做边框弱呼吸、状态点闪烁、光点循环或数字轻微 settle。

组件变体：

- `AiHealthReportPanel`：一份 AI 体检报告，多行分析和建议。
- `RadarScorePanel`：五维评分雷达图，标签贴外侧顶点。
- `KeywordAuraRing`：人物后方关键词光环。
- `ComplianceCheckTable`：违规词到合规词替换表。
- `MinimalEditSwapCard`：只替换标记词的红绿词卡。
- `GaugeScorePanel`：环形或半圆评分表。
- `BranchFlowPanel`：一个源节点分流到多个目标卡。
- `TerminalStepsPanel`：命令窗口 + 01/02/03 步骤。
- `AutoReportPipeline`：纵向节点链 + 右侧说明卡。

禁用：

- 不做顶部/底部全局进度条。
- 不把卡片做成纯色扁平矩形。
- 不把完整口播句子作为大字卡片。
- 不把雷达标签放进图内部；标签应贴在外侧顶点附近。
- 不让连线光点停在终点，必须沿路径循环运动。

### 1. Codex Agent Packaging HUD / Codex Agent 分段包装 HUD

适合：

- AI 工具能力介绍、Agent 工作流升级、视频生成链路、从单点功能到系统流程的解释。
- 需要开头强 hook、随后拆成“能力卡 / 指令面板 / 执行状态 / 工作流升级”的片段。
- 人物口播右侧或居中时，左侧有较大安全区域可承载包装的横屏/竖屏视频。

视觉结构：

- 左上角竖条 + 大写英文 HUD 标签 + 中文副标题，作为当前句子的章节锚点。
- 主视觉使用巨大粗体标题或 1-3 张 HUD 能力卡，卡片有蓝色角框、网格纹理、半透明深色底和线性 SVG 图标。
- 可使用三宫格能力卡、短命令面板、CLI 状态小面板、任务执行条、Agent Flow 双卡链路。
- 颜色以电光蓝和青色为主，黄色只用于问号、ready、agent upgrade 等重点提示。
- 背景可有局部网格和暗角遮罩，但不生成顶部/底部整条视频进度条。

字体：

```text
英文 HUD 标签：Avenir Next Condensed / DIN Condensed / Bebas Neue，ALL CAPS，letter-spacing 0.12em-0.22em。
大标题：Impact / YouSheBiaoTiHei / Source Han Sans Heavy，白色粗体，可加 1px 亮边和深色投影。
中文关键词：Source Han Sans Heavy / PingFang SC Heavy，短词优先，避免整句字幕。
命令文本：JetBrains Mono / SF Mono / Menlo。
```

Remotion 实现：

```text
top label: left vertical glow bar + uppercase label + small Chinese subtitle
corner frame: 4-corner segmented border drawn with opacity stagger
hero title: clip-path reveal + slight x slide + glow stroke/shadow
ability card: dark glass panel + blue corner ticks + SVG line icon draw + label pop
command panel: mono text type-in + ready chip pop
workflow panel: two compact HUD cards + short glowing arrow
```

动效建议：

- 关键词 cue 前 4-8 帧先出现左上 HUD 标签，竖条从 0 高度生长。
- cue 点主标题用 `clip-path inset` 横向揭示，带 12-20px 滑入，不做整屏闪烁。
- 能力卡按 6-10 帧错峰弹入，角框先亮，SVG 图标再描线，文字最后进入。
- 命令面板只打短 prompt/命令，不打完整口播；ready chip 在关键词后 8-14 帧 pop。
- 链路箭头要短而清晰；如果做连线，必须有循环移动的柔和光晕点。

禁用：

- 不生成顶部/底部整条视频进度条。
- 不把卡片放到人物脸部、嘴部或中间字幕安全区。
- 不把三宫格能力卡做得过大；口播包装里单张卡宽度优先控制在画面宽度 18%-28%。
- 不使用负字距；标题不长期常驻遮挡主体。

### 2. Holographic Glass HUD / 全息玻璃 HUD

适合：

- prompt、命令、AI task、生成状态、工具面板。
- 比 `Premium Tech HUD` 更偏蓝紫全息、命令面板和状态 chip 的片段。

视觉结构：

- 黑色/深蓝黑玻璃主卡，青色和紫色双层描边。
- 小型状态 chip、命令行短文本、角标线框。
- 背景可有极淡网格和 HUD 点阵，但不做全局进度条。
- 图标使用简单线性 SVG，不使用复杂图片图标。

Remotion 实现：

```text
container: backdrop-filter blur(10px-16px), dark glass gradient
border: cyan/violet double stroke
shadow: weak outer glow + inset highlight
text: Inter Black / JetBrains Mono / Source Han Sans Heavy
motion: corner frame draw -> panel slide -> chip pop -> mono text type-in
```

动效建议：

- 关键词 cue 前 4-6 帧绘制角标线框。
- cue 点主卡轻微透视滑入，`scale 0.96 -> 1`。
- 命令文字可用 6-12 帧打字机，但不要打完整长句。
- 待机只做边框弱呼吸和光标闪烁。

禁用：

- 不做整屏扫描光。
- 不做顶部/底部全局进度条。
- 不把卡片做成纯色扁平矩形。

### 3. Kinetic Sticker Cards / 动感贴纸卡

适合：

- 轻松口播、点击提示、拖拽操作、hook、修正动作。
- 需要更跳脱、更有创作者包装感，而不是冷静科技 HUD 的片段。

视觉结构：

- 黑色或深色磨砂贴纸卡，白色粗描边。
- 彩色厚阴影层：蓝、红、绿、黄可按语义变化。
- 圆形主图标区保留唯一主图标，例如鼠标、hook、扳手、手势。
- 不生成顶部或角落的编号小方块、状态方块或角标块。
- 可加入胶带、手绘下划线、拖拽标签、点击光圈，但必须克制。

Remotion 实现：

```text
card: dark rounded div + thick white border + colored offset shadow
main icon: circular SVG icon area with click/ripple or drag motion
corner badge: disabled; do not generate top or corner square badges
texture: subtle grain via pseudo overlay, not raster-heavy
motion: card bounce -> main icon pop -> text slide -> click ripple / drag tag
```

动效建议：

- 关键词 cue 点卡片弹入，`scale 0.90 -> 1.04 -> 1`。
- 圆形主图标在 cue 后 4-6 帧 pop，点击光圈扩散 8-14 帧。
- 不生成 `01/02/03` 这类顶部编号小方块，也不生成角落状态方块。
- 拖拽标签可沿短弧线进入，但不要越过人物脸部。

禁用：

- 不要生成顶部/角落编号小方块或彩色角标块。
- 不要同时出现多个巨大鼠标指针。
- 不要让贴纸堆叠遮挡脸、嘴或字幕。

### 4. Isometric Workflow Modules / 2.5D 工作流模块

适合：

- Agent 工作流、自动化链路、步骤拆解、从 PLAN 到 RUN 到 DONE 的过程。
- 需要表现“模块连接、任务流转、节点协作”的片段。

视觉结构：

- 多张小型 2.5D 模块卡片，带顶部面和侧边厚度。
- 细发光连线连接模块。
- 每张卡只放一个短词或状态：`PLAN`、`RUN`、`DONE`、`CHECK`。
- 颜色以深色模块为底，青色/绿色/橙色作为状态点。

Remotion 实现：

```text
card transform: perspective(900px) rotateX(8deg) rotateY(-10deg)
side thickness: pseudo layer offset 8px-14px
connector: SVG path stroke-dashoffset draw animation
shadow: soft ambient occlusion under each module
```

动效建议：

- 模块按关键词 cue 依次从下方或侧边飞入。
- 连线用 `strokeDashoffset` 从前一个节点画到下一个节点。
- 当前关键词对应模块点亮，前一个模块降亮。
- 完成态用绿色 check 芯片短促 pop。

禁用：

- 不做复杂真实 3D 模型。
- 不让所有节点同时发光。
- 不在画面中心堆太多模块。

### 5. Soft Clay Neumorphic Cards / 柔和黏土拟物卡

适合：

- 友好教程、步骤提示、轻量设置、AI 助手能力介绍。
- 需要降低科技冷感、让画面更亲和的片段。

视觉结构：

- 深色暖调背景上的柔和 2.5D 圆角卡片。
- 凸起/内凹按钮、柔和阴影、缎面塑料或软黏土质感。
- 小型模块 tiles、pill 卡、中心关键词块。
- 颜色使用深梅紫、石墨、柔和青、蜜桃、奶油白、低饱和绿。

Remotion 实现：

```text
card: rounded div, satin gradient, soft box-shadow
raised surface: light top-left shadow + dark bottom-right shadow
inset icon: inner shadow + subtle SVG icon
motion: springy rise -> soft press -> tile snap-in
```

动效建议：

- 关键词 cue 点卡片从下方轻弹上来，`y 28 -> -4 -> 0`。
- 按钮或 tile 在关键词落点后做一次 soft press。
- 多个小模块可磁吸排列，但一屏不超过 3 个主元素。
- 待机只做极轻微浮动，不做强发光。

禁用：

- 不要赛博霓虹过度发光。
- 不要把所有卡片做成同一个圆角 pill。
- 不要使用过多奶油/米色导致画面变单调。

### 6. Glitch Terminal Cards / 故障终端卡

适合：

- 错误、修复、命令执行、代码、状态切换、从 ERROR 到 PATCH 到 RESOLVED 的片段。
- AI 工具、CLI、自动化任务执行类内容。

视觉结构：

- 深黑/墨绿色终端底。
- 非对称框线、条码条、状态 LED、危险标签。
- Monospace 命令短句和关键词 chip。
- 红色错误态、蓝色处理中、绿色完成态。

Remotion 实现：

```text
terminal card: dark panel + mono font + thin frame lines
glitch: 4-8 frames only, translateX +/-2px, opacity jitter
status leds: small circles with semantic colors
barcode: repeated linear-gradient stripes
chip: ERROR / PATCH / RESOLVED
```

动效建议：

- ERROR 关键词落点触发红色卡片短抖 2-3 次。
- PATCH 触发蓝色修复 chip 贴上去。
- RESOLVED 触发绿色边框点亮和 check 图标 pop。
- glitch 只用于强调瞬间，不要持续闪烁。

禁用：

- 不要整屏闪烁。
- 不要长代码块。
- 不要让 glitch 影响人物脸部或字幕。

## Selection Guide / 选择规则

| 字幕语义 | 推荐风格 |
|---|---|
| AI 工具、状态、概念解释 | `Neon Analytics HUD`、`Codex Agent Packaging HUD` 或 `Holographic Glass HUD` |
| 视频诊断、体检报告、流量评分、合规检查 | `Neon Analytics HUD` |
| Agent 工作流升级、视频生成链路、能力总览 | `Codex Agent Packaging HUD` |
| prompt、命令、任务面板 | `Holographic Glass HUD` |
| 点击、拖拽、轻松口播、hook 修正 | `Kinetic Sticker Cards` |
| 工作流、步骤、Agent 链路 | `Isometric Workflow Modules` |
| 友好教程、步骤提示、轻量设置 | `Soft Clay Neumorphic Cards` |
| 错误、修复、CLI、状态切换 | `Glitch Terminal Cards` |

## Shared Quality Checklist / 通用质检

- 是否优先使用默认 `Neon Analytics HUD`；当前共 7 种：1 种基础默认风格 + 6 种扩展风格。
- 是否一条视频最多 1 个主风格 + 1 个辅助风格。
- 是否按字幕关键词落点触发。
- 是否避开脸、嘴和字幕安全区。
- 是否没有顶部/底部全局进度条。
- 是否没有扁平纯色卡片。
- 是否明确写出字体、材质、动效、布局和质量风险。
- 如果使用 `Kinetic Sticker Cards`，是否没有生成顶部/角落编号小方块或状态角标。
