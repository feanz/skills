# Skills

A collection of [Agent Code] skills for common git workflows.

## Available Skills

| Skill | Description |
|-------|-------------|
| `azure-cost-report` | Create a markdown report of costs for the current month in production azure |
| `azure-prod-alert-report` | Create a markdown report of significant alerts in the last week in production azure |
| `azure-prod-performance-report` | Create a markdown report of significant performance issues in the last week in production azure |
| `babysit-pr` | Monitor a pull request through review and CI until it is ready |
| `commit` | Create a git commit using conventional commits format |
| `commit-push-pr` | Commit, push, and open a PR in one step |
| `file-pr` | File a concise pull request for the current branch |
| `full-send` | Implement, verify, review, and merge a pull request |
| `full-stop` | Implement, verify, and review a pull request without merging |
| `git-clean` | Cleans up all git branches marked as [gone], including removing associated worktrees |
| `sol-loop` | Review code with Sol in a bounded feedback loop |

## Installation

Install all skills from this repo using the [Vercel Labs skills tool](https://github.com/vercel-labs/skills):

```bash
npx skills add feanz/skills
```

To install a specific skill:

```bash
npx skills add feanz/skills/babysit-pr
```

```bash
npx skills add feanz/skills/azure-cost-report
```

```bash
npx skills add feanz/skills/azure-prod-alert-report
```

```bash
npx skills add feanz/skills/azure-prod-performance-report
```

```bash
npx skills add feanz/skills/commit
```

```bash
npx skills add feanz/skills/commit-push-pr
```

```bash
npx skills add feanz/skills/file-pr
```

```bash
npx skills add feanz/skills/git-clean
```

```bash
npx skills add feanz/skills/sol-loop
```

```bash
npx skills add feanz/skills/full-send
```

```bash
npx skills add feanz/skills/full-stop
```

## Usage

Once installed, invoke a skill in Claude Code with the slash command:

```
/babysit-pr
/azure-cost-report
/azure-prod-alert-report
/azure-prod-performance-report
/commit
/commit-push-pr
/file-pr
/git-clean
/sol-loop
/full-send
/full-stop
```

## Attribution

`sol-loop`, `full-send`, and `full-stop` come from Theo Browne's [tstack](https://github.com/t3dotgg/tstack) and are distributed under its MIT license. See [third-party notices](THIRD_PARTY_NOTICES.md) for the pinned source revision and license. `full-send` and `full-stop` also use this repository's `file-pr` and `babysit-pr` skills.
