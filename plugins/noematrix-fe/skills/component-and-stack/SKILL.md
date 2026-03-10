---
name: component-and-stack
description: 组件写法、技术栈与 MCP 细节。硬性约束见 technical-conventions 规则。写组件、选库、接 Figma/Antd/NoeMatrix 时按需参考。
---

# 组件规范（细节）

硬性约束（MCP 顺序、不覆盖组件样式、Form/文案/拦截器）见 **technical-conventions** 规则。

- 使用函数组件和 Hooks，严格 TypeScript，Props 接口明确定义
- 性能关键处用 `memo`

# 技术栈

- React + TypeScript，Ant Design，SCSS Modules
- 图标：`src/assets/iconfont/`

# MCP 补充

- Figma 生成代码放在对应目录下的 **`view/`**
- 组件查找顺序：NoeMatrix → Ant Design（详见 technical-conventions）
