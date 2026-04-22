# Seedance 2.0 Prompt Craft Notes

> 从 awesomevideoprompts.com（2201+ 提示词案例库）提炼的实战经验。
> 用途：补充 seedance-package-spec.md，聚焦提示词写作层面的可执行技巧。
> **v2.0 升级**: 新增第十二章运镜设计写作（基于38种专业运镜技巧分类体系）

## 一、提示词宏观结构

高质量 Seedance 提示词通常包含以下分层，按顺序书写：

```
1. 格式声明    FORMAT / STYLE / MODE
2. 主体描述    SUBJECT（外貌、服装、状态、情绪）
3. 环境场景    ENVIRONMENT（空间、天气、时间）
4. 光影色彩    LIGHTING + COLOR LOGIC
5. 情绪基调    MOOD（一句话定义）
6. 运镜方式    CAMERA（每个镜头单独标注）
7. 动作链      ACTION SEQUENCE（动词驱动）
8. 物理反馈    PHYSICAL FEEDBACK（冲击、震动、速度感）
9. 声音氛围    SOUND / AMBIENCE
10. 技术标签   TECH TAGS（分辨率、帧率、色彩空间）
```

## 二、时间轴分段规范

### 短视频（15s 情绪短片）

秒级精度控制，每个时间段聚焦一个核心动作/情绪：

```
0-2s  建立镜头 / 钩子
2-5s  状态转变 / 冲突启动
5-9s  强度递进 / 高潮推进
9-12s 转折 / 悬念
12-15s 落点 / 释放
```

### 中短视频（30-60s 主题短片）

以 Seedance 的 ≤15s 上限为基准切分段落，推荐 2-4 段：

```
SEG01_0-12s   开场建立 + 钩子
SEG02_12-27s  核心内容 / 冲突
SEG03_27-40s  高潮 / 转折
SEG04_40-53s  收束 / CTA
```

段落长度跟随戏剧节奏，不要机械填满 15s。

### 中长片（1-3min 叙事短片）

段落数量不设上限，以镜头块（shot-block）为单位：

- 每个生产单元 ≤15s
- 戏剧动作完成就结束，不强行拉长
- 关键转折点、揭秘点、情绪峰值用秒级精度标注

## 三、运镜术语速查（v2.0 扩展版 — 38种专业运镜分类体系）

> 基于「38种运镜技巧分类总表」六大类完整扩展。每个运镜标注：编号、中英文名、适用场景、Seedance 提示词写法示例。

### 3.1 推拉变焦类 (Zoom & Focus)

| # | 中文 | 英文 | 适用场景 | Seedance 写法示例 |
|---|------|------|---------|-------------------|
| 01 | 慢推 | Slow Dolly In / Push In | 情绪渐进、角色内心靠近 | "camera slowly pushes in at 0.5cm/s, imperceptible approach" |
| 02 | 急推 | Crash Zoom / Smash Zoom | 惊悚揭示、冲击瞬间 | "rapid crash zoom to face in 0.3s, disorienting push" |
| 03 | 慢拉 | Slow Dolly Out / Pull Back | 释然、孤独感、空间展示 | "camera gently pulls back revealing isolation, slow retreat" |
| 04 | 光学变焦推拉 | Optical Zoom (In/Out) | 焦点切换、心理距离变化 | "lens zooms from 50mm to 85mm during monologue" |
| 05 | 变焦+移动反向 | Dolly Zoom / Vertigo Effect | 迷幻、时空扭曲、量级跃迁 | "dolly out while zooming in — background warps, subject stays same size" |
| 06 | 变焦焦点切换 | Rack Focus / Focus Pull | 前后景关系、威胁暗示 | "focus pulls from her eyes to the shadow behind her shoulder" |

### 3.2 垂直水平移动类 (Vertical & Horizontal Movement)

