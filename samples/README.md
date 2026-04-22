# 样例项目：mranti-family-thriller（暂缓探视）

> **版本**: v1.0 样例 | **模式**: 30-60s 主题短片 | **总时长**: 52s

## 说明

这是一个完整的 8 阶段流水线输出样例，展示了从分析到 Seedance 提示词包的完整流程。

**注意**：此样例基于 **v1.0 模板**生成。v2.0 的输出会额外包含：
- 🎥 每个 SEG 内的**运镜设计块**（主运镜★ + 辅运镜☆ + 情绪目标）
- ✅ **运镜自检清单**（9项检查）
- 📊 **运镜设计总表**（附录A/B/C）
- 更详细的**运镜参数**（速度/距离/焦段/持续时间）

## 文件列表

| 序号 | 文件 | 阶段 | 说明 |
|------|------|------|------|
| 01 | selected-direction.md | Stage 2 | 选定的创意方向 |
| 02 | script-v1.md | Stage 3 | 初版剧本 |
| 03 | script-review-summary-v1.md | Stage 4 | 第一轮审查结果 |
| 04 | script-v2-approved.md | Stage 3 | 通过审查的修订剧本 |
| 05 | producer-handoff.md | Stage 5 | 制片主任资产拆解 |
| 06 | banana2-asset-package.json | Stage 6 | Banana 2 资产包总览 |
| 07-13 | banana2 *.json | Stage 6 | 各类资产 JSON（角色/场景/道具） |
| 14 | storyboard-timeline.md | Stage 7 | 分镜时间轴 |
| 15 | seedance-package-final.md | Stage 8 | Seedance 提示词包（终版） |
| 16 | seedance-package-production.md | Stage 8 | 生产执行版提示词 |
| 17 | banana2-prompts-production.md | Stage 8 | Banana 2 生图提示词 |

## 如何参考这个样例

1. **按顺序阅读**：从 01 → 17，体验完整的流水线
2. **对比审查前后**：02 vs 04 看审查如何驱动剧本迭代
3. **对照模板**：用 `references/` 下的 v2.0 模板对比此样例的差异
