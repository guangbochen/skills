---
name: example-skill
description: A template showing this repo's per-skill layout and conventions. Copy the folder when starting a new skill, and delete it once real skills exist. Use when the user asks how to add a skill to this repo.
---

# Example Skill

This skill is a template, not a tool. It demonstrates the anatomy every skill in this repo shares:

- **`SKILL.md`** (this file): frontmatter with `name` and `description`, then the body the agent reads.
- **`agents/openai.yaml`**: Codex UI metadata, and the invocation policy for user-invoked skills.

## Invocation mode

Decide this first, because it shapes the frontmatter:

- **Model-invoked** (the default, and what this file is): the `description` is model-facing, with rich trigger phrasing ("Use when the user wants..., mentions...") so auto-invocation fires.
- **User-invoked**: add `disable-model-invocation: true` to the frontmatter and `policy.allow_implicit_invocation: false` to `agents/openai.yaml`. The `description` becomes human-facing: one line, no trigger lists.

See `.agents/invocation.md` for the full rules, including how skills call each other (an explicit `Call the Skill tool with "<name>"` instruction, never a cross-folder link).

## Promoting a skill

This skill lives in `in-progress/`, so nothing registers it anywhere. When a skill moves into `engineering/` or `productivity/` (the promoted buckets), it must gain:

1. An entry in the top-level `README.md` (under **User-invoked** or **Model-invoked**), with the name linked to its `SKILL.md`.
2. An entry in the bucket's own `README.md`.
3. A path in `.claude-plugin/plugin.json`'s `skills` array, then `claude plugin validate . --strict`.
4. A docs page at `docs/<bucket>/<skill-name>.md`, written to `.agents/writing-docs.md`.

Skills in `misc/`, `in-progress/`, and `deprecated/` get none of these.

## House style

No em-dashes in any prose. Match the terse, declarative tone of the existing skills.
