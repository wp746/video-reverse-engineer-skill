---
name: video-reverse-engineer
description: Hollywood Prototype Reconstruction (好莱坞原型重构) Creative Engine. Deconstructs uploaded videos across 10 distinct layers, performs style-switching (e.g. animation to photorealism) and theme migration, and outputs a copy-pasteable handover package for image2 (Banana 2) and seedance2.0 backends.
---

# Video Prototype Reconstruction System (好莱坞原型重构系统)

Use this skill when the user wants to deconstruct a creative short film or reference video, extract its deep structural blueprint ("the skeleton"), migrate it into another style (e.g. animation to photorealism) or theme, and output exact asset JSON and video prompts for `image2` (Banana 2) + `seedance2.0` rendering backends.

---

## 1. What This Skill Is

This is not a simple video summarizing tool. It is an **industrial-grade Hollywood front-end reconstruction workflow**:

```text
[Reference Video Ingestion]
         │
         ▼
[Stage 1: 10-Layer Deconstruction] (Plot, Character, Style, Prop, Dialogue, Composition, Camera, VFX, SFX, Pacing)
         │
         ▼
[Stage 2: Style & Theme Migration] (Animation -> Photorealism style-switching, Theme mapping)
         │
         ▼
[Stage 3: Reconstructed Script] (Locked narrative sequences, spatial geography)
         │
         ▼
[Stage 4: Sequential Review Gating] (Committee score >= 90, minimum thresholds)
         │
         ▼
[Stage 5: Producer Breakdown & Handover] (Asset mapping & continuity risk plans)
         │
         ▼
[Stage 6: image2 Asset JSON Package] (Consistent character sheets, scene grids, prop JSON)
         │
         ▼
[Stage 7: Storyboard & Timeline] (Time-sliced SEG timeline tables)
         │
         ▼
[Stage 8: seedance2.0 Prompts Compilation] (Playbook-compliant feeding prompts)
```

---

## 2. Default Operating Rule

The default execution sequence is:
`Deconstruct (10 layers) -> Style & Theme Migration -> User Review -> Script Writing -> Review Board Gating -> Producer Handover -> image2 JSON Assets -> Storyboard -> seedance2.0 Prompts Package.`

**CRITICAL CONSTRAINT**: Do not skip script review or skip directly from deconstruction to prompts. Do not generate video prompts before image2 static assets are defined and bound using the `@` syntax.

---

## 3. Ingestion & Routing

Upon receiving user videos, links, or timestamps:
- Read [video-input-ingestion.md](references/video-input-ingestion.md) to parse duration, aspect ratio, boundaries, and transcript.
- Define the production **Mode Routing** early:
  - `15s emotion short` (Frame-by-frame emotion curves, second-level accuracy).
  - `30-60s theme short` (Segmented production built around <=15s Seedance units).
  - `1-3min narrative short` (Shot-block pacing, high transition control).

---

## 4. References & Specifications

Ensure you read and strictly enforce the following documents:
- [prototype-reconstruction-framework.md](references/prototype-reconstruction-framework.md) for the 10-layer standard, style-switching, and theme-shifting rules.
- [backend-handover-protocol.md](references/backend-handover-protocol.md) for image2 JSON formats and seedance2.0 prompt parameter requirements.
- [script-review-order.md](references/script-review-order.md) for the committee review sequence and threshold gating.
- [asset-package-spec.md](references/asset-package-spec.md) for character, scene, and prop breakdown guidelines.
- [banana2-asset-json-spec.md](references/banana2-asset-json-spec.md) for Google Banana 2 JSON formatting.
- [producer-handoff.md](references/producer-handoff.md) for the producer's handover package structure.
- [prompt-compilation-playbook.md](references/prompt-compilation-playbook.md) for the 8 core video prompting rules (Clear duties, Continuity first, Physical camera, Space VFX, Performance emotion, Change chains, Safe zones, and Static/Dynamic separation).
- [seedance-package-spec.md](references/seedance-package-spec.md) for the timeline table and segment prompt structure.

---

## 5. Stages of Production

