# The canonical install block

One install story, one wording. `README.md`, `.changeset/*`, and every page under `docs/` must say **this** and nothing else. Change it here first, then propagate.

## Managed installs first

Lead with installs that update themselves. Fall back to skills.sh, labelled "manual updates", only for agents that have no such install. Call a route managed only if it updates without the user running a command. Put any one-time opt-in beside its install command. Never promise "instant".

Every managed route installs from this repo's own marketplace, `.claude-plugin/marketplace.json` and `plugin.json`. Those routes reinstall only when the `version` in `plugin.json` changes. The Release workflow runs `npm run version`, which copies that field from `package.json`, so users get a release when the "chore: version skills" PR merges.

| Agent         | Route                       | Updates itself?                                          |
| ------------- | --------------------------- | -------------------------------------------------------- |
| Claude Code   | `@guangbochen` marketplace  | Yes, when a release merges                               |
| Codex         | `@guangbochen` marketplace  | Yes, at startup, by default                              |
| Copilot CLI   | `@guangbochen` marketplace  | Yes, after a one-time `autoUpdate: true`                 |
| Everyone else | skills.sh                   | No. Run `npx skills update`, and re-run `add` for new skills |

## Claude Code

<canonical-block name="claude-code">

```bash
claude plugin marketplace add guangbochen/skills
claude plugin install guangbochen-skills@guangbochen
```

Updates itself when a release merges.

</canonical-block>

## Codex

<canonical-block name="codex">

```bash
codex plugin marketplace add guangbochen/skills
codex plugin add guangbochen-skills@guangbochen
```

Updates itself at startup.

</canonical-block>

## GitHub Copilot (CLI and VS Code)

Use the marketplace, not a direct repo install. Direct repo installs are deprecated and can't auto-update.

<canonical-block name="copilot">

```bash
copilot plugin marketplace add guangbochen/skills
copilot plugin install guangbochen-skills@guangbochen
```

Then, once, add to `~/.copilot/settings.json`:

```json
{
  "extraKnownMarketplaces": {
    "guangbochen": { "source": { "source": "github", "repo": "guangbochen/skills" }, "autoUpdate": true }
  }
}
```

</canonical-block>

## Every other agent, or editable files (skills.sh)

`-a` preselects the agent. Prefer skills.sh to an agent's own repo installer, because those may also pull in `misc/` and `in-progress/`. `npx skills update` skips skills added since `add`, so the block tells users to re-run `add`.

<canonical-block name="other-agents">

```bash
npx skills@latest add guangbochen/skills -a <agent>  # omit -a to choose
```

To update, run `npx skills@latest update`, and re-run `add` to pick up new skills.

</canonical-block>

Use the single-skill form wherever one skill is named on its own.

<canonical-block name="skills-sh-one-skill">

```bash
npx skills@latest add guangbochen/skills --skill=<name>
```

```bash
npx skills@latest update <name>
```

</canonical-block>

`skills@latest` is the pinned spelling everywhere.

## The two routes are exclusive

The plugin is a managed, read-only bundle you subscribe to. skills.sh writes files you own and edit. Installing both leaves the user with every skill twice: always say "pick one".
