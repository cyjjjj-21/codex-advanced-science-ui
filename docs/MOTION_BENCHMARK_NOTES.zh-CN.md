# motion-mvp phase 2 结论

这份文档记录 `motion-mvp` 第二阶段用真实动态 benchmark 压测规则后的结论，避免后续只靠聊天记忆回想。

## Benchmark A：Distill

- 观测页面：
  - `https://distill.pub/`
  - `https://distill.pub/2016/misread-tsne/`
- 首页判断：
  - 更像研究型解释期刊入口，而不是海报首页、museum 序厅或故事档案馆
  - 品牌气质来自作者署名、引用、代码开放、长文可信度与统一排版系统
- 动态证据：
  - 至少抽样了 3 个 `.runner.clickable`
  - 点击后都不是跳转详情页，而是把参数同步进上方试验台，并触发可视化状态变化
  - 滑杆直接驱动原位状态更新
  - 交互主语言是 `sticky sync / parameter swap / inline update`
- 归属结论：
  - 它不是 `playful-data-essay` 的简单学术版
  - 当前更适合记录为 `scholarly explorable explanation` 新候选
  - 本阶段只形成判断依据，不直接升格成新 option
- 为什么不能直接并入 `playful-data-essay`：
  - 语气更学术、更论文化，而不是杂志式 playful editorial
  - 交互承担的是参数推理和解释验证，不是读者参与型故事体验
  - 页面世界观来自研究解释系统，不来自可玩故事实验室

## Benchmark B：Apple Scroll Narrative

- 观测页面：
  - `https://www.apple.com/`
  - `https://www.apple.com/airpods-pro/`
- 首页判断：
  - Apple 首页继续强化品牌宇宙、全局导航秩序和产品专题入口
  - 不是新风格证据，只提供品牌化基线
- 动态证据：
  - `AirPods Pro 3` 页面完成了 4 个 scroll 关键帧采样
  - 页面存在稳定的 sticky local nav
  - `#highlights-gallery-item-*` 的 hash 轮播切换被确认可用
  - section 内 `Live Translation / Controls / Siri / Connectivity` tab 切换会原位替换内容
- 归属结论：
  - 它强化 `cinematic-narrative`
  - 同时帮助校准它与 `image-led-premium` 的边界
  - 不足以形成新 option
- 为什么不新建 option：
  - 动态虽然强，但仍服务滚动分镜与品牌故事推进
  - 点击行为主要是 hash 切换、tab 切换和 staged reveal，不是新的阅读哲学
  - 页面仍然更像成熟的 scroll narrative，而不是新的 explorable explanation 或数据交互范式

## 对 motion 维度的结论

- 已证明够用的维度：
  - `scroll_narrative`
  - `state_transition_style`
  - `sticky_reveal_behavior`
  - `click_state_pattern`
- 仍偏模糊的维度：
  - `hover_behavior`
  - `cursor_interaction`
  - 原因：很多高质量动态站点的主差异并不依赖 hover 或 cursor，而依赖 scroll 和 click-state
- 当前判断：
  - motion 维度已经足以支持真实 benchmark 的初步归类
  - 它确实提升了“是否应升格新 option”的判断准确度
  - 已具备进入下一阶段的条件，但下一步更适合补更多动态 benchmark，而不是马上升格新 option
