# Research-First

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![GitHub release](https://img.shields.io/github/v/release/niveku/research-first-skill)](https://github.com/niveku/research-first-skill/releases)
[![Claude Code Plugin](https://img.shields.io/badge/Claude%20Code-Plugin-blueviolet)](https://docs.claude.com/claude-code)
[![Validate Plugin](https://github.com/niveku/research-first-skill/actions/workflows/validate-plugins.yml/badge.svg)](https://github.com/niveku/research-first-skill/actions/workflows/validate-plugins.yml)

A Claude Code plugin / agent skill that enforces a **research-first workflow**: always search for existing tools, libraries, MCPs, templates, frameworks, datasets, and open-source resources before creating anything from scratch.

Built for **Claude Code**. Also compatible with Codex, Gemini CLI, Cursor, and any agent that reads SKILL.md.

Works for any workflow: development, writing, data analysis, ops, and research.

## What it does

When you ask your agent to build, write, analyze, or automate something, this skill makes it:

1. **Detect your existing context** - reads config files, style guides, data sources, and current stack.
2. **Search for existing solutions** across multiple layers:
   - Connected MCPs, plugins, and skills
   - Official registries (Anthropic MCP registry, Smithery.ai, mcp.run, Glama.ai)
   - GitHub repos, `awesome-*` lists, and open-source tools
   - Templates for writing, data, and process tasks (Notion, Kaggle, Hugging Face, etc.)
   - Developer forums (Reddit, HN, GitHub Discussions) for unfiltered opinions
   - Free-tier services via [free-for.dev](https://free-for.dev)
3. **Validate rigorously** - activity, adoption, security (CVEs), license, and fit.
4. **Detect self-promotional bias** - cross-references 3+ sources, flags "Top 10" blogs that rank their own product #1.
5. **Recommend one clear solution** with alternatives and trade-offs.
6. **Only then create** - using found resources instead of reinventing the wheel.

## Why

Creating from scratch when a battle-tested solution already exists is the most expensive mistake in any workflow. A 5-minute search can save hours of work and weeks of maintenance.

## Install

### Claude Code (recommended)

Add the marketplace, then install the plugin:

```bash
/plugin marketplace add niveku/research-first-skill
/plugin install research-first@niveku-plugins
```

Once installed, the skill triggers automatically. No manual invocation needed.

### Other agents (Codex, Gemini CLI, Cursor, etc.)

Copy the skill folder into your agent's skills directory:

```bash
# Example: Claude Code manual install (per project)
cp -r skills/research-first .claude/skills/

# Example: Claude Code manual install (global)
cp -r skills/research-first ~/.claude/skills/

# Other agents: check your agent's skill directory convention
cp -r skills/research-first <your-agent-skills-dir>/
```

## Usage

Once installed, the skill activates when you ask your agent to build, create, or implement something. No special commands needed.

**Development:**
- "Add authentication to my Next.js app"
- "I need web scraping in Python"
- "Set up CI/CD with free hosting for my React app"
- "Is there a library for X?"

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
research-first-skill/
├── .claude-plugin/
│   ├── plugin.json          # Plugin manifest
│   └── marketplace.json     # Marketplace entry (for /plugin install)
├── skills/
│   └── research-first/
│       ├── SKILL.md         # The skill instructions (loaded first)
│       └── references/
│           ├── dev.md       # Dev-specific search patterns
│           ├── writing.md   # Writing/content templates
│           ├── data.md      # Data, ML, analysis resources
│           └── ops.md       # CI/CD, infra, SOP resources
├── .github/workflows/
│   └── validate-plugins.yml # CI: validates plugin.json + SKILL.md
├── README.md
├── CHANGELOG.md
├── CONTRIBUTING.md
└── LICENSE
```

The skill uses **progressive disclosure**: `SKILL.md` loads first with the core workflow, and domain-specific details in `references/*.md` load only when relevant.

## Contributing

See [CONTRIBUTING.md](./CONTRIBUTING.md).

## License

MIT
