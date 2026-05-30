# 后端交付生产包 (Backend Handover Package)

本包已按照“后端交付协议”编译完成，包含用于 **image2** 的静态资产配置 JSON，以及用于 **seedance2.0** 的动态视频段提示词表。直接复制相应块即可投喂生产。

---

## 一、静态资产生成包 (image2 - Banana 2 JSON)

请复制以下 JSON 块投喂至 **image2**，生成统一的角色设定板、场景总宫格、多视角关键场景图及关键道具设计。

```json
{
  "project_id": "reconstructed-project-001",
  "project_title": "重构项目名",
  "mode": "15s-emotion | 30-60s-theme | 1-3min-narrative",
  "visual_bible": {
    "core_style": "写实电影感，高逼真物理细节",
    "palette": "色温基调与色值说明",
    "lighting_principle": "光影方向与明暗质感法则",
    "texture_keywords": ["高精度皮肤纹理", "真实服装织物缝线", "物理折射与反射"],
    "continuity_rules": [
      "角色面部特征完全锁定",
      "服装细节与配饰跨视图保持高度一致",
      "场景地理与光源方向在各视角中保持统一"
    ]
  },
  "assets": {
    "characters": [
      {
        "asset_id": "char-001",
        "asset_type": "character",
        "name": "新角色名",
        "narrative_role": "主角",
        "must_reference_in_seedance": true,
        "sheet_spec": {
          "aspect_ratio": "16:9",
          "layout": ["face_closeup", "front_view", "side_view", "back_view", "costume_detail_nine_grid"]
        },
        "identity_core": {
          "age_feel": "年龄感说明",
          "gender_presentation": "性别与气质呈现",
          "temperament": "性格与神态特质",
          "stable_recognition_anchors": ["锚定特征1", "锚定特征2", "锁定的服装剪裁与配色"]
        },
        "face_design": {
          "face_shape": "脸型描述",
          "eyes": "眼型与神态描述",
          "skin": "高逼真写实皮肤纹理，微汗/毛孔/细小瑕疵说明",
          "hair_shape": "发型与发丝走向描述",
          "hair_color": "发色说明"
        },
        "costume_system": {
          "outerwear": "外衣剪裁与材质（如：厚羊毛粗呢、磨损的棕色牛皮）",
          "inner_layers": "内衬层次结构描述",
          "accessories": ["配饰及细节设计描述"],
          "material_notes": ["粗糙织物", "局部皮革反光"],
          "wear_and_damage": ["轻微磨损/做旧细节描述"]
        },
        "costume_detail_nine_grid": [
          "1. 领口与内衬层次近景",
          "2. 肩部缝线与面料质感",
          "3. 袖口磨损细节",
          "4. 腰带扣金属微光与质感",
          "5. 裤装面料褶皱细节",
          "6. 鞋头皮革做旧痕迹",
          "7. 核心配饰工艺近照",
          "8. 织物边缘线头微小细节",
          "9. 特征磨损/泥点特写"
        ],
        "banana2_prompt_package": {
          "system_intent": "生成一张用于写实视频制作的16:9角色资产设定板，锁定面部与服装一致性。",
          "generation_prompt": "一张16:9电影级写实角色资产设定板... (Playbook规范化生成的写实资产Prompt)",
          "consistency_notes": ["通过@角色名引用时，重点继承面部特征与服装细节。"]
        }
      }
    ],
    "scenes": [
      {
        "scene_id": "scene-grid-001",
        "asset_type": "scene_master_grid",
        "banana2_prompt_package": {
          "system_intent": "生成写实场景总宫格，锁定各场景色彩和光影基调。",
          "generation_prompt": "场景宫格生成Prompt..."
        }
      }
    ],
    "props": []
  }
}
```

---

## 二、动态视频生成包 (seedance2.0)

请参考以下时间轴与分段提示词。生成视频时，确保开启 `@` 资产引用功能，将每一段提示词投喂给 **seedance2.0**。

### 1. 分镜时间轴表格 (Reconstructed Timeline)

| 分段编号 | 时间跨度 | 画面尺寸/机位 | 运镜轨迹 | 关联资产 | 叙事/情感职责 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **SEG01** | `0-12s` | 中远景，低角度机位 | 机械滑轨缓慢横移 | `@角色-001`, `@场景-001` | 建立环境氛围，带入角色状态 |
| **SEG02** | `12-24s` | 中景，平视视角 | 缓慢向前推进并滞后锁定 | `@角色-001`, `@场景-001` | 冲突引入，情绪绷紧 |
| **SEG03** | `24-36s` | 特写，侧光剪影机位 | 微幅手持抖动 | `@角色-001`, `@场景-001`, `@道具-001` | 核心命题揭示，情绪释放 |

### 2. 视频分段执行提示词 (Seedance Feeding Prompts)

请逐段复制以下框内的提示词投喂给 **seedance2.0**。

```text
================================================================================
【分段编号】: SEG01_0-12s
【关联资产】: @角色-001, @场景-001
【安全区规划】:
  - 0-1.5s: 锁定初始中景构图，角色保持站立吸气微动，无剧烈动作。
  - 10.5-12s: 画面在横移终点锁定，微风吹拂发梢，作为过渡安全区。
【连续性锚点】: 锁定暗红羊毛大衣材质、左侧45度柔和侧光、发丝反光。
【出片提示词 (Seedance 2.0 Feeding Prompt)】:
(Incorporate Rule 1 to 8: English translation for the model)
At 0-1.5s, hold a stable medium wide composition of @char-001 standing motionless in @scene-001 under the dim overcast light. 
From 1.5s to 10.5s, camera slowly tracks laterally from right to left with a steady slider motion. @char-001 slowly turns her head, her dark gray wool coat catching the soft orange light of the fading sun. Atmospheric dust motes float lazily, reflecting the light in the air. 
At 10.5-12.0s, camera comes to a complete stop, locking on a clean medium silhouette.
================================================================================
```

*(后续分段按此模板输出...)*
