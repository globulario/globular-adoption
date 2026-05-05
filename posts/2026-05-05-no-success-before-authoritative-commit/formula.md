# Reusable Content Formula — `bug → invariant → implementation → proof`

**Purpose:** A repeatable structure for Globular posts that keeps them grounded in real engineering work and resistant to hype drift.

---

## Template

> **[Bug]** — Open with the concrete failure. Specific symptoms, not abstractions. Short lines.
>
> One or two single-line beats showing the repetition or absurdity of the failure. ("Again. And again. And again.")
>
> **[Invariant]** — State the rule the system now enforces. One sentence. Plain language.
>
> **[Implementation]** — Describe the change in mechanism. No code unless it earns its place. Use real state names or component names from the codebase, but explain them inline. One or two sentences per moving part.
>
> **[Proof]** — Show that the new behavior holds under stress. A demo. A failover. A killed leader. A reconciler that goes quiet. Give the reader something they could verify.
>
> Close with a denial-triplet that names what cannot exist anymore.
>
> No [thing 1].
> No [thing 2].
> No [thing 3].
>
> Hashtags. Sparing.

---

## Worked example — applying the formula to PR-4 (convergence outbox)

**Topic:** "Break installSkipAllowed loop" — the change that introduced the convergence outbox before the atomic-commit work.

> **[Bug]**
>
> The reconciler dispatched an install. The node-agent reported back through a side-channel the controller didn't durably consume. If the controller missed the report — restart, lag, lost message — the node was done, but the controller didn't know. Reconciler saw drift. Dispatched again. Node-agent skipped (already installed). Reconciler still saw drift. Dispatched again. Skipped. Drift. Dispatch. Skip.
>
> The "install skip allowed" flag kept the cluster from breaking, and kept the loop from ending.
>
> **[Invariant]**
>
> Node-agent outcomes must be durably written to a place the controller is guaranteed to drain. No outcome may rely on the controller being awake to receive it.
>
> **[Implementation]**
>
> A convergence outbox in the cluster's source of truth. Node-agents append outcomes to it. The controller drains it on every committer pass. Outcomes survive controller restarts, leader changes, and message loss, because they are not messages — they are state.
>
> **[Proof]**
>
> Restart the controller while the node-agent is reporting. New controller comes up, reads the outbox, processes the outcome it never saw the first time. Reconciler sees no drift. No re-dispatch. The skip-allowed flag is no longer load-bearing.
>
> No lost outcomes.
> No unread reports.
> No loops.
>
> #DistributedSystems #SRE

---

## Anti-hype checklist (run before publishing)

Run every post through these. Every "no" or "uncertain" is a rewrite trigger.

- [ ] **Failure mode is concrete.** Can a reader name the bug after one read?
- [ ] **Invariant is one sentence.** If it takes two, you don't have an invariant — you have a description.
- [ ] **Implementation references real components.** State names, package names, PR numbers. Vagueness here reads as fabrication.
- [ ] **Proof is something a reader could reproduce.** Or at least watch. "Trust us, it works" fails this check.
- [ ] **No replacement claims.** Globular is not pitched against AWS, Azure, or Kubernetes. It is positioned for what it is — AI-operable, layer-0 infrastructure.
- [ ] **No "magical," "revolutionary," "game-changing," "breakthrough."** Each one earns a rewrite.
- [ ] **No "first ever" / "world's first."** Unless cited and verified.
- [ ] **The denial-triplet at the end names real things.** "No partial writes" is real. "No problems" is hype.
- [ ] **Layer-0 / AI-operable framing is in the close, not the hook.** If it's in the first sentence, it reads as positioning. If it's in the close, it reads as conclusion.
- [ ] **A skeptical engineer reading this would not roll their eyes.** Read it once with that audience in mind.
- [ ] **The post doesn't promise what hasn't shipped.** If the demo isn't recorded, don't say "watch the demo."
- [ ] **Numbers are real.** PR counts, state names, transaction boundaries — verify against the actual repo, not memory.