| # | 中文 | 英文 | 适用场景 | Seedance 写法示例 |
|---|------|------|---------|-------------------|
| 07 | 下摇(俯摇) | Tilt Down | 压抑蔓延、危险从下至上 | "camera tilts slowly down from face → chest → ground → darkness below" |
| 08 | 上摇(仰摇) | Tilt Up | 希望、反抗、从地面到天空 | "camera tilts upward from ground debris to her standing silhouette against light" |
| 09 | 垂直升降 | Pedestal Up/Down | 坠落共感、同步起降 | "camera descends at matched speed as she falls, ground-level arrival sync" |
| 10 | 平移跟拍 | Tracking Shot / Dolly Track | 流畅跟随、环境展示 | "camera tracks laterally at 4m distance, matching run speed exactly" |
| 11 | 抬升/升降 | Crane Up/Down | 升华、神性、Y轴叙事 | "crane rises as she ascends, following vertical trajectory to apex" |
| 12 | 航拍前推 | Drone Push-In | 大场景进入、史诗开场 | "drone pushes forward through clouds toward isolated figure on cliff edge" |
| 13 | 弧形移动 | Arc Shot / Curved Dolly | 关系动态、环绕预备 | "camera moves along 90° arc around couple, revealing third party watching" |
| 14 | 长焦压缩 | Long Lens Compression | 孤立感、背景压迫 | "85mm compression isolates her against creamy bokeh city wall" |
| 15 | 荷兰角 | Dutch Angle / Canted Angle | 不安、失衡、危机潜藏 | "camera tilts 12° off horizontal, subliminal unease throughout shot" |
| 16 | 侧向跟踪 | Side Tracking / Lateral Truck | 动作跟随、战斗侧面视角 | "35mm side tracking at 3m left, motion-blurred background, clean combat frame" |
| 17 | 轨道环绕 | Orbit Shot | 角色展示、高光时刻 | "camera orbits 180° around her, golden hour backlight creating rim light cycle" |

### 3.3 环绕旋转类 (Rotation)

| # | 中文 | 英文 | 适用场景 | Seedance 写法示例 |
|---|------|------|---------|-------------------|
| 18 | 甩镜头 | Whip Pan | 快速转场、节奏标点 | "whip pan left following sword swing direction, 0.15s motion blur acceptable" |
| 19 | 360°全景旋转 | 360° Spin / Panorama | 展示全貌、沉浸环绕 | "full 360° rotation around frozen moment, environment reveals from all angles" |
| 20 | 快速360° | Rapid 360° Orbital | 混乱战斗、绝望包围 | "frantic 360° orbital, 1.5 revolutions in 3s, motion streaks on background" |
| 21 | 旋转加速 | Spin Acceleration | 情绪螺旋失控 | "orbital speed increases linearly: 6s/rev → 3s/rev → 1.5s/rev over 10s" |

### 3.4 特殊视角类 (Special Perspectives)

| # | 中文 | 英文 | 适用场景 | Seedance 写法示例 |
|---|------|------|---------|-------------------|
| 22 | 微距镜头 | Macro Shot (Extreme Close-Up) | 细节放大、纹理质感、微观世界 | "extreme macro: eye fills 80% of frame, iris texture visible, shallow DOF" |
| 23 | 主观镜头 | POV Shot | 沉浸代入、角色视角 | "POV from her perspective: hands gripping hammer, breath fogging in cold air" |
| 24 | 过肩镜头 | Over-the-Shoulder (OTS) | 对话、对峙、关系构图 | "OTS from behind enemy's shoulder, she is visible in foreground threat pose" |
| 25 | 穿梭镜头 | Through-Shot / Frame-Within-Frame | 突破隐喻、绝处逢生 | "camera moves through gap between monster's mandibles, emerges to reveal her counter-strike" |
| 26 | 遮挡揭示 | Reveal Behind Obstruction | 悬念揭晓、BOSS登场 | "foreground debris/parting figures slowly reveal boss silhouetted in smoke beyond" |
| 27 | 倒影/镜像 | Reflection Shot | 双重身份、内心外化 | "her reflection in puddle shows different expression than her actual face" |
| 28 | 顶视/上帝视角 | God's Eye View / Top-Down | 全局俯瞰、超越人类尺度 | "top-down 90° view: her EMP shockwave expanding in perfect ring across battlefield grid" |
| 29 | 低角度仰拍 | Low Angle / Hero Shot | 英雄化、力量感、压迫反转 | "ultra-low angle 15° above ground looking up, she towers over fallen enemies" |
| 30 | 高角度俯拍 | High Angle / Vulnerability Shot | 弱小、孤立、被围困 | "45° high angle looking down at her cornered by swarming shadows" |
| 31 | 手持摄影 | Handheld Camera | 纪实紧张、生理性不安 | "handheld micro-jitter throughout, intensity increasing with proximity to threat" |
| 32 | FPV穿越机 | FPV Drone Shot | 极速穿梭、第一人称运动 | "FPV drone weaving through steel beams at 60km/h, motion blur periphery only" |
| 33 | 一镜到底 | One-Take / Continuous Shot | 时间连续性、真实紧迫感 | "one continuous take, no cuts, camera never leaves the action space for 15s" |

