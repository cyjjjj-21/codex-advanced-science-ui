# advanced-science-ui 验证指南

这份文档用于验证 v1.5 升级后的 skill 是否真的生效，而不是只看它“看起来多了几个文件”。

## 验证目标

需要同时验证 5 件事：

1. 默认 `auto-hybrid` 仍然能稳定工作
2. 显式 `style option` 会改变输出方向
3. 新 benchmark 能被结构化吸收
4. 明显异类风格会触发“是否新建 option”的询问，而不是被直接硬混进默认模式
5. 动态交互不再只靠静态截图判断，而有明确的状态采样规则

## 关键交互规则

以下场景必须视为“直接执行优先”，不应该先弹 visual companion，也不应该先停在提案确认：

- 用户正在验证 skill 默认行为
- 用户已经明确要成品图、PNG、页面、截图或单页模版
- 用户已经显式给了 style option

允许的一句话说明：

```text
默认按 auto-hybrid 执行，主方向偏 cinematic-narrative，辅方向带一点 mission-data。
```

或：

```text
按 mission-data 执行，我会直接做成任务简报式的火星采样详情页。
```

但在这之后应直接进入产出，而不是继续兜售 visual companion 或再要一次确认。

## 推荐验证流

### 1. 默认模式验证

```text
用 $advanced-science-ui 做一个“极地海洋观测任务”的横版科普单页，不给额外 benchmark。
```

预期：

- 默认走 `auto-hybrid`
- 不要求用户先选风格
- 不弹 visual companion
- 不停在提案阶段

### 1.5 动态状态采样验证

如果任务本身带明显动效或交互，应补做以下状态采样：

- scroll 关键帧：页面起点、25%、50%、75%
- hover 前后：至少对一个主交互元素做前后对比
- sticky 切换前后：至少对一个 pin / sticky section 做前后对比
- reveal / expand 前后：至少对一个显隐状态做前后对比
- click-state sweep：至少抽样 2 到 5 个代表性点击目标，记录点击后属于哪种状态变化

验收重点：

- 动效是否服务叙事、阅读或信息揭示
- 动效是否破坏页面稳定性与可读性
- 动效是否越过当前 option 的边界
- 点击后变化到底是 modal、原位切换、sticky 同步、参数交换还是局部刷新，不能笼统记成“有很多小弹窗”

这里的 Playwright 不只是为了截图留档，而是为了做“行为采样 + 状态对照”。

推荐直接配合：

- [MOTION_VALIDATION_TEMPLATE.zh-CN.md](./MOTION_VALIDATION_TEMPLATE.zh-CN.md)
  - 统一 scroll / click-state / sticky / hover 的最小采样集

### 2. 显式 option 验证

```text
用 $advanced-science-ui，偏 mission-data，做一个火星采样任务详情页。
```

```text
用 $advanced-science-ui，偏 editorial-museum，做一个矿物标本数字图录页。
```

```text
用 $advanced-science-ui，偏 playful-data-essay，做一个“城市鸟类迁徙路径”的互动数据故事页。
```

预期：

- 两者风格差异肉眼可辨
- 两者都直接进入执行
- 不弹 visual companion
- `playful-data-essay` 会把交互机制本身当成叙事骨架，而不是只换一层配色

### 3. 补强已有风格验证

```text
学习这个新网站的首页和内容页，并更新 advanced-science-ui。
如果它只是补强现有风格，就直接更新经验库和 prompt；不要新建 option。
```

预期：

- 会同时看首页和内容页
- 会优先更新 `references/benchmark-library.md`
- 不会直接新建 option

### 4. 新风格候选验证

```text
学习这个新网站的首页和内容页，并判断它是补强现有风格，还是应该升级成新的 style option。
```

预期：

- 如果它明显偏离现有分类，会先询问用户：

```text
这个参考更适合补强现有风格，还是要单独升格成一个新的风格 option？
```

## 通过标准

只要以下条件同时成立，就算这轮升级有效：

- 默认模式能直接出活
- 显式 option 能稳定改变输出方向
- benchmark 学习结果会落进 repo 文件
- 异类风格会先询问而不是擅自吸收
- 动态体验会被按状态采样验证，而不是只停在首屏截图

## phase 2 示例

当前已经有两组真实案例可用于回归：

- `Distill`
  - 应被判断为“新候选，暂不升格”
  - 关键证据是 `sticky sync / parameter swap / inline update`
- `Apple AirPods Pro 3`
  - 应被判断为“强化已有风格”
  - 关键证据是 scroll narrative、sticky local nav、hash gallery 和 tab 切换
