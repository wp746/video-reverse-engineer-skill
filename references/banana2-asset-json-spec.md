# Banana 2 Asset JSON Spec

Use this file when generating asset-package prompts for Google Banana 2 (image2).

---

## 1. Goal

Do not output loose asset prose only. Output a stable JSON package that:
- preserves creative intent
- captures enough specificity for Banana 2 image generation
- can be reused by later production steps
- enforces a strict, fixed layout and style based on the **GlitterPixely professional layout methodology** to prevent visual drift.
- enforces a strict **Labeling & Reminder separation protocol** to enable precise downstream referencing.

---

## 2. GlitterPixely Standard Layout & Labeling Guidelines (好莱坞排版与标注设计标准)

To ensure absolute layout and style consistency across image2 generated images, every asset sheet and storyboard prompt must adhere to these fixed visual and text-rendering formulas:

### A. Character Model Sheet Layout & Labeling (资产板排版与文字标注)
To lock character features, clothing, and proportions, the prompt must enforce an **orthographic, flat-lit turnaround sheet with rendered text labels**:
- **Fixed Style Keywords**: `character model sheet, character design sheet, turnaround, multiple angles, front view, side view, back view, expressions sheet, orthographic technical illustration, clean flat lighting, solid light grey background, concept art, high consistency --ar 16:9`
- **Top Subtitle Label (英文字幕标签)**: Must instruct image2 to render a clean white text label saying `"A01"` (or `"A02"`, `"A03"`, etc. corresponding to the asset number) at the top center of the sheet.
- **Sub-Image Labels (小图底部标注)**: Must instruct image2 to render small, clean white text labels saying `"front view"`, `"side view"`, `"back view"`, and `"face closeup"` directly underneath each corresponding turnaround view.
- **Default Prompt Structure**:
  `Character model sheet of [Character Details], turnaround showing front view, side view, back view, expressions sheet, detailed technical illustration, solid light-grey background. The text label "A01" is written as clean white text at the top center of the sheet. Small, clean white text labels saying "front view", "side view", "back view", and "face closeup" are rendered directly underneath each corresponding view --ar 16:9`

### B. Cinematic Storyboard Panel Layout & Labeling (故事板单帧排版与文字标注)
To lock the cinematic staging, framing, camera angle, and composition, the prompt must enforce an **annotated, high-fidelity film panel**:
- **Fixed Style Keywords**: `cinematic storyboard panel, shot progression panel, clean film sketch, detailed line art, technical camera annotation, focal length 35mm, shot composition, film strip style, industrial concept art --ar 16:9`
- **Top Subtitle Label (英文字幕标签)**: Must instruct image2 to render a clean white text label saying `"S01"` (or `"S02"`, `"S03"`, etc. corresponding to the storyboard number) at the top center of the panel.
- **Technical Annotations**: Must declare exact camera parameters (e.g. `Shot Type: Medium Close-Up`, `Focal Length: 35mm`, `Aspect Ratio: 16:9`) inside the prompt to force the model to render authentic lens characteristics.
- **Default Prompt Structure**:
  `Cinematic storyboard panel of [Scene Description], detailed line art, film strip style, technical camera annotation, shot composition. The text label "S01" is written as clean white text at the top center of the panel --ar 16:9`

---

## 3. Bilingual Prompt & Reminder Separation Protocol (中英文分离与提示规则)

1. **Strict Language Separation**: Deliver prompts in separate, clearly marked blocks (`【英文提示词】` and `【中文提示词】`). Never mix languages in a single prompt body.
2. **User Reference Reminders (💡 后端引用提示)**:
   - Provide clear, actionable instructions explaining which assets need to be loaded as references in seedance2.0 (e.g. telling the user to generate `A01` and `S01` in image2, and then reference `A01.png/front view` and `S01.png` in Seedance).
   - **MUST NOT** include these reminder notes inside the prompt body itself, ensuring the generator receives only clean visual descriptors.

---

## 4. Top-Level Package

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

## 5. Character Asset JSON

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
    "system_intent": "Generate a single 16:9 character sheet conforming to the GlitterPixely turnaround standard and containing rendered labels.",
    "generation_prompt": "string",
    "chinese_prompt": "string",
    "consistency_notes": ["string"]
  }
}
```
