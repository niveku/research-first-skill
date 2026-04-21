# Dev Reference

Domain-specific guidance for development tasks (code, APIs, libraries, SDKs, infrastructure-as-code, backend/frontend frameworks).

## Step 1: Context detection

Check these files and signals before searching:

- `package.json`, `requirements.txt`, `pyproject.toml`, `go.mod`, `Gemfile`, `Cargo.toml` - existing dependencies
- `docker-compose.yml`, `Dockerfile` - runtime and services
- `.env.example`, `config/` - existing services the project depends on
- `README.md`, `ARCHITECTURE.md` - declared stack

**Domain-fit guidance** - use existing context as the starting point; recommend an alternative only if it clearly outweighs the switching cost:

- Project uses Supabase -> start with Supabase Auth; suggest a standalone lib only if the use case is beyond what Supabase supports.
- Project uses Prisma -> prefer compatible adapters; suggest a different ORM only if Prisma has a hard limitation here.
- Project uses React -> default to React-compatible tools; flag a framework switch only if it would meaningfully solve a problem React can't.
- Project uses Next.js -> prefer Next.js-native patterns (App Router, server actions) before third-party libs.

## Step 2b: Web search patterns

- `"best open source {thing} {language} 2025 2026"` - recent recommendations
- `"{problem} library {language} github stars:>500"` - popular, vetted libraries
- `"free tier {service type} developer"` - free services
- `"awesome-{topic}" github` - curated lists
- `"{specific tool} alternatives open source"` - options when you already know one tool

**Reddit (unfiltered opinions):**
- `"{problem} site:reddit.com r/programming OR r/webdev OR r/node OR r/python"`
- `"{tool} site:reddit.com r/ClaudeAI OR r/LocalLLaMA OR r/ChatGPT"` for AI-adjacent tools

**Hacker News:** `"{tool} site:news.ycombinator.com"` via hn.algolia.com

**GitHub:** `"{tool name} site:github.com/discussions"` for real-world usage reports

**Dev.to / Hashnode:** `"{tool} review site:dev.to"` for recent developer experience posts

## Step 2c: Reusable patterns and templates

- GitHub code search: `"boilerplate {stack}"`, `"starter {framework}"`
- Official framework recipes: Next.js examples repo, Vercel templates, Django packages
- Snippet sites: GitHub Gists, CodeSandbox templates

## Step 5: Execution guidance for dev

- Install the recommended library/service instead of reimplementing.
- Reference official docs and examples - don't guess APIs. If the library is on context7, use it.
- Keep dependencies minimal - don't pull a whole framework for one utility.
- Document where the solution came from (a comment with the repo URL or docs link).
- Run `npm audit` / `pip audit` after adding new dependencies.

## Key resource lists (dev)

**Free tools and services:**
- [free-for.dev](https://github.com/ripienaar/free-for-dev) - free tiers for SaaS, PaaS, IaaS
- Awesome lists per domain (`awesome-nodejs`, `awesome-python`, etc.)

**MCP, skills, and plugin ecosystems:**
- `search_mcp_registry` - MCPs available to connect
- `search_plugins` - installable plugins
- [punkpeye/awesome-mcp-servers](https://github.com/punkpeye/awesome-mcp-servers)
- [modelcontextprotocol/servers](https://github.com/modelcontextprotocol/servers)
- Smithery.ai, mcp.run, Glama.ai/mcp

**Objective metrics sources (hard to fake):**
- [npm trends](https://npmtrends.com) - compare npm package popularity
- [PyPI stats](https://pypistats.org) - Python package download stats
- [GitHub star history](https://star-history.com) - star growth over time
- [Socket.dev](https://socket.dev) - security analysis of npm/PyPI packages

**Forums:**
- Reddit: r/programming, r/webdev, r/node, r/python, r/rust, r/golang, r/devops
- Hacker News (via hn.algolia.com)
- Stack Overflow
- GitHub Discussions on the repo itself
