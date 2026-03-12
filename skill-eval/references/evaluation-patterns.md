# Evaluation Patterns

Use these patterns to keep skill evaluation compact and repeatable.

## 1. Trigger fit

Questions:

- Is this clearly the best skill for the request?
- Would another installed skill plausibly compete?
- Does the current description over-trigger on nearby requests?
- Does it miss obvious requests that should route here?

Suggested quick rating:

- Strong fit
- Acceptable fit
- Ambiguous
- Wrong skill

## 2. Boundary clarity

Check whether neighboring skills are separated by:

- primary artifact (`video file` vs `subtitle file` vs `folder layout` vs `publish copy`)
- primary action (`transform` vs `organize` vs `rewrite` vs `evaluate`)
- output type (`new media export` vs `renamed files` vs `SRT/VTT` vs `text pack`)

If two skills still overlap, prefer sharpening the description before expanding the body.

## 3. Execution quality

After the skill triggers, judge whether it:

- followed the promised workflow
- checked prerequisites before claiming success
- used deterministic tools/scripts when appropriate
- preserved important user data
- reported outputs and tradeoffs clearly

## 4. Regression discipline

When you change a skill, re-check at least:

- 3 obvious should-trigger requests
- 3 obvious should-not-trigger requests
- 3 boundary cases

This keeps iteration cheap while still catching most regressions.

## 5. Minimal evaluation note format

Use this structure in `evaluation-log.md`:

- Date:
- Skill:
- Main trigger issue:
- Main execution issue:
- Changes made:
- Result after retest:
- Remaining risk:
