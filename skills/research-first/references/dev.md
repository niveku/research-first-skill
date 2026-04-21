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

## Step 2b: Finding similar open-source projects (do this FIRST for whole-product tasks)

When the request is "build a CRM", "make a Notion clone", "create a task manager", "I need a dashboard tool", or anything that describes a *product* rather than a *component*, the highest-leverage search is: **does something like this already exist as open source?**

### What to look for

Four outcomes, in priority order:

1. **Use directly** - if an OSS project solves the user's problem and is actively maintained, that's usually the answer. Self-host or use a managed version.
2. **Self-host and adapt** - if the project is close but needs small modifications and its license allows it.
3. **Fork and extend** - if the project is close but missing features. Check license compatibility (MIT/Apache/BSD are safe; GPL/AGPL are copyleft and will force your fork to be GPL/AGPL too).
4. **Reference architecture** - if none of the above fits, still read the code: data models, API design, auth flow, and background-job strategy are often worth copying.

Include paid commercial alternatives as well, but flag them clearly as paid. Prioritize OSS.

### Search patterns

**Web queries:**
- `"open source {category} github"` - e.g., `"open source CRM github"`
- `"self-hosted {product}"` - e.g., `"self-hosted analytics"`
- `"{commercial product} open source alternative"` - e.g., `"Notion open source alternative"`
- `"{product category} like {known product}"` - e.g., `"project management like Asana self-hosted"`
- `"{category} open source 2025"` - recent, avoids abandoned projects

**GitHub-native:**
- `github.com/topics/{topic}` - e.g., `github.com/topics/crm`, `github.com/topics/self-hosted`, `github.com/topics/low-code`
- GitHub search syntax: `in:name,description,topics {keyword} stars:>500 pushed:>2025-06-01` - finds popular AND active projects
- `github.com/trending` - today's / this week's trending repos by language
- `github.com/trending/{language}?since=monthly` - monthly trending per language

**Alternative databases:**
- [alternativeto.net](https://alternativeto.net) - largest software alternatives DB. Always filter by "Open Source" license and by "Self-Hosted" platform if you plan to host it yourself.
- [openalternative.co](https://openalternative.co) - curated OSS alternatives to popular SaaS (hand-picked, higher signal than alternativeto.net).
- [privacyguides.org/tools](https://www.privacyguides.org/tools/) - privacy-respecting alternatives, most are OSS.

### Canonical curated lists

- [awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted) - canonical list of self-hostable software. 15k+ stars. Categorized by function (CRM, analytics, chat, file sharing, etc.). Always check this first for "can I self-host something like X" questions.
- [awesome-oss-alternatives](https://github.com/RunaCapital/awesome-oss-alternatives) - maps OSS projects to commercial SaaS they replace.
- [awesome-{topic}](https://github.com/sindresorhus/awesome) - start here to find the topic-specific awesome list.
- [LibHunt](https://www.libhunt.com) - compares OSS projects by activity + popularity side-by-side.

### Evaluating similar projects (before recommending)

For each candidate, check the Step 3 criteria (activity, adoption, security, license, docs, fit) and additionally:

- **Scope match**: does it solve 80%+ of the user's problem, or is it a toy/demo?
- **Self-hostability**: if the user needs to own the data, does it have a Docker image, deployment guide, or Helm chart?
- **License compatibility with fork intent**: if the user plans to modify it heavily, is the license compatible with their distribution plan?
- **Community health**: open issues responded to within days/weeks, not months. Contributor count > 5 (not a one-person project about to be abandoned).
- **Data portability**: can the user export their data if they outgrow the project?

### Presenting similar-project findings in Step 4

Frame it clearly:

- "There are 3 similar OSS projects: **{A}** (recommended - most active, fits your stack), **{B}** (has more features but heavier), **{C}** (reference only - unmaintained but its data model is worth studying)."
- "Commercial equivalents: **{X}** ($N/mo, saves the build time) - use only if self-hosting isn't an option."
- For "fork and extend" recommendations: name the exact features the user would add on top, and confirm license compatibility.

## Step 2c: Web search patterns

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

## Step 2d: Reusable patterns and templates

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

**OSS alternatives / similar-project discovery:**
- [awesome-selfhosted](https://github.com/awesome-selfhosted/awesome-selfhosted) - self-hostable software
- [awesome-oss-alternatives](https://github.com/RunaCapital/awesome-oss-alternatives) - OSS replacements for SaaS
- [alternativeto.net](https://alternativeto.net) - broad alternatives database (filter OSS)
- [openalternative.co](https://openalternative.co) - curated OSS SaaS alternatives
- [privacyguides.org/tools](https://www.privacyguides.org/tools/) - privacy-respecting OSS
- [LibHunt](https://www.libhunt.com) - side-by-side OSS project comparison
- [GitHub Trending](https://github.com/trending), `github.com/topics/{topic}`

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
