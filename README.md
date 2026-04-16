# Video Reverse Engineer Skill

一个面向 AI 短片创作者的工业化反推与生产 skill。

它不是“帮你分析一下视频”这么简单，而是把一个优秀短片从参考素材一路推进到：

- 深度反推
- 三个同类型创意方向
- 过审脚本
- 资产包设计
- 分镜与时间轴
- Seedance 2.0 成片提示词

适合 15 秒情绪短片、30-60 秒主题短片、1-3 分钟叙事短片。

## Quick Start

如果你现在就要把这个 skill 交给 OpenClaw 或 Hermes，用下面这组信息就够了。

安装仓库地址：

`https://github.com/wp746/video-reverse-engineer-skill.git`

技能入口地址：

`https://raw.githubusercontent.com/wp746/video-reverse-engineer-skill/main/SKILL.md`

压缩包地址：

`https://github.com/wp746/video-reverse-engineer-skill/archive/refs/heads/main.zip`

推荐先看：

- [OpenClaw / Hermes 安装与调用模板](docs/openclaw-hermes-install.md)
- [SKILL.md](SKILL.md)

## 它能解决什么问题

这个 skill 主要解决 6 类高频问题：

1. 看到了一个很强的 AI 短片，但只会说“好厉害”，不知道它到底好在哪里。
2. 想模仿原片的深度、情绪和结构，但又不想做一比一抄袭。
3. 脚本写出来总觉得虚，缺少导演、编剧、摄影、美术、服化道、后期这些专业维度的审查。
4. 脚本能看，但一到资产拆解、角色三视图、场景多视角、关键道具提炼就乱。
5. Seedance 2.0 提示词写不稳，人物一致性、场景连续性、镜头节奏和空间逻辑经常出 bug。
6. 想形成一个可重复调用的生产流程，而不是每次都从零开始重新想。

## 核心功能

这个 skill 的核心能力包括：

1. 参考视频反推
   支持链接、本地视频、截图、时间戳材料，拆解创作逻辑、视觉逻辑、叙事逻辑、节奏逻辑、分镜逻辑、台词逻辑、声音逻辑、风格逻辑。

2. 三方向衍生创意
   基于参考片先给出 3 个“同类型、同深度、同情绪密度”的创意方向，让用户做选择，而不是直接乱写剧本。

3. 工业级脚本审查
   脚本会经过顺序化专家审查链路，达不到阈值不进入下一阶段。

4. 制片主任资产拆解
   从通过审查的脚本里提炼人物、场景、道具，形成 Banana 2 可直接执行的资产包 JSON。

5. 分镜与时间轴设计
   把内容拆成可生产的分段与镜头时间轴，支持 `SEG01_0-12s` 这种编号方式。

6. Seedance 2.0 提示词生产
   根据脚本、资产和时长，为每个段落生成精细化提示词，尽量锁定人物、服装、场景、光影、空间和镜头连续性。

## 标准工作流

默认工作流是：

`参考视频输入 -> 内容提取 -> 深度反推 -> 3 个创意方向 -> 用户选方向 -> 写脚本 -> 专家团审查 -> 制片主任拆资产 -> Banana 2 资产包 -> 分镜时间轴 -> Seedance 2.0 提示词包`

不会默认跳过脚本阶段直接生成视频提示词。

## 审查机制

脚本不是“写完就过”，而是进入顺序化审核。

核心规则：

- 总分必须 `>= 90`
- 关键岗位低于阈值直接打回
- 不通过就重写，再审，直到通过

当前 skill 内已经封装了这些审核角色提示词：

- 导演总审
- 编剧审查
- 摄影审查
- AI 可执行性审查
- 美术风格审查
- 服化道审查
- 后期声音审查

## 输出物

这个 skill 最终可以产出：

- 参考片反推分析文档
- 三个创意方向提案
- 多轮修订后的通过版脚本
- 审查汇总与评分结果
- 制片主任 handoff 文档
- Banana 2 角色资产 JSON
- Banana 2 场景资产 JSON
- Banana 2 道具资产 JSON
- 分镜与时间轴文档
- Seedance 2.0 分段提示词包
- 完整样例项目

