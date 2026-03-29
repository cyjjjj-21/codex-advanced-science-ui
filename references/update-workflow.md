# Update Workflow

当用户提供新的 benchmark 网站时，`advanced-science-ui` 应按以下流程吸收，而不是直接把观察结果塞进主 prompt。

## 标准流程

1. 明确观察对象
   - 至少看首页
   - 至少看一个代表性内容页
   - 必要时补看第二个内容页，避免误判
   - 如果该站的高级感明显依赖动态体验，必须额外观察滚动、hover、sticky、reveal 或 click 后状态变化

2. 按统一维度记录
   - 参考 `style-axes.yaml`
   - 记录这个站在首页叙事、内容页系统、图像策略、排版节奏、元信息、数据表达和动态交互语言上的特点
   - 如果动态特征明显，至少补齐：
     - 滚动是否改变叙事结构
     - hover 是否承担信息揭示
     - sticky 是否参与章节推进
     - 点击热点触发的是弹层、原位切换、参数同步，还是新的阅读面板
     - 鼠标交互是点缀还是核心语言
   - 对明显交互型站点，至少做一次代表性 `click-state sweep`
     - 选择 2 到 5 个代表性点击目标
     - 记录它们属于 modal、inline update、sticky sync、parameter swap、reveal panel 或 drill-down 的哪一类
     - 判断这些点击后状态变化是在补强解释，还是已经构成新的阅读范式

3. 对比现有 option
   - 判断它最接近哪个现有 option
   - 判断它是在强化已有 option，还是在挑战现有分类
   - 新增风格判断时，同时参考静态维度和动态维度，不只看截图

4. 写入 benchmark library
   - 使用 `templates/benchmark-entry.md`
   - 先把观察沉淀成案例条目，再考虑更新 prompt
   - 如果动态体验是该站的重要组成，条目中必须显式写出“动态交互学习重点”“click-state sweep 结果”和“动态风险提醒”

5. 判断是否要询问用户
   - 如果明显偏离现有 option，先问用户是否要新建 style option
   - 如果只是补强现有分类，直接更新经验库和 prompt 草稿

6. 更新稳定 prompt
   - 仅把跨站稳定规律写入 `PROMPT.md`
   - 单站点特性优先留在 benchmark library，不要全部升格进主 prompt

## 强制要求

- 不允许只看首页就做总结
- 不允许把所有新观察直接写进主 prompt
- 不允许遇到明显异类风格时擅自创建新 option 而不询问用户
- 不允许把风格 option 越分越细，直到失去可用性
- 不允许把“动态更强”直接等同于“新风格”；只有当动态语言已经改变阅读范式时，才考虑新 option 候选
- 不允许把“点击后东西很多”粗暴记成“弹窗多”；必须区分 modal、原位切换、sticky 同步、参数交换和局部刷新
