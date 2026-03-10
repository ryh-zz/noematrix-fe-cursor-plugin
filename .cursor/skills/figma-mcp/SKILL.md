---
name: figma-mcp
description: 使用 Figma MCP 从设计稿生成或核对 UI 代码、截图与变量。在设计稿还原、实现新页面或核对视觉时使用。
---

# Figma MCP

## 何时使用

- 需要根据 **Figma 设计稿实现或还原 UI** 时
- 需要 **设计稿截图** 做参考时
- 需要 **设计变量（颜色、字体等）** 时
- 设计稿链接中包含 `node-id` 或需要指定节点时

## 常用工具

| 用途           | 工具                         | 说明 |
|----------------|------------------------------|------|
| 生成 UI 代码   | `mcp_Figma_get_design_context` | 需 `nodeId`、`fileKey`，可从 Figma URL 解析 |
| 节点结构概览   | `mcp_Figma_get_metadata`      | 仅结构/ID/名称，不生成代码 |
| 截图           | `mcp_Figma_get_screenshot`   | 需 `nodeId`、`fileKey` |
| 设计变量       | `mcp_Figma_get_variable_defs`| 取节点相关变量定义 |
| FigJam 内容    | `mcp_Figma_get_figjam`       | 仅用于 FigJam 文件 |

## URL 解析

- 设计稿 URL 形如：`https://figma.com/design/{fileKey}/xxx?node-id=1-2`
- **fileKey**：`/design/` 后第一段（若有 branch 则用 branchKey）
- **nodeId**：`node-id=1-2` → 使用 `1:2`（冒号）

## 项目约定

- 生成的前端代码放在 **对应 feature 下的 `view/` 或 `ui/` 目录**
- 生成后需按项目规范调整：样式用 SCSS 变量/CSS 变量、组件优先 NoeMatrix 再 antd、不改 antd/NoeMatrix 组件样式
- 图片等资源下载到 `src/assets/img/`，图标优先用项目 iconfont
