# Skills

A collection of agent skills for git workflows and Azure reporting.

## Available Skills

| Skill | Description |
|-------|-------------|
| `azure-cost-report` | Create a markdown report of costs for the current month in production azure |
| `azure-prod-alert-report` | Create a markdown report of significant alerts in the last week in production azure |
| `azure-prod-performance-report` | Create a markdown report of significant performance issues in the last week in production azure |
| `babysit-pr` | Monitor a pull request through review and CI until it is ready |
| `commit` | Create a git commit using conventional commits format |
| `commit-push-pr` | Commit, push, and open a PR in one step |
| `council` | Review or get feedback from three models across different providers |
| `file-pr` | File a concise pull request for the current branch |
| `full-send` | Implement, verify, review, and merge a pull request |
| `full-stop` | Implement, verify, and review a pull request without merging |
| `git-clean` | Cleans up all git branches marked as [gone], including removing associated worktrees |
| `leaving-pr-comments` | Format agent-authored GitHub comments with attribution |
| `sol-loop` | Review code with Sol in a bounded feedback loop |

## Installation

Install all skills from this repo using the [Vercel Labs skills tool](https://github.com/vercel-labs/skills):

```bash
npx skills add feanz/skills
```

The Theo-derived workflows are bundled here so existing installations keep
working without fetching remote skill instructions at invocation time. They are pinned copies, not
live references. See [upstream maintenance](#upstream-maintenance) for the source
revision and the one intentional customization.

To install the complete workflow bundle, including its dependencies:

```bash
npx skills add feanz/skills --skill file-pr babysit-pr sol-loop full-send full-stop leaving-pr-comments council
```

To use Theo's unmodified versions and track his repository directly instead:

```bash
npx skills add t3dotgg/tstack --skill file-pr babysit-pr sol-loop full-send full-stop leaving-pr-comments council
```

Choose one source for these names; do not install both copies. Direct upstream
installation does not include this repository's Sol High customization. For
personal defaults with unmodified upstream skills, put the preference in your
user-level `AGENTS.md` or `CLAUDE.md`, as upstream recommends.

To install a specific skill (also install the dependencies listed below):

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
npx skills add feanz/skills/council
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

```bash
npx skills add feanz/skills/leaving-pr-comments
```

### Workflow dependencies

- `full-send` uses `sol-loop`, `file-pr`, and `babysit-pr`.
- `full-stop` uses `full-send` and therefore its dependencies.
- `file-pr` and `babysit-pr` use `leaving-pr-comments`.
- `council` requires a harness that can delegate to models from three different
  providers; it reports unavailable providers rather than substituting them.
- Outside T3 Code, `babysit-pr` uses its bundled executable `scripts/pr-wait`
  and requires Python 3 and an authenticated GitHub CLI (`gh`).

The [Agent Skills specification](https://agentskills.io/specification) supports
instructions that reference other files, but does not define remote skill aliases
or automatic skill dependency installation. Codex's
[`agents/openai.yaml` dependencies](https://developers.openai.com/codex/skills/)
declare tools, not other skills. A URL-only wrapper would require the agent to
fetch instructions and their resources at runtime; it is not a portable install
redirect. The [skills CLI](https://github.com/vercel-labs/skills) can install from
the upstream repository directly, but linked agent directories are local links,
not remote references. Install the dependency bundle explicitly.

## Usage

Once installed, invoke a skill in Claude Code with the slash command:

```
/babysit-pr
/azure-cost-report
/azure-prod-alert-report
/azure-prod-performance-report
/commit
/commit-push-pr
/council
/file-pr
/git-clean
/leaving-pr-comments
/sol-loop
/full-send
/full-stop
```

## Upstream maintenance

The upstream bundle is pinned to t3dotgg/tstack revision
`1085050f3baed1ac724caa4a8166145fb2ac88af`, verified against `main` on
4 November 2026. It includes `file-pr`, `babysit-pr`, `sol-loop`, `full-send`,
`full-stop`, `council`, and the required `leaving-pr-comments` helper, with upstream scripts
and agent metadata. Existing local `file-pr` and `babysit-pr` UI metadata is retained.

The only instruction customization is in `sol-loop/SKILL.md`: use the latest
available Sol at **high effort** unless the user chooses another effort, and
report when high effort is unavailable. This preserves the intentional local
preference rather than silently reverting it during synchronization.

For a future refresh, compare the seven complete upstream skill directories at a
new pinned revision, including scripts and `agents/` files; preserve that Sol
preference and the existing local UI metadata. Update this revision and the
third-party notices together. Keep a copy of the upstream license inside each
skill so individual installations retain attribution. Check the upstream README
for new dependencies before publishing.

`full-send` and `full-stop` instructions already match this revision; their
missing agent metadata is included in this refresh. The other upstream skills
(`takeover` and `modernize`) have no local equivalents and are not
imported. `commit`, `commit-push-pr`, `git-clean`, and the Azure reporting skills
remain unchanged.

To check and update installed skills with the skills CLI:

```bash
npx skills check
npx skills update
```

Updates follow the installed source; this repository's bundle advances only when
its pinned copies are refreshed. These commands are manual, not an automatic sync.

## Attribution

The seven workflow skills listed under upstream maintenance come from Theo Browne's
[tstack](https://github.com/t3dotgg/tstack) and are distributed under its MIT
license. See [third-party notices](THIRD_PARTY_NOTICES.md) for provenance and the
license. Each imported skill also includes its own copy of that license.
