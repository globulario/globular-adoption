# Globular Adoption Plan — V2: Proving AI-Operated Infrastructure

> **Mission**: Make Globular the open-source reference platform for AI-operated infrastructure: a system where applications, services, packages, nodes, workflows, identity, health, history, and remediation are explicit enough for both humans and AI agents to understand and operate safely.
>
> **North star**: Prove that AI agents can safely understand, diagnose, and help operate real infrastructure through Globular.
>
> **Primary public metric**: GitHub stars.
>
> **Secondary metrics**: quickstart completions, demo views, first external users, first contributors, consulting leads, and production experiments.

---

## The Thesis

Infrastructure is entering a new era.

The old model assumes humans operate infrastructure through dashboards, YAML, shell commands, logs, alerts, and tribal knowledge.

The next model assumes AI agents will participate in operations.

For AI agents to operate infrastructure safely, the infrastructure must expose structured operational truth:

- What should exist
- What is installed
- What is running
- What changed
- What failed
- Who is allowed to act
- Which action is safe
- How convergence is verified

Most platforms can be wrapped by AI after the fact.

Globular is different because it is built around explicit state, typed operations, workflows, RBAC, service discovery, gRPC, MCP, and convergence.

Globular’s adoption strategy is therefore not only to prove that it can run applications.

It must prove something larger:

> **Globular is a credible architecture for AI-operated infrastructure.**

---

## The Positioning

Globular should not be positioned as “Kubernetes but different.”

That is the wrong battlefield.

Kubernetes is the dominant workload orchestration ecosystem. Competing with it directly triggers defensive comparisons, ecosystem questions, and trust objections.

Globular should be positioned as:

> **Open-source infrastructure for AI-operated clusters.**

Or shorter:

> **Globular makes infrastructure readable enough for AI agents to operate safely.**

The comparison becomes:

| Existing model | Globular model |
|---|---|
| Human-operated infrastructure | Human + AI-operated infrastructure |
| Logs and dashboards | Structured operational truth |
| Shell scripts and tribal memory | Typed operations and workflows |
| Implicit state | Explicit state layers |
| Best-effort diagnosis | Doctor findings and workflow history |
| AI as chatbot | AI as secured operator through MCP/gRPC/RBAC |
| Kubernetes as workload substrate | Globular as AI-readable infrastructure substrate |

Globular can support Kubernetes later.

But the core message is not:

> “Globular replaces Kubernetes.”

The core message is:

> **“Globular explores what infrastructure must become when AI agents participate in operations.”**

---

## The AI Operation Plane

Globular exposes infrastructure through secured, discoverable, machine-readable control surfaces.

```text
Claude / Codex / AI agent
        ↓
MCP tools
        ↓
gRPC reflection / service APIs
        ↓
RBAC + mTLS + token validation
        ↓
Workflow engine / doctor / controller
        ↓
Cluster state changes
        ↓
Verification and convergence
```

This is the jewel.

Globular does not give AI a dangerous shell.

It gives AI a secured, discoverable, typed, permissioned control surface.

That is a major architectural distinction.

### Safe agency

The future is not:

> “Let AI run random commands on servers.”

The future is:

> **“Let AI inspect, reason, propose, and act through safe platform operations protected by RBAC and verified by workflows.”**

Every serious demo, article, and doc should reinforce:

- AI can discover available operations
- AI can inspect real cluster state
- AI can compare desired vs installed vs runtime
- AI can diagnose drift
- AI can propose typed remediation
- AI actions are RBAC-controlled
- Mutating actions can require approval
- Workflows record what happened
- Doctor verifies the result
- The cluster converges

---

## The Core Challenge

Globular is technically strong for its use case, but it has the hardest adoption problem in software: it requires a **mental model shift** before the value is visible.

You cannot demo the whole idea in 30 seconds.

The people who most need it do not yet have the vocabulary to search for it.

People already understand Kubernetes, Docker, Terraform, CI/CD, monitoring dashboards, and cloud platforms.

They do not yet have common language for:

- AI-readable infrastructure
- Explicit operational truth
- Agent-safe control surfaces
- Workflow-driven remediation
- Convergent cluster state
- Infrastructure that can explain itself

That means Globular must not be presented only as “a platform.”

It must be presented as an answer to a future problem:

> **What does infrastructure need to look like when AI agents are expected to help operate it?**