### 3.5 引导跟随类 (Following & Guiding)

| # | 中文 | 英文 | 适用场景 | Seedance 写法示例 |
|---|------|------|---------|-------------------|
| 34 | 背影跟拍 | Following Shot from Behind | 孤独旅程、离去、余韵 | "camera follows from 3m behind, capturing her walking into fading light" |
| 35 | 视线引导 | Eyeline Match / Gaze Guide | 注意力引导、威胁方向 | "her gaze directs camera pan right → revealed: enemy emerging from shadow" |
| 36 | 物体引导 | Object-Guided Move | 以物带镜、创意转场 | "camera follows falling feather down through entire scene, landing reveals body" |

---

## 四、运镜叙事设计原则

> v2.0 新增章节。运镜不是装饰，而是**和剧本同等重要的叙事层**。

### 4.1 运镜选择四步法

```
Step 1: 读情绪 —— 这段戏的核心情绪是什么？（恐惧/愤怒/释然/孤独...）
Step 2: 选类型 —— 从六大类中选最匹配的1-3种主运镜
Step 3: 定参数 —— 速度/距离/角度/焦段/持续时间
Step 4: 写理由 —— 为什么这种运镜能最好地表达这个情绪？
```

### 4.2 运镜与剧情的映射矩阵

| 剧情类型 | 推荐主运镜 | 辅运镜 | 避免使用 |
|---------|-----------|--------|---------|
| 开场建立 | Slow Dolly In + Rack Focus | Low Angle | Crash Zoom / Whip Pan |
| 对峙张力 | Tilt Down→Up + Static Hold | Dutch Angle | Handheld jitter |
| 战斗动作 | Side Tracking + Whip Pan + Crash Zoom Hit | Pedestal Down | Static / Slow Dolly |
| 跑酷逃亡 | Lateral Tracking + Crane Up + Long Lens | Dutch Angle (落地时) | Static / Macro |
| 近身缠斗 | Handheld (三阶段强度) + Through-Shot | Rack Focus | Smooth dolly / Wide orbit |
| 能力释放/充能 | Macro → Dolly Zoom → Reveal Behind | - | Handheld / Fast cut |
| BOSS战/高潮 | Rapid 360° + Multi-style per round | Variable per round | Single technique |
| 终极技/决战 | Crane Up → Apex Freeze → Free Fall → Rush In + Macro | Time Dilation effect | Ground-level static |
| 收束/尾声 | Slow Dolly In (镜像对称) + Follow Behind + Tilt Up | Long Lens compression | Crash Zoom / Whip Pan |

### 4.3 运镜节奏设计

运镜有自己的"呼吸节奏"，应与动作/情绪节奏**同频但相位偏移**：

```
动作节奏：   ████░░████░░█████
运镜节奏：   ░░████░░███░░████    （滞后0.5-1s，形成"预判-确认"结构）

原理：
- 动作启动时，运镜先稳住（给观众"要发生了"的预判感）
- 动作执行中，运镜跟进（确认/放大）
- 动作收尾时，运镜 lingering（延展余韵）
```

### 4.4 镜像对称设计原则

当首尾两段存在主题呼应时，运镜也应做精确镜像：

```
镜像对称七维度检查表：
□ 运镜技术相同（如都是 Slow Dolly In）
□ 方向相反或速度不同（推 vs 拉 / 快 vs 慢）
□ 起始位置呼应（同样的机位高度/距离）
□ 焦点转移路径相反（脸→眼镜 vs 眼镜→脸）
□ 光线逻辑互补（暗调冷光 vs 暖调柔光）
□ 表情弧线闭合（准备/专注 → 释然/微笑）
□ 后续衔接不同（→对峙高潮 vs →黑场结束）
```

## 五、角色一致性技巧

### 参考图引用法

```
@ img1 : character reference, main character A, [具体服装/外貌描述], consistent identity throughout
@ img2 : character reference, main character B, [具体服装/外貌描述], consistent identity throughout
```

### 文字锚定法（无参考图时）

在每一段提示词中反复强调以下锚点：
- 面部结构（face structure: narrow jaw, high cheekbones...）
- 发型（hair: shoulder-length black straight hair...）
- 服装层次（wardrobe: layered dark jacket over white t-shirt...）
- 体型姿态（body: athletic build, slight forward lean...）

连续性注意事项写法：
```
Continuity: same face structure, same wardrobe layers, same hair length from previous segment
```

## 六、物理约束声明

高质量提示词会主动声明物理边界，防止 AI 生成不合理画面：

```
推荐写法：
- "grounded physics, no floating"           # 保持物理合理性
- "no extra characters in frame"           # 限制画面中角色数量
- "one continuous take, no cuts"            # 一镜到底
- "no anime, no cartoon style"              # 排除特定风格
- "no glass-breaking, no explosion"         # 限制破坏类型
- "realistic cloth physics"                 # 服装物理真实
- "natural body weight distribution"        # 身体重心自然
```

## 七、感官多层次描述

不要只写视觉，要叠加多个感官维度：

```
视觉：色彩方案、光影类型、材质纹理、运动模糊
听觉：环境音效、脚步声、风声、音乐节奏（描述性标注）
触觉/物理：冲击震动、速度感、重力感、温度（通过画面暗示）
```

示例：
```
视觉：warm golden hour light, deep amber tones, dusty atmospheric haze
听觉暗示：footsteps crunch on dry leaves, distant thunder
物理反馈：camera shakes slightly on impact, cloth ripples from wind gust
```

## 八、风格锚定引用法

直接引用知名风格作为创作锚点，比抽象描述更有效：

```
动漫：
- "like Ufotable or MAPPA"           # 热血战斗
- "Studio Ghibli inspired"            # 治愈温暖
- "Makoto Shinkai lighting"           # 唯美光影

电影：
- "Denis Villeneuve style"            # 史诗科幻
- "Wes Anderson color palette"        # 对称构图
- "Christopher Nolan practical effects" # 实拍质感

纪实：
- "documentary-style texture, film grain"
- "National Geographic cinematography"
```

## 九、技术标签组合

根据项目需求选择标签组合：

```
基础画质：
  8K / 4K / 1080p

帧率：
  24fps cinematic motion blur / 60fps smooth / 120fps slow motion

光影：
  cinematic lighting / HDR / natural lighting / volumetric light
  golden hour / blue hour / neon-lit / moody chiaroscuro

色彩空间：
  filmic color grading / Kodak Portra emulation
  naturalistic film print / desaturated cold tone

质感：
  film grain / hyper-realistic / photorealistic
  soft dreamy / heavy contrast / low-key lighting

设备模拟（可选）：
  shot on Arri Alexa / RED Komodo / IMAX
  anamorphic lens / 35mm film / 16mm
```

## 十、动词驱动原则

用强动词而非静态形容词驱动动作描述：

```
❌ 弱：A warrior stands in the arena
✅ 强：A warrior CHARGES across the arena, sword raised, cloak billowing

❌ 弱：The car moves fast through the city
✅ 强: The car PLUNGES through neon-lit streets, tires SCREAMING, leaving sparks in its wake

❌ 弱：She looks at the camera
✅ 强：She WHIPS toward camera, eyes locked, breath visible in cold air
```