## 资产规则

内置规则已经按照你的生产习惯封装：

- 人物资产：一张 `16:9` 图内包含面部特写、正侧背、服装细节九宫格
- 场景资产：先做场景总宫格，再拆关键场景多视角
- 道具资产：只要“反复出现”或“叙事关键”满足其一就单独立项
- 字段风格：英文字段 + 中文内容
- 分段编号：如 `SEG01_0-12s`

## 适用人群

适合这些人：

- AI 短片导演
- AI 视觉创作者
- 想做情绪短片、主题短片、叙事短片的个人作者
- 想把“参考视频分析”变成固定工作流的团队
- 要把 Banana 2 和 Seedance 2.0 串起来做量产的人

## 仓库结构

仓库根目录就是 skill 根目录，已经可直接分发：

- `SKILL.md`
- `agents/openai.yaml`
- `references/`
- `assets/`
- `samples/mranti-family-thriller/`

## 安装地址

如果 OpenClaw 或 Hermes 支持直接从 GitHub 仓库安装 skill，优先给它这个地址：

`https://github.com/wp746/video-reverse-engineer-skill.git`

也可以给它仓库页面地址：

`https://github.com/wp746/video-reverse-engineer-skill`

如果对方支持用原始入口文件识别 skill，可以再补这个地址：

`https://raw.githubusercontent.com/wp746/video-reverse-engineer-skill/main/SKILL.md`

如果对方更适合下载压缩包安装，可以用：

`https://github.com/wp746/video-reverse-engineer-skill/archive/refs/heads/main.zip`

## OpenClaw / Hermes 使用建议

如果它们支持“从 Git 仓库安装 skill”，一般直接填仓库地址即可：

```text
https://github.com/wp746/video-reverse-engineer-skill.git
```

如果它们支持“从 skill 入口文件识别”，就填：

```text
https://raw.githubusercontent.com/wp746/video-reverse-engineer-skill/main/SKILL.md
```

如果它们支持“先导入仓库，再读取根目录 skill”，这个仓库本身已经是 skill 根目录，不需要再额外指定子路径。

更完整的安装与调用模板见：

- [docs/openclaw-hermes-install.md](docs/openclaw-hermes-install.md)

## 怎么使用

最常见的 3 种用法：

### 1. 给一个参考视频链接

比如：

```text
请用 video-reverse-engineer skill 分析这个视频：
https://example.com/video
先做深度反推，再给我 3 个同类型衍生方向。
```

### 2. 上传一个本地视频

比如：

```text
请分析我上传的短片。
按 30-60 秒主题短片模式拆解，
先输出反推报告，再给 3 个创意方向。
```

### 3. 从脚本阶段继续推进

比如：

```text
我选第 2 个方向。
请开始写脚本，并进入专家团审核。
低于 90 分打回重写，直到通过。
通过后再做资产拆解、分镜和 Seedance 提示词。
```

## 推荐调用方式

推荐你在调用时明确这 4 件事：

1. 参考素材是什么
2. 想做的时长模式是什么
3. 当前要推进到哪个阶段
4. 输出格式偏好是什么

一个更完整的调用示例：

```text
请调用 video-reverse-engineer skill。

参考素材：<视频链接或上传视频>
目标模式：30-60s theme short
目标：先做精细反推，再给我 3 个创意方向
输出要求：
- 要拆创作逻辑 / 视觉逻辑 / 叙事逻辑 / 节奏逻辑
- 要说明哪些必须保留，哪些必须变化
- 创意方向要给资产复杂度和时长建议
```

## 内置样例

仓库中自带了一个完整样例项目：

`samples/mranti-family-thriller/`

它展示了从创意方向选择、脚本、评审、制片 handoff，到 Banana 2 资产和 Seedance 提示词包的完整链路。

## 联系方式

- 微信：`ds2dy-pp`

## License

本仓库当前未额外声明商业授权条款时，请先默认按源码与提示词资产仓库的常规谨慎方式使用；如果你准备把它用于团队分发、商业服务或二次售卖，建议先补充明确的 LICENSE 与商用说明。
