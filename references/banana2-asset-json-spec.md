# Banana 2 Asset JSON Spec

Use this file when generating asset-package prompts for Google Banana 2.

## Goal

Do not output loose asset prose only.

Output a stable JSON package that:

- preserves creative intent
- captures enough specificity for Banana 2 image generation
- can be reused by later production steps
- makes character / scene / prop generation less dependent on ad hoc rewriting

## General rules

- Prefer narrative, cinematic descriptions over keyword piles
- Keep field names stable across projects
- Put the most model-critical visual information into dedicated fields instead of hiding everything in one paragraph
- Use JSON as the container, but keep the actual visual prompt language natural and specific
- Avoid vague adjectives unless they are grounded by visible details
- Use `English field names + Chinese content` as the default package language rule

## Top-level package

Use this top-level structure:

```json
{
  "project_id": "string",
  "project_title": "string",
  "mode": "15s-emotion | 30-60s-theme | 1-3min-narrative",
  "visual_bible": {
    "core_style": "string",
    "palette": "string",
    "lighting_principle": "string",
    "texture_keywords": ["string"],
    "continuity_rules": ["string"]
  },
  "assets": {
    "characters": [],
    "scenes": [],
    "props": []
  }
}
```

## Character asset JSON

Each major character should be packaged like this:

```json
{
  "asset_id": "char-001",
  "asset_type": "character",
  "name": "string",
  "narrative_role": "string",
  "must_reference_in_seedance": true,
  "sheet_spec": {
    "aspect_ratio": "16:9",
    "layout": [
      "face_closeup",
      "front_view",
      "side_view",
      "back_view",
      "costume_detail_nine_grid"
    ]
  },
  "identity_core": {
    "age_feel": "string",
    "gender_presentation": "string",
    "temperament": "string",
    "stable_recognition_anchors": ["string"]
  },
  "face_design": {
    "face_shape": "string",
    "eyes": "string",
    "nose": "string",
    "mouth": "string",
    "skin": "string",
    "hair_shape": "string",
    "hair_color": "string",
    "special_marks": ["string"]
  },
  "body_design": {
    "build": "string",
    "height_impression": "string",
    "posture": "string"
  },
  "costume_system": {
    "outerwear": "string",
    "inner_layers": "string",
    "lower_garment": "string",
    "footwear": "string",
    "accessories": ["string"],
    "material_notes": ["string"],
    "wear_and_damage": ["string"]
  },
  "costume_detail_nine_grid": [
    "detail-1",
    "detail-2",
    "detail-3",
    "detail-4",
    "detail-5",
    "detail-6",
    "detail-7",
    "detail-8",
    "detail-9"
  ],
  "banana2_prompt_package": {
    "system_intent": "Generate a single 16:9 cinematic character asset sheet for production use.",
    "generation_prompt": "string",
    "negative_risk_notes": ["string"],
    "consistency_notes": ["string"]
  }
}
```

### Character prompt writing rule

The `generation_prompt` should explicitly describe:

- one 16:9 sheet
- face close-up placement
- front / side / back full-body views
- clothing-detail nine-grid
- clean layout for production reference use
- white or controlled neutral background when needed for clarity

### Costume-detail nine-grid priority

The clothing-detail nine-grid should be `shot-usage-oriented`, not just costume-design-oriented.

Prioritize the nine details most likely to affect:

- close-up recognition
- medium-shot continuity
- motion readability
- material consistency across Seedance segments

Typical high-priority areas:

- collar / neckline
- shoulder silhouette
- sleeve cuff
- chest layering
- waist / belt structure
- lower garment texture
- footwear silhouette
- dominant accessory
- signature wear / damage / pattern

## Scene asset JSON

Master scene grid and key-scene multi-angle sheets should both use JSON packaging.

### Master scene grid

```json
{
  "asset_id": "scene-grid-001",
  "asset_type": "scene_master_grid",
  "grid_spec": {
    "format": "3x3 | 3x4 | 4x4",
    "scene_count": 0,
    "empty_slots_allowed": true
  },
  "scenes": [
    {
      "scene_id": "scene-001",
      "name": "string",
      "story_function": "string",
      "time_of_day": "string",
      "space_layout": "string",
      "lighting": "string",
      "palette": "string",
      "atmosphere": "string",
      "key_objects": ["string"],
      "banana2_cell_prompt": "string"
    }
  ],
  "banana2_prompt_package": {
    "system_intent": "Generate a production-use scene master grid with unified style.",
    "generation_prompt": "string",
    "consistency_notes": ["string"]
  }
}
```

### Key-scene multi-angle sheet

```json
{
  "asset_id": "scene-key-001",
  "asset_type": "scene_multi_angle",
  "name": "string",
  "must_reference_in_seedance": true,
  "angles": [
    {
      "angle_id": "hero",
      "purpose": "string",
      "space_layout": "string",
      "lighting": "string",
      "key_objects": ["string"],
      "banana2_angle_prompt": "string"
    },
    {
      "angle_id": "side",
      "purpose": "string",
      "space_layout": "string",
      "lighting": "string",
      "key_objects": ["string"],
      "banana2_angle_prompt": "string"
    },
    {
      "angle_id": "reverse",
      "purpose": "string",
      "space_layout": "string",
      "lighting": "string",
      "key_objects": ["string"],
      "banana2_angle_prompt": "string"
    }
  ],
  "banana2_prompt_package": {
    "system_intent": "Generate a multi-angle reference sheet for a key scene used in video continuity.",
    "generation_prompt": "string",
    "continuity_notes": ["string"]
  }
}
```

## Prop asset JSON

Only create standalone prop JSON when the prop is recurring or narratively critical.

```json
{
  "asset_id": "prop-001",
  "asset_type": "prop",
  "name": "string",
  "owner": "string",
  "narrative_function": "string",
  "must_reference_in_seedance": true,
  "design_core": {
    "material": "string",
    "shape_language": "string",
    "scale_impression": "string",
    "wear_and_damage": "string",
    "era_world_alignment": "string"
  },
  "banana2_prompt_package": {
    "system_intent": "Generate a production-use prop design reference.",
    "generation_prompt": "string",
    "continuity_notes": ["string"]
  }
}
```

## Output principle

When the user asks for asset-package prompts, provide:

1. the extracted asset table in readable prose
2. the Banana 2 JSON package
3. if useful, a human-readable prompt preview for quick inspection

The JSON should be the canonical version.

## Language example rule

Good default:

```json
{
  "name": "沈砚",
  "temperament": "克制、敏锐、带明显疲惫感",
  "generation_prompt": "一张16:9角色资产设定板，左侧为面部特写，中央为全身正面、侧面、背面三视图，右侧为服装细节九宫格..."
}
```

Avoid mixing unstable field naming conventions across projects.
