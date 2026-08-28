# NoeMatrix FE Cursor Plugin

基于 Cursor 插件机制的 **React + TypeScript + Ant Design** 前端项目插件，为 NoeMatrix 前端团队提供统一规则、技能、验证 Agent 与 MCP 配置。

## 插件元数据

- **插件名**：`noematrix-fe`
- **版本**：`1.2.2`
- **发布形态**：Team Marketplace / 本地安装
- **许可证**：`UNLICENSED`

## 包含内容

### Rules（规则）

| 文件 | 说明 |
|------|------|
| `technical-conventions.mdc` | 核心技术约定（alwaysApply） |
| `project-context.mdc` | 项目上下文（alwaysApply） |
| `state-management.mdc` | 状态管理规范 |
| `routing.mdc` | 路由约定 |
| `react-ts-patterns.mdc` | React + TypeScript 模式 |
| `package-manager.mdc` | 包管理器使用 |
| `file-naming.mdc` | 文件命名规范 |

### Skills（技能）

| 技能 | 说明 |
|------|------|
| `antd-mcp` | Ant Design MCP 使用 |
| `figma-mcp` | Figma MCP 设计稿还原 |
| `noematrix-mcp` | NoeMatrix 组件库 MCP |
| `component-and-stack` | 组件与技术栈使用 |
| `react-antd-dev` | React + Ant Design 开发 |
| `src-tree` | 项目结构导航 |
| `style-standards` | 样式规范 |
| `technical-best-practices` | 技术最佳实践 |

### Agents（子代理）

| 代理 | 说明 |
|------|------|
| `verifier` | 验证已实现工作，执行约束检查与测试汇报 |

## 发布与自动更新（GitHub 仓库）

仓库在 GitHub 时，Team Marketplace 会从该仓库拉取插件；更新随仓库推送生效。

### 管理员侧

1. **开启自动刷新**：Cursor Dashboard → **Settings → Plugins → Team Marketplaces** → 选中本插件源 → 开启 **Enable Auto Refresh**。  
   推送至默认分支（如 `main`）后，会触发刷新（若未生效可尝试在设置中手动点击 Refresh 或清除 `~/.cursor/plugins/cache/` 后重装）。
2. **发布新版本**：
   - 在 `.cursor-plugin/plugin.json` 中修改 `version`（语义化版本，如 `1.2.3`）。
   - 提交并推送到 `main`（或你的默认分支）。
   - （可选）打 tag 并推送，以触发 GitHub Release，便于查看版本历史：
     ```bash
     git tag v1.2.3
     git push origin v1.2.3
     ```
   - 本仓库已配置 GitHub Actions：推送时校验 `plugin.json`，打 `v*` tag 时创建 Release 并校验版本与 tag 一致。

### 成员侧

- 若团队已开启 Auto Refresh，插件会随仓库更新；若未收到更新，可在 Cursor 插件设置中手动 **Refresh** 或 **卸载后重新安装** 该插件。

## 安装方式

### 方式一：Team Marketplace（推荐）

1. 在 Cursor Dashboard → **Settings → Plugins → Team Marketplaces** 中点击「Import」。
2. 粘贴 GitHub 仓库 URL：`https://github.com/ryh-zz/noematrix-fe-cursor-plugin`。
3. 团队成员在 Cursor 插件面板中即可看到并安装。

### 方式二：本地路径安装

```bash
git clone https://github.com/ryh-zz/noematrix-fe-cursor-plugin.git ~/cursor-plugins/noematrix-fe
```

在 Cursor **Settings → Plugins** 中添加本地路径 `~/cursor-plugins/noematrix-fe`。

### 方式三：项目内嵌

将 `rules/`、`skills/`、`agents/` 复制到业务项目的 `.cursor/` 目录下：

```bash
cp -r rules/ <your-project>/.cursor/rules/
cp -r skills/ <your-project>/.cursor/skills/
cp -r agents/ <your-project>/.cursor/agents/
```

## MCP 配置

插件依赖以下 MCP 服务（需在 Cursor MCP 设置中单独配置）：

| MCP 服务 | 用途 | 对应技能 |
|----------|------|----------|
| **Figma** | 设计稿还原、截图、设计变量 | `figma-mcp` |
| **Ant Design** | 组件 API / 示例查询 | `antd-mcp` |
| **NoeMatrix** | 自研组件库文档与类型 | `noematrix-mcp` |

组件查找顺序：**NoeMatrix → Ant Design**。

## 项目约定摘要

- **样式**：颜色用 `src/styles/theme.css` 变量，间距/字号用 `src/styles/foundation.scss`；`font-weight` 仅 400 或 600
- **组件**：优先 NoeMatrix，无则用 Ant Design；不覆盖组件默认样式；表单用 antd Form
- **包管理**：统一使用 Yarn 1.x
- **其他**：不修改 `src/services/request.ts` 的请求拦截逻辑

细节见 `rules/` 与 `skills/` 目录。

## 许可证

与主项目一致。
