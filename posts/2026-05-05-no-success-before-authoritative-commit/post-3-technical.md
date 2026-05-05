# Post 3 — Technical Explainer

**Status:** Draft.
**Channel:** LinkedIn (primary).
**Slot:** Day 3 (Friday) of the one-week schedule.
**Audience:** Engineers who want the actual mechanism.

---

## Final LinkedIn version

> Here is the install path Globular used to have.
>
> Step 1: reconciler dispatches an install action.
>
> Step 2: node-agent installs the package locally.
>
> Step 3: controller writes installed-state to the cluster's source of truth.
>
> Step 4: controller writes the result, promoting it to "committed."
>
> Step 5: controller deletes the action record to clean up.
>
> Steps 3, 4, and 5 were three sequential writes. Three places a leader could die.
>
> If the leader died between any of them, the next leader saw a contradiction. The node had finished. The source of truth had no record of it. The reconciler saw drift and dispatched the install again. And again.
>
> The fix is straightforward: collapse those three writes into a single atomic transaction.
>
> Outcomes now move through two explicit states.
>
> Locally complete, pending sync — the node finished, but the cluster has not yet accepted the result.
>
> Committed — the controller has landed all three writes atomically, and the cluster believes the install happened.
>
> Nothing exists in between. There is no leader-failover window where the node has succeeded but the cluster disagrees.
>
> This is a small change in code and a large change in what the rest of the system can assume. Every loop above this — drift detection, reconciliation, dispatch — now reasons over outcomes that are either fully committed or not yet promoted. Not partially anything.
>
> No partial commits.
> No phantom states.
> No loops.
>
> #DistributedSystems #SRE #ControlPlane #Reliability

---

## Concise note for GitHub release notes

> **Atomic convergence commit (PR-3 through PR-7)**
>
> Convergence outcomes from node-agents are now committed to the cluster's source of truth via a single atomic etcd transaction. The previous path performed three sequential writes (installed-state, result promotion, action cleanup), which left a leader-failover window in which the node had completed locally but the cluster had no record of it. That window allowed the drift reconciler to re-dispatch the same install indefinitely.
>
> Outcomes now move through two explicit states:
>
> - `OutcomeSuccessLocalPendingSync` — node-agent reports the local install completed; not yet authoritative.
> - `OutcomeSuccessCommitted` — controller has landed installed-state, result promotion, and cleanup atomically.
>
> Behavior changes:
>
> - Node-agent outcomes are routed through a convergence outbox the controller drains (PR-4).
> - The committer is leader-only and re-processes any pending-sync result from scratch on failover; no partial-write states survive a leader change (PR-5).
> - The reconciler suppresses re-dispatch for blocked outcomes (PR-6).
> - Dispatch is gated by a critical-key preflight (PR-7).
>
> No migration steps required. Existing pending results from prior versions are re-processed by the new committer on first leader election after upgrade.

---

## Diagram idea

**Title:** *Why three writes were one write too many*

**Concept:** A timeline diagram, two rows.

- **Top row — Old path:** Five labeled boxes left-to-right: `Dispatch` → `Local install` → `Write installed-state` → `Promote result` → `Cleanup action`. A jagged red line crosses between any of the last three boxes labeled **"leader dies here."** A return arrow loops back to `Dispatch`, labeled **"reconciler re-dispatches forever."**

- **Bottom row — New path:** Three boxes: `Dispatch` → `Local install (Pending Sync)` → `Atomic commit (installed-state + result + cleanup)`. A jagged red line crosses anywhere along it. A short arrow continues forward into `New leader resumes from Pending Sync`. No back-loop.

The visual point: in the old path, the failure window is wide and recovery loops backward. In the new path, the failure window collapses to a single transaction boundary and recovery moves forward.

Tooling suggestion: Excalidraw or tldraw — the hand-drawn aesthetic reads as engineering-honest, not marketing.
