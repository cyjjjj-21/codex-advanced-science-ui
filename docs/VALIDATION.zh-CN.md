# advanced-science-ui 验证指南

这份文档用于验证 v1.5 升级后的 skill 是否真的生效，而不是只看它“看起来多了几个文件”。

## 验证目标

需要同时验证 4 件事：

1. 默认 `auto-hybrid` 仍然能稳定工作
2. 显式 `style option` 会改变输出方向
3. 新 benchmark 能被结构化吸收
4. 明显异类风格会触发“是否新建 option”的询问，而不是被直接硬混进默认模式

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

### 2. 显式 option 验证

```text
用 $advanced-science-ui，偏 mission-data，做一个火星采样任务详情页。
```

```text
用 $advanced-science-ui，偏 editorial-museum，做一个矿物标本数字图录页。
```

预期：

- 两者风格差异肉眼可辨
- 两者都直接进入执行
- 不弹 visual companion

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
