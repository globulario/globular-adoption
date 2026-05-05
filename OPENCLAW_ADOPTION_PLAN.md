# Globular × OpenClaw — Adoption Operating Plan

> **Role of OpenClaw**: Adoption operator assistant. It drafts, structures, schedules, and tracks. Humans approve everything before it is public.
>
> **Core rule**: OpenClaw drafts. Human approves. Nothing auto-posts.

---

## The Central Idea

Engineering progress happens continuously on Globular.

Most of it never becomes public signal.

OpenClaw is the conversion layer:

```
Engineering event
      ↓
OpenClaw agent
      ↓
Structured drafts (thread / post / article / script / FAQ)
      ↓
Human review + edit
      ↓
Approved content
      ↓
Published + tracked
      ↓
Feedback summary → next week's inputs
```

Every real technical event — a release, a fixed bug, an added invariant, a working demo — is raw material.

OpenClaw converts raw material into public proof.

---

## Positioning to Enforce in All Content

Every agent and every draft must stay inside these rails.

### What Globular is

- Open-source, AI-operable cluster substrate
- Layer-0 infrastructure (before workloads: identity, membership, certs, packages, state, health)
- The operational awareness layer underneath everything else
- A platform that makes infrastructure understandable enough for humans and AI agents to operate safely

### The two-sentence positioning

> "AWS sells managed infrastructure.
> Globular makes infrastructure manageable."

Alternative:

> "Globular is the open machine that lets your own infrastructure behave like a cloud."

### What Globular is not

- Not a Kubernetes replacement (never say this)
- Not an AWS/Azure competitor (never say this)
- Not a monitoring tool
- Not a deployment pipeline

### Safe framing for Kubernetes questions

> "Globular can complement Kubernetes by giving it operational awareness. Kubernetes runs workloads. Globular can explain the substrate under them."

### The four truth layers (always use this framing)

```
Artifact → Desired → Installed → Runtime
```

Never collapse these. Drift between layers is the story.

---

## The Six Content Pillars

Every piece of content maps to one or more pillars.

| Pillar | Core message | Example angle |
|---|---|---|
| **AI-operable infrastructure** | AI cannot operate fog. It needs explicit truth. | "Claude diagnosed a real cluster drift — here is what it saw." |
| **Layer-0 substrate** | Before workloads, there is identity, membership, storage, certs, packages. | "Kubernetes runs workloads. Globular explains what is under them." |
| **Operational awareness** | Globular does not just restart things. It explains what mismatch exists. | "Artifact, Desired, Installed, Runtime: where is the drift?" |
| **Sovereign / private cloud** | Keep your machines. Make them behave like a cloud. | "Cloud power without cloud captivity." |
| **Build in public** | Share hard failures honestly. Show what invariant was added. | "What broke this week and what invariant fixed it." |
| **Killer demo** | Break something. Show Globular detecting it. Show the repair. | "Kill a service. Watch Globular explain the mismatch." |

---

## Six OpenClaw Agents

---

### Agent 1: Globular Release Explainer

**Trigger**: A new release, changelog entry, or architecture milestone.

**Inputs**:

```
- GitHub release notes or commit summary
- Changelog entry (raw)
- Architecture notes (optional)
- One-sentence description of what changed and why
```

**Outputs** (drafts, human approves each):

| Output | Format | Audience |
|---|---|---|
| Technical summary | 3–5 bullet points | Engineers |
| Simple explanation | 2–3 paragraphs, no jargon | Non-experts |
| X/Twitter thread | 5–8 tweets | Developers, infra builders |
| LinkedIn post | 150–300 words | Platform engineers, CTOs |
| Mastodon post | Single toot, 450 chars | FOSS/homelab community |
| Reddit/HN explanation | Plain-text paragraph, HN style | Technically skeptical audience |
| Medium article outline | H1 + 5 section headers + bullet notes | Long-form readers |
| README changelog paragraph | Markdown, matches Globular style | Contributors, evaluators |
| Demo script seed | 3–4 sentences describing what to show | Video/demo producer |
| FAQ item | Q + short answer + detailed answer | Docs team |
| One-sentence positioning line | Single sentence | All channels |

