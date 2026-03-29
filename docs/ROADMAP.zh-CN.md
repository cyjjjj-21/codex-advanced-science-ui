# advanced-science-ui 演进路线图

## 背景

`advanced-science-ui` 当前已经能把科普、教学、研究传播类界面的视觉方向从“网课平台感 / SaaS 卡片墙 / 模板科技风”拉回到“数字展览 + 科学纪录片 + 编辑型内容系统”的轨道上。

但它现在本质上仍然是一个偏静态的 skill：

- 经验主要写死在 `SKILL.md` 和 `PROMPT.md`
- 参考网站的学习结果还没有变成结构化资产
- 新增 benchmark 时缺少统一吸收流程
- 如果新参考风格与现有总结差异很大，还没有明确的分流与提问机制

因此，接下来的演进目标不是简单“再加一些 prompt”，而是把它升级成一个可持续迭代的设计知识系统。

## 总体目标

把 `advanced-science-ui` 从“静态 prompt 包”升级为“可积累、可分流、可刷新”的高级科普 UI skill。

核心能力分三步建立：

1. 让新参考网站可以按统一框架被学习和记录
2. 让学习结果可以稳定刷新主 prompt，而不是人工随意拼接
3. 让明显不同的设计哲学可以升格成可选风格 option，而不是被强行混进默认模式

## 非目标

以下内容不属于当前两阶段的范围：

- 不做自动联网抓取和全自动 benchmark 解析
- 不做数据库、服务端或独立管理后台
- 不做复杂的参数化 prompt 引擎
- 不追求一次性穷尽所有教育 / 科普 / 展览 UI 风格

当前优先级是：先把知识结构和更新流程搭稳，再谈自动化。

## 阶段划分

### v1.5：结构化升级

定位：在不改变当前 skill 使用门槛的前提下，让它具备“可持续吸收新参考站”的能力。

#### 目标

- 把已有经验从单段 prompt 中拆成多层结构
- 建立 benchmark 学习记录机制
- 建立风格维度与已有风格大类
- 建立“何时自动吸收、何时询问用户是否创建新 option”的决策规则
- 保持当前使用体验尽量不变

#### 交付物

- 一个重构后的 `SKILL.md`
- 一个保留稳定输出能力的 `PROMPT.md`
- 一份面向人类可读的 `STYLE_OPTIONS.md`
- 一套 `references/` 下的结构化知识文件
- 一套 benchmark / option 模板文件
- 一套更新 workflow 文档

#### 建议目录

```text
codex-advanced-science-ui/
├── SKILL.md
├── PROMPT.md
├── README.md
├── STYLE_OPTIONS.md
├── docs/
│   └── ROADMAP.zh-CN.md
├── references/
│   ├── benchmark-library.md
│   ├── style-axes.yaml
│   ├── style-options.yaml
│   ├── update-workflow.md
│   ├── prompt-assembly-rules.md
│   └── decision-rules.md
├── templates/
│   ├── benchmark-entry.md
│   └── style-option.md
└── examples/
```

#### 核心设计

1. `SKILL.md`
   只保留触发条件、工作流程、默认行为、询问时机和自检标准。

2. `PROMPT.md`
   只保留当前稳定版的高阶提示，不再承担“经验仓库”的角色。

3. `references/benchmark-library.md`
   记录每个参考网站的学习摘要，要求同时覆盖首页和代表性内容页。

4. `references/style-axes.yaml`
   定义统一分析维度，例如：
   - hero_narrative
   - content_page_system
   - typography_voice
   - image_strategy
   - grid_rhythm
   - metadata_behavior
   - data_expression
   - cta_tone
   - motion_density
   - cinematicness
   - editorialness
   - industrialness

5. `references/style-options.yaml`
   记录已确认的风格 option 及其适用场景。

6. `references/decision-rules.md`
   规定以下判断：
   - 何时属于“强化已有风格”
   - 何时属于“修正已有风格”
   - 何时属于“新增风格候选”
   - 何时必须先询问用户

7. `references/update-workflow.md`
   固化“收到新网站后该怎么学”的标准流程。

#### 默认风格 option

当前内置以下 6 类：

- `auto-hybrid`
- `cinematic-narrative`
- `editorial-museum`
- `mission-data`
- `image-led-premium`
- `playful-data-essay`