The plan attacks adoption from four directions:

1. **Prove the thesis** with a real AI-operated cluster demo
2. **Lower the barrier to belief** with a fast quickstart and one working app
3. **Build the audience** through articles, videos, communities, and demos
4. **Build trust** through documentation, security posture, repeatable tests, and honest limitations

---

## Four Target Audiences

Each audience has a different entry point, a different first article, and a different demo.

The plan serves all four but speaks to each in their own language.

| Audience | The pain they feel right now | What triggers adoption |
|---|---|---|
| **AI infrastructure / agentic ops builders** | “Agents need safe operational tools, not shell access.” | “Globular exposes infrastructure through MCP/gRPC/RBAC.” |
| **Developer** — building microservices, gRPC systems, APIs | “I keep reinventing auth, certs, routing, versioning.” | “I can stop assembling this myself.” |
| **Operator** — small team, no dedicated infra person | “I can’t tell what the cluster thinks vs what’s real.” | “I can finally reason about state.” |
| **Startup** — 0→1, no DevOps hire, needs production semantics early | “Kubernetes is overkill but I need real cluster behavior.” | “This gives me production semantics on day one.” |

---

## The Three Proofs Globular Must Show

Globular adoption depends on three proofs.

### Proof 1: It can run real applications

Infrastructure without an application is a beautiful engine bolted to a table.

Globular needs one clean application demo.

Recommended first app:

# Globular Catalog

A practical CRUD/catalog app that shows:

- Service definition
- Generated or scaffolded backend
- RBAC actions
- Frontend/admin UI
- Package publication
- Installation
- Routing
- Monitoring
- Upgrade
- Backup/restore
- AI-assisted diagnosis

This app proves Globular is not only an infrastructure experiment.

It is a platform for shipping software.

---

### Proof 2: It can operate real infrastructure

Globular must show Day-0, Day-1, drift, failure, and recovery.

Demo scenario:

```text
Install 3-node Globular
Deploy Catalog app
Break one service or node
Doctor detects degradation
AI inspects MCP/gRPC/CLI state
AI explains the root cause
AI proposes safe remediation
Workflow executes
Cluster converges
```

This proves Globular is operationally serious.

---

### Proof 3: AI can understand and operate it

This is the strongest proof.

The killer claim is not:

> “AI helped write Globular.”

The killer claim is:

> **“Claude and Codex helped test, debug, and operate Globular by reasoning about sequence states, synchronization overload, readiness gates, stale state, workflow failures, and convergence.”**

That is AI-assisted distributed-systems engineering.

This should become the core public story.

---

# Phase 1 — Foundation

*Nothing else works without this. This is the floor.*

---

## 1.1 GitHub Repository Polish

The GitHub page is the universal landing page.

Every article, every tweet, every HN post, every Reddit post, every demo ends here.

It must do the work of conversion.

The README must answer five questions fast:

1. What is Globular?
2. Why does it exist?
3. Why is it different?
4. Can I run it?
5. Can AI really operate it?

### README opening

Suggested opening:

> **Globular is an open-source platform for AI-operated infrastructure.**
>
> It exposes services, packages, nodes, workflows, identity, health, and history as structured operational truth so humans and AI agents can understand and operate distributed systems safely.

### README rewrite checklist

- [ ] Lead with one sentence that names the pain, not only the solution:
  - *“Most software projects begin with an application idea and end with an infrastructure problem.”*
- [ ] Show the AI Operation Plane diagram immediately
- [ ] Show the 4-layer diagram immediately
- [ ] Explain the four truth layers:
  - Artifact / Repository
  - Desired State
  - Installed / Observed State
  - Runtime Health
- [ ] Show one real CLI example:
  - artifact → desired → installed → running
- [ ] Show one MCP/gRPC example:
  - AI agent inspects health, drift, workflow state, and proposes action
- [ ] Show one real `globular` command that does something difficult on other platforms in very few lines
- [ ] Add badges:
  - build status
  - license
  - latest release
  - docs
- [ ] Add a “Quick install” block:
  - copy-paste
  - one command
  - first cluster running
- [ ] Link to:
  - quickstart
  - operator course
  - docs
  - GitHub Discussions or Discord
  - demo video
  - AI Operation Plane doc
