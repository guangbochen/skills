# Skills

A curated collection of agent skills for my personal work.

Skills are small, easy to adapt, and composable. They work with any model.

## Installation

A plugin updates itself. [skills.sh](https://skills.sh/guangbochen/skills) copies editable files into your project, and you update them by hand. Pick one per agent, because installing both gives you every skill twice. The canonical wording lives in [.agents/install-block.md](./.agents/install-block.md).

### Claude Code

```bash
claude plugin marketplace add guangbochen/skills
claude plugin install guangbochen-skills@guangbochen
```

Updates itself when a release merges.

### Codex

```bash
codex plugin marketplace add guangbochen/skills
codex plugin add guangbochen-skills@guangbochen
```

Updates itself at startup.

### GitHub Copilot (CLI and VS Code)

Use the marketplace, not a direct repo install. Direct repo installs are deprecated and can't auto-update.

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

### Every other agent, or editable files (skills.sh)

```bash
npx skills@latest add guangbochen/skills -a <agent>  # omit -a to choose
```

To update, run `npx skills@latest update`, and re-run `add` to pick up new skills.

## The skills

Skills live in bucket folders under `skills/`. Only `engineering/` and `productivity/` are promoted: they ship in the plugin and get docs pages under `docs/`.

- [engineering](./skills/engineering/README.md): daily code work
- [productivity](./skills/productivity/README.md): daily non-code workflow tools
- [in-progress](./skills/in-progress/README.md): beta, feedback wanted
- [misc](./skills/misc/README.md): kept around, rarely used
- [deprecated](./skills/deprecated/README.md): no longer used

Promoted skills, grouped by invocation mode:

**User-invoked**

_None yet._

**Model-invoked**

- [ste-writing](./skills/productivity/ste-writing/SKILL.md): write and review prose deliverables (PRDs, specs, design docs, proposals) in ~80% ASD-STE100 Simplified Technical English.

## Developing this repo

The conventions (bucket rules, plugin manifest sync, docs pages, invocation modes, releases) live in [AGENTS.md](./AGENTS.md), the default agent-instructions file; [CLAUDE.md](./CLAUDE.md) is a symlink to it for Claude Code. Run `scripts/link-skills.sh` to symlink the skills into your local harnesses for daily use.
