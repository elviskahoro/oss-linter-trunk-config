# Agent instructions

## Working issues and labels

Follow these rules whenever you pick up, work, or release a GitHub issue in this repo.

### Visibility

gh-dash hides issues labeled `status::*` and `gas-city`. Label hygiene therefore decides what humans see: a missed or wrong label changes what they can find.

### Labels

| Label | Meaning |
| --- | --- |
| `status::in_progress` | Claimed and being worked on by an agent. Do not pick up. |
| `status::blocked` | Waiting on another issue in this repo ("blocked by #N"). |
| `status::blocked-external` | Waiting on something outside the repo (another repo, upstream, a vendor). |
| `status::deferred` | Parked on purpose; revisit date is in a comment. |
| `needs-human` | A person must decide. Agents must not pick up. |
| `gas-city` | Routed to Gas City. Conductor dispatch must not pick up. |
| `stale-claim` | Claim has no recent heartbeat; reclaimable. |

### Picking up work

1. Never pick up an issue labeled `needs-human`, `status::in_progress`, `status::blocked`, `status::blocked-external`, `status::deferred`, or `gas-city`.
2. An issue labeled `stale-claim` may be reclaimed. Re-claim it and comment that you took over.

### Claiming (required before any work)

3. When you start an issue, claim it first: add `status::in_progress`, assign yourself, and leave a one-line "starting" comment.
4. If `status::in_progress` is already present, stop. Two agents must never work one issue.
5. Re-read the labels right after claiming. If another agent claimed at the same moment, back off.
6. For long-running work, comment periodically so the claim does not become a `stale-claim`.

### Releasing

7. When done, put `Closes #N` in the PR body and remove `status::in_progress` once the PR is open. Merge closes the issue.
8. If you abandon or fail, remove `status::in_progress` and comment what happened and what remains. Never leave a dead claim.
9. If you need a decision you cannot make, remove `status::in_progress`, add `needs-human`, and comment the exact question. Do not guess. Never remove `needs-human` yourself.

### Blocked and deferred

10. Blocked by another issue in this repo: add `status::blocked`, comment "blocked by #N", and release the claim.
11. Blocked by something outside the repo: add `status::blocked-external`, comment what you are waiting on, and release the claim.
12. Never set `status::deferred` yourself. Only a human parks work.
