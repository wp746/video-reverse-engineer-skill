# Backend Handover Protocol (image2 + seedance2.0)

Use this reference during **Stage 5 (Producer Breakdown)** and **Stage 8 (Seedance Prompt Compilation)** to prepare the final deliverable for the production backend.

---

## 1. The Handover Stance

The front-end design must deliver an **unambiguous, copy-pasteable production package** to the backend models. The backend consists of:
- **image2** (Google Banana 2): Handles static asset generation (consistent characters, scenes, and key props).
- **seedance2.0**: Handles dynamic motion rendering (stitching segments based on assets).

To avoid generation drift, the handover package enforces a strict **Asset-prompt Binding Mechanism** using the `@` prefix.

---

## 2. image2 (Banana 2) Handover Protocol

The static asset package must be formatted as a stable, parser-ready JSON document.

### Character Asset Specifications
For every major character, deliver the exact JSON structure defined in [Banana 2 Asset JSON Spec](banana2-asset-json-spec.md). Ensure the `banana2_prompt_package.generation_prompt` incorporates our **Style Switching Rules**:
- Explicitly dictate the 16:9 multi-view sheet.
- Bind targeted physical materials (e.g. skin pores, fabric textures) rather than generic keywords.
- Define a white or neutral gray background to ease clean alpha-channel extraction.

### Scene Master Grid Specifications
Deliver a `scene_master_grid` JSON. It establishes the overall scene registry and spatial color palette, preventing environment color drift across Seedance segments.

### Key-Scene Multi-Angle Specifications
Deliver a `scene_multi_angle` JSON for critical environments requiring repeated return or complex camera staging. Deliver three precise prompt entries:
- `@场景-001/hero` (Master view establishing geometry).
- `@场景-001/side` (Side view establishing depth).
- `@场景-001/reverse` (Reverse-angle/counterpoint view for character dialogue).

---

## 3. seedance2.0 Handover Protocol

The dynamic motion package must be delivered as a structured markdown document containing the **Timeline Table** and **Segment Execution Prompts**.

### Timeline Table Structure
Deliver a chronological segment registry mapping:
- Segment ID (e.g. `SEG01_0-12s`)
- Camera Framing & Angle
- Camera Motion Profile
- Bound Assets (`@角色-001`, `@场景-001`, `@道具-001`)
- Dramatic Pacing Task

### Segment Prompt Compilation Rules
Every segment prompt must follow the standard 6-part block and enforce the 8 rules in the [Prompt Compilation Playbook](prompt-compilation-playbook.md):

```text
=========================================
[SEGMENT_ID_TIME]: e.g., SEG01_0-12s
【关联资产】: @角色-001, @场景-001, @道具-001
【安全区规划】: 
  - 0-1.5s: Hold initial composition, stable breathing micro-motion.
  - 10.5-12.0s: Transition hold, lock framing to prevent stitching warp.
【连续性锚点】: Costume layers, hair shape, camera angle height, light source direction.
【出片提示词 (Seedance 2.0 Feeding Prompt)】:
(Playbook-Compliant prompt body, written in English for high model fidelity)
=========================================
```

---

## 4. Front-to-Back Matching Principle

Before delivering the package, the agent must run a strict **Handover Consistency Scan**:
1. **Asset Completeness**: Every `@角色`, `@场景`, or `@道具` referenced in the Seedance segment prompts must exist as a fully defined asset in the `image2` JSON package. No phantom assets are allowed.
2. **Material Synchronization**: If a costume layer or prop material is changed during style switching (e.g. from an animated robe to a heavy wool coat), the description in `image2`'s `costume_system` must match the `costume` description in the Seedance video prompt exactly.
3. **Spatial Continuity**: The lighting direction defined in the `image2` scene grid must match the lighting vector declared in the seedance prompt's environment section.
