<p align="center">
  <img src="https://raw.githubusercontent.com/octos-org/.github/main/profile/octos-wordmark.png" alt="OCTOS" width="680">
</p>

<p align="center"><a href="https://github.com/octos-org/.github/blob/main/profile/README.md">English</a> · <b>中文</b></p>

> 像章鱼一样——9 个大脑，每条触手独立思考，却共享同一个大脑。

Octos 是一个用 Rust 构建的开源 AI 智能体平台。它把任意大语言模型变成多渠道、多用户的智能助手——以一个自包含、零运行时依赖的二进制文件交付。

接入你的 LLM API 密钥与消息渠道，Octos 负责其余一切：对话路由、工具执行、记忆、供应商故障切换与多租户隔离。通过 Web 仪表板或 REST API 管理数百个 AI 智能体 Profile。

## 仓库

| 仓库 | 说明 |
|------|------|
| **[octos](https://github.com/octos-org/octos)** | 核心平台——Rust 二进制、16 家 LLM 供应商、14 个渠道、DOT 流水线引擎、多租户网关、`octos serve` Web/API 后端 |
| **[octos-web](https://github.com/octos-org/octos-web)** | Web 客户端——内嵌于 `/app/` 的 React SPA（聊天、Slides Studio、Sites、语音），通过 UI Protocol 与 `octos serve` 通信 |
| **[octos-tui](https://github.com/octos-org/octos-tui)** | 终端客户端——基于 UI Protocol 的 Rust TUI（实时流式、审批、diff、引导） |
| **[octos-hub](https://github.com/octos-org/octos-hub)** | 社区技能注册表——安装与分享智能体技能 |

## 核心能力

- **API 优先** —— REST + WebSocket UI Protocol 后端（`octos serve`）。在其之上构建任意前端：Web、终端、移动端、CI/CD
- **多租户** —— 16GB 上运行 200+ 个 Profile。每个 Profile 是一个隔离的操作系统进程。支持 Family Plan 子账户
- **16 家 LLM 供应商** —— Anthropic、OpenAI、Gemini、Vertex AI、OpenRouter、DeepSeek、Moonshot/Kimi、Qwen、MiniMax、Zhipu/GLM、Z.AI、Groq、NVIDIA、Ollama、vLLM、r9s——以及任意通过 `base_url` 接入的 OpenAI/Anthropic 兼容端点
- **多 LLM 流水线** —— DOT 图工作流。逐节点选择模型。运行时动态并行分叉
- **自适应路由** —— 三层故障切换，含 Hedge 竞速、Lane 评分与熔断器
- **丰富的工具集** —— shell、文件、搜索、web、浏览器、MCP、office、spawn/cron —— 每一轮都把完整的已启用工具集发送给模型
- **14 个渠道** —— Telegram、Discord、Slack、WhatsApp、飞书/Lark、钉钉、企业微信、微信、Matrix、LINE、QQ 机器人、邮件、Twilio（短信）、Web/API——以及 CLI
- **自动记忆** —— 捕获 → 抽取 → 整合进长期记忆，另有情景记忆（redb）与会话（JSONL + LLM 压缩）层
- **5 种队列模式** —— Followup、Collect、Steer、Interrupt、Speculative——按会话控制智能体并发
- **原生 Office 套件** —— 纯 Rust 处理 PPTX/DOCX/XLSX（zip + quick-xml）
- **沙箱隔离** —— bwrap + sandbox-exec + Docker。工作区级 `deny(unsafe_code)`

## 安装

```bash
# 一键安装脚本——安装二进制并将 `octos serve` 设为服务（macOS / Linux）
curl -fsSL https://github.com/octos-org/octos/releases/latest/download/install.sh | bash

# Homebrew（macOS Apple Silicon、Linux x86_64/ARM64）
brew install octos-org/tap/octos

# npm（macOS Apple Silicon、Linux x86_64/ARM64、Windows x64）
npm install -g @octos-org/octos
```

```powershell
# Windows（PowerShell）
irm https://github.com/octos-org/octos/releases/latest/download/install.ps1 | iex
```

或使用完整特性集从源码编译（REST API + 仪表板 + 渠道）：

```bash
cargo install --path crates/octos-cli \
    --features "api,telegram,discord,dingtalk,whatsapp,feishu,twilio,wecom,wecom-bot,audio_mp3"
```

## 快速开始

```bash
export DEEPSEEK_API_KEY=your-key
octos chat --provider deepseek     # 交互式 CLI
octos serve                        # Web 仪表板 + REST API → http://localhost:50080
```

## 文档

- [手册（中文）](https://github.com/octos-org/octos/tree/main/book-zh) · [Handbook (English)](https://github.com/octos-org/octos/tree/main/book)
- [中文 README](https://github.com/octos-org/octos/blob/main/README-zh.md) · [README (English)](https://github.com/octos-org/octos/blob/main/README.md)

---

*用 Rust 构建，由 9 个大脑驱动。*
