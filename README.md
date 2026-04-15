# Research-First Skill

A Claude skill that enforces a **research-first workflow** — always search for existing tools, libraries, MCPs, plugins, and open-source projects before writing code from scratch.

## What it does

When you ask Claude to build, implement, or automate something, this skill makes it:

1. **Detect your existing stack** — reads `package.json`, `requirements.txt`, etc. to understand what you already use
2. **Search for existing solutions** across multiple layers:
   - Connected MCPs, plugins, and skills
   - Official registries (Anthropic MCP registry, Smithery.ai, mcp.run, Glama.ai)
   - GitHub repos, community lists (`awesome-*`), and open-source tools
   - Developer forums (Reddit, HN, GitHub Discussions) for unfiltered opinions
   - Free-tier services via [free-for.dev](https://free-for.dev)
3. **Validate candidates rigorously** — checks stars, downloads, activity, security (CVEs), license, and stack fit
4. **Detect self-promotional bias** — cross-references 3+ sources, flags "Top 10" blogs that rank their own product #1
5. **Recommend one clear solution** with alternatives and trade-offs
6. **Only then write code** — using the found resources instead of reinventing the wheel

## Why

Writing code from scratch when a battle-tested solution already exists is the most expensive mistake in software development. A 5-minute search can save hours of coding and weeks of maintenance.

## Install

### Option 1: Double-click the `.skill` file

Download `research-first.skill` and double-click it. It installs automatically in Claude (Cowork or Claude Code).

### Option 2: Manual install (Claude Code)

```bash
# Global (all projects)
cp -r research-first/ ~/.claude/skills/

# Per project
cp -r research-first/ .claude/skills/
```

### Option 3: Manual install (Cowork)

Copy the `research-first/` folder to your Cowork skills directory.

## Usage

Once installed, the skill triggers automatically whenever you ask Claude to build something. No special commands needed.

Examples of prompts that trigger it:

- "Add authentication to my Next.js app"
- "I need web scraping in Python"
- "Set up CI/CD with free hosting for my React app"
- "Build a REST API with a database"
- "Automate my deployment pipeline"

## What's inside

```
research-first/
└── SKILL.md          # The skill instructions
research-first.skill  # Packaged skill (installable)
README.md             # This file
LICENSE               # MIT License
```

## License

MIT
