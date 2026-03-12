# Evaluation Log — video-subtitle

## Round 1
- Date: 2026-03-12
- Skill: `video-subtitle`
- Main trigger issue: overlapped with `video-ffmpeg` on requests that mention extracting audio from video.
- Main execution issue: risk of over-promising transcription when ASR tooling is not present.
- Changes made: tightened the skill description to prioritize subtitle/transcript artifacts over generic media processing.
- Result after retest: clearer routing for subtitle-file work; burn-in/export tasks remain routed to `video-ffmpeg`.
- Remaining risk: mixed requests that ask for both subtitle cleanup and final media export may still need explicit tie-breaking.