- [ ] Add clear project status:
  - experimental / beta / v1
  - known limitations
  - what is production-ready
  - what is not

### GitHub repository hygiene

- [ ] Topics/tags:
  - `ai-infrastructure`
  - `agentic-ops`
  - `mcp`
  - `grpc`
  - `distributed-systems`
  - `platform-engineering`
  - `self-hosted`
  - `bare-metal`
  - `devops`
  - `kubernetes-alternative`
  - `cluster`
  - `golang`
- [ ] Description field:
  - short
  - searchable
  - accurate
- [ ] Social preview image:
  - AI Operation Plane or 4-layer diagram with Globular name
- [ ] Releases:
  - every version tagged
  - changelog
  - upgrade notes
- [ ] Issues:
  - good first issue labels
  - help wanted labels
- [ ] CONTRIBUTING.md:
  - clear path for external contributors
- [ ] SECURITY.md:
  - how to report vulnerabilities
  - RBAC / AI operation safety statement
- [ ] ROADMAP.md:
  - short, honest, current
- [ ] Known limitations:
  - clearly documented
  - no hidden monster under the rug

---

## 1.2 The Quickstart

*The most important technical asset for adoption.*

If this is broken, nothing else matters.

### Target experience

A developer or operator with a Linux VM can go from zero to a running single-node Globular cluster with at least one service deployed in **under 30 minutes**.

The experience must feel like magic, not like a checklist.

Better: it must feel like **boring magic**.

The user should think:

> “That was surprisingly clear.”

### Quickstart must cover

1. Bootstrap a single node
2. Deploy the echo service or Catalog demo
3. See the four truth layers in the CLI:
   - artifact
   - desired
   - installed
   - runtime
4. Run doctor
5. Trigger a small controlled drift
6. See Globular detect the drift
7. Repair or reconcile
8. Verify green state
9. Optional: add a second node
10. Optional: deploy an update

### Example quickstart path

```text
Install Globular
Start node
Run globular status
Deploy echo service
Run globular doctor
Break service
Run drift report
Repair
Verify convergence
```

### Where it lives

`globular-quickstart` repo, if it already exists.

If not, create one.

### Validation rule

A person who has never seen Globular must be able to complete it with zero help.

Test this with real strangers.

Track:

- where they stop
- what command fails
- what term confuses them
- how long it takes
- whether they understand why Globular exists

---

## 1.3 Core Architecture Docs

Globular needs serious architecture docs.

Not too many at first. Just enough to prove the thesis.

### Required docs

```text
docs/architecture/why-globular.md
docs/architecture/explicit-state-layers.md
docs/architecture/ai-operation-plane.md
docs/architecture/workflows-and-convergence.md
docs/architecture/rbac-and-safe-agent-operations.md
docs/architecture/globular-vs-kubernetes.md
docs/operations/failure-recovery-demo.md
```

### Most important doc

# `docs/architecture/ai-operation-plane.md`

It should explain:

1. Why AI needs structured operational truth
2. Why shell access is unsafe
3. Why dashboards are insufficient
4. How MCP exposes tools
5. How gRPC reflection exposes service operations
6. How RBAC controls all actions
7. How workflows prevent random mutation
8. How doctor findings guide diagnosis
9. How convergence is verified
10. How actions are audited

This doc is the intellectual core of Globular.

---

## 1.4 Community Home

People who try the quickstart will have questions.

There must be exactly **one place** to ask.

Choose one:

- GitHub Discussions
- Discord

Do not split attention too early.

Recommended channels if Discord:

```text
#general
#help
#quickstart
#show-and-tell
#ai-operations
#roadmap
```

Month 1 rule:

> Dave answers every serious question personally.

Speed of response is a signal that the project is alive.

Pin a “getting started” thread with:

- quickstart link
- demo video
- known issues
- how to ask for help
- current roadmap

---

## 1.5 Simple Landing Page

Not a sales page.

A map.

`globular.io` should have:

- One-sentence value statement
- AI Operation Plane diagram
- 4-layer diagram
- “Get started in 30 minutes” → quickstart
- Demo video
- Links to:
  - GitHub
  - docs
  - operator course
  - community
  - Medium article

### Suggested hero

> **Infrastructure for AI operators.**
>
> Globular is an open-source platform that makes distributed systems explicit, observable, and safe for human and AI-assisted operations.

---

# Phase 2 — Content Engine

