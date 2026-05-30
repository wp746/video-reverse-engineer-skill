# 后端交付生产包 (Backend Handover Package)

本包已按照“好莱坞原型重构交付标准”编译完成，包含用于 **image2** 的静态资产/故事板双语提示词，以及用于 **seedance2.0** 的动态视频段提示词表。直接复制相应块即可投喂生产。

---

## 一、静态资产生成包 (image2 双语提示词 - 资产板标准)

请直接复制以下中英文提示词投喂至 **image2**，生成统一的角色正交三视图设定板、场景 9 宫格细节板及关键道具设计。

### 1. 角色设计板 (Character Sheets)
* **【英文提示词 (English Prompt)】**：
```text
(Character sheet turnaround prompt with top A01/A02 label and front/side/back view bottom sub-labels)
```
* **【中文提示词 (Chinese Prompt)】**：
```text
(角色资产正交三视图提示词，包含顶部大字A01/A02标签，与底部正面/侧面/背面小字子标签)
```
* **💡 引用关系与后端联动提醒 (NOT in prompt)**：
  > (说明后续在 Seedance 2.0 中生成视频时，全能参考如何载入此角色板及精准绑定具体视图)

---

### 2. 场景 9 宫格设计板 (Scene 9-Box Grids)
* **【英文提示词 (English Prompt)】**：
```text
(Scene 9-box grid concept design sheet prompt with top A03/A04 label and 9 detailed viewpoint cell sub-labels)
```
* **【中文提示词 (Chinese Prompt)】**：
```text
(场景9宫格细节概念板提示词，包含顶部大字A03/A04标签，与每个子格底部的英文命名小标签)
```
* **💡 引用关系与后端联动提醒 (NOT in prompt)**：
  > (说明后续在 Seedance 2.0 中生成视频时，全能参考如何载入此场景板及精准引用特定区域作为光源与氛围约束)

---

## 二、故事板生成包 (image2 双语提示词 - 故事板双格标准)

请直接复制以下提示词投喂至 **image2**，生成电影故事板图像（包含顶部 `S0X` 标签，以及故事预演、机位运动与运镜方式、音效与特效呈现）。

### 📊 故事板-S01：[分镜名]
* **【英文提示词 (English Prompt)】**：
```text
(Cinematic storyboard split-screen prompt showing main shot and insert closeup, top label S01, and technical shot annotations)
```
* **【中文提示词 (Chinese Prompt)】**：
```text
(电影故事板双格排版线稿提示词，包含顶部大字S01标签，主画面与特写图底部英文子标签)
```
* **💡 引用关系与后端联动提醒 (NOT in prompt)**：
  > (详细说明此故事板引用了哪些 A0X 角色/场景资产，以及后续在 seedance2.0 中如何绑定此帧)

---

## 三、动态视频生成包 (seedance2.0 15秒段提示词)

请参考以下时间轴与分段提示词。生成视频时，确保开启 **全能参考** 引用功能，将每一段提示词投喂给 **seedance2.0**。

### 🎬 SEG01_0-15s：[段落名]
* **💡 后端引用与资产绑定提示 (NOT in prompt)**：
  > 1. **角色参考**：加载角色板 `A01.png`，并对其中 `A01 - front view` 和 `A01 - face closeup` 区域进行精准绑定。
  > 2. **场景参考**：加载教室概念板 `A03.png` 中的 `A03 - wide view`。
  > 3. **故事板参考**：加载故事板 `S01.png` 中的 `S01 - main shot`。
* **【安全区规划】**：
  - `0-1.5s`：首帧稳定微动安全区规划。
  - `13.5-15s`：尾帧锁定稳定微动安全区规划。
* **【出片提示词 (Seedance 2.0 Feeding Prompt)】**：
```text
At 0-1.5s, hold a stable cinematic shot matching STORYBOARD_01...
From 1.5s to 13.5s, [Primary dramatic action and physical camera motion]...
At 13.5-15.0s, camera stabilizes on the ending frame...
```