关键强动词库：
charges, bursts, plunges, erupts, smashes, whips, crashes, surges,
leaps, vaults, shatters, spirals, cascades, ripples, ignites,
dissolves, fractures, detonates, ascends, descends, converges

## 十一、完整提示词范例

```
FORMAT: 15s / 2 shots / vertical 9:16
SUBJECT: A lone female samurai, aged 28, sharp jawline, chin-length black hair tied partially back, wearing weathered dark indigo kimono with frayed edges, carrying a notched katana
ENVIRONMENT: Rain-soaked narrow stone alley at dusk, paper lanterns casting warm pools of light, steam rising from grates
MOOD: Melancholic tension, suppressed rage
COLOR LOGIC: Desaturated cold teal base, warm amber accent from lanterns, deep shadows
STYLE: Live-action Japanese period drama, realistic fabric physics, no anime

SHOT FLOW:

0:00-0:07 ESTABLISHING – LOW DOLLY
Camera inches forward at ground level through puddle reflections. The samurai walks TOWARD camera in slow, deliberate steps. Rain streams off her tilted brim hat. Her hand rests on the katana hilt, knuckles pale.
(Camera: low dolly, 24fps, shallow depth of field, anamorphic flare from lantern)

0:07-0:15 ACTION – WHIP PAN TO TRACKING
At frame midpoint she DRAWS the blade in a single fluid motion—whip pan matches the slash direction—camera now TRACKS beside her as she MOVES through three shadow attackers in rapid succession. Each cut is a single clean stroke. Rain droplets freeze mid-air around the final slash.
(Camera: whip pan into lateral tracking, 120fps ramp to 24fps, motion blur on arms, hyperfocal)

Tech tags: 4K | 24fps cinematic | volumetric rain | film grain | desaturated teal-amber grade | Arri Alexa texture
```

## 十二、常见错误避坑

| ❌ 错误 | ✅ 正确 |
|---------|---------|
| "beautiful scene" | 具体描述光影和构图 |
| 每段塞入太多动作 | 每段聚焦一个核心动作 |
| 不标注运镜 | 每个镜头写明具体运镜 |
| 运镜只写名称不写参数 | 写清速度/距离/焦段/持续时间+为什么选它 |
| 全片只用一种运镜 | 根据情绪变化设计运镜节奏（呼吸式变化） |
| 忽略物理约束 | 主动声明 grounded physics |
| 风格描述抽象 | 引用具体作品/工作室名 |
| 忘记连续性 | 每段写 continuity notes |
| 技术标签缺失 | 末尾补充分辨率/帧率/色调 |
| 角色描述不一致 | 每段重复关键外貌锚点 |
| 运镜与动作不同步 | 运镜节奏滞后动作0.5-1s形成预判-确认结构 |
| 首尾段无呼应 | 开场/收束做镜像对称检查（七维度） |

---

## 十三、运镜提示词写作实战模板

> v2.0 新增。直接可用的运镜段落写作模板，按 SEG 类型分类。

### 13.1 标准运镜声明块格式

每个 SEG 提示词中，运镜部分应独立成块：

```markdown
### 🎥 运镜设计

| 项目 | 设计 |
|------|------|
| **主运镜** | ★[运镜名](#编号) — 一句话说明用法 |
| **辅运镜A** | ☆[运镜名](#编号) — 用法说明 |
| **辅运镜B** | ☆[运镜名](#编号) — 用法说明（可选） |
| **情绪目标** | "这段运镜要传达什么感觉" |
| **为什么这样组合** | 选这种运镜的叙事理由 |
```

### 13.2 提示词内的运镜写法（CAMERA MOVEMENT 段）

在 Seedance 提示词正文内，运镜用 `─── CAMERA MOVEMENT ───` 独立段落：

