Professional Talking-Head Reel

An end-to-end Codex skill for transforming raw doctor, clinician, expert, or professional talking-head footage into a polished vertical social video.

The workflow starts with word-accurate dialogue editing in Video User, then moves through subtitle reconstruction, person cutout, brand packaging, deterministic GSAP motion in HyperFrames, production QA, and final H.264/AAC MP4 delivery.

## What it does

- Removes long pauses, empty waits, unusable fillers, repetitions, stutters, and false starts without changing the speaker's meaning.
- Builds edits on word boundaries with padded cuts and short audio fades for natural joins.
- Preserves chronology, clinical claims, names, terminology, and audio sync.
- Reconstructs accurate output-timeline captions after editorial cuts.
- Creates mobile-readable semantic captions with restrained keyword highlighting.
- Supports person cutout and replacement backgrounds with edge-quality checks.
- Adds a topic title, professional identity card, logo, and brand-safe vertical layout.
- Uses a seek-safe, deterministic GSAP timeline inside HyperFrames.
- Runs automated layout, motion, contrast, runtime, codec, and encoded-frame checks.
- Delivers a publication-ready Instagram Reels MP4.

## Best for

- Doctors and clinicians
- Medical and health educators
- Expert explainers
- Professional thought-leadership videos
- Branded talking-head Reels and Shorts

It is not intended to invent medical claims, rewrite the speaker's message, fabricate credentials, or replace fact checking.

## Default output

- Aspect ratio: 9:16
- Resolution: 1080 × 1920
- Frame rate: preserves the source frame rate; normally 30 fps for talking-head material
- Video: H.264 High profile, `yuv420p`
- Audio: AAC-LC, 48 kHz stereo
- Container: MP4
- Delivery target: Instagram Reels and similar vertical social platforms

## Requirements

This is an orchestration skill. The following capabilities must also be available:

- [Video User](https://github.com/browser-use/video-use)
- HyperFrames and the relevant HyperFrames skills
- GSAP
- FFmpeg and FFprobe
- Node.js 22 or newer
- Python environment required by Video User
- ElevenLabs/Scribe API access for word-level transcription

Recommended HyperFrames skills:

- `hyperframes`
- `general-video`
- `hyperframes-core`
- `hyperframes-animation`
- `hyperframes-creative`
- `hyperframes-cli`
- `media-use`
- `gsap`

On Apple Silicon, CoreML is the preferred local background-removal provider when supported.

## Installation

### Install with Codex

Ask Codex:

```text
Use $skill-installer to install this skill:
https://github.com/YOUR_USERNAME/professional-talking-head-reel
```

### Manual installation

Clone the repository into your personal Codex skills directory:

```bash
git clone \
  https://github.com/YOUR_USERNAME/professional-talking-head-reel.git \
  ~/.codex/skills/professional-talking-head-reel
```

Restart or refresh Codex if the skill is not immediately listed.

Install and configure Video User, HyperFrames, FFmpeg, and the required API credentials separately. Do not place API keys inside this repository.

## Minimum input

Only a raw video file is strictly required.

For a complete branded result, provide these when available:

- Transparent logo or brand assets
- Exact speaker name and professional credentials
- Required title, disclaimer, or must-keep wording
- Background or visual style guide
- Target platform when it is not Instagram Reels

The skill may derive a provisional topic or title from the transcript. It never infers credentials or uncertain medical facts.

## Usage

### Standard invocation

```text
Use $professional-talking-head-reel to turn this raw talking-head footage
into a polished Instagram Reels video and deliver the final MP4.
```

### With episode-specific information

```text
Use $professional-talking-head-reel for this video.

Speaker: [exact name]
Role and credentials: [verified text]
Required title: [title]
Logo: [file path]
Must keep: [important lines]
Must remove: [unwanted section]
Output: Instagram Reels MP4
```

## Workflow

The skill follows seven production stages:

1. **Inventory** — inspect source files, metadata, brand assets, and missing inputs.
2. **Transcribe and analyze** — create a cached word-level transcript and identify pauses, fillers, retakes, key claims, and uncertain terms.
3. **Confirm the edit strategy** — present one short editorial plan before changing the spoken cut.
4. **Create the clean master** — build a word-boundary EDL, add cut padding and audio fades, normalize pacing and loudness, then inspect every edit boundary.
5. **Rebuild captions and media assets** — map words to the actual rendered timeline, group captions semantically, prepare the logo/background, and verify the person cutout.
6. **Package in HyperFrames** — create the vertical composition, title, identity card, logo, captions, highlights, and deterministic GSAP motion.
7. **Check, preview, and deliver** — run HyperFrames checks and snapshots, obtain preview approval, render through the CLI, then verify the encoded MP4.

See the detailed executable procedure in [`references/sop.md`](references/sop.md).

## Fixed production rules

- Never cut inside a word.
- Pad every cut edge by 30–200 ms.
- Apply a 30 ms audio fade at every segment boundary.
- Prefer removing redundancy over mechanically accelerating speech.
- Use word-level verbatim transcription and cache it per source.
- Rebuild caption timing from actual rendered segment durations.
- Apply subtitles after overlays when using the Video User render chain.
- Keep all animation seek-safe and deterministic.
- Do not use unverified credentials, medical claims, or transcript guesses.
- Do not render final delivery until the user has reviewed the HyperFrames preview.

## Dynamic decisions

The following are re-evaluated for every video:

- Topic and title
- Speaker identity fields
- Key claims and protected lines
- Which fillers or repeated attempts can be removed safely
- Target runtime and pacing
- Whether 1.15× speed treatment remains natural
- Loudness correction
- Subject crop and headroom
- Background choice
- Caption grouping and highlighted terms
- Title and identity-card timing
- Palette, typography, and frame rate
- Final ending duration

See [`references/variables.md`](references/variables.md) for the complete decision table.

## Quality assurance

The release gates cover:

- Speech integrity and natural edit boundaries
- Caption synchronization through the final word
- Hair, shoulder, clothing, and hand-edge quality after background removal
- Instagram-safe layout and caption placement
- HyperFrames runtime, layout, motion, and contrast checks
- H.264/AAC codec, resolution, frame rate, audio format, duration, and encoded-frame verification
- Hash verification after copying the final deliverable

Known recovery procedures include caption drift, duplicated boundary words, VP9 alpha misreporting, GSAP/CSS transform conflicts, local preview permissions, unreachable Studio render servers, and unintended tail frames.

See [`references/qa-recovery.md`](references/qa-recovery.md).

## Project structure

```text
professional-talking-head-reel/
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── sop.md
    ├── variables.md
    └── qa-recovery.md
```

Video User session outputs are stored separately in the source video's `edit/` directory. User footage, renders, transcripts, brand assets, and credentials should not be committed to this repository.

## Security and privacy

- Never commit `.env` files or API keys.
- Never publish user footage, transcripts, credentials, or medical information without explicit permission.
- Keep source media untouched.
- Use user-owned or clearly licensed visual assets.
- Treat captions and medical terminology as accuracy-sensitive content.

## License

Choose and add a license before public distribution. MIT is a practical default for an open-source workflow skill, but confirm that every bundled dependency and asset may be referenced or redistributed under your chosen terms.

