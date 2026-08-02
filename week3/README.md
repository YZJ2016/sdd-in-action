# Week 3

## 代码在哪

本周实操文档带你从 BMAD 规划一路做到 metrics collector 落地。两个分支各有分工：

| 分支 | 内容 | 什么时候用 |
|:--|:--|:--|
| `master` | 起始基线，7 个 Agent 已就位，没有 metrics 相关代码 | 跟着文档动手时从这里出发 |
| `feature/add-metrics-collector-local` | 完成态参考答案 | 做完了想对答案，或者中途卡住想看成品 |

```bash
# 对答案
git fetch origin
git checkout feature/add-metrics-collector-local
```

完成态分支里能看到文档提到的全部产物：

- `code/workflows/metrics_collector.py` — `track_metrics` decorator 与 `flush_metrics_node`
- `code/openspec/changes/add-metrics-collector/` — proposal / design / spec / tasks 四件套
- `code/_bmad-output/planning-artifacts/` — BMAD 阶段产出的 PRD 与架构文档

实操文档里的代码块是命令与关键片段，完整源码以本仓库为准。

## 文章

- [BMAD 的 12+ 角色不是越多越好 · 怎么挑](./advance/01-BMAD的12角色怎么挑.md)
- [多 Agent 协作的 spec 和单 Agent 有什么不一样](./advance/02-多Agent和单Agent的spec区别.md)
- [BMAD 和 OpenSpec 怎么配合 · 不要当成替代关系](./advance/03-BMAD和OpenSpec怎么配合.md)
- [Agent 间的"对话历史"要不要写进 spec](./advance/04-Agent间对话历史要不要写进spec.md)
- [什么情况下应该退回单 Agent](./advance/05-什么情况该退回单Agent.md)

## 工具

Week 3 装 BMAD（Week 1 的 skill 和 Week 2 的 OpenSpec 继续保留）：

```bash
cd your-project && npx bmad-method install
```

BMAD 不替代 OpenSpec。BMAD 管视角（多角色 review）· OpenSpec 管流程（change 生命周期）。
