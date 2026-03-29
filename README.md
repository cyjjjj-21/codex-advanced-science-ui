# Codex 高级科普 UI Skill

这是一个给 Codex 用的本地 skill，用来把“科普 / 教学 / 研究传播 / 展览式知识内容”做得更像数字展览、科学任务档案和纪录片页面，而不是传统网课平台或 SaaS 卡片站。

## 这个 skill 解决什么问题

默认情况下，模型很容易把“教育类 UI”写成这几种东西：

- 网课平台
- 卡片墙
- 模板化暗色科技风
- 只有首页好看、内容页很普通的两张皮

这个 skill 的目标就是纠正这种偏差，让 Codex 同时学会：

- 首页的电影海报感
- 内容页的编辑系统感
- 科学信息的可信度与秩序感
- 以及在需要时，用成熟的互动式 visual essay 讲故事

## 当前能力

这个 skill 现在不只是“一段 prompt”，而是一套可迭代的设计能力，已经具备：

- 默认 `auto-hybrid`
  - 用户不指定风格时，自动判断主方向与辅方向
- 显式 `style option`
  - 当前支持 `cinematic-narrative`、`editorial-museum`、`mission-data`、`image-led-premium`、`playful-data-essay`
- benchmark 学习
  - 新参考网站会同时看首页和内容页，再写入经验库
- 动态交互观察
  - 如果 benchmark 的高级感依赖滚动、hover、sticky 或 reveal，skill 会把动态语言也纳入结构化观察
  - 对交互型站点，会补做 `click-state sweep`，区分 modal、原位切换、sticky 同步、参数交换和局部刷新
- 风格分流
  - 遇到明显异类风格时，会先判断是否该升级成新的 option，而不是硬混进默认模式
- 结构化知识层
  - benchmark、style option、prompt、decision rules、validation 分层维护
- 执行优先
  - 当用户已经明确要 PNG、页面或截图时，优先直接执行，不先兜售额外流程

## 参考来源

这个 skill 的审美与结构规律来自对以下站点的首页与代表性内容页的拆解：

