# Coder Arena

A comprehensive comparison and benchmark arena for AI coding agents, agent harnesses, and related tooling.

## Overview

Coder Arena is a research project that tracks, compares, and benchmarks various AI coding agents and their supporting infrastructure. We organize these tools into logical categories for systematic evaluation.

## Project Structure

```
coder_arena/
├── coding-agents/
│   ├── agent-harnesses/     # Complete agent frameworks & orchestration
│   ├── agent-runtimes/      # Agent execution platforms
│   ├── cli-agents/          # Terminal-based coding agents
│   ├── models/              # Open-weight coding LLMs
│   └── tooling/             # Skills frameworks, performance tools
└── README.md
```

## Architecture: How the Categories Interact

The 5 categories form a layered stack — each layer depends on the one below it:

```
┌─────────────────────────────────┐
│         CLI Agents              │  End-user tools you type into
│  (claude-code, aider, kimi-cli) │
├─────────────────────────────────┤
│       Agent Harnesses           │  Orchestration & multi-agent logic
│  (AutoGLM, ChatDev, DeepCode)  │
├─────────────────────────────────┤
│       Agent Runtimes            │  Execution environment & lifecycle
│  (hermes, openclaw, coze-studio)│
├─────────────────────────────────┤
│          Models                 │  The LLM "brain"
│  (GLM-5, Kimi-K2, DeepSeek)    │
├─────────────────────────────────┤
│         Tooling                 │  Cross-cutting: skills, eval, optimization
│  (superpowers, coze-loop)       │
└─────────────────────────────────┘
```

### Layer Dependencies

**Models → everything above**
The LLM is the shared dependency. A CLI agent like `kimi-cli` calls Kimi-K2; `hermes-agent` can swap between GLM-5 and Kimi-K2 via provider config. Models are interchangeable — most projects in upper layers support multiple model backends.

**Runtimes → harnesses & CLI agents**
Runtimes provide the execution sandbox (process isolation, tool dispatch, file access, memory). A harness like `ChatDev` or `Open-AutoGLM` needs a runtime to actually run its agents.

**Harnesses → CLI agents**
Harnesses define the *how* (multi-agent coordination, tool selection, retry logic, workflow DAGs). CLI agents are typically a harness + TUI/REPL on top. For example, `claude-code` = Anthropic's harness + CLI interface; `ChatDev` = multi-agent harness (CEO + CTO + programmer roles) with no CLI — a framework you program against.

**Tooling → all layers**
- `superpowers` / `GLM-skills` / `openskills` — prompt/skill packs that enhance any agent above
- `coze-loop` / `kimi-agent-sdk` — evaluation & SDK tools for measuring agent quality
- `repo2skill` — converts repos into skills that any upper-layer agent can consume

### Key Overlaps

The boundaries are porous. A "runtime" that grows a REPL becomes a "CLI agent". A "CLI agent" that exposes delegation APIs becomes a "runtime". The categories are organizational convenience, not rigid walls.

| Project | Primary category | Also acts as |
|---------|-----------------|--------------|
| coze-studio | Runtime | Harness (full platform with workflow builder) |
| hermes-agent | Runtime | Harness (delegation, skills, cron) |
| openclaw | Runtime | CLI agent (has a TUI) |
| Open-AutoGLM | Harness | CLI agent (has its own agent loop) |
| claw-code | CLI agent | Runtime (designed as platform) |

## Categories

### 1. Agent Harnesses (10 projects)

Complete frameworks for building and orchestrating AI agents:

