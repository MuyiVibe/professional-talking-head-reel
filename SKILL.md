Professional Talking-Head Reel

Produce a clean, accurate, professional 9:16 talking-head video while preserving the speaker's meaning and keeping decisions autonomous wherever the source supports them.

## Required routing

1. Read `video-use/SKILL.md` completely and inspect every file in `video-use/helpers/` before cutting. Use its helpers instead of recreating transcription, EDL, timeline, grading, or render logic.
2. Read `hyperframes/SKILL.md` before video packaging and follow its route. For this workflow, the normal route is `general-video` plus `hyperframes-core`, `hyperframes-animation`, `hyperframes-creative`, `media-use`, `hyperframes-cli`, and `gsap` as applicable.
3. Read [references/sop.md](references/sop.md) for the executable stage-by-stage procedure.
4. Read [references/variables.md](references/variables.md) during intake and content analysis.
5. Read [references/qa-recovery.md](references/qa-recovery.md) before preview and final render.

## Operating contract

- Preserve chronology, meaning, clinical claims, names, terminology, and audio sync. Never invent credentials, quotations, medical claims, or uncertain transcript text.
- Start with audio-first editorial decisions; use visuals at cut boundaries and composition decisions.
- Keep all source media untouched. Put Video User work in `<source-dir>/edit/`; create the HyperFrames project in an explicit writable project directory.
- Reuse cached word-level transcripts unless the source changed.
- Automate objective work. Ask only for missing facts that cannot be inferred safely, genuine subjective choices, the Video User strategy confirmation, and final render approval after the HyperFrames preview.
- Treat an invocation of this skill plus a complete brief as approval of the standard aesthetic defaults, but still present the short Video User cut strategy before making speech edits, as required by Video User.
- Use local/user-owned media. If a suitable background is missing, use a clearly documented replaceable placeholder; do not silently source unknown or risky media.
- No music, extra B-roll, visual effects, transitions, rewriting, or voice replacement unless requested.

## Default delivery profile

- Instagram Reels / vertical social: 1080×1920, 9:16.
- Preserve source frame rate; use 30 fps for ordinary talking-head material unless the source or brief requires 60 fps.
- Final: MP4, H.264 High profile, `yuv420p`, AAC-LC, 48 kHz stereo.
- Use HyperFrames `delivery` quality and CLI rendering after preview approval.
- Keep the source's aspect and resolution in the clean master; crop/reframe only in the vertical packaging composition.

## Completion condition

The task is complete only when the delivered MP4 has passed transcript/cut review, visual boundary review, HyperFrames check, rendered-frame inspection, and `ffprobe` verification. Report any placeholder or uncertain transcript term in the handoff.