*Content is the primary discovery mechanism. Each post is a permanent beacon.*

## The Content Strategy

Every piece of content targets a **specific person with a specific pain who is searching for something specific**.

Not:

> “Here is Globular.”

Instead:

> “Here is the problem you are already fighting, and here is a new way to understand it.”

Each post must:

1. Name the pain in the title
2. Be honest and concrete
3. Show real code, CLI output, MCP output, diagrams, or logs
4. Link to the quickstart at the end
5. Link to the demo video
6. Invite feedback

### Cadence

Minimum: **2 posts per month**

Quality over volume.

One excellent post beats five thin ones.

---

## Series 1 — AI-Operated Infrastructure

This is the sharpest series.

| # | Title | Target searcher | Core argument |
|---|---|---|---|
| 1 | *Infrastructure for AI Operators* | AI/infra/platform engineers | AI agents need structured state, typed operations, RBAC, and workflows, not random shell access. |
| 2 | *Why AI Can’t Operate Most Platforms Safely* | AI-curious engineers | Logs, dashboards, YAML, and SSH are not enough for safe agency. |
| 3 | *I Let Claude Diagnose a Live Cluster* | AI/MCP community, developers | The MCP/gRPC/RBAC demo. |
| 4 | *The AI Operation Plane* | Platform engineers, architects | Define Globular’s architecture for agentic operations. |
| 5 | *From Incident to Convergence* | SRE/operator | Real failure → AI diagnosis → workflow remediation → verified convergence. |

---

## Series 2 — The Architecture Series

For operators and senior developers.

| # | Title | Target searcher | Core argument |
|---|---|---|---|
| 1 | *Why your deployment model lies to you* | Operator tired of “it works in staging” | Introduces the 4 layers and names why compression creates lies. |
| 2 | *The four layers every distributed system actually has* | Architect / senior dev | Deep dive on Repository → Desired → Installed → Runtime. |
| 3 | *What does “desired state” actually mean?* | DevOps / SRE | Desired ≠ installed ≠ running. Most platforms conflate them. |
| 4 | *How to diagnose a cluster that won’t tell you the truth* | Operator in pain | Walk through a real divergence scenario using Globular doctor. |
| 5 | *Convergence is the real contract* | Distributed systems audience | The platform’s job is to bring reality back to intent. |

---

## Series 3 — The Developer Series

For developers building services.

| # | Title | Target searcher | Core argument |
|---|---|---|
| 1 | *gRPC services in production without Kubernetes* | Developer who loves gRPC, hates K8s complexity | Globular is a strong home for gRPC-native services. |
| 2 | *From source code to running service in one platform* | Developer drowning in glue work | The full lifecycle in one coherent model. |
| 3 | *Building a media pipeline on Globular* | Developer with files, transcoding, background jobs | Concrete scenario from the intro article, actually shown. |
| 4 | *RBAC that doesn’t require a PhD* | Developer who has fought IAM | Globular’s permission model: explicit, readable, gRPC-native. |
| 5 | *Building a real app on Globular* | App developer | Catalog app walkthrough. |

---

## Series 4 — The Startup Series

For founders and small teams.

| # | Title | Target searcher | Core argument |
|---|---|---|
| 1 | *You don’t need a DevOps hire if your platform is explicit* | Startup founder / solo dev | Globular gives production semantics without a platform team. |
| 2 | *Why we built our startup on Globular* | Other startup founders | Case study format: real scenario, real tradeoffs, real outcome. |
| 3 | *The hidden tax of assembling your own infrastructure* | CTO / technical founder | Quantify the cost of glue work in real developer-hours. |

---

## Series 5 — Honest Comparisons

This prevents confusion.

| # | Title | Core argument |
|---|---|
| 1 | *Globular Is Not Kubernetes* | Globular solves a different problem. |
| 2 | *Kubernetes Is a Workload Engine. Globular Is an AI-Readable Infrastructure Substrate.* | Different layers, different goals. |
| 3 | *When You Should Use Kubernetes Instead of Globular* | Honest limitations build trust. |
| 4 | *Bare Metal, AI Agents, and the Missing Operational Layer* | The future architecture argument. |

---

## Distribution per post

Every post follows this distribution playbook:

