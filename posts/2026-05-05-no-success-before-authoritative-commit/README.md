# Campaign — "No success before authoritative commit"

**Date drafted:** 2026-05-05
**Status:** Drafts. Nothing is published or scheduled.
**Subject:** The atomic-convergence-commit architecture change (PR-3 through PR-7).

This folder contains a 6-part adoption package built around a single Globular architecture change: the controller now commits convergence outcomes to etcd via a single atomic transaction, instead of three sequential writes. The change retires a long-standing class of "package re-installs forever" failures.

## Contents

| File | Purpose |
|------|---------|
| `post-1-war-story.md` | LinkedIn Post 1 — the failure mode that forced the change |
| `post-2-contrarian.md` | LinkedIn Post 2 — "most distributed systems lie about success" |
| `post-3-technical.md` | LinkedIn Post 3 — the actual mechanism, plus a release note and a diagram idea |
| `demo-material.md` | Demo script, walkthrough, terminal checklist, screenshot list, post-after-record draft |
| `schedule.md` | One-week posting schedule with goals, audience, CTAs |
| `formula.md` | Reusable `bug → invariant → implementation → proof` template + worked example + anti-hype checklist |

## Editorial rules (apply to everything in this folder)

- Drafts only. Nothing auto-posts.
- Claims must be grounded in actual code, PRs, docs, or recorded demos.
- Globular is positioned as **AI-operable, layer-0 infrastructure**.
- Globular is **not** pitched as a replacement for AWS, Azure, or Kubernetes.
- House voice: short lines, single-line beats, no founder-voice openers, end on a denial-triplet, layer-0 framing in the close (not the hook).
- Run every post through the anti-hype checklist in `formula.md` before publishing.

## Source material

- Five-PR series, May 2026: PR-3 (ConvergenceResult model), PR-4 (convergence outbox), PR-5 (atomic etcd Txn — commit `bbee8836`), PR-6 (block-aware reconciler), PR-7 (critical-key preflight).
- `services/docs/operators/convergence-model.md` — Four Truth Layers.
- `services/golang/installed_state/convergence.go` — outcome state machine.
- `services/golang/cluster_controller/cluster_controller_server/convergence_committer.go` — leader-only committer.
- `services/golang/fix/failure-patterns-and-invariants.md` — Pattern 5 (orphaned critical state) and Pattern 11 (unguarded runtime destructive action).
