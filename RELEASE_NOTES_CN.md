# 发布说明

## v1.6.1

这个版本没有新增 style option，而是把 [MoMA](https://www.moma.org/) 的机构化图录能力吸收进了现有 `editorial-museum` 分支。

### 本版新增

- `references/benchmark-library.md` 新增 MoMA benchmark 条目
- `references/style-options.yaml` 与 `STYLE_OPTIONS.md` 强化 `editorial-museum`
- `PROMPT.md` 补上馆藏目录级元信息、展厅/楼层定位、作品标签系统这类能力

### 这次补强了什么

MoMA 让这条分支更像真实博物馆网站，而不只是“安静留白的高级感”。新增的重点不是表面风格，而是：

- 馆藏标签系统
- 作者 / 年份 / 材质 / 安装历史等正式元信息
- 展览页、作品页、杂志页三种内容类型仍然共用同一套机构化阅读秩序

## v1.6.0

这个版本把 [The Pudding](https://pudding.cool/) 升级成了新的 style option：`playful-data-essay`。

它不再被当作现有 museum / mission / cinematic 分支的补丁，而是作为一条单独的“互动式 visual essay / explorable explanation”路线保留下来。

### 本版新增

- 新 option：`playful-data-essay`
- `STYLE_OPTIONS.md` 增加对应说明、适用场景和禁忌项
- `PROMPT.md` 增加对互动式 visual essay 的触发与边界规则
- `references/benchmark-library.md` 新增 The Pudding benchmark 条目
- `references/style-options.yaml` 增加结构化 option 定义

### 为什么不混进默认模式

The Pudding 的强项是“一个洞察配一个定制机制”，它和现有 `editorial-museum`、`mission-data` 的稳定内容系统思路不同。如果直接混入默认 `auto-hybrid`，容易把大多数普通科普页面带偏成过度交互、过度 playful 的方向。

## v0.1.0

这是 `codex-advanced-science-ui` 的首个公开版本。

这个版本主要解决一个很具体的问题：很多模型在写“科普 / 教学 / 研究传播”类页面时，容易把界面做成传统网课平台、SaaS 卡片墙，或者只有首页好看、内容页迅速退化成普通文章模板。

这个 skill 通过一组更明确的设计约束，把方向收紧到：

- 首页像电影海报
- 内容页像数字图录或科学任务档案
- 图像、数据、术语、正文和 CTA 属于同一套视觉系统

### 本版包含

- `SKILL.md`
  - 高级科普 UI 的触发条件与执行规则
- `PROMPT.md`
  - 可直接复用的中文高阶提示词
- `agents/openai.yaml`
  - 中文默认 prompt 与 UI 元数据
- `LICENSE` 与 `LICENSE.zh-CN.md`
  - 开源协议与中文说明
- `assets/preview.svg`
  - 仓库预览图

### 参考方法

本 skill 的规则并不是凭空写出来的，而是基于对以下站点首页与代表性内容页的拆解提炼：

- OceanX
- Brooklyn Museum
- NASA JPL
- MasterClass

重点吸收的不是“长得像”，而是这些站共同具备的系统能力：

- 强世界观的首页
- 稳定可读的内容页
- 统一的元信息与图文结构
- 科学传播里的高级编辑感与可信度

### 适用场景

- 科普网站
- 教学网站
- 数字展览
- 研究传播页面
- 需要承载长文、媒体、术语和数据的知识型产品页面
