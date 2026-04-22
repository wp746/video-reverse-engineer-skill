# 常见问题与排错指南 (Troubleshooting)

> 使用 video-reverse-engineer skill 时遇到问题？先来这里找答案。

---

## 🔴 高频问题（90% 的用户会碰到）

### Q1: 审查总不过怎么办？

**症状**: Stage 4 反复打回，改了还是不过。

**排查步骤**:

1. **查看具体哪个岗位扣分最多**
   ```
   打开 review-summary.md → 找到最低分的岗位 → 读该岗位的具体评语
   ```

2. **常见扣分原因速查表**:

   | 岗位 | 常见扣分原因 | 快速修复 |
   |------|------------|---------|
   | 导演总审 | 结构失衡（高潮太早/太晚） | 调整节拍表中各段时长比例 |
   | 编剧审查 | 对白冗余 / 动机不足 | 删掉没有推动剧情的对白；给关键动作加动机 |
   | 摄影/运镜 | 运镜单一 / 与情绪不匹配 | 参考 cinematography-design-guide.md 的映射矩阵 |
   | AI 可行性 | 描述过于抽象 / 无法锁定画面 | 加入更多视觉锚点和物理约束 |
   | 美术风格 | 风格引用太泛 / 色彩逻辑混乱 | 改用具体影片/工作室名 + 固定色板 HEX |
   | 服化道 | 角色外貌前后不一致 | 建立角色锚点卡并在每段重复 |
   | 后期声音 | 音乐节奏与画面脱节 | 画出音乐曲线与情绪曲线对照检查 |

3. **如果总分 ≥ 90 但某个关键岗位 < 阈值**
   - 这是「一票否决」规则生效。即使总分够了也不行。
   - 必须把那个岗位的问题修到阈值以上。

---

### Q2: 生成的视频和预期差距很大

**症状**: Seedance 提示词看起来很详细，但实际生成的视频完全不对。

**常见原因和修复**:

| 原因 | 表现 | 修复方法 |
|------|------|---------|
| **提示词过长** | Seedance 截断了后半部分 | 每段控制在 150-200 词以内，核心信息放前半部分 |
| **矛盾指令** | 同时要求"缓慢"和"快速" | 统一时间/速度相关的描述，去掉矛盾的 |
| **缺少物理约束** | 角色飘浮 / 穿模 / 不自然姿态 | 加上 `grounded physics, no floating, natural body weight` |
| **角色描述不够具体** | 每次生成的角色长得不一样 | 建立详细的 character anchor card 并每段重复关键特征 |
| **运镜指令太复杂** | AI 无法理解复杂的运镜组合 | 拆成 1 主 + 1 辅，不要超过 2 种运镜 |
| **风格冲突** | 同时要求多种风格 | 只保留一个主风格，其他作为微调 |

**调试技巧**: 把提示词拆成最简版本测试，逐步加回元素，找出是哪一部分导致偏离。

---

### Q3: 不知道该选哪种运镜

**症状**: 看到 36 种运镜不知道选哪个。

**使用四步法**:

```
Step 1: 这段戏的核心情绪是什么？（恐惧/愤怒/释然/孤独...）
Step 2: 去 cinematography-design-guide.md 的「映射矩阵」找对应情绪的推荐运镜
Step 3: 定参数（速度/距离/角度/焦段）
Step 4: 写为什么（这种运镜能最好地表达这个情绪的理由）
```

**快捷查询表**（最常用的 10 种）:

