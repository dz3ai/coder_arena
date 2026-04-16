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
│   └── tooling/             # Skills frameworks, performance tools
└── README.md
```

## Categories

### 1. Agent Harnesses (9 projects)

Complete frameworks for building and orchestrating AI agents:

| Project | Language | Description |
|---------|----------|-------------|
| [opencode](coding-agents/agent-harnesses/opencode) | TypeScript | The open source coding agent |
| [oh-my-openagent](coding-agents/agent-harnesses/oh-my-openagent) | TypeScript | The best agent harness (formerly oh-my-opencode) |
| [claw-code](coding-agents/agent-harnesses/claw-code) | Rust | Fast repo built with oh-my-codex |
| [DeepCode](coding-agents/agent-harnesses/DeepCode) | Python | Open Agentic Coding (Paper2Code, Text2Web, Text2Backend) |
| [deepagents](coding-agents/agent-harnesses/deepagents) | Python | LangChain/LangGraph-based agent harness |
| [deer-flow](coding-agents/agent-harnesses/deer-flow) | Python | Long-horizon SuperAgent with sandboxes, memory, tools |
| [OpenHarness](coding-agents/agent-harnesses/OpenHarness) | Python | Open Agent Harness |
| [trae-agent](coding-agents/agent-harnesses/trae-agent) | Python | LLM-based general purpose software engineering agent |
| [agents](coding-agents/agent-harnesses/agents-claude) | C# | Intelligent automation for Claude Code |

### 2. Agent Runtimes (9 projects)

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

### 3. CLI Agents (5 projects)

Terminal-based coding assistants:

| Project | Language | Description |
|---------|----------|-------------|
| [claude-code](coding-agents/cli-agents/claude-code) | Shell/TypeScript | Anthropic's agentic coding tool |
| [gemini-cli](coding-agents/cli-agents/gemini-cli) | TypeScript | Google Gemini-powered terminal agent |
| [qwen-code](coding-agents/cli-agents/qwen-code) | TypeScript | Qwen-powered coding agent |
| [kimi-cli](coding-agents/cli-agents/kimi-cli) | Python | Moonshot Kimi-powered CLI agent |
| [crush](coding-agents/cli-agents/crush) | Go | Glamourous agentic coding for all |

### 4. Tooling (8 projects)

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

*Last updated: 2026-04-15*
*Total submodules: 27*