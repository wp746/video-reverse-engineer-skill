# OpenClaw / Hermes 安装与调用模板

这份文档是给 OpenClaw、Hermes 或团队同事直接使用的。

如果对方支持从 GitHub 仓库安装 skill，优先使用这个地址：

`https://github.com/wp746/video-reverse-engineer-skill.git`

如果对方支持从入口文件识别 skill，可以使用：

`https://raw.githubusercontent.com/wp746/video-reverse-engineer-skill/main/SKILL.md`

如果对方只支持下载压缩包后导入，可以使用：

`https://github.com/wp746/video-reverse-engineer-skill/archive/refs/heads/main.zip`

## 这个 skill 是干什么的

这是一个给 AI 视频创作者使用的“参考片反推 + 衍生创作 + 审查 + 资产 + 分镜 + Seedance 生产”一体化 skill。

它不是只做分析，而是把工作流从参考片推进到生产阶段。

## 它适合解决的问题

- 深度拆解一个优秀 AI 短片为什么有效
- 给出 3 个同类型、同深度、同情绪密度的创意方向
- 先写剧本，再经过专家团审核，不达标打回
- 从通过版剧本中提炼角色、场景、道具资产
- 生成 Banana 2 资产包 JSON
- 生成按时间段编号的分镜与 Seedance 2.0 提示词

## 默认工作流

默认链路是：

`参考视频 -> 深度反推 -> 3 个创意方向 -> 选方向 -> 写脚本 -> 专家团审查 -> 制片主任拆资产 -> Banana 2 资产包 -> 分镜时间轴 -> Seedance 2.0 提示词`

## 推荐安装方式

### 方式 1：Git 仓库安装

如果 OpenClaw 或 Hermes 支持 Git 仓库地址，直接填：

```text
https://github.com/wp746/video-reverse-engineer-skill.git
```

### 方式 2：入口文件安装

如果它们支持直接读取 skill 入口文件，填：

```text
https://raw.githubusercontent.com/wp746/video-reverse-engineer-skill/main/SKILL.md
```

### 方式 3：压缩包导入

如果它们只能导入压缩包，使用：

```text
https://github.com/wp746/video-reverse-engineer-skill/archive/refs/heads/main.zip
```

## 安装后怎么调用

推荐在调用时明确这 4 个变量：

1. 参考素材
2. 时长模式
3. 当前阶段
4. 输出要求

## 最短调用模板

```text
请调用 video-reverse-engineer skill。

参考素材：<视频链接 / 上传视频 / 截图组>
目标模式：30-60s theme short
目标：先做精细反推，再给 3 个创意方向
```

## 参考视频分析模板

```text
请调用 video-reverse-engineer skill 分析这个参考片。

参考素材：
https://example.com/video

要求：
1. 拆创作逻辑、视觉逻辑、叙事逻辑、节奏逻辑
2. 逐段说明这个片子为什么成立
3. 指出哪些元素必须保留，哪些必须变化，避免直接复制
4. 最后给我 3 个同类型衍生方向
```

## 选方向后写脚本模板

```text
我选择第 2 个方向。

请继续调用 video-reverse-engineer skill：
1. 开始写脚本
2. 脚本完成后进入专家团顺序审查
3. 总分低于 90 分直接打回重写
4. 通过后再进入制片主任拆资产
```

## 直接推进到生产模板

```text
请调用 video-reverse-engineer skill。

已知条件：
- 参考片已经分析完
- 创意方向已经选定
- 现在从脚本阶段开始

要求：
1. 写脚本
2. 进入专家审查
3. 输出审查结论与评分
4. 通过后提炼角色、场景、道具
5. 生成 Banana 2 资产包 JSON
6. 生成分镜时间轴
7. 生成 Seedance 2.0 分段提示词
```

## 输出物说明

这个 skill 正常会产出：

- 反推分析文档
- 三方向创意提案
- 审核通过版剧本
- 审查评分汇总
- 制片主任 handoff 文档
- Banana 2 资产包 JSON
- 分镜时间轴
- Seedance 2.0 提示词包

## 推荐对模型说清楚的参数

### 时长模式

- `15s emotion short`
- `30-60s theme short`
- `1-3min narrative short`

### 当前阶段

- `analysis`
- `creative-directions`
- `script`
- `review`
- `producer-breakdown`
- `asset-package`
- `storyboard`
- `seedance-package`

### 输出格式偏好

- `英文字段 + 中文内容`
- `按时间段编号`
- `SEG01_0-12s`
- `Banana 2 JSON`
- `Seedance 2.0 package`

## 给 OpenClaw / Hermes 的简短描述

如果对方需要一个一句话介绍，可以直接用这段：

```text
video-reverse-engineer 是一个面向 AI 视频创作者的工业化生产 skill，用于从参考短片出发，完成深度反推、三方向创意提案、脚本审查、资产拆解、分镜时间轴与 Seedance 2.0 提示词生产。
```

## 联系方式

- 微信：`ds2dy-pp`