| 情境 | 首选运镜 | 备选 |
|------|---------|------|
| 开场建立 | Slow Dolly In (#01) | Rack Focus (#06) |
| 对峙紧张 | Tilt Down→Up (#07/#08) | Dutch Angle (#15) |
| 战斗打击 | Crash Zoom Hit (#02) | Whip Pan (#18) |
| 角色展示 | Orbit Shot (#17) | Arc Shot (#13) |
| 逃跑/追逐 | Side Tracking (#16) | FPV Drone (#32) |
| 细节特写 | Macro Shot (#22) | Slow Dolly In (#01) |
| 主观代入 | POV Shot (#23) | Handheld (#31) |
| 能力释放 | Dolly Zoom (#05) | Reveal Behind (#26) |
| BOSS登场 | Reveal Behind Obstruction (#26) | Top-Down (#28) |
| 收束结尾 | Following Shot (#34) | Slow Dolly In (#01镜像) |

---

### Q4: 跨段连续性断裂

**症状**: SEG-01 和 SEG-02 的角色/场景看起来不像同一个片子。

**检查清单**:

```
□ 每段的角色外貌锚点（面部/发型/服装/体型）是否一致？
□ 光源方向是否统一？
□ 色调逻辑是否有突变？
□ 首帧衔接方案（方案A截取/方案B描述）是否已定义？
□ seedance-package-output-template.md 的「连续性方案」章节是否填写？
```

**修复方法**:
- 在每段提示词开头加 continuity note（连续性备注）
- 用方案A（首帧截取法）替代方案B（首帧描述法），实际视频衔接更稳定
- 建立「角色锚点速查表」，每次写提示词时逐项核对

---

## 🟡 中频问题

### Q5: 资产生图效果不好

**症状**: 用 Banana 2 生成的角色/场景图和剧本描述不符。

**优化建议**:

1. **角色资产**: 确保 JSON 中的 prompt 包含足够多的固定特征词
2. **场景资产**: 先出 master grid（全局概览），再补 multi-angle（多角度细节）
3. **道具资产**: 独立的道具必须单独出图，不能依赖场景中的道具质量
4. **迭代策略**: 第一版通常只到 60-70%，需要根据结果调整 prompt 再生成

详见 `references/banana2-asset-json-spec.md`

### Q6: 项目太大管不住

**症状**: 1-3min 的短片，段数太多，信息量爆炸。

**管理方法**:
- 用 `seedance-package-output-template.md` 的「全片概览」表作为全局导航
- 每完成一个 SEG 就更新进度标记
- 运镜设计总表（附录A映射矩阵）帮助追踪运镜多样性
- 如果超过 12 个 SEG，考虑拆成上下两部

### Q7: 想从中间某个阶段重新开始

**不需要重跑前面的阶段**，只要告诉 AI：

```
"我已经完成了 Stage 1-3（分析+方向+剧本），
 请从 Stage 4 审查开始"
```

AI 会要求你提供前一阶段的输出文件作为输入。

---

## 🟢 低频但重要的问题

### Q8: Skill 文件引用路径报错

**症状**: AI 报告找不到某个 reference 文件。

**检查**:
1. 文件确实存在于 `references/` 目录下
2. SKILL.md 中的路径正确（注意：v2.0 后部分模板移到了 `references/`）
3. 如果是从 GitHub 新 clone 的，确保拉取了最新代码

**当前正确的文件清单**:
```
references/
├── analysis-framework.md              ✅ 存在
├── asset-package-spec.md               ✅ 存在
├── banana2-asset-json-spec.md          ✅ 存在
├── cinematography-design-guide.md      ✅ v2.0 新增
├── producer-handoff.md                 ✅ 存在
├── script-review-order.md              ✅ 存在
├── script-template.md                  ✅ v2.0 新增
├── seedance-package-output-template.md ✅ v2.0 升级
├── seedance-package-spec.md            ✅ 存在
├── seedance-prompt-craft-notes.md      ✅ v2.0 升级（38种运镜）
├── seedance-segment-template.md        ✅ v2.0 升级
├── storyboard-timeline-template.md     ✅ v2.0 新增
├── video-input-ingestion.md            ✅ 存在
└── review-prompts/
    ├── ai-feasibility-review.md        ✅ 存在
    ├── art-style-review.md             ✅ 存在
    ├── chief-director-review.md        ✅ 存在
    ├── cinematography-review.md        ✅ v2.0 新增
    ├── costume-props-review.md         ✅ 存在
    ├── post-sound-review.md            ✅ 存在
    └── screenwriter-review.md          ✅ 存在
```

### Q9: 如何给 skill 贡献内容？

欢迎贡献！流程：

1. Fork 这个仓库
2. 创建特性分支 (`git checkout -b feature/xxx`)
3. 提交更改 (`git commit -m 'add xxx'`)
4. 推送分支 (`git push origin feature/xxx`)
5. 创建 Pull Request

**贡献类型**:
- 📝 新的审查提示词模板
- 🎬 新的运镜技巧案例
- 📊 更好的模板格式
- 🐛 Bug 修复
- 🌍 多语言支持（目前中文+英文）

### Q10: 版本兼容性

| 版本 | 关键变化 | 兼容性 |
|------|---------|--------|
| v1.0 | 初始版本，13种运镜 | — |
| v2.0 | 38种运镜体系、审查增强、模板升级 | v1.0 的项目可继续使用，但建议迁移到 v2.0 模板 |

**从 v1 迁移到 v2**:
- 替换 segment template 和 output template 为 v2.0 版本
- 在现有 SEG 中补充 🎥 运镜设计块
- 补充运镜自检（至少 6/9 项通过）
- 运行 cinematography-review 做一次运镜审查

---

## 还没找到答案？

如果以上都没有解决你的问题：

1. 检查 [`README.md`](./README.md) 是否有相关说明
2. 查看 [`samples/mranti-family-thriller/`](./samples/mranti-family-thriller/) 样例项目对比你的输出
3. 在 GitHub 上提 Issue：[wp746/video-reverse-engineer-skill](https://github.com/wp746/video-reverse-engineer-skill/issues)
