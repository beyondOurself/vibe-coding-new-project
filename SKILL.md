---
name: vibe-coding-new-project
description: >-
  Vibe Coding 新项目：默认在项目根目录创建 RESEARCH/PRD/TECH_DESIGN/AGENTS/README/TODO 模版文档，并补全 .cursorignore、DESIGN.md（UI 设计规范，AGENTS.md 须强制引用；格式见 getdesign.md），除非用户明确不要。
  Use when starting a greenfield project, 从0到1, 新项目, 初始化仓库, 写 PRD, AGENTS.md, TODO.md,
  或用户要求按 Vibe Coding 五步推进；用户说不要文档/只要代码时则不创建。
---

# Vibe Coding 新项目

## 何时启用

用户要做**新项目 / 从 0 到 1 / 先规划再写代码**时，**必须先读并遵循本 Skill**，再写实现代码。

## 默认创建模版文档（强制）

**只要判断为「新项目」且用户未特别声明不要**，**必须在项目根目录新建或补全**下列文件（可用占位小节 + 已聊到的内容先填，再迭代）：

| 文件 | 作用 |
|------|------|
| `RESEARCH.md` | 需求研究 |
| `PRD.md` | 产品需求 |
| `TECH_DESIGN.md` | 技术设计 |
| `AGENTS.md` | AI 开发指令 |
| `README.md` | 项目说明、如何运行、目录与规范摘要 |
| `TODO.md` | 进度清单（可从 PRD 的 MVP 拆项） |
| `.cursorignore` | Cursor 索引忽略规则（见下方「7) `.cursorignore` 参考模板」） |
| `DESIGN.md` | **UI 设计规范**（范本：`ui.vintage.loongzero.com/themes/market-nest/DESIGN.md`；标准见 [getdesign.md](https://getdesign.md/what-is-design-md)） |

**例外（不创建或仅口头约定）**：用户明确说「不要模版文档」「跳过文档」「只要代码/原型」「不要 RESEARCH/PRD」等 —— 按其要求执行，不强行落盘。

- **ALWAYS**：判定为「新项目」时，**先**在项目根目录创建或补全上表 8 个文件（可带占位与后续再填），**再**进入脚手架与业务代码。
- **NEVER**：仅因「省事」省略模版；未收到用户「不要文档」类声明时，**不得**跳过落盘。

## 核心原则

- **先规划，再写代码**：默认先落上述模版再进大规模业务代码；仅在用户声明不要文档时，可直接写代码。
- **MVP 优先**：先最小可用，再扩展。
- **小步迭代**：脚手架 → 核心功能逐条 → 体验与性能。
- **限定修改范围**：每次让模型改代码时，指明文件路径与「不要动其他文件」。
- **维护 `TODO.md`**：用清单记录 `进行中 / 待开发 / 阻塞 / 已完成`，每完成一个功能或重要改动就更新，必要时同步 `README.md`。

## 文档职能分层（强制）

- `RESEARCH.md`：记录调研事实、问题分析与结论，回答“**为什么这样做**”。
- `PRD.md`：记录目标用户、需求范围、MVP 与验收边界，回答“**要做什么**”。
- `TECH_DESIGN.md`：记录技术选型、实现边界、目录与接口方案，回答“**怎么实现**”。
- `AGENTS.md`：记录长期有效的开发规范、流程规则、协作约束，回答“**如何持续协作**”；**须在正文中明确：`DESIGN.md` 为 UI 设计规范单一事实来源，实现 UI 时强制参考**。
- `DESIGN.md`：记录 UI 设计语言与可执行规范（设计图案/意图、色板、排版、字号层级、间距、圆角、阴影、组件形态、交互状态、Do/Don't 等），回答“**界面长什么样、怎么搭**”；格式与组织方式对齐 [What is DESIGN.md?](https://getdesign.md/what-is-design-md)（getdesign.md 生态标准）。
- `TODO.md`：记录可执行任务与状态流转，回答“**当前做到哪里**”。
- `README.md`：记录项目说明、启动方式、目录概览与关键约束摘要，回答“**项目如何上手**”。

禁止混放：
- 不把长期规范写进 `TODO.md`（放 `AGENTS.md`）。
- 不把任务状态写进 `PRD.md` / `TECH_DESIGN.md`。
- 不把临时讨论、聊天结论直接当正式规范。

## 五步工作流（顺序固定）

1. **Research** → 仓库根目录 `RESEARCH.md`（目标、调研、核心需求）。
2. **PRD** → `PRD.md`（概述、用户、功能列表、MVP/后续、界面、边界）。
3. **Tech Design** → `TECH_DESIGN.md`（技术栈、目录结构、数据模型、关键点）。
4. **AGENTS** → `AGENTS.md`（概述、规范、风格、测试、注意事项；**含「UI 与 DESIGN.md」强制条款**；Windows 需写 OS/终端/兼容命令）。
5. **DESIGN**（有 UI 时）→ `DESIGN.md`（按 [getdesign.md](https://getdesign.md/what-is-design-md) 标准落盘；无 UI 的纯后端/工具项目可占位说明「不适用」）。
6. **Build** → 按 `PRD` + `TECH_DESIGN` + `AGENTS` + `DESIGN.md`（涉及界面时）初始化工程，再分功能实现，每步可运行、可测、可提交 Git。

**并行文档**：`README.md`（项目说明、运行方式、目录与规范）；`TODO.md`（进度清单，可从 PRD 的 MVP 拆成勾选项）。初始化后即可建立 `TODO.md`，随开发更新。

三步迭代：**框架能跑** → **核心功能一条条** → **打磨细节**。

## TODO.md 标准（强制）

- 状态分区固定为：`进行中`、`待开发`、`阻塞`、`已完成`（可选 `变更记录`）。
- 任务标题格式固定为：`项目-类型-序号 + 动词 + 结果`。
  - 示例：`APP-M-008 接入订单详情接口`
- 类型建议固定：`M` 业务模块、`C` 组件能力、`S` 样式资源、`I` 工程基础设施、`D` 文档流程。
- 每条任务至少包含：
  - `范围`：影响文件或目录
  - `验收`：可验证结果
  - 阻塞任务补充 `阻塞原因`、`需要协作`
- 任务来源需可追溯到 `PRD.md`（需求范围）与 `TECH_DESIGN.md`（实现范围）。
- 任务状态变更只做两步：移动分区 + 更新字段；禁止在多个分区重复出现。
- 每次批量调整任务后，在 `变更记录` 增加一条日期与动作说明。

## 协助用户时的默认动作

1. **第一步**：在仓库根目录创建上表 **8 个模版文件**（缺则补全，已有则对齐更新），除非用户已声明不要。其中 `.cursorignore` **默认按下方参考模板落盘**，再按项目类型（uni-app / Web / 后端等）增删条目。
2. 若只有模糊想法：用「先问再答」补全需求，**写入 `RESEARCH.md` / `PRD.md`** 再往下。
3. 若用户直接要代码：仍**默认先创建/更新模版文档**，再初始化工程；仅当用户声明不要文档时跳过。
4. 生成初始化或实现时，引用 `PRD.md`、`TECH_DESIGN.md`、`AGENTS.md`；**涉及页面/组件/样式时须先读 `DESIGN.md` 并严格对齐**。
5. 实现单功能时，使用「单功能模版」，并**限定文件范围**。
6. 完成一条功能后：更新 `TODO.md`（及必要时 `README.md`）。

7. 文档更新遵循联动顺序：
   - 需求变更：先 `RESEARCH.md` / `PRD.md`
   - 方案变更：再 `TECH_DESIGN.md`
   - 规则沉淀：更新 `AGENTS.md`
   - 视觉/组件规范变更：同步 `DESIGN.md`（格式参考 [getdesign.md](https://getdesign.md/what-is-design-md)）
   - 执行落地：最后更新 `TODO.md`

## 必备提示模版（直接可用）

**扩写 PRD（用户先写一段话）**

```
请帮我把下面需求扩展成完整 PRD，包含：产品概述与目标用户、功能列表、MVP 与后续版本、界面设计要求、技术栈建议、非功能性需求（性能、安全等）。

【用户的一段话】
```

**初始化工程**

```
请根据 PRD.md、TECH_DESIGN.md、AGENTS.md 和 DESIGN.md（有 UI 时）初始化项目并创建基本结构：安装依赖、目录结构、开发环境配置、基础路由与页面框架，确保项目能启动；页面样式须对齐 DESIGN.md。
```

**单功能**

```
我要实现【功能名】。请根据 PRD.md、TECH_DESIGN.md 与 DESIGN.md（涉及 UI 时），在【路径/组件名】完成【行为描述】。
```

**限定范围**

```
仅修改 【文件路径】：
1. 【具体改动】
2. 保持现有样式与布局
3. 不要改动其他文件
```

**需求五要素（口头梳理时用）**：是什么、为什么、怎么做、什么样、何时何地（可选 + 受众）。

**更新任务清单**

```
我们刚完成了【功能名】。请更新 TODO.md：该项标为已完成，并调整「进行中」与「待开发」列表。
```

## 心法（对齐行为）

| 心法 | 行为 |
|------|------|
| Planning | 优先补文档与边界，避免边聊边堆需求 |
| MVP | PRD 里区分必须做 / 后续 |
| 迭代 | 一次一个可测小步 |
| 上下文 | 新会话贴技术栈 + PRD 要点 |
| 产品化 | 需求可验收、少形容词、多具体约束 |

## 参考文档

更全模版、示例表、完整案例（作品集串五步）：见本 Skill 目录下 `references/VibeCoding精华.md`。

若工作区已有同名 `VibeCoding精华.md`，以**工作区文件**为准（可能更新）。

## 参考应用模板（app.vintage.loongzero.com / property_uniapp）

以下模板来自真实项目文档结构，可作为新项目初始化时的直接参考。

### 1) `AGENTS.md` 参考模板

```md
# AGENTS

> 用于约定本项目长期适用的**开发规范、流程约束、协作规则**等基础原则。
> 与 RESEARCH.md（方案/结论沉淀）、TODO.md（执行性业务进度）联动，为所有新功能、代码实现和任务协作提供统一的团队“工作基线”。
> 仅记录项目长期约束和反复复用的标准，**不存放临时方案、日常进度、讨论记录**。

## 项目概述
- 一句话说明项目形态、技术栈、发布端。

## 开发规范
- 默认最小改动；优先修改用户指定路径；不扩散无关重构。
- 复用优先：高复用逻辑尽量组件化/模块化。
- Windows 环境补充 PowerShell 与路径兼容要求。

## UI 与 DESIGN.md（强制）
- 项目根目录 **`DESIGN.md`** 为本项目 **UI 设计规范** 的单一事实来源，用于描述设计图案/意图、色板、排版、字号层级、间距、圆角、阴影、组件形态、交互状态及 Do/Don't 等可执行约束。
- **生成或修改任意页面、组件、样式相关代码前，须先阅读并严格遵守 `DESIGN.md`**；禁止自创与规范冲突的配色、字号、间距或组件形态。
- `DESIGN.md` 的结构与写法对齐 [getdesign.md — What is DESIGN.md?](https://getdesign.md/what-is-design-md)；新建或大幅改版时按该标准组织（设计令牌、组件规范、交互状态等须给出明确值或约束）。
- 若项目尚无 `DESIGN.md` 却要做 UI，须先按 getdesign 标准补齐该文件，再写界面代码，不得无规范盲改。
- 多主题/多皮肤项目可在子目录各放一份 `DESIGN.md`（如 `themes/<id>/DESIGN.md`），`AGENTS.md` 中须写明以哪份为准及切换规则。

## 文档协作规范（vibe-coding-new-project）
- 文档顺序：`RESEARCH.md` -> `PRD.md` -> `TECH_DESIGN.md` -> `AGENTS.md` -> `TODO.md`
- 职责分层明确，不混放内容。

## 跨设备开发流程（强制）
- 开发前先读 `TODO.md`
- 以 `TODO.md` 作为任务状态单一事实来源

## 代码风格
- 缩进、命名、注释、页面注册规则等

## 测试与发布
- 提交前编译/运行检查
- 密钥与证书不可提交

## 注意事项
- 记录长期有效的工程约束（例如特定构建/样式限制）
```

### 2) `RESEARCH.md` 参考模板

```md
# 需求调研报告 — <项目名>

> 用于沉淀需求来源、市场信息、竞品对比与关键问题结论，为需求立项和方案选择提供证据。
> 与 PRD.md（需求定义）、TECH_DESIGN.md（技术设计）联动，作为“为什么这样做”的依据文档。
> 仅记录调研事实、分析过程与结论，**不存放任务排期和长期工程规范**。

## 一、项目背景与目标
## 二、市场现状分析
## 三、竞品对比
## 四、用户需求洞察
## 五、风险与约束
## 六、结论与建议
```

### 3) `PRD.md` 参考模板

```md
# 产品需求文档（PRD）

> 用于定义本项目“要做什么、为谁做、做到什么程度”的产品目标与范围基线。
> 与 RESEARCH.md（调研依据）、TECH_DESIGN.md（技术落地方案）、TODO.md（执行进度）联动，作为需求评审与范围控制的统一依据。
> 仅记录稳定需求与验收边界，**不存放实现细节、临时讨论和日常任务流转**。

_版本：v1.0_
_更新日期：YYYY-MM-DD_
_产品负责人：<name>_

## 文档协作与交付约束
- MVP/迭代条目可拆分到 `TODO.md`
- 变更顺序：先改 PRD，再同步 TECH_DESIGN 与 TODO

## 一、项目背景及目标
## 二、目标用户
## 三、需求范围及版本规划（MVP / 后续）
## 四、详细功能列表
## 五、用户体验与设计规范
- 可执行视觉规范落盘于根目录 `DESIGN.md`（见 [getdesign.md](https://getdesign.md/what-is-design-md)）；`AGENTS.md` 强制开发时引用
## 六、技术与数据要求
## 七、边界与限制
## 八、非功能性需求
## 九、里程碑与进度
## 十、后续规划
```

### 4) `TECH_DESIGN.md` 参考模板

```md
# 技术设计

> 用于定义本项目“怎么实现”的技术方案、架构约束、依赖选型与实现边界。
> 与 PRD.md（需求目标）、RESEARCH.md（方案依据）、TODO.md（执行任务）联动，作为研发实现与评审的技术基线。
> 仅记录可复用的技术决策与实现规范，**不存放临时排障记录和日常进度状态**。

## 文档协作约束
- 与 PRD 的 MVP 范围一致
- 与 TODO 建立任务映射

## 技术栈
## 目录结构
## 数据与接口约定
## 路由与页面结构
## 关键技术方案（含风险与回退策略）
## 多端/环境差异说明
## 常见问题与排查
```

### 5) `TODO.md` 参考模板

```md
# 进度清单（唯一事实源）

> 用于跟踪本项目可执行任务的当前状态与流转，作为跨设备协作的统一进度面板。
> 与 PRD.md（需求范围）、RESEARCH.md（结论依据）、TECH_DESIGN.md（技术方案）、AGENTS.md（长期规范）联动，保障执行与目标一致。
> 仅记录任务项与状态变化，**不存放方案长文、调研细节与规范正文**。

## 使用规则
- 状态分区固定：`进行中`、`待开发`、`阻塞`、`已完成`
- 标题格式：`项目-类型-序号 + 动词 + 结果`（如：`APP-M-008 接入订单详情接口`）
- 类型建议：`M/C/S/I/D`
- 每条任务至少含：`范围`、`验收`
- 阻塞任务补充：`阻塞原因`、`需要协作`
- 任务来源可追溯到 `PRD.md` + `TECH_DESIGN.md`

## 进行中
- [ ] APP-M-001 <任务名>
  - 范围：`<path>`
  - 验收：<可验证结果>

## 待开发
- [ ] APP-M-002 <任务名>
  - 范围：`<path>`
  - 验收：<可验证结果>

## 阻塞
- [ ] APP-M-003 <任务名>
  - 阻塞原因：<原因>
  - 需要协作：<角色/团队>

## 已完成
- [x] APP-M-000 <任务名>
  - 范围：`<path>`
  - 验收：<可验证结果>

## 变更记录（近 7 天）
- YYYY-MM-DD：<变更说明>
```

### 6) `README.md` 参考模板

```md
# <项目名>

## 说明
- 一句话说明项目定位与技术栈。

## 如何运行
1. 使用团队约定工具启动（例如 HBuilderX / CLI）
2. 安装依赖并运行

## 目录摘要
| 路径 | 作用 |
|------|------|
| `pages/` | 页面目录 |
| `main.uts` / `App.uvue` | 入口与根组件 |
| `TECH_DESIGN.md` | 技术设计 |
| `DESIGN.md` | UI 设计规范 |
| `TODO.md` | 任务进度 |

## 规范摘要
- 详细规则见 `AGENTS.md`

## 文档索引
- `RESEARCH.md`
- `PRD.md`
- `TECH_DESIGN.md`
- `DESIGN.md`（UI 设计规范，见 [getdesign.md](https://getdesign.md/what-is-design-md)）
- `TODO.md`
```

### 7) `DESIGN.md` 参考模板（UI 设计规范）

> 职能：**UI 设计规范**，非技术架构文档。章节结构与写法以 **`ui.vintage.loongzero.com/themes/market-nest/DESIGN.md`** 为范本（getdesign 生态实践样例）；标准说明见 [What is DESIGN.md?](https://getdesign.md/what-is-design-md)。纯后端/无界面项目可在文首注明「本项目无 UI，本文件不适用」。

```md
# <产品/主题名>

<一句话设计气质，如：Warm, community-driven, handmade feel.>

## Overview

<2–4 句：产品定位、布局气质、主色与视觉哲学、与竞品的差异。说明深度层次策略（如 flat + border 而非 shadow）。>

## Colors

- **Primary** (#XXXXXX): <用途，如 Primary CTAs、主导航激活>
- **Secondary** (#XXXXXX): <用途>
- **Tertiary** (#XXXXXX): <用途>
- **Background** (#XXXXXX): <全局页面背景>
- **Surface** (#XXXXXX): <卡片、弹层等>
- **Success** (#XXXXXX)
- **Warning** (#XXXXXX)
- **Error** (#XXXXXX)
- **Info** (#XXXXXX)

## Typography

- **Headline Font**: <字体名>
- **Body Font**: <字体名>
- **Mono Font**: <字体名>

- **Display**: <字体 字号 字重, 行高, 字距>. <使用场景>.
- **Headline**: ...
- **Subhead**: ...
- **Body Large**: ...
- **Body**: ...
- **Body Small**: ...
- **Caption**: ...
- **Overline**: ...
- **Code**: ...

## Spacing

- **Base unit:** <如 8px>
- **Scale:** <如 4, 8, 12, 16, 24, 32, 48, 64, 96, 128>
- **Component padding:** <small / medium / large 具体值>
- **Section spacing:** <mobile / tablet / desktop 分段间距>

## Border Radius

- **None:** <px> — <用途>
- **Small:** ...
- **Medium:** ...
- **Large:** ...
- **XL:** ...
- **Full:** 9999px — <圆形头像等>

## Elevation

<本主题的深度策略说明，如 flat 无阴影、用边框分层；或 shadow 阶梯。>
- **Subtle:** ...
- **Medium:** ...
- **Large:** ...
- **Overlay:** ...
- **Focus Ring:** ...

## Components

### Buttons
**Primary (Filled)** — `bg: ...`, `text: ...`, `font: ...`, `padding: ...`, `radius: ...`, `hover: ...`, `active: ...`
**Secondary (Outline)** — ...
**Ghost** — ...
**Destructive** — ...
- **Sizes**: Small `...`, Medium `...`, Large `...`
- **Disabled**: ...

### Cards
**Default** — ...
**Elevated** — ...

### Inputs
**Text Input** — `bg`, `border`, `focus`, `error`, `disabled` 等完整 token
- **Label**: ...
- **Helper text**: ...

### Chips
**Filter Chip** — ...
**Status Chip** — Success / Warning / Error 各色值

### Lists
**Default List Item** — `height`, `padding`, `divider`, `hover`, `selected`, `icon variant`

### Checkboxes
<尺寸、边框、选中/半选/禁用、与 label 间距>

### Radio Buttons
<同上粒度>

### Tooltips
<背景、字号、padding、radius、箭头、delay、位置偏好>

## Do's and Don'ts
- **Do** ...
- **Don't** ...
```

编写要求（对齐 market-nest 范本 + getdesign 标准）：
- 文首用英文或中文短句点明气质；`Overview` 写清「为什么这样设计」。
- **Colors / Typography / Spacing / Border Radius / Elevation** 须给出**具体色值、px、字体栈与使用场景**，禁止只写「温暖」「简约」等形容词。
- **Components** 按组件类型分节，每种变体用一行 token 串（`bg` / `border` / `hover` / `disabled` 等）写全，可直接对照实现。
- **Do's and Don'ts** 写业务与视觉边界（如禁止乱用主色做装饰边框），不少于 4 条 Do、4 条 Don't。
- 与 `AGENTS.md` 中「UI 与 DESIGN.md」条款一致；多主题项目可在 `themes/<id>/DESIGN.md` 各维护一份，结构同上。

### 8) `.cursorignore` 参考模板（property_uniapp）

新项目初始化时**默认创建**此文件；非 uni-app 项目可保留通用段（依赖、构建产物、IDE、日志、锁文件），删除或替换 uni-app 专有段。

```
.DS_Store
node_modules
dist
unpackage
*.log
*.tmp
*.local
.idea
.vscode
*.iml
# 编译产生的目录和文件
/build/
/__uniappview__/
/static/
/src/manifest.json
# 临时文件
*.bak
# 依赖锁定文件
package-lock.json
yarn.lock
pnpm-lock.yaml
```