1. Publish on Medium
2. Cross-post to dev.to
3. Publish or mirror on personal blog / docs site
4. Share on X/Twitter with a hook sentence, not just the title
5. Share on LinkedIn with a more business/platform framing
6. Post to relevant subreddit
7. Post to relevant HN thread if it exists
8. Save strongest posts for Show HN / Launch HN style moments

---

# Phase 3 — The MCP / AI Operation Demo

*This is the single most important asset.*

## Why this is the sharpest hook

The AI tooling space is exploding.

Every developer is paying attention.

Globular has an MCP server and gRPC reflection that lets Claude/Codex inspect and operate a real cluster through secured operations.

The important point is not the tool count.

The important point is:

> **The AI is not only reading logs. It is operating a distributed system through explicit state, typed tools, RBAC, workflows, and verification.**

That is the story.

## Demo title options

- *I gave Claude a live cluster and safe tools to operate it*
- *AI-operated infrastructure with Globular*
- *Claude diagnoses and repairs a real distributed system*
- *Globular: infrastructure that AI agents can understand*
- *Show HN: Globular, open-source infrastructure for AI-operated clusters*

## Demo scenario

A real cluster condition:

> A service is desired on three nodes but only running on one.

Alternative scenarios:

- MinIO topology divergence
- node rejoins with stale installed state
- service installed but inactive
- workflow stuck
- certificate / CA mismatch
- synchronization overload after restart

Claude is given the MCP tools and asked:

> “What’s wrong with this cluster?”

## What the video shows

1. Claude uses cluster health tools
2. Claude sees something is off
3. Claude drills into drift report
4. Claude inspects node full status
5. Claude checks workflow history
6. Claude confirms installed vs desired mismatch
7. Claude explains in plain English:
   - what diverged
   - why it matters
   - what the safe fix is
8. Claude proposes typed gRPC action or workflow remediation
9. Human approves
10. Globular executes the workflow
11. Claude verifies cluster health is green again

## Why this works

It is not Claude generating code.

It is Claude operating a real distributed system using explicit structure.

That is genuinely different and timely.

## Video format

Length: 5–8 minutes.

Structure:

```text
0:00 The problem
0:45 What Globular exposes
1:30 The cluster is degraded
2:30 Claude investigates
4:00 Claude explains root cause
5:00 Safe remediation
6:00 Verification
7:00 Why this matters
```

## Short clips

Create short clips from the full video:

- 30 seconds: Claude finds the drift
- 60 seconds: Claude explains the cluster state
- 90 seconds: AI remediation through RBAC workflow

## Where to post

- YouTube full version
- X/Twitter 90-second clip
- LinkedIn
- HN:
  - “Show HN: I built open-source infrastructure that Claude can operate through MCP/RBAC”
- Anthropic MCP community / showcase
- Reddit r/programming
- Reddit r/selfhosted
- Reddit r/devops
- Reddit r/golang
- Platform engineering communities

## This post should be the HN moment

Do not post it until:

- quickstart works
- README is clear
- demo video is ready
- GitHub repo looks alive
- known limitations are documented

HN traffic without a working first experience is wasted lightning.

---

# Phase 4 — Community Seeding

*Find where the audience lives. Contribute, don’t advertise.*

## Rule

Never post:

> “Check out my project.”

Post something useful:

- an insight
- a comparison
- a real failure
- a diagram
- a lesson learned
- a working demo

Let the project emerge naturally.

---

## Reddit

| Subreddit | Audience | What to post |
|---|---|---|
| r/selfhosted | Operators tired of K8s for small workloads | The 4-layer article, quickstart link, AI-operated self-hosting angle |
| r/devops | DevOps engineers | Architecture series, drift/convergence lessons |
| r/kubernetes | K8s users frustrated with complexity | Honest comparison, not attack |
| r/programming | General developers | MCP/AI operation demo |
| r/golang | Go developers | Service implementation pattern, gRPC architecture |
| r/LocalLLaMA | AI builders | Safe tools for real agentic operations |
| r/MachineLearning | AI/infra builders | AI agents operating real infra safely |
| r/startups | Founders | Production semantics without DevOps hire |

---

## Hacker News

HN is the highest-leverage single channel for technical projects.

One good post can drive thousands of stars.

One bad post can burn attention.

### Show HN draft

