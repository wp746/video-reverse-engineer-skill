# Banana 2 Asset JSON Spec

Use this file when generating asset-package prompts for Google Banana 2 (image2).

---

## 1. Goal

Do not output loose asset prose only. Output a stable JSON package that:
- preserves creative intent
- captures enough specificity for Banana 2 image generation
- can be reused by later production steps
- enforces a strict, fixed layout and style based on the **GlitterPixely professional layout methodology** to prevent visual drift.

---

## 2. GlitterPixely Standard Layout Guidelines (好莱坞排版设计标准)

To ensure absolute layout and style consistency across image2 generated images, every asset sheet and storyboard prompt must adhere to these fixed visual formulas:

### A. Character Model Sheet Layout (角色资产板排版)
To lock character features, clothing, and proportions, the prompt must enforce an **orthographic, flat-lit turnaround sheet**:
- **Fixed Style Keywords**: `character model sheet, character design sheet, turnaround, multiple angles, front view, side view, back view, expressions sheet, orthographic technical illustration, clean flat lighting, solid light grey background, concept art, high consistency --ar 16:9`
- **Avoid**: Floating perspectives, dynamic shadows, busy environments, or anime-style rendering (unless anime is the target medium).
- **Default Prompt Structure**:
  `[Bilingual Prompts]: Character model sheet of [Character Details], turnaround showing front view, side view, back view, expression sheet, detailed technical illustration, solid light-grey background --ar 16:9`

### B. Cinematic Storyboard Panel Layout (故事板单帧排版)
To lock the cinematic staging, framing, camera angle, and composition, the prompt must enforce an **annotated, high-fidelity film panel**:
- **Fixed Style Keywords**: `cinematic storyboard panel, shot progression panel, clean film sketch, detailed line art, technical camera annotation, focal length 35mm, shot composition, film strip style, industrial concept art --ar 16:9`
- **Technical Annotations**: Must declare exact camera parameters (e.g. `Shot Type: Medium Close-Up`, `Focal Length: 35mm`, `Aspect Ratio: 16:9`) inside the prompt to force the model to render authentic lens characteristics.
- **Default Prompt Structure**:
  `[Bilingual Prompts]: Cinematic storyboard panel of [Scene Description], detailed line art, film strip style, technical camera annotation, shot composition --ar 16:9`

---

## 3. Top-Level Package

Use this top-level JSON structure:

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

---

## 4. Character Asset JSON

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
    "skin": "string",
    "hair_shape": "string",
    "hair_color": "string"
  },
  "costume_system": {
    "outerwear": "string",
    "inner_layers": "string",
    "lower_garment": "string",
    "accessories": []
  },
  "banana2_prompt_package": {
    "system_intent": "Generate a single 16:9 cinematic character asset sheet conforming to the GlitterPixely turnaround standard.",
    "generation_prompt": "string",
    "chinese_prompt": "string",
    "consistency_notes": ["string"]
  }
}
```

---

## 5. Scene & Storyboard Handover Rules

- Always provide **bilingual prompts (English + Chinese)** for every character, scene, prop, and storyboard panel.
- Ensure the storyboard prompts strictly contain the technical camera annotations and film strip styling to ensure they match the GlitterPixely layout standard.
