---
name: style-standards
description: 样式细节与变量用法。硬性约束见 technical-conventions 规则。写样式、改 UI、做 Figma 适配时按需参考。
---

# 样式规范（细节）

硬性约束（颜色/间距/禁止项/变量引入）见 **technical-conventions** 规则。

## 变量用法

- `src/styles/theme.css`：颜色类 CSS 变量
- `src/styles/foundation.scss`：间距、字体大小等 SCSS 变量，可直接使用，无需转成 `var()`
