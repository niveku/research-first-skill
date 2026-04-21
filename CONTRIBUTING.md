# Contributing

Contributions are welcome. This skill improves when real-world workflows surface gaps or better resources.

The skill is built for Claude Code (as a plugin) but the SKILL.md format is compatible with any agent that supports SKILL.md-based skills (Codex, Gemini CLI, Cursor, and others). Contributions that improve cross-agent compatibility are especially welcome.

## Ways to contribute

**Improve existing content:**
- Better search queries for a domain (add them to the matching `references/*.md`)
- More accurate domain-fit examples
- Fixes to outdated resource links or tool names

**Extend to new domains:**
- The skill currently covers dev, writing, data, and ops. Other domains (legal, design, finance, etc.) are fair game if the research-first principle applies. Add a new `references/{domain}.md` and reference it from `SKILL.md`.

**Report issues:**
- Skill triggering when it shouldn't (or not triggering when it should)
- Recommended resources that are abandoned, biased, or no longer relevant
- Plugin install failures on `/plugin install research-first@niveku-plugins`

## How to submit changes

1. Fork the repo
2. Edit the relevant file (`skills/research-first/SKILL.md` or a reference file)
3. Run the validation locally if you want:
   ```bash
   python3 -c "import json; json.load(open('.claude-plugin/plugin.json'))"
   python3 -c "import json; json.load(open('.claude-plugin/marketplace.json'))"
   ```
4. Open a PR with a short description of what you changed and why

CI will validate `plugin.json`, `marketplace.json`, and SKILL.md frontmatter automatically.

## Repository structure

```
skills/research-first/
├── SKILL.md          # Core workflow (frontmatter + 5-step process)
└── references/       # Domain-specific detail (progressive disclosure)
    ├── dev.md
    ├── writing.md
    ├── data.md
    └── ops.md
```

When adding content, ask: "does this apply across all domains, or only to one?" Cross-domain content goes in `SKILL.md`. Domain-specific content goes in the matching reference file. This keeps `SKILL.md` compact so it loads fast and doesn't crowd the agent's context.

## Guidelines

- Keep the skill focused: it should remain a *process* skill, not a domain encyclopedia.
- Each addition should reduce the chance of an agent reinventing something that already exists.
- Prefer concrete examples over general advice.
- If adding a new resource list, verify it's actively maintained and not self-promotional.
- Keep the `description` field in `SKILL.md` under ~1024 characters to preserve skill matching quality.
