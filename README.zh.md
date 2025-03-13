# 顺序思维 MCP 服务器

<div align="center">

[![License: MIT](https://img.shields.io/badge/许可证-MIT-yellow.svg)](LICENSE)
[![Language](https://img.shields.io/badge/开发语言-TypeScript-blue.svg)](https://www.typescriptlang.org/)
[![Platform](https://img.shields.io/badge/运行环境-Node.js-green.svg)](https://nodejs.org/)

[Switch to English](README.md) | [切换到英文](README.md)

</div>

## 📖 概述

这是一个 MCP 服务器实现，提供一个动态和反思性问题解决的工具，通过结构化思维过程。该服务器帮助将复杂问题分解为可管理的步骤，同时保持修订和替代路径的灵活性。

## ✨ 特性

- 🔍 将复杂问题分解为可管理的步骤
- 🔄 随着理解的加深，修订和完善思路
- 🌲 分支到替代推理路径
- 📊 动态调整思维总数
- ✅ 生成和验证解决假设

## 🛠 工具

### sequential_thinking

促进详细的逐步思维过程，用于问题解决和分析。

#### 输入参数

| 参数 | 类型 | 必需 | 描述 |
|-----------|------|----------|-------------|
| `thought` | 字符串 | 是 | 当前思维步骤 |
| `nextThoughtNeeded` | 布尔值 | 是 | 是否需要另一个思维步骤 |
| `thoughtNumber` | 整数 | 是 | 当前思维编号 |
| `totalThoughts` | 整数 | 是 | 估计所需的总思维数 |
| `isRevision` | 布尔值 | 否 | 是否修订之前的思维 |
| `revisesThought` | 整数 | 否 | 正在重新考虑的思维 |
| `branchFromThought` | 整数 | 否 | 分支点思维编号 |
| `branchId` | 字符串 | 否 | 分支标识符 |
| `needsMoreThoughts` | 布尔值 | 否 | 是否需要更多思维 |

## 🎯 用途

顺序思维工具旨在：

- 📝 将复杂问题分解为步骤
- 🎨 规划和设计时留有修订空间
- 🔄 可能需要调整方向的分析
- 🌐 全面范围可能最初不清晰的问题
- 📚 需要在多个步骤中保持上下文的任务
- 🔍 需要过滤掉无关信息的情况

## ⚙️ 配置

### 与 Claude Desktop 一起使用

将以下内容添加到你的 `claude_desktop_config.json`：

<details>
<summary>📦 NPX 配置</summary>

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@dreamboatcmcp/sequential-thinking"
      ]
    }
  }
}
```
</details>

<details>
<summary>🐳 Docker 配置</summary>

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "dreamboatcmcp/sequential-thinking"
      ]
    }
  }
}
```
</details>

### 与 Cursor IDE 一起使用

<details>
<summary>📦 NPX 方法（推荐）</summary>

1. 安装包：
```bash
# 全局安装
npm install -g @dreamboatcmcp/sequential-thinking

# 或直接使用 NPX
npx -y @dreamboatcmcp/sequential-thinking
```

2. 在 Cursor 设置中配置（JSON）：
```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@dreamboatcmcp/sequential-thinking"
      ]
    }
  }
}
```
</details>

<details>
<summary>💻 本地构建方法</summary>

1. 首先在本地构建项目：
```bash
cd /path/to/sequential-thinking
npm install
npm run build
```

2. 在 Cursor 设置中配置（JSON）：
```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "node",
      "args": [
        "/absolute/path/to/sequential-thinking/dist/index.js"
      ]
    }
  }
}
```
</details>

<details>
<summary>🐳 Docker 方法</summary>

1. 构建 Docker 镜像：
```bash
docker build -t dreamboatcmcp/sequential-thinking .
```

2. 在 Cursor 设置中配置（JSON）：
```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "dreamboatcmcp/sequential-thinking"
      ]
    }
  }
}
```
</details>

<details>
<summary>🔧 环境变量方法</summary>

1. 创建启动脚本：
```bash
#!/bin/sh
export CURSOR_MCP_CONFIG=/path/to/your/mcp_config.json
open -a Cursor
```

2. 在 `mcp_config.json` 中添加配置：
```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "node",
      "args": [
        "/absolute/path/to/sequential-thinking/dist/index.js"
      ]
    }
  }
}
```

3. 使脚本可执行：
```bash
chmod +x start_cursor_with_mcp.sh
```

> **注意**：MCP 集成主要在 Cursor IDE 的 Composer 功能中支持。
</details>

## 🚀 构建

<details>
<summary>本地构建</summary>

```bash
cd /path/to/sequential-thinking
npm install
npm run build
```
</details>

<details>
<summary>Docker 构建</summary>

```bash
# 构建 Docker 镜像
docker build -t dreamboatcmcp/sequential-thinking .

# 验证构建结果
docker images | grep sequential-thinking
```
</details>

## 📦 发布

本节说明如何将包发布到 npm 注册表。

### 前提条件

1. **Node.js 和 npm**：确保已安装 Node.js 和 npm
2. **npm 账号**：您需要一个 npm 账号才能发布包
3. **组织**：对于作用域包（例如 `@dreamboatcmcp/sequential-thinking`），您需要是该组织的成员

### 步骤 1：更新包信息

确保您的 `package.json` 包含正确的信息：

```json
{
  "name": "@dreamboatcmcp/sequential-thinking",
  "version": "0.6.2",
  "description": "MCP server for sequential thinking and problem solving",
  // 其他字段...
}
```

### 步骤 2：切换到官方 npm 注册表

如果您使用的是镜像注册表（如 npmmirror.com），请切换到官方 npm 注册表：

```bash
npm config set registry https://registry.npmjs.org/
```

### 步骤 3：登录到 npm

```bash
npm login
```

按照提示通过浏览器登录。

### 步骤 4：创建或加入组织

对于作用域包，您需要是组织的一部分：

```bash
# 检查您是否是组织的成员
npm org ls 您的组织名称

# 如果不是，可以通过 npm 网站创建新组织
# 或请组织管理员将您添加进来
```

### 步骤 5：构建包

```bash
npm run build
```

### 步骤 6：发布包

```bash
# 首次发布作用域包
npm publish --access public

# 后续更新
npm publish
```

### 步骤 7：验证发布

```bash
npm view @dreamboatcmcp/sequential-thinking
```

### 步骤 8：提交您的更改

```bash
git add .
git commit -m "feat(publish): 🚀 发布npm包@dreamboatcmcp/sequential-thinking"
git push
```

### 更新包

要更新包：

1. 对代码进行更改
2. 按照[语义化版本](https://semver.org/)更新 `package.json` 中的版本
   ```bash
   # 补丁更新（错误修复）
   npm version patch
   
   # 次要更新（新功能，向后兼容）
   npm version minor
   
   # 主要更新（破坏性变更）
   npm version major
   ```
3. 再次构建和发布
   ```bash
   npm run build
   npm publish
   ```

## ❗ 故障排除

如果你在使用 npx 方法时遇到问题，请尝试以下方法：

1. 🔧 使用本地构建方法并提供构建的 JavaScript 文件的绝对路径
2. 📝 确保文件权限设置正确：`chmod +x dist/index.js`
3. 🐳 尝试 Docker 方法作为替代
4. 📚 检查 Cursor 的文档或社区论坛以获取最新的 MCP 集成方法

## 📄 许可证

本项目根据 MIT 许可证进行许可 - 详见 [LICENSE](LICENSE) 文件。

## 🔗 源码

本项目基于 [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) 的源代码，并在 [Zengwenliang0416/mcp-server-sequential-thinking](https://github.com/Zengwenliang0416/mcp-server-sequential-thinking) 维护。 