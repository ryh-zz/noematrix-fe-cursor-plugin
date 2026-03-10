---
name: technical-best-practices
description: 实现步骤、组件拆分、样式适配与资源检查。实现需求、接 Figma 稿、做资源与样式检查时按需参考。
---

# 实现步骤

- 先实现整体布局
- 再实现具体组件
- 最后优化样式细节

# 组件拆分

- 设计稿包含多个组件时，建议分别实现
- 每个组件独立文件，便于维护

# 样式适配

- Figma 生成的代码可能需要调整以符合项目规范（见 **technical-conventions** 与 **style-standards**）

# 资源处理

- 图片资源会自动下载到 `src/assets/img/`
- 图标优先使用项目中的 iconfont：`src/assets/iconfont/`
- iconfont 找不到时用 **`.icon-default-infoCircle`** 代替
- iconfont 尺寸用 `src/styles/iconfont.scss` 中的 class 设置，没有对应 class 时用 **`.icon-size-16`** 代替

# 检查

- 检查间距和字体大小是否转换为 SCSS 变量
- 检查有无颜色未替换为 theme.css 的 var 变量
