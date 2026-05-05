# Post 1 — War Story

**Status:** Draft, publish-ready.
**Channel:** LinkedIn (primary).
**Slot:** Day 1 (Monday) of the one-week schedule.
**Voice:** House voice — short lines, beats, denial-triplet close.

---

## Final LinkedIn version

> Reconciler dispatches install.
>
> Node-agent installs the package.
>
> Controller starts writing the result.
>
> Leader crashes mid-write.
>
> New leader wakes up. No installed-state recorded. Drift detected. Dispatch install.
>
> Again. And again. And again.
>
> That was the loop we lived with. A node that had finished its job, a cluster source of truth that didn't know, and a reconciler that kept asking for the same thing forever.
>
> The fix took five PRs. The heart of it was a single rule: a result is not "success" until the cluster's source of truth has accepted it.
>
> Node-agent outcomes now flow through an outbox the controller drains.
>
> The controller promotes them with one atomic transaction — installed state, result, and cleanup, all together or not at all.
>
> If the leader dies mid-flight, the next leader sees the pending result and finishes the job cleanly. There is no half-committed state to recover from, because half-commits cannot exist.
>
> No partial writes.
> No phantom successes.
> No loops.
>
> #SRE #ControlPlane #DistributedSystems #Reliability

---

## Short version (under 900 characters)

> Reconciler dispatches install.
> Node-agent installs the package.
> Controller starts writing the result.
> Leader crashes mid-write.
>
> New leader wakes up. No installed-state recorded. Drift detected. Dispatch install. Again. And again.
>
> That was the loop. A node that finished its job, a source of truth that didn't know, a reconciler that kept asking forever.
>
> The fix: a result is not "success" until the cluster has accepted it. Node-agent outcomes flow through an outbox. The controller promotes them in one atomic transaction — installed state, result, cleanup — together or not at all.
>
> If the leader dies, the next one finishes cleanly. Half-commits cannot exist.
>
> No partial writes.
> No phantom successes.
> No loops.

---

## Alternate opening hook

> The same package installed itself eleven times before we figured out why.

Use this if you want the post to lead with consequence instead of sequence. The body that follows still works as written.

---

## Hashtags

**Primary set (LinkedIn-tuned, technical audience):**
`#SRE #ControlPlane #DistributedSystems #Reliability`

**Optional (broader reach, only if the post starts circulating):**
`#Etcd #PlatformEngineering`

**Avoid here:** `#AIInfrastructure` — this post earns the framing on principle but doesn't say it on the surface. Saving it for Post 2 keeps the tag set differentiated across the campaign.
