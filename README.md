# skill-eval for OpenClaw

A small open-source AgentSkill for evaluating other skills.

`skill-eval` helps you move from "this skill feels okay" to a lightweight, repeatable evaluation workflow:

- should-trigger examples
- should-not-trigger examples
- boundary cases
- execution-quality checks
- short regression logs

It is designed for OpenClaw / Codex-style skill workflows, but the evaluation structure is general enough to adapt elsewhere.

## Why this exists

Most skills fail in one of two ways:

1. **Trigger problems** — the skill fires when it should not, or fails to fire when it should.
2. **Execution problems** — the skill triggers correctly, but the workflow is vague, brittle, or inconsistent.

This skill gives you a compact structure for checking both.

## Repository layout

```text
skill-eval-openclaw/
├── skill-eval/
│   ├── SKILL.md
│   ├── references/
│   │   └── evaluation-patterns.md
│   └── assets/
│       └── examples/
│           ├── should-trigger.md
│           ├── should-not-trigger.md
│           ├── boundary-cases.md
│           ├── execution-checklist.md
│           └── evaluation-log.md
├── README.md
├── README.zh-CN.md
├── LICENSE
└── .gitignore
```

## What the skill does

Use `skill-eval` when creating or improving another skill and you want to:

- sharpen trigger descriptions
- audit overlap between neighboring skills
- define a minimal quality bar
- keep a short evaluation trail after each iteration

## Recommended usage

1. Read the target skill.
2. Create an `eval/` folder in that skill or next to it.
3. Copy the example files from `skill-eval/assets/examples/`.
4. Fill in realistic requests for:
   - should trigger
   - should not trigger
   - boundary cases
5. Add execution checks.
6. Update the target skill.
7. Re-test a representative subset.
8. Log what changed.

## Packaging

If you have the OpenClaw `skill-creator` packaging scripts available, package it with:

```bash
python3 /usr/local/lib/node_modules/openclaw/skills/skill-creator/scripts/package_skill.py ./skill-eval ./dist
```

That should produce a `.skill` archive in `dist/`.

## License

MIT
