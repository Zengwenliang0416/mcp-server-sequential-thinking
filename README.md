# Sequential Thinking MCP Server

<div align="center">

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Language](https://img.shields.io/badge/Language-TypeScript-blue.svg)](https://www.typescriptlang.org/)
[![Platform](https://img.shields.io/badge/Platform-Node.js-green.svg)](https://nodejs.org/)

[English](README.md) | [中文](README.zh.md)

</div>

## 📖 Overview

A powerful MCP server implementing sequential thinking protocol that provides a structured approach to problem-solving. This server helps break down complex problems into manageable steps while maintaining flexibility for revisions and alternative reasoning paths.

## ✨ Features

- 🔍 **Structured Analysis** - Break down complex problems into manageable steps
- 🔄 **Iterative Refinement** - Revise and refine thoughts as understanding deepens
- 🌲 **Alternative Pathways** - Branch into alternative paths of reasoning
- 📊 **Dynamic Adjustment** - Adjust the total number of thoughts as needed
- ✅ **Solution Validation** - Generate and verify solution hypotheses

## 🛠️ Tool Interface

### sequential_thinking

Facilitates a detailed, step-by-step thinking process for problem-solving and analysis.

#### Input Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `thought` | string | Yes | The current thinking step |
| `nextThoughtNeeded` | boolean | Yes | Whether another thought step is needed |
| `thoughtNumber` | integer | Yes | Current thought number |
| `totalThoughts` | integer | Yes | Estimated total thoughts needed |
| `isRevision` | boolean | No | Whether this revises previous thinking |
| `revisesThought` | integer | No | Which thought is being reconsidered |
| `branchFromThought` | integer | No | Branching point thought number |
| `branchId` | string | No | Branch identifier |
| `needsMoreThoughts` | boolean | No | If more thoughts are needed |

## 🎯 Use Cases

The Sequential Thinking tool is ideal for:

- 📝 Complex problems requiring step-by-step breakdown
- 🎨 Planning and design projects needing iterative refinement
- 🔄 Analysis workflows that may require course correction
- 🌐 Situations where the full scope isn't initially clear
- 📚 Tasks that need to maintain context over multiple steps
- 🔍 Filtering out irrelevant information from complex scenarios

## ⚙️ Integration Methods

### Using with Claude Desktop

<details>
<summary><b>📦 NPX Configuration</b></summary>

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@zengwenliang0416/mcp-server-sequential-thinking"
      ]
    }
  }
}
```
</details>

<details>
<summary><b>🐳 Docker Configuration</b></summary>

```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "zengwenliang0416/mcp-server-sequential-thinking"
      ]
    }
  }
}
```
</details>

### Using with Cursor IDE

<details>
<summary><b>📦 NPX Method (Recommended)</b></summary>

```bash
# Install globally
npm install -g @zengwenliang0416/mcp-server-sequential-thinking

# Or use NPX directly
npx -y @zengwenliang0416/mcp-server-sequential-thinking
```

Configure in Cursor settings (JSON):
```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "npx",
      "args": [
        "-y",
        "@zengwenliang0416/mcp-server-sequential-thinking"
      ]
    }
  }
}
```
</details>

<details>
<summary><b>💻 Local Build Method</b></summary>

Build locally:
```bash
cd /path/to/sequential-thinking
npm install
npm run build
```

Configure in Cursor settings (JSON):
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
<summary><b>🐳 Docker Method</b></summary>

```bash
# Build Docker image
docker build -t zengwenliang0416/mcp-server-sequential-thinking .
```

Configure in Cursor settings (JSON):
```json
{
  "mcpServers": {
    "sequential-thinking": {
      "command": "docker",
      "args": [
        "run",
        "--rm",
        "-i",
        "zengwenliang0416/mcp-server-sequential-thinking"
      ]
    }
  }
}
```
</details>

<details>
<summary><b>🔧 Environment Variables Method</b></summary>

Create a startup script:
```bash
#!/bin/sh
export CURSOR_MCP_CONFIG=/path/to/your/mcp_config.json
open -a Cursor
```

Add to `mcp_config.json`:
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

Make executable:
```bash
chmod +x start_cursor_with_mcp.sh
```

> **Note**: MCP integration is primarily supported in the Composer feature of Cursor IDE.
</details>

## 🚀 Building From Source

<details>
<summary><b>Local Build</b></summary>

```bash
git clone https://github.com/Zengwenliang0416/mcp-server-sequential-thinking.git
cd mcp-server-sequential-thinking
npm install
npm run build
```
</details>

<details>
<summary><b>Docker Build</b></summary>

```bash
git clone https://github.com/Zengwenliang0416/mcp-server-sequential-thinking.git
cd mcp-server-sequential-thinking
docker build -t zengwenliang0416/mcp-server-sequential-thinking .
```
</details>

## 📦 Publishing Guide

<details>
<summary><b>Publishing to npm</b></summary>

### Prerequisites

- Node.js and npm installed
- npm account with access to the @zengwenliang0416 scope
- Package built locally

### Publishing Steps

1. **Update version in package.json**
   ```json
   {
     "name": "@zengwenliang0416/mcp-server-sequential-thinking",
     "version": "0.6.2",
     "description": "MCP server for sequential thinking and problem solving"
   }
   ```

2. **Use official npm registry**
   ```bash
   npm config set registry https://registry.npmjs.org/
   ```

3. **Login to npm**
   ```bash
   npm login
   ```

4. **Build and publish**
   ```bash
   npm run build
   npm publish --access public
   ```

5. **Verify publication**
   ```bash
   npm view @zengwenliang0416/mcp-server-sequential-thinking
   ```

### Version Updates

Use semantic versioning:
```bash
# For patches (bug fixes)
npm version patch

# For minor updates (features)
npm version minor

# For major updates (breaking changes)
npm version major
```
</details>

## 🔐 CI/CD Configuration

<details>
<summary><b>Setting Up GitHub Actions</b></summary>

### Required Secrets

Add these secrets to your repository settings:

1. **NPM_TOKEN**
   - Generate at npm: Account → Access Tokens → "Automation" token type
   - Important for 2FA users: Must use "Automation" token

2. **DOCKERHUB_USERNAME**
   - Your Docker Hub username

3. **DOCKERHUB_TOKEN**
   - Generate in Docker Hub: Account Settings → Security → New Access Token

### Adding Secrets to GitHub

1. Go to repository Settings → Secrets and variables → Actions
2. Add each secret individually
3. Test the workflow by manually triggering in Actions tab

> **Note for 2FA Users**: If you have Two-Factor Authentication enabled on your npm account, you must either:
> - Use an "Automation" type token (recommended)
> - Change 2FA settings to "Authorization only" (not recommended)
> - Manually publish packages (not automated)
</details>

## ❗ Troubleshooting

If you encounter integration issues:

1. 🔧 Use the local build method with absolute path to the JS file
2. 📝 Verify file permissions: `chmod +x dist/index.js`
3. 🐳 Try Docker as an alternative
4. 📚 Consult Cursor's documentation for latest MCP integration methods

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Source Code

Based on [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers) and maintained at [Zengwenliang0416/mcp-server-sequential-thinking](https://github.com/Zengwenliang0416/mcp-server-sequential-thinking).
