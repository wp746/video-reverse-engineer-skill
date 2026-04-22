# Changelog

All notable changes to the video-reverse-engineer skill will be documented in this file.

## [v2.0.0] - 2026-04-22

### 🎬 Added — 运镜设计体系（核心升级）

**新增 4 个文件：**

| 文件 | 说明 | 大小 |
|------|------|------|
| `references/cinematography-design-guide.md` | 38种运镜匹配框架 | 13.6KB |
| `references/review-prompts/cinematography-review.md` | 运镜摄影审查提示词 | 8.0KB |
| `references/seedance-segment-template.md` | v2.0 段落模板（含运镜块） | 3.6KB |
| `references/seedance-package-output-template.md` | v2.0 输出模板（含运镜总表） | 5.5KB |

### 📝 Changed — 升级 3 个现有文件

| 文件 | 变更内容 |
|------|---------|
| `references/seedance-prompt-craft-notes.md` | 运镜术语 **13→36 种**（+177%），新增第 4 章（角色一致性技巧后插入，原编号顺延）、第 4 章运镜叙事设计原则、第 13 章运镜写作实战模板；错误避坑表新增 4 条运镜相关项 |
| `SKILL.md` | Read 引用列表新增 `cinematography-design-guide.md` 和 `cinematography-review.md` |
| `README.md` | 核心功能 / 审查机制 / 输出物 / 仓库结构 四大板块全面标注 v2.0 新增内容 |

### ✨ 功能亮点

#### 38 种运镜分类体系（六大类完整覆盖）

| 类别 | 数量 | 示例 |
|------|------|------|
| 推拉变焦类 | 6 | Slow Dolly In / Crash Zoom / Dolly Zoom / Rack Focus ... |
| 垂直水平移动 | 17 | Tilt Down→Up / Pedestal / Crane Up / Dutch Angle / Side Tracking / Orbit ... |
| 环绕旋转 | 4 | Whip Pan / 360° Spin / Rapid Orbital / Spin Acceleration |
| 特殊视角 | 12 | Macro / POV / Through-Shot / Reveal Behind / God's Eye / Handheld / FPV ... |
| 引导跟随 | 3 | Following Shot / Eyeline Match / Object-Guided Move |

每种运镜包含：**编号 + 中英文名 + 适用场景 + Seedance 提示词直接可用的英文写法示例**。

#### 四大设计工具

1. **运镜选择四步法** — 读情绪 → 选类型 → 定参数 → 写理由
2. **10 种剧情类型 × 运镜映射矩阵** — 开场/对峙/战斗/跑酷/缠斗/充能/EMP/BOSS战/终极技/收束
3. **运镜节奏设计原则** — 与动作节奏同频但相位偏移 0.5-1s
4. **镜像对称七维度检查** — 运镜/速度/方向/焦点/光线/表情/后续衔接

#### 五类 SEG 运镜写作模板

- 开场型（Slow Dolly In + Rack Focus）
- 对峙型（Tilt Down→Up 双阶段反向垂直运动）
- 战斗型（Side Tracking + Whip Pan + Crash Zoom Hit 多技组合）
- 收束镜像型（Slow Dolly In 镜像对称 + Follow Behind + Tilt Up）

#### 运镜审查体系

四维评分：
- Camera Arc Analysis（运镜弧线连贯性）
- Mirror Symmetry Check（首尾段七维度对称）
- Emotional Match（运镜与情绪的匹配度）
- Technical Execution（参数完整性 + 可执行性）

### 📊 数据统计

```
文件变更:   7 个 (+4 new, 3 modified)
代码行数:   +1146 / -100
运镜术语:   13 → 36 种 (+177%)
新增章节:   4 章
新增审查:   1 个岗位（运镜摄影审查）
新增模板:   2 个（段落 + 输出包）
```

---

## [v1.0.0] - 初始版本

- 首次发布 video-reverse-engineer skill
- 包含完整的 8 阶段工作流：参考视频反推 → 3 方向衍生创意 → 脚本审查 → 资产拆解 → 分镜时间轴 → Seedance 提示词生产
- 内置 7 岗位审查链路（导演总审/编剧/摄影/AI可执行性/美术/服化道/后期声音）
- Banana 2 资产包 JSON 规范
- 完整样例项目（mranti-family-thriller）
