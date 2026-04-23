# Globular Adoption Plan — V1

> **Mission**: Make Globular the platform of choice for developers, operators, and startups who refuse to accept that distributed systems should be opaque, fragile, or impossible to reason about.
>
> **North star metric**: GitHub stars. Everything in this plan serves that metric either directly (visibility) or indirectly (credibility, trust, community).

---

## The Core Challenge

Globular is technically superior for its use case, but it has the hardest adoption problem in software: it requires a **mental model shift** before the value is visible. You cannot demo it in 30 seconds. The people who most need it do not yet have the vocabulary to search for it.

The plan attacks this from two directions simultaneously:
1. **Build the audience** — get in front of people who have the pain
2. **Lower the barrier to belief** — make the value tangible and fast

---

## Three Target Audiences

| Audience | The pain they feel right now | What triggers adoption |
|---|---|---|
| **Developer** — building microservices, gRPC systems, APIs | "I keep reinventing auth, certs, routing, versioning" | "I can stop assembling this myself" |
| **Operator** — small team, no dedicated infra person | "I can't tell what the cluster thinks vs what's real" | "I can finally reason about state" |
| **Startup** — 0→1, no DevOps hire, needs production semantics early | "Kubernetes is overkill but I need real cluster behavior" | "This gives me production on day one" |

Each audience has a different entry point, a different first article, a different demo. The plan serves all three but speaks to each in their own language.

---

## Phase 1 — Foundation (Month 1)
*Nothing else works without this. This is the floor.*

### 1.1 GitHub Repository Polish

The GitHub page is the universal landing page. Every article, every tweet, every HN post ends here. It must do the work of conversion.

**README rewrite checklist:**
- [ ] Lead with ONE sentence that names the pain, not the solution: *"Most software projects begin with an application idea and end with an infrastructure problem."*
- [ ] Show the 4-layer diagram immediately — it is the most differentiating idea in the project
- [ ] Show ONE real CLI example: artifact → desired → installed → running
- [ ] Show ONE real `globular` command that does something impossible on other platforms in that few lines
- [ ] Add badges: build status, license, latest release
- [ ] Add a "Quick install" block — copy-paste, one command, first cluster running
- [ ] Link to: quickstart, operator course, docs, Discord

**GitHub repository hygiene:**
- [ ] Topics/tags: `distributed-systems`, `grpc`, `kubernetes-alternative`, `self-hosted`, `devops`, `ai`, `mcp`, `cluster`, `microservices`, `platform-engineering`
- [ ] Description field: short, searchable, accurate
- [ ] Social preview image: the 4-layer diagram with the Globular name
- [ ] Releases: every version tagged, with a changelog
- [ ] Issues: good first issue labels so contributors can enter
- [ ] CONTRIBUTING.md: clear path for external contributors

### 1.2 The Quickstart

*The most important technical asset for adoption. If this is broken, nothing else matters.*

**Target experience**: A developer or operator with a Linux VM can go from zero to a running single-node Globular cluster with at least one service deployed in **under 30 minutes**. The experience must feel like magic, not like a checklist.

**Quickstart must cover:**
1. Bootstrap a single node (5 minutes)
2. Deploy the echo service (2 minutes)
3. See the 4 layers in the CLI — `globular status` showing all truth layers
4. Add a second node (join workflow)
5. Deploy an update — see the artifact land, desired flip, installed confirm, runtime health green

**Where it lives**: `globular-quickstart` repo (already exists — polish and validate it)

**Validation rule**: A person who has never seen Globular must be able to complete it with zero help. Test this with a real stranger.

### 1.3 Community Home

People who try the quickstart will have questions. There must be exactly **one place** to ask.

- [ ] Open GitHub Discussions on the main repo
- [ ] Or create a Discord server with channels: `#general`, `#help`, `#show-and-tell`, `#roadmap`
- [ ] Dave answers every question personally in month 1 — speed of response is the signal that the project is alive
- [ ] Pin a "getting started" thread with the quickstart link

### 1.4 Simple Landing Page

Not a sales page. A map.

`globular.io` should have:
- The one-sentence value statement
- The 4-layer diagram
- "Get started in 30 minutes" → quickstart
- Links to: GitHub, docs, operator course, Discord
- The Medium article as "Learn more"

---

