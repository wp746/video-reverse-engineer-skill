# Seedance Package Spec

Use this file after assets are prepared and storyboard timing is known.

## Goal

Generate a Seedance 2.0 package that is:

- faithful to the approved script
- bound to approved assets
- precise enough for timing and motion control
- structured for production instead of looking like one big paragraph

## Package structure

### 1. Master control section

Include:

- project theme
- visual tone
- emotional tone
- story mode
- overall motion and pacing tendency

### 2. Asset reference table

Map:

- `@角色`
- `@场景`
- `@道具`

Each reference should clearly state its purpose.

## 3. Timeline table

For each shot or shot-block, include:

- shot id
- time range
- narrative function
- linked assets
- action chain
- emotional task
- transition relationship

Use time-based segment ids by default:

- `SEG01_0-12s`
- `SEG02_12-24s`
- `SEG03_24-36s`

The id should reflect the actual planned duration, not an arbitrary fixed 15-second block.

## 4. Seedance execution prompts

Each prompt should include at least:

- time range
- bound assets
- shot purpose
- shot size
- camera angle
- camera movement
- action sequence
- physical feedback
- light / atmosphere changes
- emotion changes
- sound / ambience

## 5. Transition notes

Explain:

- how shots connect
- where emotion rises
- where safe zones exist

## Granularity rules

### 15s emotion short

Prefer second-level precision where meaningful.

Example:

- 0-2s establish
- 2-5s shift
- 5-9s intensify
- 9-12s turn
- 12-15s hit / release

### 30-60s theme short

Use segment-level production built around Seedance's `<=15s` ceiling.

Recommended approach:

- split the short into 1 to 4 production segments
- keep each segment within `<=15s`
- prefer shorter segments when a beat completes earlier
- bind every segment to approved assets and continuity notes
- maintain style, character, costume, and spatial continuity across segments
- name segments by time range, for example `SEG01_0-12s`

### 1-3min narrative short

Use shot-block prompts with key-second control on pivots, reveals, emotional peaks, and transitions.

Avoid mechanical second-by-second writing when it stops being useful.

Recommended approach:

- divide the film into controllable production units, usually each within `<=15s`
- allow a unit to be shorter than 15 seconds when the dramatic action is complete
- avoid forcing every unit to the maximum duration
- let script logic and reference-video logic determine appropriate unit length
- preserve character, style, scene geography, and motion continuity across all units
- keep time-range ids stable across review and production

## Constraint rules

- Seedance prompts must inherit the locked script and approved assets
- do not write prompts before asset references exist
- do not add unapproved character / scene inventions casually
- keep action density realistic for the allotted time
- preserve head/tail safe zones where necessary
- every segment should include enough continuity guidance to avoid character, style, scene, or spatial drift
