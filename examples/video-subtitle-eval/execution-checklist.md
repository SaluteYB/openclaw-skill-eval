# Execution Checklist — video-subtitle

- [ ] Identify whether the input is video, audio, SRT, or VTT before acting
- [ ] Avoid claiming ASR/transcription is available without checking tooling
- [ ] Preserve the original subtitle file unless overwrite is explicitly requested
- [ ] Make timing shifts explicit in seconds or milliseconds
- [ ] Keep output in UTF-8 where possible
- [ ] Preserve subtitle order and numbering
- [ ] Use subtitle-oriented wording instead of generic ffmpeg/export language when the task is subtitle-centric
- [ ] Report output path(s) clearly