```
─── CAMERA MOVEMENT (CINEMATOGRAPHY DESIGN) ───
PRIMARY TECHNIQUE: [运镜英文名] (#编号, 时间范围, 触发条件):
[详细描述：起始位置/高度/焦段 → 移动路径 → 速度参数 → 终止位置/效果]

SECONDARY TECHNIQUE (可选):
[辅助运镜的触发时机和效果描述]

TECHNIQUE SWITCH (如果有多阶段):
Phase 1 (X-Ys): [参数]
Phase 2 (Y-Zs): [参数变化]
[Phase间过渡逻辑]
```

### 13.3 各类型 SEG 的运镜模板速查

#### 开场型（对应 3.1 推拉变焦类）

```
─── CAMERA MOVEMENT ───
PRIMARY: Slow Dolly In (#01, full segment, imperceptible approach)
Start: [起始距离]m from subject at eye-level.
Speed: [0.3-0.6]cm/s — slow enough that viewer doesn't consciously notice movement.
End: [终止距离]m — close enough to feel intimacy without invasion.
Secondary: Optical Zoom (#04) or Rack Focus (#06) at key emotional beat.
Effect: "viewer is gently drawn into character's inner world"
```

#### 对峙型（对应 3.2 垂直移动类）

```
─── CAMERA MOVEMENT ───
PHASE A — Tilt Down (#07, 0-Xs): 
Camera starts at eye-level → tilts down through body → ground → darkness/threat below.
Speed: slow deliberate (2-3s for full tilt). Purpose: threat escalation from ground up.

PHASE B — Tilt Up (#08, X-Ys, REVERSE direction):
From ground level → tilts UP past her feet → legs → torso → face → eyes.
Speed: slightly FASTER than Phase A (implies resistance/rising hope).
Final frame: her face against light source. Purpose: "she is not afraid".
```

#### 战斗型（对应多技组合）

```
─── CAMERA MOVEMENT ───
BASE MODE: Side Tracking (#33) — continuous lateral follow at [X]m distance.
Lens: [28-35]mm for clean combat framing.

IMPACT EVENT: Crash Zoom Hit (#07, at each impact frame):
At EXACT impact moment: micro push-in [+15-20%] over 0.15s → pull back.
Creates "impact pop" effect per strike.

DIRECTION CHANGE: Whip Pan (#24, between strikes):
Rapid horizontal pan following new swing direction. ~0.15-0.2s per whip.
Visual punctuation: each whip = "next attack incoming" signal.
```

#### 收束型（镜像对称版）

```
─── CAMERA MOVEMENT ───
PRIMARY: Slow Dolly In (#01, MIRROR of SEG-01):
Start position: IDENTICAL to SEG-01 start ([X]m at eye-level).
Speed: SLOWER than SEG-01 ([Y]cm/s vs original [Z]cm/s) — fatigue gentleness.
Path: same approach trajectory but with subtle differences:
  - Her hand adjusting glasses has slight tremor (fatigue micro-detail)
  - Pupils reflect warm light instead of threat glow
  - Expression arc: readiness → gentle smile (closure of emotional loop)

SECONDARY: Following Shot from Behind (#34, final 3-5s):
Transition to back-view tracking as she walks into [light/environment].
Long Lens Compression (#35) activates: background compresses, she becomes isolated silhouette.

FINAL: Tilt Up (#08, last 1-2s):
Camera tilts up from her figure to [sky/light shaft/god rays].
Fade to black during upward motion.
```

### 13.4 运镜自检清单（每段必填）

```markdown
**✅ 运镜自检**:
- [ ] 主运镜技术明确（★标记 + 编号 + 英文名）
- [ ] 辅运镜与主运镜不冲突（☆标记 + 编号）
- [ ] 运镜速度有具体数值（cm/s 或 m/s 或 °/s）
- [ ] 起始/终止位置明确（高度/距离/角度）
- [ ] 镜头焦段已标注（mm 数值）
- [ ] 多阶段运镜的切换逻辑清晰
- [ ] "情绪目标"和"为什么"两栏已填写
- [ ] 运镜节奏与动作节奏的关系已说明（同步/滞后/反向）
- [ ] 与前后段的衔接方式已定义（截帧/硬切/溶解）
```
