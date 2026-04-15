# Research-First Skill

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/niveku/research-first-skill)](https://github.com/niveku/research-first-skill/releases)

A skill for AI coding agents that enforces a **research-first workflow** — always search for existing tools, libraries, templates, frameworks, and resources before creating anything from scratch.

Built for **Claude Code**. Also compatible with Codex, Gemini CLI, Cursor, and any agent that supports SKILL.md-based skills.

Works for any workflow: development, writing, data analysis, ops, and research.

## What it does

When you ask your agent to build, write, research, or automate something, this skill makes it:

1. **Detect your existing context** — reads config files, style guides, existing assets, and current stack to understand what you already have
2. **Search for existing solutions** across multiple layers:
   - Connected MCPs, plugins, and skills
   - Official registries (Anthropic MCP registry, Smithery.ai, mcp.run, Glama.ai)
   - GitHub repos, community lists (`awesome-*`), and open-source tools
   - Templates and frameworks for writing, data, and process tasks (Notion, Kaggle, Hugging Face, etc.)
   - Developer forums (Reddit, HN, GitHub Discussions) for unfiltered opinions
   - Free-tier services via [free-for.dev](https://free-for.dev)
3. **Validate candidates rigorously** — checks stars, downloads, activity, security (CVEs), license, and fit with your context
4. **Detect self-promotional bias** — cross-references 3+ sources, flags "Top 10" blogs that rank their own product #1
5. **Recommend one clear solution** with alternatives and trade-offs
6. **Only then create** — using found resources instead of reinventing the wheel

## Why

Creating from scratch when a battle-tested solution already exists is the most expensive mistake in any workflow. A 5-minute search can save hours of work and weeks of maintenance.

## Install

### Option 1: Double-click the `.skill` file

Download `research-first.skill` and double-click it. It installs automatically in Claude Code.

### Option 2: Manual install

```bash
# Claude Code — global (all projects)
cp -r research-first/ ~/.claude/skills/

# Claude Code — per project
cp -r research-first/ .claude/skills/

# Codex / Gemini CLI / Cursor — check your agent's skills directory
cp -r research-first/ <your-agent-skills-dir>/
```

## Usage

Once installed, the skill triggers automatically. No special commands needed.

**Development:**
- "Add authentication to my Next.js app"
- "I need web scraping in Python"
- "Set up CI/CD with free hosting for my React app"
- "Build a REST API with a database"

**Writing / content:**
- "Write a product requirements document"
- "Create a weekly status report template"
- "Draft a go-to-market strategy"

**Data / analysis:**
- "Build a sales dashboard"
- "Analyze customer churn in our dataset"
- "Find a model for sentiment analysis"

**Ops / process:**
- "Automate my deployment pipeline"
- "Create an onboarding checklist for new engineers"
- "Set up infrastructure monitoring"

## What's inside

```
research-first/
└── SKILL.md          # The skill instructions
research-first.skill  # Packaged skill (installable)
README.md             # This file
CHANGELOG.md          # Version history
LICENSE               # MIT License
```

## License

MIT
