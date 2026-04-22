---
name: video-reverse-engineer
description: Use when the user wants to reverse-engineer an AI short film or creative video, extract its creative/visual/narrative logic, propose three same-depth derivative directions, then develop a reviewed script, asset package prompts, storyboard timeline, and Seedance 2.0 prompt package with sequential expert review and production gating.
---

# Video Reverse Engineer

Use this skill when the user wants to:

- analyze a strong short film or AI video deeply instead of getting shallow praise
- reverse-engineer theme, expression, pacing, shots, dialogue, sound, and style
- create a same-type but not copied new short from a reference video
- run script review before production
- extract character / scene / prop assets from a locked script
- generate Seedance 2.0-ready prompts that rely on `@角色` / `@场景` / `@道具`

## What this skill is

This is not just a video-analysis skill.

It is a production workflow:

1. extract video content when needed
2. perform precise reverse engineering
3. propose 3 derivative creative directions
4. write a script after user selection
5. run sequential industrial review on the script
6. hand approved script to producer for asset breakdown
7. generate asset-package prompts
8. build storyboard timeline
9. generate a Seedance 2.0 prompt package

## Default operating rule

The default flow is:

`analyze first -> propose directions -> user selects -> write script -> review loop -> producer breakdown -> asset package -> storyboard -> Seedance package`

Do not skip directly from analysis to Seedance prompts.

## Input handling

If the user provides:

- a link: first try to turn it into an analyzable material pack
- a video file: extract structure from the file
- screenshots / timestamps: use them directly as analysis material

The extraction phase should aim to capture:

- duration
- aspect ratio
- shot boundaries
- key frames
- subtitles / dialogue / voiceover text if available
- rough shot descriptions

If extraction is incomplete, continue with the available material and state what is missing.

Default link-source assumptions:

- Douyin / TikTok
- Xiaohongshu
- Bilibili
- X / YouTube
- local uploaded or downloaded files

## Mode routing

Choose the production mode early:

- `15s emotion short`
- `30-60s theme short`
- `1-3min narrative short`

Use the mode to control analysis granularity, script density, asset scope, and Seedance prompt granularity.

Read:

- [analysis-framework.md](references/analysis-framework.md) for reverse-engineering structure
- [script-review-order.md](references/script-review-order.md) for review order and pass gates
- [asset-package-spec.md](references/asset-package-spec.md) for asset extraction rules
- [banana2-asset-json-spec.md](references/banana2-asset-json-spec.md) for industrial Banana 2 asset packaging
- [producer-handoff.md](references/producer-handoff.md) for post-review producer breakdown and downstream package planning
- [seedance-package-spec.md](references/seedance-package-spec.md) for Seedance output structure
- [seedance-prompt-craft-notes.md](references/seedance-prompt-craft-notes.md) for Seedance prompt writing techniques extracted from 2201+ real-world cases (awesomevideoprompts.com)
- [cinematography-design-guide.md](references/cinematography-design-guide.md) for 38-type professional cinematography technique matching framework (NEW v2.0)
- [video-input-ingestion.md](references/video-input-ingestion.md) for multi-platform link ingestion
- [review-prompts/](references/review-prompts/) for hidden expert-review prompts, including cinematography-review (UPGRADED v2.0 with camera arc analysis + mirror symmetry check)

## Stage 1: Reverse engineering

Always analyze across these layers:

- creative logic
- visual logic
- narrative logic
- pacing logic
- shot logic
- dialogue / voice logic
- sound / music logic
- style / imagery logic
- migration logic

For each major shot or section, explain:

- what happens
- why it works
- what should be preserved in a derivative version
- what should be changed to avoid direct copying

## Stage 2: Three derivative directions

After analysis, propose 3 directions:

- closest to the original expressive power
- same core theme but different subject / imagery
- same emotional density but different structure / style

Each direction should include:

- one-line premise
- emotional keywords
- visual direction
- suggested runtime mode
- estimated asset complexity
- why it is worth making

## Stage 3: Script writing

Only write the script after the user selects a direction.

The script should include at least:

- one-line proposition
- theme statement
- synopsis
- role of each main character
- scene functions
- prop functions
- structural beats
- emotional curve
- dialogue / voiceover strategy
- first-pass shot intention

The script must already support later asset extraction.

## Stage 4: Sequential expert review

Do not run all reviews as a flat list. Use the sequence in [script-review-order.md](references/script-review-order.md).

The core rule is:

- total score must be `>= 90`
- key reviewers must clear their minimum threshold
- if a key reviewer vetoes, the script is rejected even when the total score is high

The script does not move forward until it passes.

## Stage 5: Producer breakdown

Once the script passes, producer work begins.

The producer must extract:

- character assets
- scene assets
- prop assets

Then the producer must prepare the downstream production package:

- asset priority
- key-scene selection
- likely segment plan
- continuity risk notes

If the script lacks enough information for asset extraction, stop and request script-level clarification instead of guessing silently.

## Stage 6: Asset package prompts

