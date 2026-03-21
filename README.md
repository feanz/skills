# Skills

A collection of [Claude Code](https://docs.anthropic.com/en/docs/claude-code) skills for common git workflows.

## Available Skills

| Skill | Description |
|-------|-------------|
| `commit` | Create a git commit using conventional commits format |
| `commit-push-pr` | Commit, push, and open a PR in one step |

## Installation

Install skills from this repo using the [Vercel Labs skills tool](https://github.com/vercel-labs/skills):

```bash
npx skills add feanz/skills
```

To install a specific skill:

```bash
npx skills add feanz/skills --skill commit
```

```bash
npx skills add feanz/skills --skill commit-push-pr
```

## Usage

Once installed, invoke a skill in Claude Code with the slash command:

```
/commit
/commit-push-pr
```
