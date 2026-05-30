---
name: video-reverse-engineer
description: Hollywood Prototype Reconstruction (好莱坞原型重构) System. Internally deconstructs reference videos across 10 layers, performs style/theme migration, and outputs a single `.md` file containing separate Chinese/English image2 prompts with S01/A01 labels and sub-labels, and <=15s seedance2.0 prompts with separated user reference reminders.
---

# Video Prototype Reconstruction System (好莱坞原型重构系统)

Use this skill when the user inputs a video file or a YouTube link. The system will internally deconstruct it, perform style-switching (e.g. animation to photorealism) and theme migration, and output a single, copy-pasteable `.md` file. 

This deliverable contains all static assets (characters, scenes, props) and storyboards formatted under the **GlitterPixely Standard Layout & Labeling (Character sheets as turnarounds with top A01/A02 and sub-labels; storyboards as film panels with top S01/S02 and camera annotations)** with strictly **separated English/Chinese prompt blocks**, and chronological <=15s video segment prompts for `seedance2.0` that leverage All-Round Reference (全能参考) with **separated user reference reminders** to ensure absolute visual consistency.

---

## 1. Core Operating Principles

- **Internalization (内部自反应机制)**: The entire 10-layer deconstruction and thematic mapping process occurs *internally* within the agent's reasoning. The final response to the user must be the **completed `.md` deliverable** containing the copy-pasteable assets, storyboards, and video prompts. Do not output lengthy, redundant analytical logs.
- **Strict Separation of Language Blocks**: Deliver prompts in separate, clearly marked blocks (`【英文提示词】` and `【中文提示词】`). Never mix languages in a single prompt body to keep them 100% clean for copying.
- **GlitterPixely Layout & Labeling Standard**: Fixes the layout and format of image2 outputs. Character sheets must be formatted as **orthographic turnaround sheets** (front/side/back view with light-grey background) with a rendered top label `"A01"` (or `"A02"`) and sub-labels (`"front view"`, `"side view"`, etc.) rendered underneath each corresponding panel. Storyboards must be formatted as **annotated cinematic panels** with a rendered top label `"S01"` (or `"S02"`) and focal length/camera type annotations.
- **User Reference Reminders (💡 后端引用提示 - 绝不放进提示词)**: Provide clear, actionable instructions explaining which assets need to be loaded as references in seedance2.0. These reminders must be placed in a dedicated section and **MUST NOT** be included inside the prompt body itself.
- **Strict 15s Segment Ceiling**: Since seedance2.0 can render at most 15 seconds at a time, the video timeline must be partitioned into blocks of at most 15 seconds (e.g., `0-15s`, `15-30s`). If a scene is longer, split it across subsequent segments while maintaining strict continuity.
- **All-Round Reference (全能参考) Binding**: Every Seedance prompt block must include explicit instructions loading the `image2` generated assets (`@角色`, `@场景`, `@故事板`) to lock pixel-perfect visual continuity.

---

## 2. Default Operating Rule

The default execution sequence is:
`Upload Video/Link -> Internal 10-Layer Deconstruction & Migration -> Output a Single .md Deliverable (image2 bilingual assets & storyboards under the GlitterPixely labeling standard + seedance2.0 <=15s prompts with separated reminders).`

---

## 3. References & Specifications

Ensure you read and strictly enforce the following documents:
- [prototype-reconstruction-framework.md](references/prototype-reconstruction-framework.md) for the 10-layer standard, style-switching, and theme-shifting rules.
- [backend-handover-protocol.md](references/backend-handover-protocol.md) for image2 JSON formats, GlitterPixely specs, separate language blocks, top labels, and user reference reminders.
- [prompt-compilation-playbook.md](references/prompt-compilation-playbook.md) for the 8 core video prompting rules (Clear duties, Continuity first, Physical camera, Space VFX, Performance emotion, Change chains, Safe zones, and Static/Dynamic separation).
- [seedance-package-spec.md](references/seedance-package-spec.md) for the timeline table, 15s budgeting, and All-Round Reference binding rules.
- [banana2-asset-json-spec.md](references/banana2-asset-json-spec.md) for Google Banana 2 JSON formatting and GlitterPixely keyword standards.
- [cinematography-design-guide.md](references/cinematography-design-guide.md) for 38-type camera techniques, SEG mapping matrix, and mirror symmetry principles.
- [seedance-prompt-craft-notes.md](references/seedance-prompt-craft-notes.md) for 36 camera terminology writing rules and English prompt examples.

---

## 4. Stages of Production

### Stage 1 & 2: Internal Deconstruction & Migration
- Perform the 10-layer deconstruction internally across plot, character, style, prop, dialogue, composition, camera, VFX, SFX, and pacing.
- Perform the style-switching (animation to photorealism) and theme migration internally based on the user's requirements.

### Stage 3 & 4: Script & Review Lock
- Draft the reconstructed script structure and execute the expert reviews internally to ensure the score is `>= 90` and AI feasibility passes.

### Stage 5: Producer Breakdown
- Extract characters, scenes, and props, and plan the timeline segment divisions strictly utilizing the <=15-second budget.

### Stage 6: image2 Bilingual Asset Generation (GlitterPixely Standard)
Generate the copy-pasteable assets section containing:
- Character sheet prompts (facial closeup, 3 views, 9-grid clothing details, flat lighting, solid light-grey background).
- Scene grids and multi-angle scene descriptors.
- Symbolic and recurring prop design parameters.
- **Must provide separate English and Chinese prompts** for every asset.
- **Enforce top labels ("A01/A02") and sub-view labels**.
- **Separate user reminders cleanly from prompt bodies**.

### Stage 7: image2 Bilingual Storyboard Generation (GlitterPixely Standard)
Design individual storyboard frames representing the narrative joints:
- Frame ID, camera framing, action, lighting, and composition.
- **Must provide separate English and Chinese prompts** for every storyboard frame, structured as cinematic panels with top labels (`"S01/S02"`) and focal length/camera type annotations.
- **Separate user reminders cleanly from prompt bodies**.

### Stage 8: seedance2.0 15s Prompts Compilation
Compile the chronological segment prompts:
- Every segment has a **strict ceiling of 15 seconds** (e.g. `0-15s`, `15-30s`).
- If a scene spans longer than 15s, split it across subsequent segments, carrying forward the ending frame and assets to maintain seamless visual continuity.
- Include explicit **All-Round Reference (全能参考)** instructions loading the `@角色`, `@场景`, and `@故事板` images generated by image2.
- Enforce the 8 prompting rules in [prompt-compilation-playbook.md](references/prompt-compilation-playbook.md).
- **Separate user reminders cleanly from prompt bodies**.

---

## 5. Handover Delivery

Deliver the completed work as a **single, clean, copy-pasteable `.md` file** utilizing the template in [backend-handover-package-template.md](assets/backend-handover-package-template.md), providing the user with all necessary bilingual image2 prompts and <=15s Seedance prompts. Keep the presentation professional, clean, and structured.
