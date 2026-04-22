# 快速入门指南 (Quick Start)

> video-reverse-engineer skill 的 5 分钟上手教程。

---

## 我能用这个 skill 做什么？

| 能力 | 输入 | 输出 |
|------|------|------|
| **参考视频反推** | YouTube/B站/抖音/小红书链接或视频文件 | 完整的创意/视觉/叙事/节奏/分镜拆解报告 |
| **三方向衍生创意** | 参考片 + 你的想法 | 3 个同深度原创方向供选择 |
| **工业级剧本创作** | 选定的方向 | 通过专家审查链的专业剧本 |
| **资产包生成** | 通过审查的剧本 | Banana 2 可直接执行的 JSON 资产包 |
| **Seedance 提示词生产** | 剧本 + 资产 | 每段带专业运镜设计的 AI 视频提示词 |
| **一键模糊转成品** | 一句话想法（"帮我写个下雨天武士"） | 生产级 Seedance 2.0 提示词 |

---

## 三种使用方式

### 方式一：完整 8 阶段流水线（推荐，适合完整项目）

```
你: "帮我分析这个视频 [链接]，然后做一套完整的反向工程"
AI: 自动走完全部 8 个阶段 → 最终交付 Seedance 2.0 提示词包
```

### 方式二：从某个阶段切入

```
你: "我已经有剧本了，帮我直接生成 Seedance 提示词"
AI: 从 Stage 6 开始执行
```

```
你: "帮我看下这个剧本能不能过审"
AI: 执行 Stage 4 专家审查链
```

### 方式三：一键模糊交付（最快，适合快速出活）

```
你: "我想要一个赛博朋克风格的跑步镜头"
AI: 直接输出生产级 Seedance 2.0 提示词 + 2-3 种变体
```

---

## 第一个项目：5 步上手

### Step 1：准备材料

你需要提供以下任一种：
- **视频链接**（YouTube / B站 / 抖音 / 小红书 / 本地文件）
- **截图 + 时间戳**
- **一段文字描述你的创意想法**

### Step 2：启动 skill

直接说：

```
"用 video-reverse-engineer 帮我分析这个 [链接/想法]"
```

skill 会自动加载所有参考文件和审查流程。

### Step 3：选择模式（如果做完整项目）

根据你的目标时长选择：

| 模式 | 适用场景 | 分析粒度 |
|------|---------|---------|
| `15s emotion short` | 抖音/TikTok/朋友圈短视频 | 精确到秒 |
| `30-60s theme short` | B站/小红书中视频 | 分段级 |
| `1-3min narrative short` | 完整叙事短片 | 镜头级 |

### Step 4：在关键节点做决策

流水线中有几个需要你拍板的节点：

1. **Stage 2** — 从 3 个创意方向中选 1 个
2. **Stage 4** — 如果审查不通过，确认是否按意见修改
3. **Stage 8** — 最终提示词包确认

其他阶段全自动运行。

### Step 5：拿到产出

最终你会收到这些文件：

```
📁 project-output/
├── analysis-report.md          # 反推分析报告
├── creative-directions.md      # 3 个创意方向
├── script-approved.md          # 通过审查的剧本
├── review-summary.md           # 审查评分汇总
├── producer-handoff.md         # 制片主任资产拆解
├── asset-package/              # Banana 2 资产 JSON 包
│   ├── characters/
│   ├── scenes/
│   └── props/
├── storyboard-timeline.md      # 分镜时间轴
├── seedance-package-v2.md      # Seedance 2.0 提示词包
└── cinematography-summary.md   # 运镜设计总表（v2.0）
```

---

## 核心概念速查

### 运镜体系 (v2.0)
- **38 种运镜技巧** 分为 6 大类：推拉变焦 / 垂直水平移动 / 环绕旋转 / 特殊视角 / 引导跟随
- 每个 SEG 提示词自动匹配 1-3 种最佳运镜，并写明速度/距离/焦段参数
- 详见 `references/cinematography-design-guide.md`

### 审查机制
- **7 个审查岗位** 顺序执行：导演总审 → 编剧 → 摄影/运镜 → AI 可行性 → 美术风格 → 服化道 → 后期声音
- 总分 ≥ 90 才能通过，关键岗位有一票否决权
- 详见 `references/script-review-order.md` 和 `references/review-prompts/`

### Seedance 提示词质量标准
每个提示词必须包含：
- 格式声明（时长/镜头数/宽高比）
- 时间轴分段（≤15s per segment）
- 专业运镜描述（不是 vague 的"camera moves"）
- 物理约束声明
- 多感官层次（视觉+声音+触感暗示）
- 技术标签（分辨率/帧率/调色）
- 风格锚定（引用具体作品）
- 动词驱动的动作描述

详见 `references/seedance-prompt-craft-notes.md`

---

## 常见问题速查

| 问题 | 解决方法 |
|------|---------|
| "我想跳过某些阶段" | 可以，明确告诉 AI 从哪个 Stage 开始 |
| "审查总是不过" | 查看 review summary 中哪个岗位分数最低，针对性修改 |
| "生成的视频和提示词不一样" | 检查是否加了足够的物理约束和角色锚点 |
| "不知道选哪个方向" | 可以让 AI 给出推荐理由，或者合并多个方向 |
| "想用自己的素材" | 在 Stage 5 资产拆解时提供你的参考图 |

---

## 下一步

- 📖 阅读 [`CHANGELOG.md`](./CHANGELOG.md) 了解最新更新
- 🔧 阅读 [`README.md`](./README.md) 了解完整的仓库结构和功能说明
- 🎬 查看 [`samples/mranti-family-thriller/`](./samples/mranti-family-thriller/) 了解完整样例项目
- ⚠️ 排查问题请查阅 [`troubleshooting.md`](./troubleshooting.md)
