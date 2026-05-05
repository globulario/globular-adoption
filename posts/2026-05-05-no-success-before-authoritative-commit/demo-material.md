# Demo Material — Atomic Commit Recovery

**Status:** Not for publication. All assets here are preparation for a recorded demo. The accompanying LinkedIn post at the bottom of this file is published **only after** the demo is recorded and reviewed.

---

## 60-second demo script (voiceover-ready)

> *(0:00)* This is Globular. Three nodes. One controller leader. I'm going to install a package — and kill the leader halfway through committing the result.
>
> *(0:08)* I dispatch the install. The reconciler picks it up. The node-agent does its work and reports back: locally complete, pending sync.
>
> *(0:20)* The controller starts the atomic commit. While it's mid-flight, I kill the leader.
>
> *(0:28)* A new leader is elected. It scans the convergence outbox. It sees the pending-sync result waiting.
>
> *(0:40)* The new leader runs the same atomic transaction the old one was about to land. Installed state, result promotion, cleanup — all in one commit.
>
> *(0:50)* Final state: success, committed. The reconciler sees no drift. No re-dispatch. No loop.
>
> *(0:58)* That's the change. Half-commits cannot exist, so half-commits never need to be cleaned up.

---

## 2-minute technical walkthrough

> *(0:00 — Intro, 15s)* Globular models cluster state in four layers: the artifact in the repository, the desired release in the source of truth, what each node reports it actually installed, and runtime health. The control loop closes the gap between layers two and three.
>
> *(0:15 — The bug, 25s)* The path that closes that gap used to be three sequential writes. If the controller's leader died between any of them, the cluster ended up in a contradiction: the node had finished, the source of truth had no record, and the reconciler saw drift and dispatched the install again. We're going to reproduce that scenario and watch the new code recover.
>
> *(0:40 — Setup, 15s)* Three-node cluster. One controller leader. Empty installed state for the package I'm about to deploy. Outbox is clean.
>
> *(0:55 — Dispatch and local install, 20s)* I dispatch the install. The reconciler picks it up. The node-agent installs locally and writes its outcome to the convergence outbox with state `OutcomeSuccessLocalPendingSync`. That state is the explicit signal: *the node is done, but the cluster has not yet accepted it.*
>
> *(1:15 — Kill the leader mid-commit, 20s)* I'm going to inject a kill signal between the moment the committer reads the pending result and the moment the atomic transaction lands. The leader dies here.
>
> *(1:35 — Recovery, 15s)* New leader is elected. Its committer loop wakes up, scans the outbox, finds the same pending-sync result, and runs the same atomic etcd transaction. Installed state, result promotion, action cleanup — together or not at all. It lands.
>
> *(1:50 — Proof, 10s)* Final state: `OutcomeSuccessCommitted`. The reconciler sees no drift. The install is not re-dispatched. The loop that used to exist here cannot exist anymore.

---

## Terminal / demo checklist

### Before recording

- [ ] Three-node test cluster up, controller leader confirmed (note which node).
- [ ] Outbox empty, package not installed anywhere, etcd installed-state key absent.
- [ ] Two terminal panes pre-arranged:
  - Pane A: controller logs (leader)
  - Pane B: etcd watch on the relevant keys (installed-state, convergence-latest, convergence-action)
- [ ] Third pane on standby for `kill -9` against the leader process.
- [ ] Reconciler poll interval visible in config (so viewers see it's not waiting hours).
- [ ] Test package chosen with a fast local install step (so the demo isn't gated on real install time).
- [ ] Convergence committer poll interval (default 15s) confirmed and noted in voiceover timing.
- [ ] Stale-pending-sync threshold (default 10 minutes) noted in case viewers ask why the new leader doesn't wait.

### During recording

- [ ] Show empty initial state (etcd watch confirms no keys).
- [ ] Dispatch install — capture the action key appearing.
- [ ] Capture node-agent logs reaching "local install complete."
- [ ] Capture outbox key transitioning to `OutcomeSuccessLocalPendingSync`.
- [ ] Kill the leader **before** the atomic Txn lands (you may need to add a deliberate delay/breakpoint in the committer for the demo).
- [ ] Capture leader election in logs.
- [ ] Capture new leader's committer picking up the pending result.
- [ ] Capture the atomic Txn landing — all three key changes appear in the same etcd revision.
- [ ] Final state shown: result key = `OutcomeSuccessCommitted`, installed-state present, action key deleted.
- [ ] Show reconciler running once more and **not** dispatching.

### After recording

- [ ] Trim to under 90 seconds for the LinkedIn cut, keep the 2-minute version for the blog/Medium embed.
- [ ] Burn-in lower-third labels for each state transition (helps viewers who watch muted).
- [ ] Sanity-check that no internal hostnames, tokens, or customer references appear on screen.

---

## Screenshots / screen captures to collect

1. **Cluster topology** at start — three nodes, leader badge on the controller. Quick context shot.
2. **Empty etcd state** — `etcdctl get` against the installed-state and convergence keys, returning empty.
3. **Dispatch moment** — convergence-action key appearing, reconciler log line.
4. **Node-agent local complete** — log line from node-agent, outbox key with `OutcomeSuccessLocalPendingSync`.
5. **Leader killed** — process dying, election starting in remaining controllers' logs.
6. **New leader committer pickup** — log line "draining outbox, found pending-sync result."
7. **Atomic Txn landing** — etcd watch output showing all three key changes at the same revision number. *(This is the money shot — make sure the revision number is visible.)*
8. **Final state** — `OutcomeSuccessCommitted`, installed-state present, action gone.
9. **Reconciler quiescent** — log line showing "no drift detected" or equivalent.

---

## LinkedIn post — to publish ONLY after the demo is recorded

> Forty seconds. One killed leader. One clean recovery.
>
> A node-agent finishes a local install. The controller starts committing the result — installed state, result promotion, cleanup — in one atomic transaction.
>
> Mid-flight, I kill the leader.
>
> The new leader is elected. It finds the pending-sync result waiting in the outbox. It runs the same transaction the old leader was about to. The cluster reaches a single committed state in one revision.
>
> The reconciler runs again. No drift. No re-dispatch. No loop.
>
> Half-commits cannot exist, so half-commits never need to be cleaned up.
>
> Short clip below. Longer technical walkthrough in the comments.
>
> No partial commits.
> No phantom states.
> No loops.
>
> #DistributedSystems #SRE #ControlPlane