### Stage 1: 10-Layer Deconstruction
Deconstruct the reference video across the 10 Hollywood dimensions detailed in [prototype-reconstruction-framework.md](references/prototype-reconstruction-framework.md):
1. **Plot (剧情)**: Structural beats.
2. **Character (角色)**: Visual anchors and archetypes.
3. **Style (风格)**: Medium, lighting, grading, textures.
4. **Prop (道具)**: Functional and symbolic props.
5. **Dialogue (台词)**: VO strategy and subtext.
6. **Composition (构图)**: Staging, focal length, depth-of-field.
7. **Camera Movement (运镜)**: Physical translation profiles.
8. **VFX (特效)**: Spatial elemental effects.
9. **SFX (音效)**: Sound acoustics and cues.
10. **Pacing (叙事节奏)**: Compression and cutting rate.

Use the human-readable [prototype-reconstruction-template.md](assets/prototype-reconstruction-template.md) for formatting.

### Stage 2: Style & Theme Migration
Perform the creative translation as requested by the user:
- **Style-Switching**: When converting from animation/3D to cinematic photorealism, strip away non-photoreal layers and substitute high-fidelity textures (skin pores, clothing seams, physical lighting refraction, and lens limitations).
- **Theme Migration**: Map the 10-layer structure onto a new thematic container. Define the mapping matrix for characters, props, scenes, and settings.

Propose 3 distinct creative migration directions for user selection before writing the script.

### Stage 3: Reconstructed Script Staging
Draft the locked script for the selected migration direction, containing:
- Premise, theme statement, and structural beats.
- Scene geography (interior/exterior, time, main light angle).
- Script action blocks ready for asset breakdown.

### Stage 4: Sequential Review Gating
Conduct the expert committee review using the sequence in [script-review-order.md](references/script-review-order.md):
1. Chief Director Review (Weight: 20, Threshold: 18)
2. Screenwriter Review (Weight: 20, Threshold: 18)
3. Cinematography Review (Weight: 15, Threshold: 13)
4. Art/Style Review (Weight: 10)
5. Costume/Props Review (Weight: 10)
6. Post/Sound Review (Weight: 10)
7. AI Feasibility Review (Weight: 15, Threshold: 13)

**Gating Rule**: Total score must be `>= 90`. Vetoes by key roles halt the pipeline immediately for script rework.

### Stage 5: Producer Handover
Upon script approval, extract P1, P2, P3 characters, scenes, and props. Prepare the Segment Plan (e.g. `SEG01_0-12s`) and define continuity risk mitigations. Follow the [producer-handoff.md](references/producer-handoff.md) guidelines.

### Stage 6: image2 (Banana 2) Asset JSON Package
Output the parser-ready, copy-pasteable JSON package containing:
- Character assets sheet prompts (closeup, multi-views, 9-grid details).
- Scene master grids and multi-angle scene descriptors.
- Symbolic and recurring prop JSON blocks.

Follow [banana2-asset-json-spec.md](references/banana2-asset-json-spec.md) and use the templates in [assets/](assets/).

### Stage 7: Storyboard & Timeline
Generate the timeline table slicing the film into controllable segment blocks (typically <=15 seconds each). Map segment duration, framing, bound assets (`@角色`, `@场景`, `@道具`), and camera profiles.

### Stage 8: seedance2.0 Prompts Compilation
Compile the dynamic motion prompts. For every segment, generate the playbook-compliant feeding prompt incorporating:
- Chronological time-slices.
- Head/tail 1.5s transition safe zones with stable micro-motions.
- Explicit physical camera trajectories, space-anchored VFX, and performance-based emotions.

Use the template in [backend-handover-package-template.md](assets/backend-handover-package-template.md).

---

## 6. Output Discipline & Handover Delivery

The final delivery must be formatted using the **[backend-handover-package-template.md](assets/backend-handover-package-template.md)** to provide the production backend with clean, copying-friendly code and text modules. 

Do not combine intermediate deconstruction files with final prompt outputs unless explicitly asked. Always maintain a professional, clean, and highly structured presentation.
