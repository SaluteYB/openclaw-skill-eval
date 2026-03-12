---
name: skill-eval
description: Evaluate, tune, and regression-check AgentSkills. Use when creating a new skill or improving an existing one and you need structured should-trigger, should-not-trigger, boundary-case, and execution-quality examples. Also use when auditing overlapping skills and sharpening trigger descriptions before release.
---

# Skill Eval

Use this skill to evaluate another skill before or after changes. The goal is to reduce black-box guessing by writing down trigger expectations, boundary conflicts, execution checks, and short iteration notes.

## Core use cases

Use this skill when you need to:

- evaluate whether a skill should trigger on realistic requests
- capture requests that should not trigger the skill
- test boundary cases where two or more skills may conflict
- define post-trigger execution quality checks
- keep a compact regression log after each improvement round

## Recommended workflow

1. Identify the target skill and read its `SKILL.md`.
2. Create an `eval/` folder inside the target skill, or a sibling folder dedicated to that skill.
3. Copy the example files from `assets/examples/`.
4. Fill in `should-trigger.md`, `should-not-trigger.md`, and `boundary-cases.md` with short, realistic user requests.
5. Fill in `execution-checklist.md` with the target skill's quality bar.
6. Test the skill conceptually or through real use.
7. Record findings in `evaluation-log.md`.
8. If trigger quality is weak, tighten the target skill's `description` before expanding its body.
9. Re-test a small representative set after each meaningful change.

## Design rules

- Prefer 8-15 short examples per bucket instead of giant datasets.
- Write examples like real user messages, not synthetic benchmark jargon.
- Include at least 3 boundary cases for neighboring skills.
- Separate trigger quality from execution quality.
- Record regressions explicitly so old failures do not quietly return.

## Evaluation buckets

### Should trigger

Use for requests where the target skill is clearly the best match.

### Should not trigger

Use for nearby requests that belong to another skill or no skill.

### Boundary cases

Use for ambiguous requests. For each case, note which skill should win and why.

### Execution checklist

Use for post-trigger quality. Example checks:

- Did it inspect inputs before acting?
- Did it verify required tools before claiming success?
- Did it preserve originals unless overwrite was requested?
- Did it stay inside the skill boundary?
- Did it report outputs and tradeoffs clearly?

## Use bundled resources

- Read `references/evaluation-patterns.md` for compact scoring guidance.
- Copy files from `assets/examples/` to bootstrap a new evaluation pack quickly.

## Output expectation

At the end of one evaluation round, produce a short summary containing:

- target skill
- main trigger conflicts found
- description changes made
- execution issues found
- current confidence
- next fixes to try