## Phase 2 — Content Engine (Month 2–3)
*Content is the primary discovery mechanism. Each post is a permanent beacon.*

### The Content Strategy

Every piece of content targets a **specific person with a specific pain who is searching for something specific**. Not "here is Globular." Instead: "here is the problem you are Googling, and here is the answer."

Each post must:
1. Name the pain in the title
2. Be honest and concrete — show real code, real CLI, real output
3. Link to the quickstart at the end
4. Be cross-posted: Medium → dev.to → personal blog

### Content Calendar

#### Series 1: The Architecture Series (for Operators and Senior Developers)

| # | Title | Target searcher | Core argument |
|---|---|---|---|
| 1 | *Why your deployment model lies to you* | Operator tired of "it works in staging" | Introduces the 4 layers, names why compression creates lies |
| 2 | *The four layers every distributed system actually has* | Architect / senior dev | Deep dive on Repository→Desired→Installed→Runtime |
| 3 | *What does "desired state" actually mean?* | DevOps / SRE | Desired ≠ installed ≠ running — most platforms conflate them |
| 4 | *How to diagnose a cluster that won't tell you the truth* | Operator in pain | Walk through a real divergence scenario using Globular's doctor |

#### Series 2: The Developer Series (for Developers building services)

| # | Title | Target searcher | Core argument |
|---|---|---|---|
| 5 | *gRPC services in production without Kubernetes* | Developer who loves gRPC, hates K8s complexity | Globular is the best home for gRPC-native services |
| 6 | *From source code to running service in one platform* | Developer drowning in glue work | The full lifecycle in one coherent model |
| 7 | *Building a media pipeline on Globular* | Developer with files, transcoding, background jobs | The concrete scenario from the intro article — actually shown |
| 8 | *RBAC that doesn't require a PhD* | Developer who's fought IAM | Globular's permission model — explicit, readable, gRPC-native |

#### Series 3: The AI Series (the sharpest hook right now)

| # | Title | Target searcher | Core argument |
|---|---|---|---|
| 9 | *I gave Claude 129 tools and pointed it at a live cluster* | AI/ML community, curious developers | The MCP demo — the most shareable thing in the project |
| 10 | *Why AI can't operate most platforms (and how to fix it)* | AI-curious engineer | Explicit architecture is the prerequisite for AI operations |
| 11 | *From incident to resolution: AI + explicit state* | SRE / operator | Walk through a real cluster incident diagnosed and resolved by the AI executor |
| 12 | *The future of platform engineering is readable systems* | Platform engineers, architects | Big picture — explicit architecture as the next wave |

#### Series 4: The Startup Series (for founders and small teams)

| # | Title | Target searcher | Core argument |
|---|---|---|---|
| 13 | *You don't need a DevOps hire if your platform is explicit* | Startup founder / solo dev | Globular gives production semantics without a platform team |
| 14 | *Why we built our startup on Globular* | Other startup founders | Case study format — real scenario, real tradeoffs, real outcome |
| 15 | *The hidden tax of assembling your own infrastructure* | CTO / technical founder | Quantify the cost of glue work in real developer-hours |

### Distribution per post

Every post follows this distribution playbook:
1. Publish on Medium
2. Cross-post to dev.to (same day)
3. Share on Twitter/X with a hook sentence, not the title
4. Share on LinkedIn (longer, more business framing)
5. Post to relevant subreddit (see community section)
6. Post to relevant HN thread if it exists, or save for Show HN

**Cadence**: Minimum 2 posts per month. Quality over volume — one great post beats five mediocre ones.

---

## Phase 3 — The MCP Demo (The Single Most Important Asset)
*This is the moment that can change the trajectory overnight.*

### Why this is the sharpest hook

The AI tooling space is exploding right now. Every developer is paying attention. Globular has a **129-tool MCP server** that lets Claude actually operate a real cluster — not just read logs, but understand topology, compare desired vs installed state, diagnose drift, plan operations, and propose typed actions.

Nobody else has this. Not Kubernetes. Not Nomad. Not any platform.

### The demo video (5–8 minutes)

**Scenario**: A real cluster condition — a service is running on one node but the desired state says it should be on three. Claude is given the MCP tools and asked: "What's wrong with this cluster?"