```text
Show HN: Globular — open-source infrastructure for AI-operated clusters

Hi HN,

I’ve been building Globular, an open-source platform for deploying and operating distributed services on bare metal.

The core idea is that infrastructure needs to become explicit enough for both humans and AI agents to reason about it.

Globular separates repository artifacts, desired state, installed state, runtime health, workflow history, and doctor findings. It exposes operations through CLI, MCP, and gRPC services protected by RBAC.

The most interesting part: Claude and Codex have been helping me test and debug the platform, not just by writing code, but by reasoning about cluster state, synchronization overload, sequence bugs, stale state, and remediation flows.

Demo video:
[link]

Quickstart:
[link]

GitHub:
[link]

I’m especially interested in feedback from people building platform engineering, self-hosted, bare-metal, or AI-agent infrastructure.
```

### Timing

Post on Tuesday or Wednesday morning US time.

Only post when:

- quickstart is solid
- README is clear
- demo works
- limitations are honest
- you are available to answer comments

---

## Discord / Slack communities

| Community | What to share |
|---|---|
| Platform engineering communities | Architecture series and AI Operation Plane |
| gRPC community | Globular as a home for gRPC services |
| ScyllaDB community | Globular as real ScyllaDB production usage |
| MinIO community | Distributed MinIO with Globular |
| MCP / Anthropic community | The AI operation demo |
| Self-hosted communities | Operator story and quickstart |

---

## X / Twitter presence

Build a presence around ideas, not announcements.

Possible threads:

- “The 4 layers every distributed system actually has”
- “What I learned building an MCP server for cluster operations”
- “Why AI agents need typed infrastructure operations, not SSH”
- “Why gRPC services deserve a better home than glue scripts”
- “How Claude helped debug real synchronization overload in Globular”

Regularly share:

- diagrams
- screenshots
- command output
- failure/recovery stories
- lessons learned from real cluster behavior

---

# Phase 5 — The Operator Course as a Funnel

The **Globular Operator Course** is a rare and serious asset.

Most open-source projects have a README.

Globular can have a full learning path.

This signals:

- The project has depth
- The maintainer is serious
- There is a learning path, not just a repo
- The ideas are bigger than the code

## Positioning

New title idea:

> **Mastering AI-Readable Distributed Systems with Globular**

Or:

> **Mastering Explicit Distributed Systems**

## Actions

- [ ] Publish the course on a dedicated readable URL
  - GitBook
  - docs site
  - Docusaurus
- [ ] Link it from README
- [ ] Link it from landing page
- [ ] Write a post:
  - “I wrote a full course on building explicit distributed systems”
- [ ] Make it the bridge between:
  - “I read the article”
  - and
  - “I want to understand this deeply”
- [ ] List it on:
  - free programming resources lists
  - awesome-selfhosted
  - awesome-distributed-systems
- [ ] Consider a recorded YouTube playlist

---

# Phase 6 — Awesome Lists and Directories

*Permanent, passive discovery.*

Submit Globular to every relevant list.

These are permanent inbound links and discovery points.

| List | Relevant because |
|---|---|
| awesome-selfhosted | Operators, self-hosters |
| awesome-distributed-systems | Architects |
| awesome-grpc | gRPC developers |
| awesome-mcp-servers | AI/MCP community |
| awesome-go | Go developers |
| Product Hunt | General tech audience |
| AlternativeTo | “Kubernetes alternative” searches |
| Hacker News Who’s Building threads | Visibility |

## Positioning in directories

Do not only say:

> “Kubernetes alternative.”

Say:

> **AI-operated infrastructure platform for distributed services.**

Or:

> **Open-source platform for AI-readable bare-metal clusters.**

---

# Phase 7 — Partnerships and Integrations

## Technology partners

Communities that benefit from Globular’s success.

| Partner / ecosystem | Why | What to do |
|---|---|---|
| Anthropic / Claude / MCP ecosystem | Globular is a serious MCP use case | Submit to MCP showcase, reach out to MCP team |
| ScyllaDB | Globular is a real ScyllaDB user | Offer a case study / joint blog post |
| MinIO | Distributed object storage story | Joint content, mention in showcase |
| etcd / CNCF | Globular is an interesting control-plane use case | CNCF blog post, KubeCon lightning talk |
| gRPC ecosystem | Globular is gRPC-native | Write about gRPC-native operations |
| Platform engineering communities | Globular speaks directly to platform pain | Architecture posts and talks |

