# skill-eval for OpenClaw

[![Release](https://img.shields.io/github/v/release/SaluteYB/openclaw-skill-eval)](https://github.com/SaluteYB/openclaw-skill-eval/releases)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)
[![CI](https://img.shields.io/github/actions/workflow/status/SaluteYB/openclaw-skill-eval/package-skill.yml?branch=main&label=package)](https://github.com/SaluteYB/openclaw-skill-eval/actions/workflows/package-skill.yml)

A small open-source AgentSkill for **evaluating other skills**.

`skill-eval` helps you move from "this skill feels okay" to a lightweight, repeatable evaluation workflow:

- should-trigger examples
- should-not-trigger examples
- boundary cases
- execution-quality checks
- short regression logs

It is designed for OpenClaw / Codex-style skill workflows, but the evaluation structure is general enough to adapt elsewhere.

中文说明见：[README.zh-CN.md](./README.zh-CN.md)

## Why this exists

Most skills fail in one of two ways:

1. **Trigger problems** — the skill fires when it should not, or fails to fire when it should.
2. **Execution problems** — the skill triggers correctly, but the workflow is vague, brittle, or inconsistent.

This skill gives you a compact structure for checking both.

## Repository layout

```text
openclaw-skill-eval/
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
├── .github/workflows/
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

## Quick example

Suppose you are refining a `video-subtitle` skill.

### should-trigger

- "Shift this SRT back by 1.2 seconds."
- "Clean this subtitle file and merge broken lines."
- "Convert this VTT into a clean SRT."

### should-not-trigger

- "Compress this MP4 to under 50MB."
- "Organize these clips into camera/date folders."
- "Write three YouTube titles for this video."

### boundary case

- "Extract audio from this interview and prepare it for subtitles."
  - Likely winner: `video-subtitle`
  - Why: the main artifact is subtitle/transcript preparation, not general export delivery.

## Installation

### Option A: download the packaged `.skill`

Download the latest `skill-eval.skill` from the [Releases](https://github.com/SaluteYB/openclaw-skill-eval/releases) page.

### Option B: use the repo directly

Copy the `skill-eval/` folder into your skills directory or local workspace skills collection.

## Packaging locally

If you have the OpenClaw `skill-creator` packaging scripts available, package it with:

```bash
python3 /usr/local/lib/node_modules/openclaw/skills/skill-creator/scripts/package_skill.py ./skill-eval ./dist
```

That should produce a `.skill` archive in `dist/`.

## Roadmap

- richer example packs for common skill categories
- optional score sheet / pass-fail rubric
- example evaluation folders for real skills

## License

MIT
