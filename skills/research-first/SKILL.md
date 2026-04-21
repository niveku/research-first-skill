---
name: research-first
description: Finds existing tools, libraries, MCPs, templates, datasets, and frameworks before creating anything from scratch. Use when the user asks to build, create, add, implement, write, draft, design, set up, automate, or analyze anything - especially on phrases like "build me a", "I want to create", "add X to my project", "is there a library for", "is there a template for", "how do I implement", "set up Y", "find a dataset for", "write a report/template/strategy/PRD". Runs BEFORE code or content is produced to prevent reinventing the wheel across dev, writing, data, ops, and research tasks.
---

# Research-First Workflow

Before writing a single line of code, drafting a document, or designing a process, find the best existing tools, libraries, templates, frameworks, and resources. A 5-minute search saves hours of work and weeks of maintenance.

## The Workflow

### Step 1: Understand the task and detect existing context (30 seconds)

Clarify:
- Core problem or deliverable
- Constraints (language, framework, budget, timeline, audience, format)
- **What's already available.** The best recommendation almost always depends on what already exists.

Load the domain-specific context detection from the matching reference:
- Dev tasks -> `references/dev.md`
- Writing / content tasks -> `references/writing.md`
- Data / analysis / ML tasks -> `references/data.md`
- Ops / process / infra tasks -> `references/ops.md`

If context is clear from the conversation, don't ask - just proceed.

### Step 2: Search for existing solutions (the core of this skill)

Run searches in parallel where possible. Breadth first, depth on the best candidates.

**2a. Check available MCPs, plugins, and skills** (skip for pure writing/content tasks):

- **Layer 1 - already connected**: if a tool in the current session handles it, use it directly.
- **Layer 2 - registries**: `search_mcp_registry` with 2-3 keyword variations. `search_plugins` for installable plugins. Check Smithery.ai, mcp.run, Glama.ai.
- **Layer 3 - community**: `awesome-mcp-servers` on GitHub, `punkpeye/awesome-mcp-servers`, `modelcontextprotocol/servers`. GitHub Discussions for real-world reports. Reddit and Hacker News for unfiltered opinions.

Forums beat blogs: developers will say "I tried X and it was terrible because..." - blogs rarely do.

**2b. Web search for tools, libraries, and resources** - query patterns are domain-specific, see the matching reference file.

**2c. Search for reusable patterns and templates** - boilerplates, starter repos, document frameworks, analysis notebooks, SOPs. See the domain reference.

### Step 3: Evaluate candidates (rigorous validation with bias detection)

For each candidate, verify:

| Criteria | What to check |
|---|---|
| **Activity** | Last commit < 6 months. Issues being addressed. |
| **Adoption** | Stars > 100 (libs), weekly downloads, used by known projects. |
| **Security** | No unpatched CVEs. Check `snyk.io` or `socket.dev` if in doubt. |
| **License** | MIT, Apache 2.0, BSD, or similarly permissive. Flag GPL/AGPL. |
| **Documentation** | README with usage examples. Ideally a docs site. |
| **Fit** | Works with existing stack. Minimal dependencies. Solves the actual problem. |

**Anti-bias filter.** Many "Top 10" blogs rank their own product #1. Mitigations:

- **Cross-reference 3+ independent sources.** If only one blog promotes it, be skeptical.
- **Prioritize objective metrics** (stars, downloads, StackOverflow question count) over opinions.
- **Prefer neutral sources**: Stack Overflow, GitHub trending, npmtrends.com, Reddit/HN threads, official framework docs.
- **When in doubt, tell the user.** If the best source is the product's own site, say so.

### Step 4: Present the recommendation

- **Recommended approach**: one clear pick with reasoning. Why it fits the existing stack.
- **What it solves**: how it addresses the task.
- **What we still need to build**: remaining custom work (if any).
- **Alternatives**: 1-2 options with trade-offs. Highlight stack-overlap alternatives.
- **Free resources found**: anything relevant from free-for.dev or similar.

### Step 5: Execute with found resources

Only now create. Install/adopt the recommended resource instead of reimplementing. Reference official docs - don't guess APIs. Document the source (URL comment, citation). Domain-specific execution guidance lives in the matching reference file.

## Effort calibration

Not every task warrants the full 5-step workflow.

| Task type | Search depth | Skip what |
|---|---|---|
| Trivial (rename, typo) | Skip entirely | Everything - just do it |
| Simple, well-known (add `.gitignore`, format a date) | 1 min max | MCP layer and forum search |
| Dev task with a clear library solution | 3-5 min | Non-dev reference files |
| Writing task (report, template) | 3-5 min | MCP layer (2a) entirely |
| Data / ML task | 5-10 min | Skip MCP unless it's a data pipeline |
| Complex or ambiguous task | Full workflow | Nothing - run all layers |

A search that takes longer than the task itself is waste.

## What NOT to do

- Don't skip the search and jump to creating, even if you "know" how.
- Don't recommend abandoned projects (12+ months no commits with open critical issues).
- Don't recommend libraries with unpatched CVEs.
- Don't add heavy frameworks when a utility would do.
- Don't spend more than 2-3 minutes searching for a simple task.
- Don't trust a single "Top 10" blog as your only source - cross-reference.
- Don't apply dev metrics (GitHub stars) to non-dev tasks (document templates).

## Edge cases

- **Trivial tasks**: skip this workflow entirely.
- **Highly custom business logic**: search won't help; note it and implement.
- **User says "write it from scratch"**: respect that, but briefly mention strong existing options.
- **Offline**: fall back to training knowledge, note you couldn't verify recency.
- **Library name confusion** (e.g., NextAuth.js -> Auth.js): clarify current name and version.
- **Non-technical user**: skip the MCP layer (2a) and focus on templates / frameworks.

## Domain reference files

Load only the one(s) relevant to the task to keep context lean:

- [`references/dev.md`](references/dev.md) - Dev tasks: context detection, web search patterns, key resource lists (npm trends, PyPI stats, free-for.dev, GitHub Discussions).
- [`references/writing.md`](references/writing.md) - Writing and content: Notion, Canva, Google Workspace templates, document frameworks.
- [`references/data.md`](references/data.md) - Data, analysis, and ML: Kaggle, Hugging Face, Papers With Code, public datasets.
- [`references/ops.md`](references/ops.md) - Ops, CI/CD, infra, and process: GitHub Actions, Terraform modules, SOP templates.