## Outreach angle

- “We built an MCP server that lets Claude operate a distributed cluster safely.”
- “We use Scylla/MinIO/etcd as part of an AI-readable infrastructure platform.”
- “We want to write a technical case study.”
- “We are exploring what infrastructure needs to expose for AI agents to operate safely.”

---

## Conference and talk opportunities

| Venue | Format | Topic |
|---|---|---|
| KubeCon / CloudNativeCon | Lightning talk or full talk | “Explicit architecture for AI-operated infrastructure” |
| GopherCon | Talk | “Building an AI-operable distributed platform in Go” |
| SREcon | Talk | “The four truth layers: making distributed systems diagnosable” |
| Local meetups | Short talk | AI-operated cluster demo |
| Platform engineering meetups | Talk | “Why readable systems are the future of platform engineering” |

---

# Phase 8 — Trust and Credibility

Infrastructure credibility is slow-cooked metal.

People do not trust cluster software because it sounds smart.

They trust it because it survives boring, repeatable tests.

## Credibility assets

Create public proof:

- [ ] Repeatable Day-0 install test
- [ ] Repeatable Day-1 join test
- [ ] Failure/recovery demo
- [ ] MinIO topology validation
- [ ] PKI cleanup and CA recovery test
- [ ] Workflow failure/retry test
- [ ] Backup/restore test
- [ ] Release upgrade test
- [ ] Security model doc
- [ ] Known limitations doc
- [ ] Public roadmap
- [ ] Public test matrix

---

## Security posture

Globular’s AI story only works if safety is serious.

Required docs:

```text
SECURITY.md
docs/security/rbac-model.md
docs/security/agent-operation-safety.md
docs/security/threat-model.md
docs/security/audit-log.md
```

Key principles:

- No AI shell by default
- Typed operations only
- RBAC controls every operation
- Mutating operations require permission
- Destructive operations require explicit human approval
- Audit every agent-triggered action
- Prefer workflow remediation over ad-hoc mutation
- Always verify convergence

---

## Command / tool safety classification

Every CLI/MCP/gRPC operation should eventually have metadata.

Example:

```json
{
  "name": "cluster.get_health",
  "category": "cluster",
  "risk": "read-only",
  "requires_auth": true,
  "rbac_action": "cluster.read",
  "mutates_state": false,
  "supports_dry_run": false,
  "output": "json",
  "safe_for_ai": true
}
```

Risk levels:

| Risk | Meaning |
|---|---|
| `read-only` | Inspects state only |
| `diagnostic` | Safe but may be expensive |
| `mutating` | Changes desired or runtime state |
| `cluster-changing` | Affects multiple nodes or cluster intent |
| `destructive` | Delete, wipe, reset, revoke, remove |

This turns the tool surface into an AI-safe cockpit.

---

# Phase 9 — Monetization Path

Globular does not need to become Linux before it helps Dave make a living.

The first money likely comes from services around the platform.

## Offer 1: Globular Infrastructure Audit

For small teams, homelabs, startups, and self-hosters.

Price idea: `$300-$800`

Includes:

- Review current infra
- Identify deployment/ops pain
- Propose Globular fit or non-fit
- Produce short migration/architecture report

---

## Offer 2: Small Cluster Install

Price idea: `$1,000-$3,000`

Includes:

- Install Globular
- Configure basic cluster
- Deploy first app/service
- Configure monitoring/doctor
- Basic AI operation setup
- Handoff documentation

---

## Offer 3: Custom App on Globular

Price idea: `$3,000-$10,000`

Includes:

- Build gRPC service
- RBAC integration
- Package/deploy through Globular
- Basic frontend/admin
- Monitoring and upgrade path

---

## Offer 4: Monthly Support

Price idea: `$200-$1,000/month`

Includes:

- Update support
- Debugging
- Backup checks
- AI operation tuning
- Priority fixes

---

# Milestones and Tracking

## Star milestones

| Stars | What it means | What to do |
|---|---|---|
| 50 | First curiosity | Ask users what attracted them |
| 100 | The project is real | Announce publicly, post roadmap |
| 250 | Early adopter community forming | Personal outreach to each serious user |
| 500 | Credibility threshold for HN | Time for Show HN if not done already |
| 1,000 | Legitimacy signal | Press outreach, case studies, conference submissions |
| 2,500 | Community has momentum | Focus shifts to contributor onboarding |