**Example input**:

> "Globular now has controller-owned installed-state commit with a durable outbox. Install workflows can no longer return success before authoritative state is committed."

**Example output — simple explanation**:

> "Distributed systems often lie by accident. A local install succeeds, but cluster truth never catches up. Globular now refuses to say 'done' until authoritative state is committed. No false positives. No silent drift."

**Example output — X/Twitter thread**:

```
1/ Distributed systems lie by accident.

A node installs a service. Returns success.
But cluster state never updates.
Now you have a ghost — installed but invisible.

2/ Globular just closed this gap.

Install workflows can no longer return success
before authoritative state is committed.

No commit = no success. Hard rule.

3/ Why does this matter?

If cluster truth is wrong, the doctor is wrong.
If the doctor is wrong, the AI diagnosis is wrong.
If the AI diagnosis is wrong, the remediation is wrong.

Everything downstream depends on committed truth.

4/ This is what layer-0 infrastructure means.

Not "restart the thing."
Explain where the mismatch is.
Refuse to lie about it.

5/ Artifact → Desired → Installed → Runtime

That is the four-layer model Globular enforces.

Every layer must be honest.
Every transition must be committed.

6/ Release note: [link]
Docs: [link]
Quickstart: [link]
```

---

### Agent 2: Globular Social Drafting Agent

**Trigger**: Topic, audience, and tone provided by human.

**Inputs**:

```
- Topic (e.g., "why explicit state matters for AI agents")
- Target audience (e.g., "platform engineers", "AI builders", "homelab community")
- Desired tone (e.g., "technical", "founder", "accessible", "provocative")
- Content pillar (optional)
- Any recent event to anchor to (optional)
```

**Outputs**:

| Output | Notes |
|---|---|
| 5 short posts (X/Mastodon) | Different angles, same topic |
| 1 technical thread (6–8 posts) | Deeper argument with code/diagrams |
| 1 founder build-in-public post | Personal, honest, no hype |
| 1 simple analogy post | For non-expert audience |
| 1 provocative/opinion post | For engagement, clearly marked as opinion |

**Guardrails the agent enforces**:

- No fake benchmark claims
- No "replaces Kubernetes" framing
- No "coming soon" without a concrete date
- No implied adoption that does not exist
- Every claim anchored to a release, doc, or demo

---

### Agent 3: Globular Community Monitor

**Trigger**: Weekly, or on demand before a launch event.

**Inputs**:

Manually provided search terms or collected from connected sources:

```
- kubernetes complexity
- self-hosted cloud
- private cloud
- AI infrastructure
- platform engineering
- homelab cluster
- edge infrastructure
- sovereign cloud
- OpenStack alternative
- K3s ops
- kubernetes operations
- cluster management
- bare metal cluster
- MCP server infrastructure
- AI agent infrastructure
```

**Outputs**:

| Output | Notes |
|---|---|
| Relevant discussion list | Title, URL, summary, audience size estimate |
| Reply priority score | High / Medium / Low |
| Spam risk warning | "This reply will look promotional" |
| Suggested reply drafts | See Agent 4 |
| Weekly engagement summary | Which communities are most active this week |
| Trending pain points | What frustrations recur across threads |
| Demo ideas from audience | What questions suggest a useful demo |
| Docs gaps identified | What confusion suggests a missing doc |

**Engagement rule**: Only reply where you have something genuinely useful to say. Do not reply to announce Globular. Reply to add clarity, share an insight, or answer a technical question — then let the project emerge naturally.

---

### Agent 4: Globular Reply Assistant

**Trigger**: A comment, question, or GitHub issue is passed to the agent.

**Inputs**:

```
- Original comment or question (full text)
- Source (GitHub / Reddit / HN / X / LinkedIn / Discord)
- Context (what article or post triggered this)
- Tone preference (optional)
```

**Outputs**:

| Output | Notes |
|---|---|
| Short reply | 1–3 sentences |
| Technical reply | Detailed, code-friendly |
| Friendly reply | Accessible, no jargon |
| Link suggestion | Best doc, demo, or article to include |
| Promotional warning | "This draft sounds like an ad — revise" |
| Escalation flag | "This needs a human decision, not a draft" |

