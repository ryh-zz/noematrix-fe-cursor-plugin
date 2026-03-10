---
name: react-antd-dev
description: Feature 结构、VM 模式与视图分层。样式与组件硬性约束见 technical-conventions。编写或修改前端功能时按需参考。
---

# React + Ant Design 开发规范

硬性约束（样式、组件、MCP、Form/文案/拦截器）见 **technical-conventions** 规则。

## 项目结构

- **Feature 模块**：`src/features/{featureName}/` 下含 `index.tsx`、`hooks/`（如 `use*VM.ts`）、`model/`、`view/`、`*.module.scss`
- **页面入口**：index 作为事件中转层，只做 `use*VM()` 与子组件的 `onXxx` 回调绑定；业务逻辑在 VM hooks 与 model 中
- **视图组件**：放在 `view/`，只负责展示与抛事件，不直接调 API 或改 Redux

## 补充

- 图标：优先 `src/assets/iconfont/`，找不到用 `.icon-default-infoCircle`；尺寸用 `src/styles/iconfont.scss` 的 class（如 `.icon-size-16`）
- 生成 UI 代码放在对应目录下的 `ui/` 或 `view/` 中
