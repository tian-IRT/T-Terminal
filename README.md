# T-Terminal

**T-Terminal** 是一款面向 Windows 的 AI 智能终端管理工具，适合需要同时管理多台服务器、频繁使用 SSH/SFTP、希望借助 AI 分析终端输出和运维问题的用户。

**T-Terminal** is an AI-assisted terminal management tool for Windows. It is built for users who manage multiple servers, work with SSH/SFTP frequently, and want an AI assistant that understands terminal context.

> 当前仓库仅用于发布可执行程序、版本说明和使用文档，源码暂不开放。  
> This repository is used only for binary releases, release notes, and documentation. Source code is not open at this time.

---

## 目录 / Contents

- [中文说明](#中文说明)
- [English](#english)
- [License](#license)
- [Third-Party Notices](#third-party-notices)

---

## 中文说明

### 1. 这是什么

T-Terminal 不是单纯的终端模拟器，它更接近一个 **面向服务器管理的工作台**：

- 你可以像普通终端一样打开 PowerShell、CMD、Bash、WSL。
- 你可以保存 SSH 主机，一键连接远程服务器。
- 你可以在右侧打开 SFTP 文件浏览器，上传、下载、拖拽文件。
- 你可以直接用本地编辑器编辑远程文件，保存后自动同步回服务器。
- 你可以让 AI 助手读取当前终端上下文，解释报错、整理排查步骤、分析命令输出。
- 你可以创建 SSH 隧道，甚至让无外网的 SSH 主机通过本机代理访问 HTTP/HTTPS。
- 你可以生成服务器巡检报告，并导出 PDF。

适合场景：

- 日常 Linux/Windows 服务器运维
- 多台 SSH 主机管理
- 内网服务器文件上传下载
- 远程配置文件快速编辑
- Docker 容器查看和排查
- 终端错误分析、命令解释、巡检报告生成
- 无外网服务器临时通过宿主机代理访问外部资源

### 2. 下载与安装

请从 [Releases](https://github.com/tian-IRT/T-Terminal/releases) 页面下载最新版本。

当前版本：

- `T-Terminal-v1.8.0-windows-x64.exe`

安装方式：

1. 下载 `T-Terminal-v1.8.0-windows-x64.exe`。
2. 放到你希望保存的位置，例如 `D:\Tools\T-Terminal\`。
3. 双击运行。
4. 如果 Windows SmartScreen 提示风险，请确认文件来自本仓库 Release 页面后再选择继续运行。

> 当前 exe 暂未做代码签名，所以 Windows 或杀毒软件可能会提示风险。你可以通过 SHA256 校验确认文件完整性。

### 3. 校验下载文件

每个 Release 会同时提供 `.sha256` 校验文件。

在 PowerShell 中进入 exe 所在目录，执行：

```powershell
Get-FileHash .\T-Terminal-v1.8.0-windows-x64.exe -Algorithm SHA256
```

当前版本 SHA256：

```text
84fea31a10e06d6e47e229bb264ce3097dffb2e995cad8095e55f84fe8b6c91a
```

请与 `T-Terminal-v1.8.0-windows-x64.exe.sha256` 中的值进行比对。两者一致，说明文件没有被篡改或损坏。

### 4. 首次启动

启动后你会看到首页和顶部工具栏。

常用入口：

- `PowerShell`：打开本地 PowerShell。
- `CMD`：打开本地 CMD。
- `Bash`：打开 Bash。
- `WSL`：打开 WSL 发行版终端。
- `Docker`：打开 Docker 辅助面板。
- `设置`：配置模型、日志、界面语言、主题等。
- 首页连接卡片：快速连接已保存的 SSH 主机。

如果你第一次使用，建议先完成三件事：

1. 在设置中配置 AI 模型。
2. 新建一个 SSH 连接。
3. 测试 SFTP 文件浏览和 AI 助手。

### 5. 配置 AI 模型

打开 `设置` / `模型管理` 后，可以添加大模型配置。

需要填写：

- 名称：用于在界面里识别，比如 `DeepSeek`、`GPT-4o`、`Ark Code`。
- Base URL：模型服务地址，例如 OpenAI 兼容接口地址。
- API Key：你的模型服务密钥。
- 模型 ID：手动填写模型 ID，例如 `gpt-4o`、`deepseek-chat`、`ark-code-latest`。

说明：

- 同一厂商、同一 Base URL 下可以添加多个不同模型 ID。
- API Key 保存在本地配置中，请保护好本机环境。
- 如果你在敏感服务器环境中使用 AI，请注意终端上下文可能会发送给你配置的模型服务。

### 6. 新建 SSH 连接

在连接管理中添加 SSH 主机，通常需要：

- 连接名称
- 主机地址
- 端口，默认 `22`
- 用户名
- 密码或密钥

添加后，你可以：

- 左键连接主机。
- 右键查看更多操作，例如打开文件浏览、生成报告。
- 在首页快速连接常用主机。

连接成功后会打开一个终端标签页。为了避免误触，关闭标签页需要 **右键标签页 → 关闭标签**。

### 7. 使用终端

终端支持常见交互：

- 输入命令并回车执行。
- 多标签页管理。
- 分屏终端。
- 搜索终端内容。
- 调整所有终端字体大小。
- 命令历史补全。

常用快捷键：

| 功能 | 快捷键 |
| --- | --- |
| 放大终端字体 | `Ctrl + +` 或 `Ctrl + =` |
| 缩小终端字体 | `Ctrl + -` |
| 历史搜索 | `Ctrl + R` |
| 接受命令补全 | `Tab` |
| 取消命令补全 | `Esc` |

说明：

- 命令历史按终端类型/连接隔离，SSH 历史不会混到本地 PowerShell 里。
- 终端中的 HTTP/HTTPS 链接会使用系统默认浏览器打开，不会在应用内部跳转。

### 8. 使用 SFTP 文件浏览器

连接 SSH 主机后，可以打开同主机的 SFTP 文件浏览器。

常见操作：

- 浏览远程目录。
- 上传文件。
- 下载文件。
- 拖拽本地文件到 SFTP 面板上传。
- 删除、重命名、复制路径。
- 打包下载。
- 将文件传输到其他主机。

拖拽上传大文件时，会显示上传进度和实时速度。断开后重新上传时，速度显示会重新计算，不会沿用上一次的旧计时。

### 9. 用本地编辑器编辑远程文件

这是 SFTP 的一个实用功能。

使用方式：

1. 打开 SFTP 文件浏览器。
2. 找到远程文件。
3. 右键文件。
4. 选择 `用本地编辑器打开`。
5. T-Terminal 会把远程文件下载到本地缓存目录。
6. 系统默认编辑器会打开这个文件。
7. 你保存文件后，T-Terminal 会自动同步回远程原路径。

注意：

- 本地临时文件不会在保存后立即删除，避免编辑器仍打开时丢失内容。
- 应用启动时会自动清理超过 7 天的远程编辑缓存。
- 如果同步失败，本地临时文件会保留，方便找回或重试。
- 写回远程时会尽量保持原远程文件权限，不会因为本地缓存文件权限改变远程脚本权限。

### 10. 使用 AI 助手

AI 助手可以读取当前终端上下文，帮助你理解命令输出、分析错误、生成排查步骤。

常见用法：

- “解释一下刚才的报错”
- “帮我分析为什么服务启动失败”
- “根据当前输出给我下一步排查命令”
- “整理这台服务器的巡检结论”
- “这个 Docker 容器为什么重启”

AI 助手有两种模式：

#### 只聊天模式

适合：

- 解释终端输出
- 分析问题
- 给建议
- 总结日志

特点：

- 可以读取终端上下文。
- 不会执行命令。
- 不会调用工具修改环境。

#### 操作模式

适合：

- 让 AI 根据上下文给出命令
- 辅助执行排查流程
- 根据命令结果继续分析

特点：

- 可以结合终端输出持续推理。
- 对高风险操作需要谨慎确认。
- 如果模型服务异常，支持短暂断链重试。

### 11. AI 会话管理

AI 助手支持会话管理：

- 新建会话
- 删除会话
- 切换历史会话
- 关闭终端后保留历史
- 不同终端之间会话隔离

这意味着：

- 本地 PowerShell 的 AI 对话不会混到 SSH 主机对话里。
- 不同 SSH 主机可以保留各自的 AI 会话上下文。
- 长任务对话会自动压缩较早上下文，减少 AI 忘记原始目标的问题。

### 12. Docker 辅助面板

Docker 面板用于辅助查看和管理容器。

常见用途：

- 查看容器列表。
- 查看容器日志。
- 进入容器终端。
- 辅助排查容器状态。

如果你连接的是远程 SSH 主机，Docker 操作依赖目标主机上 Docker 命令可用。

### 13. SSH 隧道与宿主机代理出网

T-Terminal 支持常见 SSH 端口转发：

- 本地转发
- 远程转发
- 宿主机代理出网

宿主机代理出网适合这个场景：

> 你的 Windows 本机有外网，但连接的 SSH 目标主机没有外网。你希望目标主机临时通过你的本机网络访问 HTTP/HTTPS。

创建宿主机代理后，目标主机可以使用类似下面的代理地址：

```bash
export http_proxy=http://127.0.0.1:18080
export https_proxy=http://127.0.0.1:18080
```

工具可以为当前 SSH 终端自动应用代理环境变量。后续新建或分屏同一 SSH 连接时，也会自动继承正在运行的宿主机代理配置。

注意：

- 代理仅监听目标主机的 `127.0.0.1`。
- 它用于 HTTP/HTTPS 流量。
- 不建议在不可信主机上长期保持代理开启。

### 14. 服务器报告与 PDF 导出

T-Terminal 支持生成服务器巡检报告。

常见报告内容包括：

- 系统信息
- CPU / 内存 / 磁盘
- 网络状态
- 服务状态
- Docker 状态
- 风险和异常摘要

报告可以导出为 PDF。PDF 生成使用 Go 原生方案，不依赖 Edge/Chrome 临时 HTML 打印。

### 15. 配置和数据保存位置

常见数据会保存在本机：

- 应用配置
- 模型配置
- SSH 连接信息
- 终端日志
- AI 会话历史
- SFTP 远程编辑缓存

请妥善保护你的本机用户目录、应用目录和配置文件。

### 16. 常见问题

**为什么只有 exe，没有源码？**  
当前阶段仅发布工具本体，源码暂不开放。后续是否开源会根据项目规划再决定。

**可以商用吗？**  
当前许可为专有免费软件，允许个人或内部使用。转售、二次分发修改版、托管为商业服务等行为需要获得书面许可。

**为什么 Windows 或杀毒软件提示风险？**  
当前程序暂未做代码签名。你可以通过 GitHub Release 附带的 SHA256 校验文件确认下载内容是否完整。

**AI 会不会自动执行危险命令？**  
建议默认把 AI 当作辅助分析工具使用。涉及删除、覆盖、权限修改、服务重启等动作时，请你自己确认命令含义后再执行。

**远程文件编辑失败怎么办？**  
同步失败时，本地缓存文件会保留。你可以重新打开文件、手动上传，或检查远程路径权限。

**SFTP 上传速度显示不准怎么办？**  
v1.8.0 已修复断开重传后速度沿用旧计时的问题。如果仍异常，可以关闭 SFTP 面板后重新打开。

**GitHub 下载很慢怎么办？**  
可以尝试更换网络环境。请只从官方 Release 页面下载，避免使用来源不明的二次分发包。

---

## English

### 1. What Is T-Terminal

T-Terminal is not just a terminal emulator. It is closer to a **server management workspace** for Windows.

You can use it to:

- Open local PowerShell, CMD, Bash, and WSL terminals.
- Save and connect to SSH hosts quickly.
- Browse remote files through SFTP.
- Upload, download, drag-and-drop, rename, and delete remote files.
- Edit remote files with your local default editor and sync changes back automatically.
- Ask the AI assistant to analyze terminal output, errors, logs, and troubleshooting steps.
- Create SSH tunnels and host-proxy outbound access for isolated SSH hosts.
- Generate server inspection reports and export them as PDF.

Typical use cases:

- Daily Linux/Windows server operations
- Managing multiple SSH hosts
- Uploading files to internal servers
- Editing remote configuration files
- Docker container inspection and troubleshooting
- Terminal error analysis
- Server report generation
- Temporary outbound HTTP/HTTPS access for servers without internet access

### 2. Download And Install

Download the latest build from the [Releases](https://github.com/tian-IRT/T-Terminal/releases) page.

Current build:

- `T-Terminal-v1.8.0-windows-x64.exe`

Installation:

1. Download `T-Terminal-v1.8.0-windows-x64.exe`.
2. Place it in a directory you trust, such as `D:\Tools\T-Terminal\`.
3. Double-click to run it.
4. If Windows SmartScreen shows a warning, verify that the file comes from this official Release page before continuing.

The executable is currently unsigned, so Windows or antivirus software may warn during early distribution.

### 3. Verify The Download

Each release includes a `.sha256` checksum file.

Run this in PowerShell:

```powershell
Get-FileHash .\T-Terminal-v1.8.0-windows-x64.exe -Algorithm SHA256
```

Current SHA256:

```text
84fea31a10e06d6e47e229bb264ce3097dffb2e995cad8095e55f84fe8b6c91a
```

Compare it with `T-Terminal-v1.8.0-windows-x64.exe.sha256`.

### 4. First Launch

After launching the app, you will see the home page and the toolbar.

Common entries:

- `PowerShell`: open a local PowerShell terminal.
- `CMD`: open a local CMD terminal.
- `Bash`: open Bash.
- `WSL`: open a WSL distribution terminal.
- `Docker`: open the Docker helper panel.
- `Settings`: configure model providers, logs, language, theme, and other options.
- Home connection cards: quickly connect to saved SSH hosts.

Recommended first steps:

1. Configure an AI model in Settings.
2. Add an SSH connection.
3. Try SFTP file browsing and the AI assistant.

### 5. Configure AI Models

Open `Settings` / `Model Management` to add a model configuration.

Required fields:

- Name: display name, such as `DeepSeek`, `GPT-4o`, or `Ark Code`.
- Base URL: model service endpoint, usually an OpenAI-compatible API URL.
- API Key: your model service key.
- Model ID: manually enter the model ID, such as `gpt-4o`, `deepseek-chat`, or `ark-code-latest`.

Notes:

- Multiple model IDs can share the same provider and Base URL.
- API keys are stored locally. Protect your local environment.
- AI features may send terminal context to the model provider you configure.

### 6. Add An SSH Connection

To add an SSH host, provide:

- Connection name
- Host address
- Port, usually `22`
- Username
- Password or private key

After saving the connection:

- Left-click to connect.
- Right-click for more actions, such as file browser or report generation.
- Use the home page cards for quick access.

After a successful connection, a terminal tab opens. To avoid accidental clicks, closing a tab is done through **right-click tab -> Close Tab**.

### 7. Terminal Usage

The terminal supports:

- Running commands normally.
- Multiple tabs.
- Split panes.
- Terminal search.
- Global terminal font scaling.
- Command history suggestions.

Shortcuts:

| Action | Shortcut |
| --- | --- |
| Increase terminal font size | `Ctrl + +` or `Ctrl + =` |
| Decrease terminal font size | `Ctrl + -` |
| Search command history | `Ctrl + R` |
| Accept suggestion | `Tab` |
| Cancel suggestion | `Esc` |

Notes:

- Command history is isolated by terminal source. SSH history does not appear in local PowerShell suggestions.
- HTTP/HTTPS links inside the terminal are opened with the system default browser.

### 8. SFTP File Browser

After connecting to an SSH host, open the SFTP file browser for that host.

Supported actions:

- Browse remote directories.
- Upload files.
- Download files.
- Drag local files into the SFTP panel to upload.
- Delete, rename, and copy paths.
- Archive download.
- Transfer files to another host.

Large drag-and-drop uploads show progress and live speed. If an upload is interrupted and restarted, speed calculation resets for the new transfer.

### 9. Edit Remote Files With Local Editor

This feature lets you use your normal local editor for remote files.

How to use:

1. Open the SFTP file browser.
2. Find the remote file.
3. Right-click the file.
4. Choose `Open in Local Editor`.
5. T-Terminal downloads the remote file to a local cache directory.
6. Your system default editor opens the file.
7. When you save the file, T-Terminal automatically syncs it back to the original remote path.

Notes:

- Temporary local files are not deleted immediately after saving.
- On startup, T-Terminal cleans remote-edit cache files older than 7 days.
- If sync fails, the local temporary file is kept for recovery.
- Syncing back tries not to change the original remote file permissions.

### 10. AI Assistant

The AI assistant can read terminal context and help analyze commands, errors, and logs.

Example prompts:

- "Explain the last error."
- "Why did this service fail to start?"
- "What should I check next?"
- "Summarize the server inspection result."
- "Why is this Docker container restarting?"

There are two modes:

#### Chat Mode

Best for:

- Explaining output
- Analyzing issues
- Giving suggestions
- Summarizing logs

Characteristics:

- Reads terminal context.
- Does not execute commands.
- Does not call tools that modify the environment.

#### Operation Mode

Best for:

- Generating next diagnostic commands
- Following troubleshooting workflows
- Continuing analysis from command results

Characteristics:

- Uses terminal output as context.
- Can continue reasoning across steps.
- Risky actions should be reviewed by the user before execution.

### 11. AI Session Management

The AI assistant supports:

- New sessions
- Deleting sessions
- Switching historical sessions
- Persistent history after closing terminals
- Session isolation between terminals

This means:

- Local PowerShell AI chat does not mix with SSH host chat.
- Different SSH hosts can keep separate AI context.
- Long conversations are automatically compacted into task memory to reduce forgetting the original goal.

### 12. Docker Helper Panel

The Docker panel helps inspect and manage containers.

Common uses:

- View container list.
- View container logs.
- Enter a container terminal.
- Troubleshoot container status.

For remote SSH hosts, Docker actions depend on the Docker CLI being available on the target host.

### 13. SSH Tunnels And Host Proxy

T-Terminal supports:

- Local forwarding
- Remote forwarding
- Host-proxy outbound access

Host-proxy outbound access is useful when:

> Your Windows machine has internet access, but the SSH target host does not. You want the target host to temporarily access HTTP/HTTPS through your local machine.

After creating the host proxy, the target host can use:

```bash
export http_proxy=http://127.0.0.1:18080
export https_proxy=http://127.0.0.1:18080
```

T-Terminal can apply these environment variables to the current SSH terminal automatically. New tabs or split panes for the same SSH connection can inherit the running proxy configuration.

Notes:

- The proxy listens only on the target host's `127.0.0.1`.
- It is designed for HTTP/HTTPS traffic.
- Do not keep it running for a long time on untrusted hosts.

### 14. Server Reports And PDF Export

T-Terminal can generate server inspection reports.

Typical report sections:

- System information
- CPU / memory / disk
- Network status
- Service status
- Docker status
- Risk and anomaly summary

Reports can be exported as PDF. PDF generation uses a Go-native implementation and does not depend on Edge/Chrome HTML printing.

### 15. Local Data

T-Terminal stores data locally, such as:

- App configuration
- Model configurations
- SSH connection data
- Terminal logs
- AI session history
- SFTP remote-edit cache

Please protect your local user profile, app directory, and configuration files.

### 16. FAQ

**Why is there only an executable and no source code?**  
The project currently publishes binary builds only. Source code is not open at this time.

**Can I use it commercially?**  
T-Terminal is distributed as proprietary freeware. Personal and internal use are allowed. Reselling, redistributing modified copies, or hosting it as a commercial service requires written permission.

**Why might Windows or antivirus software warn me?**  
The executable is currently unsigned. Use the SHA256 checksum from the GitHub Release to verify file integrity.

**Will AI execute dangerous commands automatically?**  
Treat AI as an assistant. For deletion, overwrite, permission changes, service restarts, or other risky actions, review the command yourself before execution.

**What if remote file editing fails?**  
The local cached file is kept when sync fails. You can reopen it, upload it manually, or check remote permissions.

**What if SFTP upload speed looks wrong?**  
v1.8.0 fixes stale speed timing after interrupted uploads. If it still looks wrong, close and reopen the SFTP panel.

**What if GitHub download is slow?**  
Try another network environment. Only download builds from the official Releases page.

---

## License

T-Terminal is distributed as proprietary freeware. See [LICENSE](LICENSE).

## Third-Party Notices

See [THIRD_PARTY_NOTICES.md](THIRD_PARTY_NOTICES.md).
