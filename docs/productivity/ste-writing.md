# ste-writing

## What it does

Writes and reviews complex prose deliverables (PRDs, design docs, implementation specs, proposals) in Simplified Technical English, the ASD-STE100 controlled language built so that technical prose has exactly one reading. The skill targets ~80% compliance, not full compliance: full ASD-STE100 would force dropping domain terms that exist only in your codebase, and a spec that renames a code concept is wrong, not simpler. Precision beats dictionary compliance.

## When to reach for it

Type `/ste-writing`, or the agent reaches for it automatically when a task fits: writing or reviewing a PRD, spec, design doc, or proposal, or any mention of STE or Simplified Technical English. It also fires for Chinese deliverables, applying the same principles.

The boundary is prose deliverables. Commit messages and code comments are out of scope: they match the surrounding style instead.

## The 80% calibration

The tilde in "~80%" is the skill's leading idea. Strictness is tuned per task:

| Task | Strictness |
| --- | --- |
| User-facing doc | Stricter, rules applied hard |
| Internal working note | Looser, judgement over rules |
| Any task with an explicit style instruction from you | Your instruction wins for that task |

Domain terms (endpoint, preset, compaction, menu row) stay exactly as the codebase spells them, in every mode.

## Reviewing, not just writing

Point it at existing prose and it reviews against the rules instead of writing fresh. The output is a violations list: the quoted sentence, the broken rule, the suggested rewrite. It offers to apply the rewrites rather than rewriting silently, so every change stays auditable.

## Common questions

**Why not full ASD-STE100 compliance?**

Full compliance restricts you to the standard's approved dictionary. Real specs need domain terms the dictionary has never heard of, and dropping or renaming them loses the precision the doc exists to preserve.

**Does it apply to Chinese documents?**

Yes. The same principles carry over: short sentences, one idea per sentence, active constructions, exact domain terms.

## It's working if

- Prose it produces reads short and active: sentences under 20 words, one idea each, no semicolons.
- Reviews come back as a violations list with quoted sentences and rewrites, not a silently edited document.
- Domain terms in the output match the codebase spelling exactly.

## Where it fits

A reach-for-it-anytime standalone for prose deliverables. Its neighbour is `writing-for-agents`, which governs documents agents read (skills, AGENTS.md); ste-writing governs documents humans read, and the two rule sets differ because the readers do.