- [OceanX](https://oceanx.org/)
- [Brooklyn Museum](https://www.brooklynmuseum.org/)
- [NASA JPL](https://www.jpl.nasa.gov/)
- [MasterClass](https://www.masterclass.com/)
- [The Pudding](https://pudding.cool/)
- [MoMA](https://www.moma.org/)
- [Fondation Cartier](https://www.fondationcartier.com/en)

不是照抄视觉，而是提炼它们共同的系统能力：

- 首屏建立世界观
- 长文内容依然高级
- 图像、数据、术语、图注和 CTA 属于同一套语言
- 在需要的时候，用定制交互把洞察变成可探索体验
- 在图录、标本、馆藏和档案场景中，把机构化元信息做成真正高级的阅读系统
- 当高级感来自动态语言时，不只看首屏截图，也会观察滚动叙事、hover 和状态切换

## 仓库结构

- `SKILL.md`
  - skill 主体，定义触发条件和执行规则
- `agents/openai.yaml`
  - UI 元数据与默认 prompt
- `PROMPT.md`
  - 一段可直接复用的中文高阶提示词
- `STYLE_OPTIONS.md`
  - 当前支持的风格 option 与调用方式
- `RELEASE_NOTES_CN.md`
  - 中文发布说明与设计来龙去脉
- `LICENSE`
  - 标准 MIT 开源许可证
- `LICENSE.zh-CN.md`
  - MIT 许可证中文说明版
- `assets/preview.svg`
  - skill 预览图
- `docs/ROADMAP.zh-CN.md`
  - skill 的 v1.5 / v2 演进路线图
- `docs/VALIDATION.zh-CN.md`
  - v1.5 升级后的验证流程与通过标准
- `references/`
  - benchmark 经验库、风格维度、决策规则、更新 workflow
- `templates/`
  - 新 benchmark 和新 style option 的记录模板

## 预览图

![高级科普 UI 预览](./assets/preview.svg)

## 安装方式

如果你希望 Codex 直接发现这个 skill，推荐把仓库克隆到本地 skills 目录：

```bash
git clone https://github.com/<your-account>/codex-advanced-science-ui.git ~/.codex/skills/advanced-science-ui
```

如果已经有本地目录，也可以直接覆盖或软链接。

如果你想先在本地试用，再决定是否覆盖现有 skill，可以这样：

```bash
git clone https://github.com/<your-account>/codex-advanced-science-ui.git ~/tmp/codex-advanced-science-ui
```

## 触发方式

你可以显式说：

```text
用 $advanced-science-ui 做这个页面
```

也可以在需求里直接写这些关键词，让它更容易自动触发：

- 科普 UI
- 教学网站
- 展览式内容页
- 科学叙事页面
- 数字图录
- 不要网课感
- 不要 SaaS 卡片墙

## 推荐搭配

如果任务是实际写前端页面，建议把这个 skill 和已有的前端实现能力一起用：

- `frontend-skill`
  - 负责整体前端高级感和落地实现
- `advanced-science-ui`
  - 负责把方向收紧到“高级科普 / 展览 / 教学叙事”

## 使用原则

这个 skill 最核心的判断标准不是“有没有做出一个漂亮 hero”，而是：

- 首页像不像一张海报
- 内容页像不像一套真正可读的知识系统
- 长内容会不会一滚到底就掉回普通模板

如果只有第一页惊艳、后面全是常规文章流，那就说明这个 skill 还没有真正生效。

从 v1.5 开始，这个 skill 还增加了两种能力：

- 能把新 benchmark 网站按统一框架吸收进经验库
- 遇到明显异类风格时，会先询问要不要升级成新的 style option，而不是直接硬混进默认 prompt

现在进一步补上了两条边界：

- `playful-data-essay` 是专门的互动叙事分支，不默认混入大多数普通项目
- `editorial-museum` 与 `mission-data` 也能吸收 Apple Environment 这种“明亮底色 + 证据组织 + 公共事务 brief”型参考，而不必只靠暗场或大片建立高级感
- `editorial-museum` 进一步吸收了 MoMA 的“馆藏目录级元信息 / 展厅与楼层定位 / 作品标签系统”能力
- `editorial-museum` 也吸收了 Fondation Cartier 的“品牌化纯色场 / 海报式机构首页 / Visit 与 Programme 并存的文化机构入口”能力
- 现在开始补“动态交互语言”这一层：以后判断 benchmark 是否挑战旧分类，不只看静态页面，也看滚动叙事、hover 行为和 reveal 机制

## 动效实现建议

这个 skill 现在会约束“动效应该长什么样、怎么验收”，但它本身保持库无关，不绑定具体实现方案。

- CSS / WAAPI
  - 默认推荐，适合克制微交互、轻 reveal 和低噪音状态切换
- Motion
  - 更适合 React 场景里的组件状态切换、presence 和布局过渡
- GSAP
  - 更适合 scroll narrative、timeline、复杂 parallax 和强编排式章节推进

选择实现库时，优先按页面气质和交互密度匹配，而不是先决定“必须上某个动画库”。

## 开源说明

本仓库使用 MIT 协议发布：

- 法律效力版本：`LICENSE`
- 中文说明版本：`LICENSE.zh-CN.md`

## 发布记录

首个公开版本的整理说明见：

- `RELEASE_NOTES_CN.md`

## 路线图

这个 skill 不是一次性 prompt，而是会持续打磨的设计能力。当前已经把后续的 `v1.5 / v2` 升级计划整理成 roadmap：

- [docs/ROADMAP.zh-CN.md](./docs/ROADMAP.zh-CN.md)

这份 roadmap 主要回答 4 个问题：

- 新 benchmark 网站以后怎么被吸收
- 学习结果如何沉淀进经验库和 prompt
- 什么时候需要把新风格升级成 option
- v1.5 和 v2 的边界、目标和进入条件分别是什么

## 验证方式

如果你想验证这个 skill 升级是否真的有效，而不是只看文档数量，直接看：

- [docs/VALIDATION.zh-CN.md](./docs/VALIDATION.zh-CN.md)

这份文档会验证：

- 默认 `auto-hybrid` 是否还能稳定工作
- 显式 style option 是否真的改变输出
- 新 benchmark 是否会落进经验库
- 明显异类风格是否会触发新 option 询问
- 新增 option 后，显式调用是否能稳定落到新分支

## v1.5 结构说明

v1.5 开始，仓库会逐步形成“工作流层 + 经验库层 + prompt 层 + option 层”的结构：

- `SKILL.md`
  - 定义如何使用 skill、何时询问用户、何时学习 benchmark
- `PROMPT.md`
  - 提供稳定版 prompt
- `STYLE_OPTIONS.md`
  - 提供当前风格大类
- `references/benchmark-library.md`
  - 沉淀参考网站的首页 + 内容页学习结果
- `references/style-axes.yaml`
  - 定义统一观察维度
- `references/style-options.yaml`
  - 维护结构化 option 元数据
- `references/decision-rules.md`
  - 定义“补强已有风格 / 修正已有风格 / 新增风格候选”的判断标准