**Example input**:

> "Why would I use Globular instead of just using Kubernetes with ArgoCD and Prometheus?"

**Example output — technical reply**:

> "Good question. Globular is not competing with that stack — it operates at a different layer. Kubernetes manages workload scheduling. ArgoCD handles desired state for manifests. Prometheus observes metrics.
>
> Globular sits below and around that: cluster membership, PKI, package lifecycle, service discovery, and the four truth layers (artifact, desired, installed, runtime). The goal is that both humans and AI agents can inspect and operate the full cluster state through typed, RBAC-controlled tools — not shells or dashboards.
>
> If you are already happy with your K8s setup, Globular is probably not your next move. If you are building bare-metal or self-hosted clusters and want operational clarity, it might be interesting. Here is the architecture overview: [link]."

---

### Agent 5: Globular Demo Script Writer

**Trigger**: A demo scenario is described.

**Inputs**:

```
- Demo scenario description
- Target audience (technical / founder / general)
- Platform (YouTube / X / LinkedIn / conference / internal)
- Available cluster state (real cluster? simulated? screenshots only?)
```

**Outputs**:

| Output | Notes |
|---|---|
| 30-second script | Hook + one action + one result |
| 2-minute script | Intro + problem + demo + payoff |
| Full technical walkthrough | Step-by-step, for engineers |
| Title options (5) | For video or article |
| Thumbnail text ideas (3) | Short, high-contrast |
| Screenshot/clip sequence | Ordered list of what to capture |
| Narration cues | What to say at each moment |

**Standard demo arc** (use this for every demo):

```
1. State the cluster is healthy (show it)
2. Introduce the break (deliberate, small, observable)
3. Show Globular detecting the mismatch
4. Show the finding (Doctor report or drift report)
5. Show the typed remediation
6. Show human approval (if mutating)
7. Show workflow executing
8. Show convergence — cluster is green again
9. One-sentence takeaway
```

**The killer demo scenario** (always available):

> A service is desired on three nodes but running on only one. Claude is given the MCP tools and asked: "What's wrong with this cluster?" Claude inspects state, explains the drift, proposes the fix. Human approves. Workflow executes. Cluster converges.

---

### Agent 6: Globular FAQ Builder

**Trigger**: A repeated question is identified (from GitHub, Reddit, Discord, comments).

**Inputs**:

```
- Original question (verbatim if possible)
- Source and frequency
- Any existing answer given
```

**Outputs**:

| Output | Notes |
|---|---|
| FAQ question (canonical form) | Clean phrasing of the question |
| Short answer | 2–3 sentences |
| Detailed answer | Full explanation, with links |
| Documentation section suggestion | Where in docs this should live |
| README addition suggestion | If the question indicates a gap in first impression |

**Priority questions to build FAQ for immediately**:

1. "Is Globular a Kubernetes replacement?"
2. "Does Globular work with Kubernetes?"
3. "Why not just use K3s + ArgoCD?"
4. "What does 'AI-operable infrastructure' actually mean?"
5. "What is the four-layer state model?"
6. "How does Globular handle security?"
7. "Can Claude actually operate a Globular cluster?"
8. "Is Globular production-ready?"
9. "What are the minimum hardware requirements?"
10. "How does Globular compare to OpenStack?"

---

## Weekly Rhythm

Every week follows this pattern. OpenClaw prepares the drafts. Human reviews and approves.

### Monday — Architecture post

Topic rotation:
- Why clusters need committed truth
- The four truth layers
- Why AI needs explicit state, not logs
- What layer-0 infrastructure means
- Why operational awareness matters before workloads

Format: Medium-length thread or LinkedIn post. Link to a doc.

### Tuesday — Demo post

Show something breaking. Show Globular detecting it. Keep it real.

Format: Short video clip (30–90 seconds) or screenshot thread. Script from Agent 5.

### Wednesday — Comparison post

Not an attack. A clarification.

Examples:
- "Kubernetes runs workloads. Globular operates the substrate."
- "ArgoCD syncs manifests. Globular commits operational truth."
- "Prometheus observes metrics. Globular reasons about state layers."

