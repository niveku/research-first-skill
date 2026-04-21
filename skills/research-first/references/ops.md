# Ops, CI/CD, Infra & Process Reference

Domain-specific guidance for ops tasks (CI/CD, infrastructure, deployment, monitoring, SOPs, runbooks, automation).

## Step 1: Context detection

Check these before searching:

- Existing CI config (`.github/workflows/`, `.gitlab-ci.yml`, `.circleci/`, `Jenkinsfile`)
- Infrastructure definitions (`terraform/`, `pulumi/`, `cdk/`, `kubernetes/`, `helm/`)
- Cloud provider in use (AWS, GCP, Azure, Cloudflare, Vercel, Railway, Fly.io)
- Existing runbooks / SOPs / onboarding docs
- Monitoring stack (Datadog, Grafana, Prometheus, Sentry, PagerDuty)
- Deployment target (VPS, Kubernetes, serverless, container platform)

**Domain-fit guidance** - extend what exists before introducing new tools:

- CI already runs on GitHub Actions -> extend the existing workflow. Suggest a new CI system only if there's a capability gap.
- Team has a runbook or SOP -> update it. Write a new one only if the scope is genuinely different.
- Infrastructure is on a cloud provider -> prefer native services. Suggest a third-party tool only if it solves something the native stack can't.
- Team uses Terraform -> find a Terraform module. Suggest a different IaC tool (Pulumi, CDK) only if Terraform can't model it.

## Step 2b: Web search patterns

- `"github actions {workflow type} example"` - CI/CD workflow templates
- `"terraform module {provider} {resource}"` - IaC modules (check [registry.terraform.io](https://registry.terraform.io))
- `"{process type} SOP template"` - standard operating procedures
- `"runbook template {system type}"` - incident response runbooks
- `"{cloud provider} {service} best practices 2025"` - cloud-native patterns
- `"kubernetes {workload type} helm chart"` - deployable charts ([artifacthub.io](https://artifacthub.io))

## Step 2c: Reusable patterns and templates

- **GitHub Actions**: starter workflows at [actions/starter-workflows](https://github.com/actions/starter-workflows), marketplace at [github.com/marketplace](https://github.com/marketplace).
- **Terraform**: [registry.terraform.io](https://registry.terraform.io) - official + community modules.
- **Helm charts**: [artifacthub.io](https://artifacthub.io) - centralized Helm chart search.
- **Runbooks**: Google SRE book (free online) for canonical incident response, PagerDuty's public runbook library, GitHub's docs repo (has real runbooks).
- **SOPs**: Process.st library, ISO 9001 examples, NIST templates for security SOPs.

## Step 5: Execution guidance for ops

- Copy and adapt the found template/workflow - only customize the parts specific to this context.
- Pin versions (action versions by commit SHA for security; Terraform provider versions in `versions.tf`).
- Test in a branch / staging before main.
- Document the source (comment at the top: `# Based on actions/starter-workflows/ci/node.js.yml`).
- For SOPs: include last-reviewed date and owner; SOPs rot fast.

## Key resource lists (ops)

**CI/CD templates:**
- [actions/starter-workflows](https://github.com/actions/starter-workflows) - official GitHub Actions starters
- [GitHub Marketplace](https://github.com/marketplace?type=actions) - community actions
- [GitLab CI templates](https://docs.gitlab.com/ee/ci/examples/)
- [CircleCI orbs](https://circleci.com/developer/orbs)

**IaC modules:**
- [registry.terraform.io](https://registry.terraform.io) - Terraform modules + providers
- [Pulumi registry](https://www.pulumi.com/registry/)
- [AWS CDK Construct Hub](https://constructs.dev)

**Kubernetes / containers:**
- [artifacthub.io](https://artifacthub.io) - Helm charts
- [kubernetes/examples](https://github.com/kubernetes/examples)
- [Docker Hub](https://hub.docker.com) official images

**SOPs and runbooks:**
- [Google SRE book](https://sre.google/books/) (free online)
- PagerDuty Incident Response docs
- [Process.st](https://www.process.st) - business SOPs
- NIST templates for security/compliance SOPs

**Monitoring / observability:**
- [Grafana dashboards](https://grafana.com/grafana/dashboards/) - community dashboards
- [Prometheus exporters](https://prometheus.io/docs/instrumenting/exporters/)
- [Datadog integrations](https://docs.datadoghq.com/integrations/)

**Free-tier services for infra:**
- [free-for.dev](https://github.com/ripienaar/free-for-dev) - filtered by category (CI, hosting, monitoring, DNS)

**Forums:**
- Reddit: r/devops, r/sysadmin, r/aws, r/kubernetes, r/Terraform, r/homelab
- Hacker News (for cloud cost / reliability discussions)
- CNCF Slack for Kubernetes/cloud-native