**What the video shows:**
1. Claude uses `cluster_get_health` — sees something is off
2. Drills in with `cluster_get_drift_report` — finds the divergence
3. Uses `cluster_get_node_full_status` on each node — confirms installed vs desired mismatch
4. Explains in plain English exactly what diverged, why it matters, and what the fix is
5. Proposes the typed gRPC action — and with approval, executes it
6. Verifies: `cluster_get_health` is green again

**Why this works**: It is not Claude generating code. It is Claude operating a real distributed system using explicit structure. That is a genuinely new thing.

**Where to post:**
- YouTube (full version with narration)
- Twitter/X (90-second clip, the diagnosis moment)
- LinkedIn
- HN: "Show HN: I built a 129-tool MCP server that lets Claude operate a live cluster"
- Anthropic's community / MCP showcase

**This post should be the HN moment.**

---

## Phase 4 — Community Seeding (Month 2–4)
*Find where the audience lives. Contribute, don't advertise.*

### Reddit

| Subreddit | Audience | What to post |
|---|---|---|
| r/selfhosted | Operators tired of K8s for small workloads | The 4-layer article, quickstart link |
| r/devops | DevOps engineers | The architecture series posts |
| r/kubernetes | K8s users frustrated with complexity | "Globular as a K8s alternative for smaller teams" — honest comparison |
| r/programming | General developers | The MCP demo post |
| r/golang | Go developers | The codebase is Go — show the service implementation pattern |
| r/MachineLearning / r/LocalLLaMA | AI builders | The MCP/AI series |
| r/startups | Founders | The startup series |

**Rule**: Never post "check out my project." Post something useful — an insight, a comparison, a real answer — and let the project emerge naturally.

### Hacker News

HN is the highest-leverage single channel for technical projects. One good post can drive thousands of stars overnight.

**The Show HN post** — draft:

> Show HN: Globular — open-source platform with explicit 4-layer architecture and 129-tool MCP server for AI-operated clusters
>
> We've been building Globular for [X], an open-source platform for deploying and operating distributed services. The core idea is that most platforms hide too much: desired state, installed state, and runtime health get compressed into one blurry "it's running" — which makes diagnosis folklore instead of engineering.
>
> Globular keeps these as explicit, independent layers. That makes the system diagnosable by humans — and, it turns out, by AI. We built a 129-tool MCP server on top of it that lets Claude actually operate the cluster: compare desired vs installed, explain drift, propose typed actions.
>
> Demo video: [link]
> Quickstart (single node in 30 min): [link]
> GitHub: [link]

**Timing**: Post on a Tuesday or Wednesday morning US time. Only post when the quickstart is solid — HN traffic without a working first experience is wasted.

### Discord / Slack communities

| Community | Where | What |
|---|---|---|
| Platformers | Slack / Discord — platform engineering communities | Share the architecture series |
| gRPC community | GitHub discussions, Discord | Globular is the best home for gRPC services |
| ScyllaDB community | Discord | Globular is a real ScyllaDB production user |
| MinIO community | Slack | Same — real distributed MinIO usage |
| MCP / Anthropic community | Discord | The 129-tool MCP server story |
| Self-hosted communities | Various Discord servers | The operator story |

### Twitter/X presence

Build a presence around the ideas, not just announcements:

- Thread: "The 4 layers every distributed system actually has (most platforms hide 3 of them)"
- Thread: "What I learned building a 129-tool MCP server for cluster operations"
- Thread: "Why gRPC services deserve a better home than Kubernetes"
- Regular: share interesting observations from real cluster behavior
- Engage with: platform engineering conversations, AI tooling discussions, self-hosting posts

---

## Phase 5 — The Operator Course as a Funnel (Month 3+)

The **Globular Operator Course** ("Mastering Explicit Distributed Systems") is a rare and serious asset. Most open-source projects have a README. We have a 4-act, 13-lecture course.

This signals:
- The project has depth
- The maintainer is serious
- There is a learning path, not just a repo

**Actions:**
- [ ] Publish the course on a dedicated readable URL (GitBook, or docs site)
- [ ] Write a post: "I wrote a full course on building explicit distributed systems"
- [ ] Make it the bridge between "I read the article" and "I want to understand this deeply"
- [ ] List it on: free programming resources lists, awesome-selfhosted, awesome-distributed-systems
- [ ] Consider: recorded video version of the course (YouTube playlist)