其中：

- `auto-hybrid` 作为默认模式
- `playful-data-essay` 作为更专门的互动叙事分支，不默认混入大多数任务
- 其余几类对应当前已经验证过的主审美来源

#### 用户交互规则

当新参考网站满足以下任意条件时，skill 应主动询问用户是否要新建风格 option：

- 与现有任一 option 在 3 个以上核心维度上差异明显
- 会明显改变默认 prompt 的整体气质
- 更像一种新的设计哲学，而不是现有大类的变体
- 适用场景非常专门，单纯混入默认模式会降低稳定性

建议询问语句统一为：

“这个参考更适合补强现有风格，还是要单独升格成一个新的风格 option？”

#### 验收标准

v1.5 完成后，应满足以下条件：

- 新参考网站可以被写入统一结构，而不是自由散文式总结
- 当前 benchmark 与 style option 可以被持续整理进经验库，并保持文档与结构化元数据一致
- `PROMPT.md` 仍可独立工作，不依赖人工口头解释
- skill 能区分“默认自动模式”和“显式指定风格模式”
- 当出现明显异类参考时，skill 会先问，不会直接把新风格硬塞进默认经验

#### 风险

- 结构一旦设计得过重，后续维护会变慢
- 维度过多会让学习成本上升，维度过少又会失去判断力
- 如果 option 分得太细，调用体验会变复杂

因此 v1.5 的原则是：先做轻量结构化，不做过度系统化。

### v2：半自动刷新与更强的风格管理

定位：在 v1.5 的结构化基础上，让知识沉淀和 prompt 刷新更高效，但仍保持人工决策在关键节点上。

#### 目标

- 提高 benchmark 更新效率
- 降低人工整理 prompt 的成本
- 增强风格 option 的治理能力
- 为后续更强自动化留下接口

#### 候选能力

1. benchmark 录入辅助
   - 根据统一模板生成新 benchmark 条目的草稿
   - 强制提醒补齐首页和内容页观察

2. prompt 刷新辅助
   - 根据经验库重组稳定 prompt 草稿
   - 标出“新增规则”“修正规则”“冲突规则”

3. 风格 option 管理增强
   - 为每个 option 增加适用任务、禁忌场景、推荐混搭关系
   - 支持“强指定”“弱偏向”“自动判断”三种调用方式

4. 差异提醒
   - 当新 benchmark 与现有 option 偏差大时，自动生成“是否新建 option”的提议说明

5. 版本记录
   - 对 skill 的知识结构演化增加版本日志

#### 验收标准

v2 完成后，应满足以下条件：

- 新 benchmark 的录入明显比 v1.5 更快
- 主 prompt 的刷新过程更可追踪
- 风格 option 的增加和调整更可控
- 即便 benchmark 数量增长，整体结构依然清晰

## 执行顺序

建议按以下顺序推进：

1. 完成 v1.5 的目录重构
2. 把当前 benchmark 迁移并持续整理进经验库
3. 固化 decision rules 和 update workflow
4. 重写 `SKILL.md` 和 `PROMPT.md`
5. 补 `STYLE_OPTIONS.md`
6. 用 1 到 2 个新增参考网站试跑一次更新流程
7. 再评估是否进入 v2

## 进入 v2 的前提

只有当以下条件满足时，再启动 v2：

- v1.5 结构已经实际使用过至少几轮
- 已经遇到至少 1 次“是否拆出新风格 option”的真实判断场景
- 当前手工刷新 prompt 的维护成本开始明显上升

如果这些条件还没满足，就优先继续打磨 v1.5，不着急上自动化。

## 当前决策结论

当前项目采用以下策略：

- 先做 `v1.5`
- 先解决结构化知识、更新流程、风格分流
- `v2` 暂时作为已确认方向保留，不抢先实现

这意味着后续每次新增 benchmark，都应该优先检验：

- 这条经验应该进入经验库哪里？
- 它是在强化旧风格，还是在挑战旧分类？
- 它会不会影响默认 prompt 的稳定性？

只有先把这三个问题答清楚，`advanced-science-ui` 才会越来越像一个“可生长的设计系统”，而不是越来越长的一段 prompt。