## Operational milestones

| Milestone | Meaning | Action |
|---|---|---|
| First external quickstart success | More important than stars | Interview the user |
| First outside deployment | Major credibility | Write case study |
| First paid audit/install | Monetization proof | Productize offer |
| First contributor | Community proof | Improve onboarding |
| First AI operation demo replication | Thesis proof | Write technical breakdown |

---

## Monthly content targets

| Month | Content | Community | Technical |
|---|---|---|---|
| 1 | 1 article: Infrastructure for AI Operators | Set up Discord/Discussions | Quickstart validated |
| 2 | 2 articles + MCP demo video | First Reddit posts | README polished |
| 3 | 2 articles | HN Show HN post | Awesome lists submitted |
| 4 | 2 articles | First external contributor | Operator course published |
| 5+ | 2 articles/month | Conference submissions | Partner outreach |

---

# 90-Day Execution Plan

The next 90 days should be ruthless.

No feature wandering.

The goal is:

> **Turn Globular from a private battleship into a visible proof of future infrastructure.**

---

## Month 1 — Make it Believable

Deliverables:

- [ ] Rewrite README around AI-operated infrastructure
- [ ] Add AI Operation Plane diagram
- [ ] Add 4-layer state diagram
- [ ] Validate quickstart
- [ ] Publish architecture docs
- [ ] Create GitHub Discussions or Discord
- [ ] Add SECURITY.md and CONTRIBUTING.md
- [ ] Prepare Catalog app or echo service demo
- [ ] Write “Infrastructure for AI Operators” article

Success criteria:

- New user can understand the project in 5 minutes
- New user can run quickstart in under 30 minutes
- Repo looks alive and serious

---

## Month 2 — Make it Visible

Deliverables:

- [ ] Record MCP/AI cluster demo
- [ ] Publish demo video
- [ ] Publish 2 articles
- [ ] Share in AI/MCP communities
- [ ] Share in self-hosted/platform communities
- [ ] Submit to awesome lists
- [ ] Start collecting feedback

Success criteria:

- People understand the AI operation angle
- First strangers try the quickstart
- First GitHub issues/discussions appear

---

## Month 3 — Make it Sellable

Deliverables:

- [ ] Publish Catalog app demo
- [ ] Publish failure/recovery demo
- [ ] Publish service offering page
- [ ] Post Show HN
- [ ] Reach out to 20 relevant people/communities
- [ ] Offer first Globular audit/install package
- [ ] Publish known limitations

Success criteria:

- First consulting lead
- First external user/tester
- First serious technical feedback
- First contributor or potential contributor

---

# The Manifesto as a Permanent Asset

A manifesto belongs in the world.

Possible title:

> **Infrastructure Must Become Readable to AI**

Alternative titles:

- *The Missing Layer: Why Kubernetes Is a Workload Engine, Not an AI-Readable Infrastructure Substrate*
- *A Manifesto for AI-Operated Infrastructure*
- *The Future of Platform Engineering Is Readable Systems*
- *Why Infrastructure Needs an Operation Plane for AI Agents*

This is a polarizing, opinion-led piece.

It should position Globular not merely as a product, but as an answer to a named gap in the ecosystem.

---

# What We Are Not Doing

- Not claiming Globular replaces Kubernetes everywhere
- Not competing with Kubernetes on its own terms
- Not chasing hype without working demos
- Not hiding limitations
- Not giving AI unsafe shell access as the main story
- Not adding 40 features before the first public proof
- Not trying to explain the entire universe before showing value
- Not optimizing only for GitHub stars
- Not posting vague announcements
- Not building community faster than product reliability

---

# The Single Most Important Thing

If only one thing gets done from this plan, it is:

# The AI-Operated Cluster Demo

A real Globular cluster.

A real failure.

A real AI agent.

Real MCP/gRPC/RBAC operations.

A real diagnosis.

A safe workflow.

Verified convergence.

That demo is the spearhead.

Everything else exists to support it.

---

# Final Message

Globular should be presented as more than a platform.

It is a thesis:

> **Infrastructure must become explicit enough for AI agents to operate safely.**

Globular is the working experiment that proves this thesis.

The adoption plan is therefore not simply marketing.

It is a proof campaign.

First prove the future.

Then invite people to run it.