Format: Short thread or infographic.

### Thursday — Build-in-public post

Honest. Personal. Real.

Template:
```
What broke: [short description]
Why it broke: [honest explanation]
What invariant was added: [one sentence]
What the cluster does now that it did not before: [one sentence]
```

This is the highest-trust content. Do not make it sound polished.

### Friday — Release summary

Only if there is a real release. Do not manufacture content.

Template:
```
v[X.Y.Z] is out.

What changed: [2–3 bullet points]
What this means: [one sentence]
Why it matters: [one sentence]
Link: [release notes]
```

---

## Approval Workflow

```
Step 1: Engineering event occurs (release, fix, milestone, demo, doc)
Step 2: Human feeds event to OpenClaw agent (brief description)
Step 3: OpenClaw produces all drafts
Step 4: Human reviews each draft
Step 5: Human edits where needed (OpenClaw can revise on request)
Step 6: Human marks drafts as approved
Step 7: OpenClaw schedules or exports to platform
Step 8: Human gives final confirmation before any post goes live
Step 9: Post is published
Step 10: OpenClaw tracks reactions, questions, and objections
Step 11: Weekly feedback summary delivered to human
```

**Nothing is posted without Step 8.**

**No exceptions.**

---

## Content Templates

### Template A: Engineering milestone post

```
We just [what changed].

Before: [old behavior in one sentence]
After: [new behavior in one sentence]

Why it matters:
[2–3 sentences on the operational consequence]

[Link to release or doc]
```

### Template B: Build-in-public post

```
Honest update from building Globular.

What we discovered: [the failure or gap]
What we thought: [the wrong assumption]
What the cluster actually did: [the real behavior]
What we changed: [the invariant added]

This is what explicit infrastructure looks like from the inside.
```

### Template C: Concept explanation post

```
[Provocative or counterintuitive claim as first line]

Here is what that actually means:

[Simple explanation — 3–4 sentences]

In Globular:
[How Globular addresses this — 2–3 sentences]

[Link to docs or demo]
```

### Template D: Demo post

```
Break something.
Show what the cluster says.
Fix it.
Verify it.

[Short clip or screenshot]

Thread below ↓
```

### Template E: Comparison post

```
[Tool A] does [X].
[Tool B] does [Y].

These are different problems.

[1–2 sentences on how they can coexist or complement each other]

Globular's layer: [one sentence]
```

### Template F: FAQ post

```
Question we get a lot:

"[question]"

Short answer:
[2–3 sentences]

Longer answer in the docs: [link]
```

---

## Launch Checklist (Pre-HN / Pre-Show HN)

Before any major launch moment, every item must be checked:

### Technical readiness

- [ ] Quickstart works end-to-end for a first-time user
- [ ] Quickstart tested by someone who has never seen Globular
- [ ] All four truth layers are visible in the CLI output
- [ ] Doctor works and produces readable findings
- [ ] Drift report works
- [ ] At least one convergence scenario documented

### Repository readiness

- [ ] README leads with the AI-operable positioning
- [ ] AI Operation Plane diagram is in the README
- [ ] Four-layer diagram is in the README
- [ ] Quick install block is copy-paste ready
- [ ] GitHub topics/tags are set
- [ ] CONTRIBUTING.md exists
- [ ] SECURITY.md exists
- [ ] ROADMAP.md exists
- [ ] Known limitations are documented honestly
- [ ] Releases are tagged with changelogs

### Content readiness

- [ ] At least one architecture article is published
- [ ] Demo video exists (5–8 minutes minimum)
- [ ] Short demo clip exists (30–90 seconds)
- [ ] FAQ covers the top 10 questions
- [ ] At least one build-in-public post exists

### Community readiness

- [ ] GitHub Discussions or Discord is open
- [ ] A "getting started" pinned post exists
- [ ] Dave is available to respond within hours during launch day

### OpenClaw readiness

- [ ] Reply drafts prepared for the 10 most likely objections
- [ ] Community monitor terms are configured
- [ ] Launch thread drafted and approved
- [ ] LinkedIn post drafted and approved
- [ ] Reddit posts drafted for r/selfhosted, r/devops, r/golang
- [ ] HN Show HN post drafted and approved
- [ ] Week 1 content calendar is scheduled

