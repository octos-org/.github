```
 ██████╗  ██████╗████████╗ ██████╗ ███████╗
██╔═══██╗██╔════╝╚══██╔══╝██╔═══██╗██╔════╝
██║   ██║██║        ██║   ██║   ██║███████╗
██║   ██║██║        ██║   ██║   ██║╚════██║
╚██████╔╝╚██████╗   ██║   ╚██████╔╝███████║
 ╚═════╝  ╚═════╝   ╚═╝    ╚═════╝ ╚══════╝
```

# Octos 🐙

**Open Cognitive Tasks Orchestration System**

> Like an octopus — 9 brains, every arm thinks independently, but they share one brain.

Octos is an open-source AI agent platform built in Rust. It turns any LLM into a multi-channel, multi-user intelligent assistant — deployed as a single self-contained binary with zero runtime dependencies.

Connect your LLM API keys and messaging channels. Octos handles conversation routing, tool execution, memory, provider failover, and multi-tenant isolation. Manage hundreds of AI agent profiles through a web dashboard or REST API.

## Repositories

| Repo | Description |
|------|-------------|
| **[octos](https://github.com/octos-org/octos)** | Core platform — Rust binary, 16 LLM providers, 14 channels, DOT pipeline engine, multi-tenant gateway, `octos serve` web/API backend |
| **[octos-web](https://github.com/octos-org/octos-web)** | Web client — React SPA embedded at `/app/` (chat, Slides Studio, Sites, Voice), talks to `octos serve` over the UI Protocol |
| **[octos-tui](https://github.com/octos-org/octos-tui)** | Terminal client — Rust TUI over the UI Protocol (live streaming, approvals, diffs, onboarding) |
| **[octos-hub](https://github.com/octos-org/octos-hub)** | Community skill registry — install and share agent skills |

## Key Capabilities

- **API-first** — a REST + WebSocket UI Protocol backend (`octos serve`). Build any frontend on top: web, terminal, mobile, CI/CD
- **Multi-tenant** — 200+ profiles on 16GB. Each profile is an isolated OS process. Family Plan sub-accounts
- **16 LLM providers** — Anthropic, OpenAI, Gemini, Vertex AI, OpenRouter, DeepSeek, Moonshot/Kimi, Qwen, MiniMax, Zhipu/GLM, Z.AI, Groq, NVIDIA, Ollama, vLLM, r9s — plus any OpenAI/Anthropic-compatible endpoint via `base_url`
- **Multi-LLM pipelines** — DOT graph workflows. Per-node model selection. Dynamic parallel fan-out
- **Adaptive routing** — 3-layer failover with Hedge racing, Lane scoring, and circuit breakers
- **LRU tool deferral** — 15 active tools for fast LLM reasoning, 34+ available on demand
- **14 channels** — Telegram, Discord, Slack, WhatsApp, Feishu/Lark, DingTalk, WeCom, WeChat, Matrix, LINE, QQ Bot, Email, Twilio (SMS), Web/API — plus the CLI
- **Automatic memory** — capture → extraction → consolidation into long-term memory, plus episodic (redb) and session (JSONL + LLM compaction) layers
- **5 queue modes** — Followup, Collect, Steer, Interrupt, Speculative — per-session agent concurrency control
- **Native office suite** — PPTX/DOCX/XLSX via pure Rust (zip + quick-xml)
- **Sandbox isolation** — bwrap + sandbox-exec + Docker. `deny(unsafe_code)` workspace-wide

## Quick Start

```bash
# CLI (chat only)
cargo install --path crates/octos-cli
export ANTHROPIC_API_KEY=your-key
octos chat

# Full: web dashboard + REST API + all channels
cargo install --path crates/octos-cli \
    --features "api,telegram,discord,dingtalk,whatsapp,feishu,twilio,wecom,wecom-bot,audio_mp3"
octos serve   # http://localhost:50080
```

## Documentation

- [Handbook (English)](https://github.com/octos-org/octos/tree/main/book) · [手册（中文）](https://github.com/octos-org/octos/tree/main/book-zh)
- [README (English)](https://github.com/octos-org/octos/blob/main/README.md) · [中文 README](https://github.com/octos-org/octos/blob/main/README-zh.md)

---

*Built with Rust. Powered by 9 brains.*
