# Prompt Compilation Playbook

Use this reference when compiling video-generation prompts for **Seedance 2.0** or **Kling** after assets are locked and the storyboard is structured.

---

## The Core Stance

Premium AI video prompts are not defined by chaotic adjective piles or length. They are defined by **precision, physical logic, and structural boundaries**. 

Always separate static consistency (handled by [Banana 2 Asset Pack](banana2-asset-json-spec.md)) from dynamic motion (handled by the video prompt).

---

## The 8 Industrial Prompting Rules

### Rule 1: Clear Shot Duties (镜头职责清晰)
Every prompt must slice time and allocate clear narrative or visual tasks to specific seconds. Do not let the model guess the pacing.
- **Vague**: "A character walks in a busy street and then looks back in shock."
- **Industrial**: 
  - `0-3s`: Establish the character moving forward at a steady pace through a dense crowd.
  - `3-6s`: A sudden loud noise occurs behind; the character halts abruptly, shoulder tensing.
  - `6-10s`: The character turns their head 90 degrees back, eyes widening in shock.

### Rule 2: Continuity First, Changes Second (先锁连续性，再写变化)
Always establish the consistent anchor points (character identity, clothing layers, spatial geography, and lighting) before introducing any action or deformation.
- **Vague**: "A girl runs in the forest, she has black hair and a red dress."
- **Industrial**: 
  - `Anchors`: Bind `@char-001` (black hair semi-tied, dark grey tunic with collar embroidery) in `@scene-001` (dusk forest, soft orange sun shafts filtering through birch branches).
  - `Motion`: The character runs forward at a frantic pace, her dress hem catching on low ferns.

### Rule 3: Physical-Level Camera Motions (镜头运动具体到物理层)
Describe camera motion with physical attributes: height, trajectory, speed, mechanical/handheld feel, lag/shudder, and the final resting frame.
- **Vague**: "Cinematic tracking shot of a man."
- **Industrial**: "Camera begins at waist height, tracking laterally from right to left on a mechanical slider. The movement is smooth and constant. As the character turns, the camera undergoes a subtle handheld lag before locking onto a clean medium close-up."

### Rule 4: Space-and-Material-Anchored VFX (特效依附材质与空间)
Special effects must not float in abstract space. They must interact with physical boundaries, surface textures, reflectivity, and gravity.
- **Vague**: "Awesome magical energy swirls around."
- **Industrial**: "Ethereal light-blue energy flows along the physical grain of the wooden table, illuminating the microscopic cracks. The light reflects off the character's cheekbones, casting dynamic cyan shadows, and kicking up fine glowing dust particles that float suspended in the immediate atmosphere."

### Rule 5: Performance-Based Emotions (情绪靠表演与光影)
Replace empty emotional words (e.g., "sad", "shocked", "epic") with physical indicators: breathing rate, eye contact, muscle tension, neck posture, and shadow intersection.
- **Vague**: "The protagonist is extremely sad and premium looking."
- **Industrial**: "The character's shoulders slump slightly, chest rise-and-fall decelerating. Their gaze drifts downward, shifting from the key side-light into deep facial shadow, lips parted slightly, conveying a sense of profound exhaustion."

### Rule 6: The Chain of Changes (控制变化链)
A complete video prompt should govern the causal loop of changes:
1. **Subject Action**: What the character/object does.
2. **Camera Motion**: How the view adapts.
3. **Environment Reaction**: How dust, light, or water respond to the action.
4. **Sound/Pacing Synchronization**: The implied acoustic beat.
5. **Recovery/Hold**: How the action settles.

### Rule 7: Safe Zones for Editing (留下安全区)
Never pack high-velocity actions or transitions into the first or last 1.5 seconds of a prompt. Provide "handle space" (safe zones) to ensure clean editing and stitching without warp artifacts.
- `0-1.5s`: Hold initial composition with subtle micro-motions (breathing, ambient wind) to lock stability.
- `1.5-8.5s`: Execute primary action and camera translation.
- `8.5-10s`: Transition into a stable hold to allow downstream video cross-dissolves or cuts.

### Rule 8: Strict Separation of Static and Dynamic (动静分工)
Do not re-describe a character's nose shape, height, or coat buttons in the video prompt if they are already defined in the character sheet JSON. Wasting tokens on static parameters increases model drift. Keep the video prompt focused purely on **the delta of change**.

---

## The Seedance 2.0 Prompt Structure

Every shot prompt compiled in Stage 8 must adopt the following template:

```text
[SEGMENT_ID_TIME]
【关联资产】: @角色 / @场景 / @道具
【安全区规划】: 首尾各 1.5 秒锁定稳定微动。
【连续性锚点】: 锁定外形、色彩、光照方向。
【执行提示词】:
(Prompt Body)
1. Establish: [Rule 2 & 7: 0-1.5s Initial state, assets & spatial setup]
2. Action Chain: [Rule 1 & 6: Primary dramatic motion & subject action]
3. Camera Path: [Rule 3: Physical camera height, speed, and tendency]
4. VFX & Space: [Rule 4: Material-anchored effect reaction]
5. Performance & Light: [Rule 5: Emotional lights, shadows, and subtle facial beats]
6. Recovery: [Rule 7: Final hold structure]
```

---

## Comparison Matrix

| Aspect | Amateur Prompt | Industrial Prompt (This Playbook) |
| :--- | :--- | :--- |
| **VFX** | "Epic golden light glow." | "Golden liquid light flows strictly along the engraved steel grooves, emitting a soft amber illumination that bounces off the character's leather gloves." |
| **Camera** | "Drone shot." | "High-angle camera slowly cranes downward from 5 meters to 2 meters, maintaining a steady 15-degree pitch, slowly revealing the courtyard geography." |
| **Emotion** | "He looks angry." | "His jaw clenches, facial muscles tightening under low-key red rim-lighting. His eyes narrow and lock onto the target, breathing quickening." |
| **Pacing** | One flat description block. | Segmented timeline with explicit safe zones at the head and tail of the shot. |