---

## Metrics to Track

### Weekly OpenClaw report

OpenClaw delivers this summary every Friday:

| Metric | Track because |
|---|---|
| Posts drafted | Volume of raw material |
| Posts approved | Conversion from draft to use |
| Posts published | Actual output |
| Best-performing topic | Double down |
| Worst-performing topic | Drop or reframe |
| Questions received | FAQ gaps |
| Objections raised | Positioning gaps |
| Docs gaps identified | What the audience finds unclear |
| Demo ideas from audience | What to build next |
| GitHub issues created | Operational follow-through |
| README changes suggested | First-impression gaps |
| Next week recommendations | Input to Monday planning |

### Adoption metrics (monthly)

| Metric | Target (Month 1) | Target (Month 3) |
|---|---|---|
| GitHub stars | 25 | 100 |
| Quickstart completions (tracked via community) | 3 | 20 |
| Demo video views | 100 | 1,000 |
| Community members (Discord/Discussions) | 10 | 50 |
| External questions received | 5 | 30 |
| External contributors | 0 | 1 |
| Consulting leads | 0 | 1 |

### Quality gates (never sacrifice these for metrics)

- No post published without human approval
- No claim made without a release, demo, or doc to back it
- No fake adoption signals (no "everyone is using Globular")
- No engagement bait (no questions that aren't genuine)

---

## Risks and Guardrails

### Risk 1: Over-claiming

**Risk**: A draft claims Globular replaces Kubernetes, or is production-ready everywhere, or has adoption it does not have.

**Guardrail**: Every agent checks claims against this list before outputting:
- Is this backed by a release, doc, or demo? If no → flag.
- Does this say "replaces Kubernetes"? → Rewrite.
- Does this imply adoption that does not exist? → Remove.
- Is this a benchmark claim without data? → Remove.

---

### Risk 2: Sounding like a bot

**Risk**: OpenClaw-generated content sounds corporate, templated, or hollow.

**Guardrail**: Build-in-public posts are always human-written or heavily edited. OpenClaw drafts are starting points, not finished products. Human voice must be present, especially in founder posts.

---

### Risk 3: Burning attention before the product is ready

**Risk**: A big launch moment (HN, Reddit) happens before quickstart is solid.

**Guardrail**: The launch checklist is a hard gate. No Show HN without every item checked. Traffic without a working first experience is wasted.

---

### Risk 4: Engagement without follow-through

**Risk**: Community asks questions that never get answered. Issues get filed and sit.

**Guardrail**: Month 1 rule — Dave answers every serious question personally within 24 hours. OpenClaw tracks unanswered questions in the weekly report. Unanswered questions become docs or FAQ items.

---

### Risk 5: Pillar drift

**Risk**: Content starts drifting toward general "DevOps tips" or general "AI tips" without Globular grounding.

**Guardrail**: Every post must anchor to at least one of the six content pillars. If a post does not map to a pillar, OpenClaw flags it before approval.

---

### Risk 6: Approval fatigue

**Risk**: Human stops reviewing carefully because there are too many drafts.

**Guardrail**: OpenClaw produces a maximum of 3 drafts per event. Human picks one and edits it. Quality over volume. Do not generate 12 versions of the same post.

---

## The Single Most Important Deliverable

The AI-Operated Cluster Demo.

OpenClaw's entire job exists to support this moment.

When the demo is ready:

1. Agent 5 produces the full script
2. Agent 1 produces the release thread
3. Agent 2 produces all platform posts
4. Agent 4 prepares replies for the top 10 objections
5. Agent 3 identifies the best communities to engage
6. Human reviews and approves everything
7. Demo is published
8. OpenClaw tracks every reaction
9. Week 1 feedback summary drives the next content decisions

---

## Main Adoption Message (Repeat This Everywhere)

> "Globular is not another orchestrator.
>
> Globular is an AI-operable cluster substrate.
>
> Its promise: make infrastructure understandable enough that humans and AI agents can operate it safely."

---

*This document is the operating plan. OpenClaw agents execute it. Humans approve everything.*
