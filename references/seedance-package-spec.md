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

Every Seedance prompt must be compiled strictly using the standard template in [prompt-compilation-playbook.md](prompt-compilation-playbook.md) and adhere to the 8 industrial prompting rules. 

Each prompt should include at least:

- **Segment ID & Time**: Chronologically tracked and precise (e.g. `SEG01_0-12s`).
- **Duties and Safe Zones**: Head and tail safe zones (at least 1.5s each) locked with stable micro-motions.
- **Continuity Anchors**: Explicit binding of approved assets (`@角色`, `@场景`, `@道具`) and lighting direction.
- **Physical Camera motion**: Concrete speed, height, trajectory, and camera type (mechanical/handheld).
- **Space-and-Material VFX**: Effects physically bound to space and reflectivity, avoiding floating descriptions.
- **Performance-based Emotion**: Dramatic lights/shadows, neck posture, chest breathing, and eye direction instead of simple adjectives.
- **The Change Chain**: The causal action loop (subject action -> camera path -> environment reaction -> recovery).

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

- **Strict Playbook Enforcement**: Every prompt must pass a sanity check against the 8 industrial prompting rules in [prompt-compilation-playbook.md](prompt-compilation-playbook.md).
- **Inheritance & Binding**: Seedance prompts must strictly inherit the locked script and approved assets; do not write prompts before `@` asset references exist.
- **No Random Inventions**: Do not add unapproved character features, costumes, or scene attributes casually.
- **Action Density**: Keep action density physically realistic for the allotted segment duration.
- **Safe Zone Handles**: Ensure the head and tail 1.5 seconds have clear, stable holding instructions to support clean transitions and avoid warp artifacts.
- **Continuity Guidance**: Every segment must specify spatial and lighting boundaries to avoid character, style, scene, or spatial drift.
