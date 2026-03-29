# motion MVP 最终验证

这份文档给 `advanced-science-ui` 的 motion MVP 做最终验收，重点回答两件事：

1. 这套动态维度是否已经覆盖真实网站里的关键交互语言
2. 这套规则是否已经足以支持“补强旧风格 / 修正旧风格 / 新候选”的判断

## 推荐验证流

### 验证样本 A：Distill

- 页面：
  - `https://distill.pub/`
  - `https://distill.pub/2016/misread-tsne/`
- 目标：
  - 验证 `click_state_pattern`
  - 验证 `state_transition_style`
  - 验证 `sticky_reveal_behavior`
- 预期结论：
  - `新候选，暂不升格`
- 关键证据：
  - 点击小图会把参数同步进上方试验台
  - 滑杆直接驱动原位状态变化
  - 主交互语言是 `sticky sync / parameter swap / inline update`

### 验证样本 B：Apple Scroll Narrative

- 页面：
  - `https://www.apple.com/`
  - `https://www.apple.com/airpods-pro/`
- 目标：
  - 验证 `scroll_narrative`
  - 验证 `sticky_reveal_behavior`
  - 验证 `click_state_pattern`
- 预期结论：
  - `强化已有风格`
- 关键证据：
  - sticky local nav
  - hash gallery 切换
  - tab 切换
  - staged media progression

### 验证样本 C：The Pudding - Happy Map

- 页面：
  - `https://pudding.cool/`
  - `https://pudding.cool/2026/02/happy-map/`
- 目标：
  - 验证 `hover_behavior`
  - 验证 `cursor_interaction`
  - 验证 canvas / 地图交互如何影响阅读
- 预期结论：
  - `强化已有风格`
- 关键证据：
  - 鼠标在 canvas 上移动时，cursor 会在 `grab` 与 `pointer` 间切换
  - 点击可选点后，会原位展开人物卡片，而不是跳转或弹出传统 modal
  - hover / cursor 在这里承担的是“发现可探索数据点”的功能，而不是纯装饰微交互

## 最终结论

### 1. 已经被真实样本压实的维度

- `scroll_narrative`
- `state_transition_style`
- `sticky_reveal_behavior`
- `click_state_pattern`
- `hover_behavior`
- `cursor_interaction`

### 2. 现阶段已经能稳定区分的三类情况

- `强化已有风格`
  - 例如 Apple Scroll Narrative、The Pudding Happy Map
- `新候选，暂不升格`
  - 例如 Distill
- `建议升格新 option`
  - 当前还没有在 motion MVP 阶段直接执行，但判定模板已经准备好

### 3. MVP 是否达到“可用”

- 结论：`是`
- 原因：
  - 已经有覆盖 scroll、click-state、sticky、hover、cursor 的真实样本
  - 已经有统一的动态验证模板
  - 已经有统一的分类输出模板
  - 已经证明动态语言会影响风格归类，而不是只作为页面装饰

### 4. 当前仍然不做的事

- 不做性能 profiling
- 不做触摸手势 / mobile gesture 专项建模
- 不做动画库绑定
- 不做自动化脚本生成器

## 建议下一步

如果继续往前推进，最值的方向是：

- `style 治理增强`
  - 特别是继续观察 Distill 这一类是否最终需要独立 option
- 或 `动态验证模板化 + 半自动执行`
  - 把当前模板进一步变成可复用脚手架
