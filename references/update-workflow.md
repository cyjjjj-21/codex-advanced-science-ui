# Update Workflow

当用户提供新的 benchmark 网站时，`advanced-science-ui` 应按以下流程吸收，而不是直接把观察结果塞进主 prompt。

## 标准流程

1. 明确观察对象
   - 至少看首页
   - 至少看一个代表性内容页
   - 必要时补看第二个内容页，避免误判

2. 按统一维度记录
   - 参考 `style-axes.yaml`
   - 记录这个站在首页叙事、内容页系统、图像策略、排版节奏、元信息和数据表达上的特点

3. 对比现有 option
   - 判断它最接近哪个现有 option
   - 判断它是在强化已有 option，还是在挑战现有分类

4. 写入 benchmark library
   - 使用 `templates/benchmark-entry.md`
   - 先把观察沉淀成案例条目，再考虑更新 prompt

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