| Project | Language | Description |
|---------|----------|-------------|
| [oh-my-openagent](coding-agents/agent-harnesses/oh-my-openagent) | TypeScript | The best agent harness (formerly oh-my-opencode) |
| [DeepCode](coding-agents/agent-harnesses/DeepCode) | Python | Open Agentic Coding (Paper2Code, Text2Web, Text2Backend) |
| [deepagents](coding-agents/agent-harnesses/deepagents) | Python | LangChain/LangGraph-based agent harness |
| [deer-flow](coding-agents/agent-harnesses/deer-flow) | Python | Long-horizon SuperAgent with sandboxes, memory, tools |
| [OpenHarness](coding-agents/agent-harnesses/OpenHarness) | Python | Open Agent Harness |
| [trae-agent](coding-agents/agent-harnesses/trae-agent) | Python | LLM-based general purpose software engineering agent |
| [agents](coding-agents/agent-harnesses/agents-claude) | C# | Intelligent automation for Claude Code |
| [Open-AutoGLM](coding-agents/agent-harnesses/Open-AutoGLM) | Python | Zhipu AI deep-research + coding agent |
| [ChatDev](coding-agents/agent-harnesses/ChatDev) | Python | Multi-agent software house (Tsinghua / OpenBMB) |
| [oh-my-claudecode](coding-agents/agent-harnesses/oh-my-claudecode) | TypeScript | Teams-first multi-agent orchestration for Claude Code |

### 2. Agent Runtimes (11 projects)

Platforms and infrastructure for running AI agents:

| Project | Language | Description |
|---------|----------|-------------|
| [openclaw](coding-agents/agent-runtimes/openclaw) | TypeScript | Personal AI assistant, any OS, any platform |
| [nanoclaw](coding-agents/agent-runtimes/nanoclaw) | TypeScript | Lightweight OpenClaw alternative with Apple containers |
| [ironclaw](coding-agents/agent-runtimes/ironclaw) | Rust | OpenClaw-inspired, privacy & security focused |
| [zeroclaw](coding-agents/agent-runtimes/zeroclaw) | Rust | Fast, small, autonomous AI infrastructure |
| [hermes-agent](coding-agents/agent-runtimes/hermes-agent) | Python | The agent that grows with you |
| [nanobot](coding-agents/agent-runtimes/nanobot) | Python | Ultra-lightweight personal AI agent |
| [quantumclaw](coding-agents/agent-runtimes/quantumclaw) | JavaScript | AI agent runtime with knowledge graph brain |
| [phantom](coding-agents/agent-runtimes/phantom) | TypeScript | AI co-worker with MCP server, persistent memory |
| [claw-ai-lab](coding-agents/agent-runtimes/claw-ai-lab) | Python | One dashboard, an entire research team |
| [coze-studio](coding-agents/agent-runtimes/coze-studio) | Go/TypeScript | ByteDance all-in-one AI agent development platform |
| [hiagent-python-sdk](coding-agents/agent-runtimes/hiagent-python-sdk) | Python | ByteDance enterprise coding/service agent SDK |

### 3. CLI Agents (10 projects)

Terminal-based coding assistants:

| Project | Language | Description |
|---------|----------|-------------|
| [claude-code](coding-agents/cli-agents/claude-code) | Shell/TypeScript | Anthropic's agentic coding tool |
| [opencode](coding-agents/cli-agents/opencode) | TypeScript | The open source AI coding agent |
| [claw-code](coding-agents/cli-agents/claw-code) | Rust | Clean-room Claude Code rewrite |
| [aider](coding-agents/cli-agents/aider) | Python | AI pair programmer in terminal |
| [gemini-cli](coding-agents/cli-agents/gemini-cli) | TypeScript | Google Gemini-powered terminal agent |
| [qwen-code](coding-agents/cli-agents/qwen-code) | TypeScript | Qwen-powered coding agent |
| [kimi-cli](coding-agents/cli-agents/kimi-cli) | Python | Moonshot Kimi-powered CLI agent |
| [crush](coding-agents/cli-agents/crush) | Go | Glamourous agentic coding for all |
| [copilot-cli](coding-agents/cli-agents/copilot-cli) | Go | GitHub Copilot CLI (ACP-compatible) |
| [DeepSeek-Reasonix](coding-agents/cli-agents/DeepSeek-Reasonix) | TypeScript | DeepSeek-native coding agent, prefix-cache optimized |

### 4. Models (3 projects)

Open-weight coding LLMs:

