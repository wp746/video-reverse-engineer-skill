# Asset Package Spec

Use this file after the script passes review and the producer begins breakdown.

This file defines extraction logic.

For the final prompt container format used with Banana 2, also read [banana2-asset-json-spec.md](banana2-asset-json-spec.md).

## Goal

Convert an approved script into asset-generation instructions that can later support:

- `@角色`
- `@场景`
- `@道具`
- storyboard binding
- Seedance 2.0 prompt writing

## Producer breakdown order

1. extract characters
2. extract scenes
3. extract props
4. identify which assets are standard versus key
5. prepare prompt input fields for asset generation

If the script does not contain enough information, return a clarification request instead of improvising silently.

## Character asset default spec

Each major character should produce one `16:9` sheet containing:

- face close-up
- full-body front view
- full-body side view
- full-body back view
- clothing-detail nine-grid

### Character extraction fields

- identity / role
- age feel
- gender presentation
- temperament
- face shape and features
- hair shape / color
- body build / height impression
- costume layers
- accessories
- shoes
- stable identification anchors

### Clothing-detail nine-grid

The nine-grid should focus on details that matter for later consistency, such as:

- collar
- shoulder structure
- sleeves
- chest / torso layering
- belt / waist treatment
- lower garment texture
- footwear
- signature accessory
- damage / wear / pattern detail when relevant

## Scene asset default spec

Default scene flow:

1. build a master scene grid first
2. identify key scenes
3. build multi-angle sheets for key scenes

### Scene extraction fields

- scene type
- spatial layout
- time of day
- main light / secondary light
- palette
- atmosphere
- key furniture / objects
- depth and layering
- angle requirements

### Key-scene multi-angle sheet

For important scenes, create a sheet that may include:

- hero angle
- side angle
- reverse / complementary angle

## Prop asset standalone rule

A prop gets its own asset if either condition is true:

- it recurs across the piece
- it is narratively critical

### Prop extraction fields

- name
- narrative function
- owner / user
- material
- wear / age / damage
- scale impression
- era / world alignment
- whether it needs independent `@` reference later

## Asset prompt packaging principle

Do not just produce a loose list.

For each asset, prepare:

- extracted asset brief
- prompt-ready structured input
- any consistency notes required for later video generation

The canonical machine-oriented output should be JSON for Banana 2.
