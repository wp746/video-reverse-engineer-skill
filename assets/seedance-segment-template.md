# Seedance Segment Template

Use this template when building segment-level production units for Seedance 2.0.

Default naming rule:

- `SEG01_0-12s`
- `SEG02_12-24s`
- `SEG03_24-33s`

The segment duration should follow dramatic logic, not mechanically fill 15 seconds.

```text
[Segment ID]
SEG01_0-12s

[Segment Purpose]
这一段承担什么叙事和情绪任务

[Time Range]
0-12s

[Bound Assets]
@角色1：主角
@场景3：雨夜石板巷主视角
@道具1：佩剑

[Continuity Notes]
- 与上一段保持同一人物面部结构和服装层次
- 保持雨夜巷子的空间方向一致
- 远处暖色灯笼位置不要漂移

[Shot Breakdown]
- 0-3s：建立镜头
- 3-7s：动作推进
- 7-10s：情绪收紧
- 10-12s：为下一段埋爆点

[Seedance Prompt]
写一段完整的、可直接执行的Seedance提示词，明确镜头运动、动作链、物理反馈、光影变化、声音与情绪推进。

[Head/Tail Safe Zone]
- 前0.5s：留建立缓冲
- 后0.5s：留衔接缓冲

[Next Segment Handoff]
下一段需要承接什么动作、情绪、空间方向
```
