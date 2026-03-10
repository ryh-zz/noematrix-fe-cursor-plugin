---
name: noematrix-mcp
description: 使用 NoeMatrix MCP 查询公司自研组件库的组件列表与 API。在需要 NoeMatrix 组件用法或类型定义时使用。
---

# NoeMatrix MCP

## 何时使用

- 需要 **公司自研 NoeMatrix 组件** 的用法、Props、TypeScript 类型时
- 做 UI 时优先选用 NoeMatrix 已有组件，没有再考虑 Ant Design
- 与 Ant Design MCP 配合：先 NoeMatrix，没有再查 antd

## 使用方式

| 用途         | 工具                             |
|--------------|----------------------------------|
| 看有哪些组件 | `mcp_noematrix_list_components`  |
| 组件文档与 TS 定义 | `mcp_noematrix_get_component_doc`，参数 `componentName` |

**组件名称示例**：`NmEmpty`、`GlobalLoading`、`Table`、`StatusTag`、`BatteryPower`、`NmMenu` 等（与 list 返回一致，区分大小写）。

## 约定

- 遇到 NoeMatrix 组件时 **直接使用，不修改其样式**
- 项目中已依赖 `noematrix-component-library`，按文档引入即可
- 生成或修改的 UI 放在对应 feature 的 `view/` 或页面级 `ui/` 目录
