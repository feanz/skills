---
name: babysit-pr
description: Monitor a GitHub pull request through review and CI, investigate new feedback, fix valid findings, respond to false positives, and report when the latest commit is ready. Use when the user asks to watch, monitor, shepherd, or babysit a PR, including after another skill files one.
---

# Babysit PR

Monitor the pull request until its latest commit is ready for the user or until progress requires their decision.

## Establish the baseline

1. Identify the PR from the user's link or number, the current branch, or the branch's open PR.
2. Record the latest head commit and push time.
3. Inspect the PR diff, review state, unresolved threads, required checks, and mergeability before changing anything.
4. Read repository instructions and keep the user's original goal as the scope boundary.

## Monitor

Use the harness's PR or task-waiting tools when available. Otherwise, poll with `gh` for review threads, comments, check results, mergeability, and changes to the base branch. Stay quiet when nothing has changed.

On every new head commit, refresh the baseline and evaluate checks and feedback for that commit. Do not act on stale check results or superseded comments without first confirming they still apply to the current source.

Continue until one of the stop conditions below is met. Do not treat a single quiet poll as completion.

## Handle feedback and failures

For each new review finding or failed check:

1. Verify it against the current source, diff, repository instructions, and relevant test output.
2. Fix genuine defects and CI failures that remain within the PR's original goal.
3. Run focused validation, then commit and push the fix using the repository's conventions.
4. Distinguish failures caused by the PR from unrelated infrastructure flakes. Retry a likely flake only when safe; report persistent or ambiguous failures.
5. For an incorrect or inapplicable bot finding, reply with a concrete technical reason and resolve or dismiss it when authorized by the platform.
6. Do not let review feedback expand the PR beyond the user's goal. Surface worthwhile out-of-scope work separately.

Never make a code change merely to satisfy a bot. Treat human review comments as authoritative feedback but ask the user when addressing one requires a product decision or meaningful scope change.

When replying on the user's behalf, make the automation explicit:

```md
[MODEL-SLUG] RESPONDING ON BEHALF OF [USER]
=====

[actual reply]
```

Use the real model identifier when known and the user's name or handle when available. Do not post filler or status comments.

## Track the base branch

Watch for changes to the base branch and update or rebase the PR when needed to restore mergeability or validate against material overlapping changes. Do not force-push unless the user has already authorized that workflow.

If another merged or active PR makes this PR obsolete, stop monitoring, explain the overlap, and ask before closing the PR unless closure was explicitly authorized. Stop and ask if conflict resolution requires a product or design choice.

## Stop conditions

Report that the PR is ready only when all required checks pass on the latest head commit, review bots are clear, actionable threads are resolved, and the PR is mergeable.

Stop earlier and report the blocker when progress requires user input, credentials, unavailable infrastructure, a scope decision, or an unauthorized destructive action.

Merge or close the PR only when the user explicitly requested it. Otherwise, leave the ready PR open and report its URL, latest commit, checks, and review status.
