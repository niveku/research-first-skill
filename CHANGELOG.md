# Changelog

## [1.2.0] - 2026-04-20

### Changed
- **Repository converted to Claude Code plugin format** - installable via `/plugin marketplace add niveku/research-first-skill` + `/plugin install research-first@niveku-plugins`
- Moved `research-first/` -> `skills/research-first/` per Claude Code plugin convention
- Rewrote frontmatter `description` with Anthropic's recommended triggering pattern (exact-phrase triggers in quotes, "Use when" framing). Condensed from ~700 chars of folded YAML to ~665 chars of a single matcher-friendly line. Improves skill activation on phrases like "build me a", "is there a library for", "how do I implement".
- Split monolithic SKILL.md into progressive disclosure: core workflow in `SKILL.md`, domain specifics loaded on demand from `references/dev.md`, `references/writing.md`, `references/data.md`, `references/ops.md`.

### Added
- `.claude-plugin/plugin.json` - plugin manifest with keywords for registry discoverability
- `.claude-plugin/marketplace.json` - marketplace entry for standalone distribution
- `.github/workflows/validate-plugins.yml` - CI validates `plugin.json`, `marketplace.json`, and SKILL.md frontmatter on every push/PR
- README badges: plugin badge, CI status badge
- `.gitignore` hardened (`.claude/`, `.env`, build artifacts, common Python/Node caches)

### Deprecated
- `research-first.skill` binary (old zip packaging). Use `/plugin install` or manual `cp skills/research-first/` instead.

## [1.1.0] - 2026-04-15

### Changed
- Generalized skill from dev-only to any workflow: writing, data analysis, ops, and research
- Updated frontmatter description to trigger on non-development tasks (reports, templates, strategies, datasets, processes)
- Generalized Step 1 context detection to cover style guides, existing assets, and domain-specific resources — not just code files
- Expanded Step 2b search patterns with domain-specific queries for writing, data, ops, and research tasks
- Generalized Step 2c to "Reusable Patterns and Templates" covering non-code domains
- Updated Step 5 with domain-specific execution guidance for each workflow type
- Added non-technical user edge case (skip MCP layer for writing/process tasks)

### Added
- Templates and frameworks resource list: Notion, Canva, Google Workspace, Miro/FigJam, Process.st
- Data and ML resources: Kaggle, Hugging Face, Papers With Code, Google Dataset Search, Awesome Public Datasets
- Domain-fit examples in Step 1 (Notion workspace, BigQuery, existing doc templates)
- New "What NOT to Do" rule: don't apply dev-centric metrics to non-dev tasks

## [1.0.0] - 2026-04-12

### Added
- Initial release
- Research-first workflow with 5-step process
- Multi-layer MCP/plugin/skill search (Smithery, mcp.run, Glama, awesome-mcp-servers)
- Anti-bias filter for self-promotional content
- Rigorous candidate evaluation criteria (activity, adoption, security, license, fit)
- Key resource lists: free-for.dev, npm trends, PyPI stats, GitHub star history, Socket.dev
- Community forum search patterns (Reddit, HN, GitHub Discussions, Dev.to)
