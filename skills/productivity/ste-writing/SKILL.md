---
name: ste-writing
description: Write and review complex prose deliverables (PRDs, design docs, implementation specs, proposals) in ~80% ASD-STE100 Simplified Technical English style. Use when writing or reviewing a PRD, spec, design doc, or proposal; when the user mentions STE, ASD-STE100, or Simplified Technical English; when a document must be unambiguous for later agent implementation. 中文场景同样适用：写或评审 PRD、设计文档、规格说明、提案时触发。Not for commit messages or code comments.
---

# STE writing (~80% ASD-STE100)

Write the deliverable in Simplified Technical English style. "80%" is a calibration range, not full ASD-STE100 compliance: full compliance would force dropping domain terms and lose precision.

## Style rules

- Short sentences. Aim for ≤20 words.
- Active voice. One idea per sentence.
- No semicolons. Use two sentences instead.
- Plain vocabulary. Prefer the common word over the formal one.

## Domain terms

- Keep Technical Names and domain terms exactly as the codebase uses them (endpoint, preset, compaction, menu row).
- Precision beats dictionary compliance. A spec that renames a code concept is wrong, not simpler.

## Calibration

- Tune the strictness per task: stricter for user-facing docs, looser for internal working notes. Dynamic adjustment is expected.
- An explicit style instruction from the user overrides this skill for that task.

## Scope

- Applies to prose deliverables: PRDs, design docs, implementation specs, proposals.
- Commit messages and code comments match the surrounding style instead.

## Non-English deliverables

- For a Chinese deliverable, apply the same principles: short sentences, one idea per sentence, active constructions, exact domain terms.

## Reviewing against STE

When the task is to review or simplify existing prose:

1. Check each sentence against the style rules: length, voice, one idea, no semicolons, plain vocabulary.
2. Check that domain terms match the codebase exactly. Flag any renamed concept.
3. Report violations as a list: quote the sentence, name the broken rule, give the rewrite.
4. Offer to apply the rewrites. Do not rewrite silently: a review the user cannot audit is not a review.
