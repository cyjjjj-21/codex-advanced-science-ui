# 动态验证模板

这份模板用于给 `advanced-science-ui` 的 benchmark 学习提供统一的动态验证脚手架。目标不是做性能 profiling，而是稳定判断一个站点的动态语言到底在服务什么阅读范式。

## 什么时候必须启用

满足任意一条就应启用：

- 页面高级感明显依赖滚动叙事
- 页面存在 sticky section、章节 pin、hash gallery 或 staged reveal
- 页面有多个点击后原位变化的交互热点
- 页面把参数、图示、控制条或媒体状态做成解释机制的一部分

## 最小采样集

### 1. Scroll 关键帧

- 至少采样 4 帧：
  - `0%`
  - `25%`
  - `50%`
  - `75%`
- 记录：
  - 当前主标题或主视觉内容
  - 是否存在 sticky local nav / pinned control
  - 滚动是否改变叙事结构，而不只是把内容往下推

### 2. Click-State Sweep

- 至少抽样 `2 到 5` 个代表性点击目标
- 对每个目标必须记录：
  - `触发前状态`
  - `触发动作`
  - `触发后状态`
  - `类型判断`

可用类型：

- `modal`
- `inline update`
- `sticky sync`
- `parameter swap`
- `reveal panel`
- `drill-down`

禁止写法：

- “会弹窗”
- “会变化”
- “有很多小交互”

必须写清到底是哪一种状态变化。

### 3. Sticky / Tab / Gallery 检查

- 至少记录 1 个：
  - sticky section
  - tab 切换
  - gallery/hash 切换
  - staged reveal
- 重点判断：
  - 它是在帮助组织阅读
  - 还是已经构成新的阅读哲学

### 4. Hover / Cursor 检查

- 如果页面明显依赖 hover 或 cursor interaction，再补做这一项
- 记录：
  - hover 是信息提示、图像强化还是交互主骨架
  - cursor 是装饰、导航辅助还是控制机制

如果页面不依赖 hover / cursor，不必强行记录为“高”。

## 判断模板

### 记录格式

- `触发前状态`：
- `触发动作`：
- `触发后状态`：
- `类型判断`：
- `对阅读范式的影响`：

### 问题清单

每轮动态验证至少回答：

1. 动态是在推进叙事，还是只在制造热闹？
2. 点击后是打开新层，还是原位切换？
3. sticky 是辅助导航，还是主叙事装置？
4. 动态语言是在强化已有 option，还是已经挑战旧分类？

## 最终输出要求

动态验证结束后，至少产出这些结论：

- `scroll_narrative`
- `state_transition_style`
- `sticky_reveal_behavior`
- `click_state_pattern`
- `动态交互学习重点`
- `动态风险提醒`

如果某站的关键差异主要来自动态语言，必须在结论里明确写出：

- 它是强化已有风格
- 修正已有风格
- 新候选，暂不升格
- 建议升格新 option

不要只写“这个站很会动”。