---

## Phase 6 — Awesome Lists and Directories (Month 2+)
*Permanent, passive discovery.*

Submit Globular to every relevant list. These are permanent inbound links and discovery points.

| List | URL | Relevant because |
|---|---|---|
| awesome-selfhosted | github.com/awesome-selfhosted | Operators, self-hosters |
| awesome-distributed-systems | github.com/theanalyst/awesome-distributed-systems | Architects |
| awesome-grpc | github.com/grpc-ecosystem/awesome-grpc | gRPC developers |
| awesome-mcp-servers | github.com/punkpeye/awesome-mcp-servers | AI/MCP community |
| awesome-go | github.com/avelino/awesome-go | Go developers |
| Product Hunt | producthunt.com | General tech audience |
| AlternativeTo | alternativeto.net | "Kubernetes alternative" searches |
| Hacker News Who's Hiring / Who's Building | HN monthly threads | Visibility |

---

## Phase 7 — Partnerships and Integrations (Month 3+)

### Technology partners (communities that benefit from Globular's success)

| Partner | Why | What to do |
|---|---|---|
| ScyllaDB | Globular is a real production user and showcase | Reach out, offer a case study / joint blog post |
| MinIO | Same — distributed MinIO with Globular is a real story | Joint content, mention in their showcase |
| Anthropic / Claude / MCP ecosystem | 129-tool MCP server is a flagship use case | Submit to MCP showcase, reach out to the MCP team |
| etcd / CNCF | Globular's architecture is an interesting etcd use case | CNCF blog post, KubeCon lightning talk |

### Conference and talk opportunities

| Venue | Format | Topic |
|---|---|---|
| KubeCon / CloudNativeCon | Lightning talk or full talk | "Explicit architecture as a Kubernetes alternative for smaller clusters" |
| GopherCon | Talk | "Building a distributed platform in Go" |
| SREcon | Talk | "The 4 truth layers: making distributed systems diagnosable" |
| Local meetups | Short talk | Use the "realistic comparison" scenario from the article |

---

## Milestones and Tracking

### Star milestones (and what to do at each)

| Stars | What it means | What to do |
|---|---|---|
| 100 | The project is real | Announce publicly, post on all social channels |
| 250 | Early adopter community forming | Personal outreach to each one — who are they, what are they building? |
| 500 | Credibility threshold for HN | Time for the Show HN post if not done already |
| 1,000 | Legitimacy signal | Press outreach, case study posts, conference submissions |
| 2,500 | Community has its own momentum | Focus shifts to contributor onboarding, not just user acquisition |

### Monthly content targets

| Month | Content | Community | Technical |
|---|---|---|---|
| 1 | 1 article (intro done) | Set up Discord/Discussions | Quickstart validated |
| 2 | 2 articles + MCP demo video | First Reddit posts | README polished |
| 3 | 2 articles | HN Show HN post | Awesome lists submitted |
| 4 | 2 articles | First external contributor | Operator course published |
| 5+ | 2 articles/month | Conference submission | Partner outreach |

---

## The Manifesto as a Permanent Asset

"A Manifesto for the Cloud Substrate" is a foundational document that belongs in the world. Consider:

- Publishing it as a standalone post: *"The missing layer: why Kubernetes is a workload engine, not a cluster substrate"*
- This is a polarizing, opinion-led piece — exactly what gets shared on HN and Twitter
- It positions Globular not as a product but as an answer to a named gap in the ecosystem

---

## What We Are NOT Doing

- Not chasing vanity metrics (Twitter followers, LinkedIn engagement) at the expense of depth
- Not posting vague announcements — every post is concrete, honest, and shows real things working
- Not competing with Kubernetes on its own terms — Globular is for a different use case and is honest about that
- Not building a community that outpaces the product — stars and users must be able to actually run the thing

---

## The Single Most Important Thing

If only one thing gets done from this plan, it is the **MCP demo video**.

It is the only thing that cannot exist on any other platform. It is timely (AI tooling is the hottest topic in tech right now). It is visual. It is concrete. It shows the deepest and most differentiating idea in Globular in 5 minutes.

Everything else in this plan builds on that foundation.

---

*Plan authored: 2026-04-23. Review and update monthly.*
*Owner: Dave Courtois + Claude*
