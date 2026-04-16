# Video Input Ingestion

Use this file when the user gives a video link or uploaded video before reverse engineering begins.

## Goal

Convert a mixed-source video input into an analyzable material pack.

## Common source types

- Douyin / TikTok
- Xiaohongshu
- Bilibili
- X / YouTube
- locally uploaded or downloaded files

## Ingestion principle

Do not pretend that a link automatically equals full understanding.

The system should attempt to collect:

- source url
- title if available
- duration
- aspect ratio
- accessible transcript / subtitles if available
- shot boundaries or rough section boundaries
- key frames or user-provided screenshots

## If the source is incomplete

Proceed in two layers:

### Layer 1: best-effort extraction

Use what is available to build the first analysis pack.

### Layer 2: explicit gap report

State what is missing, such as:

- no clean frame sequence
- no transcript
- unclear shot boundaries
- missing ending frames

Then continue the workflow as far as is safely possible.

## Material pack target

Aim to turn the input into a pack containing:

- `source_summary`
- `timeline_summary`
- `key_frames`
- `text_layer`
- `rough_shot_descriptions`

The reverse-engineering phase should begin from this pack rather than directly from the raw link.