| Project | Org | Description |
|---------|-----|-------------|
| [DeepSeek-Coder](coding-agents/models/DeepSeek-Coder) | DeepSeek (深度求索) | Open coding LLM + agent |
| [Kimi-K2](coding-agents/models/Kimi-K2) | Moonshot AI (月之暗面) | Open-weight coding model |
| [GLM-5](coding-agents/models/GLM-5) | Zhipu AI (智谱 AI) | Open coding LLM + agent tools |

### 5. Tooling (11 projects)

Skills frameworks, performance optimization, and developer tools:

| Project | Language | Description |
|---------|----------|-------------|
| [superpowers](coding-agents/tooling/superpowers) | Shell | Claude Code core skills library |
| [superpowers-lab](coding-agents/tooling/superpowers-lab) | Shell | Experimental skills for Claude Code |
| [everything-claude-code](coding-agents/tooling/everything-claude-code) | JavaScript | Agent harness performance optimization |
| [antigravity-awesome-skills](coding-agents/tooling/antigravity-awesome-skills) | Python | 1000+ agentic skills collection |
| [openskills](coding-agents/tooling/openskills) | TypeScript | Universal skills loader for AI coding agents |
| [npxskills](coding-agents/tooling/npxskills) | TypeScript | Open agent skills tool |
| [repo2skill](coding-agents/tooling/repo2skill) | Shell | Repository to Skill converter |
| [coze-loop](coding-agents/tooling/coze-loop) | TypeScript | ByteDance agent evaluation framework |
| [kimi-agent-sdk](coding-agents/tooling/kimi-agent-sdk) | TypeScript | Moonshot AI agent SDK |
| [GLM-skills](coding-agents/tooling/GLM-skills) | Shell | Zhipu AI skills collection |

## Closed-Source Watchlist

Notable Chinese AI coding agents without open-source repos (tracked for awareness):

| Project | Provider | Type |
|---------|----------|------|
| Qoder / QoderWork | Alibaba (阿里云) | Agentic IDE + enterprise edition |
| 通义灵码 Tongyi Lingma | Alibaba (阿里云) | Coding LLM + IDE plugin |
| 文心快码 Wenxin Code | Baidu (百度) | Code generation / review IDE plugin |
| 秒哒 MiaoDa | Baidu (百度) | Code agent (90% auto-generation) |
| 豆包编程助手 Doubao Coding | ByteDance (字节跳动) | IDE / VS Code plugin (aka MarsCode) |
| Coze | ByteDance (字节跳动) | Low-code + agent builder |
| 星火代码 SparkCode | iFlytek (科大讯飞) | Coding agent + multi-language |
| 元宝 YuanBao | Tencent (腾讯) | WeChat/PC AI assistant (includes coding) |
| WorkBuddy | Tencent (腾讯) | Enterprise coding/DevOps agent |
| SkyAGI | Kunlun (昆仑万维) | Open-source coding agent |

## Goals

- **Compare Performance**: Benchmark different agents on identical coding tasks
- **Evaluate Capabilities**: Test code generation, debugging, refactoring, and more
- **Analyze Architecture**: Understand design patterns and trade-offs
- **Track Ecosystem**: Monitor the rapidly evolving AI coding agent landscape
- **Objective Analysis**: Provide data-driven recommendations

## Getting Started

### Clone with Submodules

```bash
git clone --recursive https://github.com/dz3ai/coder_arena.git
cd coder_arena
```

### Update Submodules

```bash
git submodule update --init --recursive
git submodule update --remote
```

### Explore a Specific Agent

```bash
cd coding-agents/cli-agents/claude-code
ls -la
```

## Benchmarking

Benchmarking framework coming soon. Planned metrics:

- Code generation accuracy
- Speed of task completion
- Context window utilization
- Tool use effectiveness
- Multi-file editing capabilities
- Debug and fix performance

## Contributing

This is a research project. Contributions welcome:
- Additional agents to track
- Benchmark task definitions
- Performance comparison scripts
- Documentation improvements

## Related Projects

- [AllClaws](https://github.com/dz3ai/allclaws) - Personal AI agent platform research
- [awesome-agent-runtimes](https://github.com/dz3ai/awesome-agent-runtimes) - Production-grade agent execution environments

## License

MIT

---

*Last updated: 2026-05-23*
*Total submodules: 45*
