# Producer Handoff

Use this file after the script has passed all required expert reviews.

## Goal

Turn the approved script into a production-ready handoff package.

The producer is not re-writing the script.

The producer is preparing the next stages so that:

- assets can be generated cleanly
- key scenes are prioritized correctly
- Seedance segments can be planned without drift
- downstream work does not have to guess basic production decisions

## Producer responsibilities

### 1. Script readiness confirmation

Before doing any breakdown, confirm:

- script review has passed
- no blocking reviewer notes remain
- theme and runtime mode are locked

If these are not true, stop and push back upstream.

### 2. Asset breakdown

Extract:

- major characters
- supporting characters that need assets
- all scenes
- key scenes requiring multi-angle treatment
- recurring props
- narratively critical props

### 3. Asset priority

Rank assets by downstream importance:

- P1: cannot proceed without this asset
- P2: strongly preferred for stability
- P3: optional or can be described in text if needed

### 4. Continuity risk mapping

Identify continuity risks such as:

- same character across many segments
- costume continuity under action
- repeated return to the same space
- important recurring prop behavior
- directionality or geography that must not drift

### 5. Segment planning

Prepare a first-pass segment plan using Seedance-sized production units.

Default naming:

- `SEG01_0-12s`
- `SEG02_12-24s`

Each segment should note:

- segment purpose
- likely assets used
- continuity risks
- whether the duration is stable or likely to change after storyboard refinement

## Producer handoff package

The producer should hand over a package containing:

1. script lock summary
2. asset breakdown table
3. asset priority table
4. key-scene expansion list
5. continuity risk notes
6. first-pass segment plan
7. downstream instructions for asset, storyboard, and Seedance stages

## Producer decision rules

- Do not create extra assets without a production reason
- Do not skip a critical recurring prop
- Do not over-build every scene into a heavy multi-angle asset
- Do create multi-angle assets for scenes that carry emotional, spatial, or action continuity burden
- Do keep segment boundaries aligned with dramatic logic, not arbitrary time filler

## Output structure

Use this structure:

```text
[制片主任交接包]

一、锁定信息
- 目标模式：
- 核心命题：
- 目标总时长：
- 当前脚本版本：

二、资产拆解
- 角色：
- 场景：
- 道具：

三、资产优先级
- P1：
- P2：
- P3：

四、关键场景扩展清单
1. ...
2. ...

五、连续性风险
1. ...
2. ...
3. ...

六、分段初稿
- SEG01_0-12s：
- SEG02_12-24s：
- SEG03_24-33s：

七、下游执行指令
- 资产阶段：
- 分镜阶段：
- Seedance阶段：
```
