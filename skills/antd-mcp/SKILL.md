---
name: antd-mcp
description: 使用 Ant Design MCP 查询组件文档与用法。在需要 antd 组件 API、示例或引入方式时使用。
---

# Ant Design MCP

## 何时使用

- 需要 Ant Design 组件的 **API、Props、示例** 时
- 不确定用哪个 antd 组件或写法时
- 与 NoeMatrix 搭配：NoeMatrix 没有的组件再查 antd

## 使用方式

调用 **`mcp_ant-design_get_antd_doc`**，传入文档路径：

| 场景       | path 示例                    |
|------------|------------------------------|
| 组件文档   | `/components/button-cn`      |
| 组件文档   | `/components/table-cn`       |
| 介绍/概览  | `/docs/react/introduce-cn`   |

- 路径一般为 `/components/{组件名}-cn` 或 `/docs/...`
- 查完后直接按文档使用组件，**不要改 antd 默认样式**

## 约定

- 项目中已通过 `ConfigProvider` 配置主题与中英文 locale，组件按文档正常使用即可
- 遇到 antd 组件时直接使用，不额外包一层或覆盖样式