Generate prompt-ready asset packages using [asset-package-spec.md](references/asset-package-spec.md) and [banana2-asset-json-spec.md](references/banana2-asset-json-spec.md).

Default character asset package:

- one `16:9` sheet
- face close-up
- front / side / back full-body views
- clothing-detail nine-grid

Default scene asset package:

- first create a master scene grid
- then create multi-angle sheets for key scenes

Default prop rule:

- create a standalone prop asset if it is recurring or narratively critical

Default asset prompt container:

- output stable industrial JSON for Banana 2
- keep narrative visual language inside the JSON fields
- treat JSON as the canonical asset-package format

Useful starter templates live in:

- [banana2-character-asset-template.json](assets/banana2-character-asset-template.json)
- [banana2-scene-master-grid-template.json](assets/banana2-scene-master-grid-template.json)
- [banana2-scene-multi-angle-template.json](assets/banana2-scene-multi-angle-template.json)
- [banana2-prop-asset-template.json](assets/banana2-prop-asset-template.json)

## Stage 7: Storyboard timeline

After assets are defined, build the storyboard timeline.

Each shot should include:

- shot id
- time range
- narrative purpose
- linked character / scene / prop assets
- shot size
- camera angle
- camera motion
- action chain
- emotional task
- light / atmosphere notes

## Stage 8: Seedance 2.0 package

Generate a package, not a single loose paragraph.

The default package should include:

- master control prompt
- asset reference table with `@` mappings
- shot timeline table
- shot-level or segment-level Seedance prompts
- transition notes

Useful starter templates live in:

- [seedance-segment-template.md](assets/seedance-segment-template.md)
- [seedance-package-output-template.md](assets/seedance-package-output-template.md)

For human-readable intermediate outputs, also use:

- [analysis-output-template.md](assets/analysis-output-template.md)
- [creative-directions-template.md](assets/creative-directions-template.md)
- [script-review-summary-template.md](assets/script-review-summary-template.md)
- [producer-handoff-template.md](assets/producer-handoff-template.md)

Granularity rule:

- `15s`: second-level control where useful
- `30-60s`: segment the piece around Seedance's `<=15s` ceiling, with continuity across segments
- `1-3min`: break the film into controllable shot-block segments, usually within `<=15s`, while preserving continuity across all segments

Every Seedance prompt must stay faithful to the approved script and bound assets.

## Output discipline

When possible, deliver outputs in this order:

1. extraction summary
2. reverse-engineering report
3. 3 creative directions
4. approved script
5. producer asset breakdown
6. asset-package prompts
7. storyboard timeline
8. Seedance 2.0 package

## Seedance 2.0 Prompt — Autonomous Trigger Rule

**This rule applies globally**, not only within the 8-stage pipeline.

### Trigger conditions

Whenever the user's request involves ANY of the following, autonomously apply Seedance 2.0 prompt expertise:

1. **Explicit request**: User directly asks for Seedance / AI video prompts
2. **Vague creative idea**: User describes a scene, mood, story fragment, visual concept, or "I have an idea..." — proactively craft a production-ready Seedance 2.0 prompt from it
3. **Video production context**: User is working on a short film, ad, social media video, or any video content that could use AI generation
4. **Prompt improvement**: User shares an existing prompt and wants it better — rewrite it using the craft notes

### Mandatory knowledge source

Always base all Seedance 2.0 prompt output on:
- [seedance-prompt-craft-notes.md](references/seedance-prompt-craft-notes.md) — 2201+ case-extracted techniques

Do NOT improvise Seedance prompts without consulting this file.

### Quality standard

Every Seedance 2.0 prompt must include:
- **Format declaration** (duration, shot count, aspect ratio)
- **Time-axis segmentation** (second-level or segment-level, following the ≤15s rule)
- **Explicit camera movement** per shot (specific cinematography terms, not vague descriptions)
- **Physical constraints** (grounded physics, character count limits, etc.)
- **Multi-sensory layers** (visual + sound hints + physical feedback)
- **Technical tags** (resolution, framerate, color grading)
- **Style anchoring** (reference specific works/studios when applicable)
- **Verb-driven action description** (strong verbs, not static adjectives)

### One-click delivery for vague ideas

When the user gives a vague idea like "我想要一个下雨天武士的镜头" or "帮我写个赛博朋克跑步的", do NOT ask clarifying questions — directly deliver:
1. A production-ready Seedance 2.0 prompt (following all quality standards above)
2. Optionally 2-3 creative variations (different mood / camera / style) so the user can pick

### Output language

- Prompt text itself: **English** (Seedance 2.0 performs best with English prompts)
- Explanations and context: **Chinese** (match user's communication language)

## Important constraints

- Do not let surface aesthetics replace theme analysis
- Do not jump into prompt writing before script review passes (within the 8-stage pipeline)
- Do not generate asset prompts before producer breakdown (within the 8-stage pipeline)
- Do not treat Seedance output as a one-paragraph task when assets and shot timing matter
- Do not directly copy the reference video's literal characters, scenes, or lines unless the user explicitly wants a close remake
