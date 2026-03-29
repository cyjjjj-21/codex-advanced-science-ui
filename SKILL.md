---
name: advanced-science-ui
description: Use when designing science communication, educational, museum-like, or longform knowledge interfaces, especially requests mentioning 科普 UI、教学网站、展览式内容页、研究叙事页面，or when the design must avoid 网课平台感、SaaS 卡片墙、模板化暗色科技风。
---

# 高级科普 UI

## 概览

把科学传播和教学界面当成一套完整的编辑系统来设计：首页要有电影海报感，内容页要能承载长文、图像、数据和术语，而且始终保持同一套审美气质。

如果当前任务已经会用 `frontend-skill`，把它当作基础实现层；本 skill 负责把视觉方向拉向“数字展览、任务档案、纪录片式叙事”，避免做成普通课程平台。

v1.5 开始，这个 skill 不再只有一段固定 prompt，而是由以下几层组成：

- `SKILL.md`
  - 触发条件、默认工作流、何时询问用户
- `PROMPT.md`
  - 稳定版全局 prompt
- `STYLE_OPTIONS.md`
  - 当前可选风格大类
- `references/`
  - benchmark 库、风格维度、决策规则、更新流程
- `templates/`
  - 新 benchmark 和新 option 的记录模板

## 默认工作流

### 1. 先判断调用模式

- 如果用户没有明确指定风格，默认使用 `auto-hybrid`
- 如果用户显式指定风格，就按 `STYLE_OPTIONS.md` 的对应 option 执行
- 如果用户同时给了新的 benchmark 站点，就先进入 benchmark 学习流程，再决定是否刷新分类

### 2. 先选主方向，再允许辅方向

- 永远不要平均混搭所有参考气质
- 必须有一个主方向
- 辅方向只能少量补充，不允许把页面做成风格拼盘

### 3. 输出时同时约束首页与内容页

- 首页必须建立世界观
- 内容页必须撑住长内容
- 图像、术语、图注、数据、元信息和 CTA 必须属于同一套视觉语言

### 4. 如果用户给了新的 benchmark 站点

- 必须同时观察首页和代表性内容页
- 先按 `references/style-axes.yaml` 做结构化观察
- 再写入 `references/benchmark-library.md`
- 然后依据 `references/decision-rules.md` 判断它是在强化旧风格、修正旧风格，还是应升格为新的 option

## 当前 option

当前默认支持以下风格大类：

- `auto-hybrid`
- `cinematic-narrative`
- `editorial-museum`
- `mission-data`
- `image-led-premium`

具体定义见 `STYLE_OPTIONS.md` 与 `references/style-options.yaml`。

## 何时询问用户

当新 benchmark 满足以下任意条件时，不要擅自把它混入默认经验，先问用户：

- 与现有任一 option 在 3 个以上核心维度上差异明显
- 更像一种新的设计哲学，而不是现有变体
- 混入默认模式会明显改变当前 skill 的整体气质
- 适用场景过于专门，直接并入默认模式会降低稳定性

标准问法：

“这个参考更适合补强现有风格，还是要单独升格成一个新的风格 option？”

## 稳定设计原则

- 把首屏当海报，不要当课程目录
- 内容页不能掉回普通 CMS 模板
- 图像必须承担叙事职责，而不是只做装饰
- 数据和元信息要像任务简报，不要像营销 badge
- 标题、正文、图注、术语、指标必须属于同一套信息系统
- 中文技术 UI 中，中文和拉丁/数学文本要分别保持稳定统一的字体体系

## 必须避免

- 网课平台感
- SaaS 仪表盘式卡片拼盘
- 廉价未来风发光边框
- 过多的 pills、徽章、tab 和小控件
- 首页高级、内页普通的“两张皮”
- 只有装饰作用、没有叙事作用的媒体

## 自检问题

- 首页是不是第一眼就建立了世界观？
- 内容页能不能撑住长阅读而不散？
- 元信息、图像、数据和正文是不是像同一套系统？
- 如果去掉阴影和渐变，页面还高级吗？
- 在桌面、中间宽度和手机上，是否依然稳定、安静、可读？
