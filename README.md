# React + Ant Design + NoeMatrix Cursor Plugin

基于当前 Cursor 配置与 MCP 整合的内网版 Cursor 插件，为 **React + TypeScript + Ant Design** 前端项目提供统一规则、技能、验证 Agent 与内置 MCP 配置。

## 插件元数据

- **插件名**：`react-antd-noematrix`
- **版本**：`1.0.0`
- **发布形态**：内网使用
- **许可证**：`UNLICENSED`
- **Logo**：`assets/logo.svg`

## 包含内容

- **Rules**：技术约定、包管理器、项目上下文、路由/状态/React 规范、文件命名等
- **Skills**：Ant Design / NoeMatrix / Figma MCP 使用、组件与样式规范、src-tree、实现步骤等
- **Agents**：验证子代理（verifier），用于对已实现工作做约束检查与测试汇报

## 内置 MCP 配置

插件根目录已内置 `.mcp.json`，包含以下服务：

| MCP 服务     | 用途 |
|-------------|------|
| **Figma**   | 设计稿还原、截图、设计变量，对应技能 `figma-mcp` |
| **Ant Design** | 组件 API/示例，对应技能 `antd-mcp` |
| **NoeMatrix**  | 自研组件库文档与类型，对应技能 `noematrix-mcp` |

组件查找顺序：**NoeMatrix → Ant Design**；Figma 生成代码放在对应目录下的 `ui/` 或 `view/`。

### Figma 密钥

出于安全考虑，插件中的 Figma 配置使用环境变量：

```bash
export FIGMA_API_KEY=your_figma_api_key
```

然后重启 Cursor，使 `.mcp.json` 中的 `--figma-api-key=${FIGMA_API_KEY}` 生效。

## 内网分发方案（纯公司内部使用）

插件可以放在**内网 GitLab** 上，用以下任一方式给同事使用。

### 方案一：内网 GitLab + 本地安装（推荐）

1. 将本仓库推送到内网 GitLab（如 `https://gitlab.company.com/fe/cursor-plugin`）。
2. 同事在本地 clone 该仓库到固定目录，例如：
   ```bash
   git clone https://gitlab.company.com/fe/cursor-plugin.git ~/cursor-plugins/noematrix-fe
   ```
3. 在 Cursor 中把该**本地目录**添加为插件：
   - 打开 **Settings → Features → Plugins**（或 **Cursor Settings → Plugins**）；
   - 若有「Add from path」/「从路径添加」等选项，选择 `~/cursor-plugins/noematrix-fe`；
   - 若无，可尝试 Team Marketplaces 中粘贴内网 GitLab 的仓库 URL（部分版本可能支持除 GitHub 外的 Git URL，需实测）。
4. 更新时在本地执行 `git pull`，必要时重启 Cursor。

适合：内网环境、不希望依赖公网 Cursor Marketplace。

### 方案二：项目内嵌（不依赖 Cursor 插件机制）

不通过 Cursor 的「安装插件」，而是把本仓库的规则与技能放到各业务项目里：

- 将 `.cursor/rules`、`.cursor/skills`、`.cursor/agents` 复制到业务项目的 `.cursor/` 下；或
- 用 **Git submodule** 把本仓库挂到业务项目，例如 `git submodule add <内网 GitLab 仓库 URL> .cursor/plugin`，再在项目内通过符号链接或构建步骤把 `plugin/rules`、`plugin/skills` 等暴露到 `.cursor/`。

这样规则与技能随项目仓库走，不依赖 Cursor 是否支持「从路径添加插件」。

### 方案三：Team Marketplace + GitHub（若可用）

若公司使用 **GitHub Enterprise** 或允许用 GitHub 私有仓库：

1. 将本仓库镜像或推送到 GitHub（含私有仓库）。
2. 在 Cursor 的 **Dashboard → Settings → Plugins → Team Marketplaces** 中「Import」并粘贴该 **GitHub 仓库 URL**。
3. 为对应分发组设为必装或选装，团队成员在 Cursor 的插件面板中即可看到并安装。

官方文档目前仅写明支持 **GitHub** 仓库 URL，内网 GitLab URL 在 Team Marketplaces 中是否可用需在你们当前 Cursor 版本中实测。

---

## 安装与使用

1. 将本仓库添加为 Cursor 插件（本地路径或 Git 仓库；内网推荐见上节「内网分发方案」）。
2. 确保当前环境可访问 `FIGMA_API_KEY`，并且能连通 `ant-design`、`noematrix` 对应的内网地址。
3. 重启 Cursor 让插件内 `.mcp.json` 生效。
4. 规则与技能会自动参与 AI 对话；需要验证实现时，可调用 **verifier** Agent。

## 项目约定摘要

- **样式**：颜色用 `src/styles/theme.css` 变量，间距/字号用 `src/styles/foundation.scss`；`font-weight` 仅 400 或 600。
- **组件**：优先 NoeMatrix，无则用 Ant Design；不覆盖组件默认样式；表单用 antd Form。
- **包管理**：统一使用 Yarn 1.x。
- **其他**：不修改 `src/services/request.ts` 的请求拦截逻辑。

细节见插件内 `rules` 与 `skills`。

## 许可证

与主项目一致。
