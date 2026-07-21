# Week 1

## 文章

- [SDD 的 95/5 原则](./advance/01-SDD的95-5原则.md)
- [SDD 工具四层金字塔](./advance/02-四层金字塔.md)
- [老项目逆向策略](./advance/03-老项目逆向策略.md)
- [Spec 的粒度怎么把握](./advance/04-Spec的粒度怎么把握.md)
- [AI 给的 spec 我该信多少](./advance/05-AI给的spec我该信多少.md)
- [SDD 遇到紧急 bug 怎么办](./advance/06-SDD遇到紧急bug怎么办.md)
- [团队里只有我想用 SDD 怎么办](./advance/07-团队里只有我想用SDD怎么办.md)

## 工具

Week 1 装 3 个开源 skill（来自 [mattpocock/skills](https://github.com/mattpocock/skills)）：

```bash
# 1. 安装（交互式选择 skill 与 coding agent）
npx skills@latest add mattpocock/skills

# 2. 每个 repo 跑一次，配置 tracker（选 Local markdown）
/setup-matt-pocock-skills
```

> **工具时效说明（2026-07 核实）**：Matt Pocock 的 skills 集合已调整——
> `to-issues` 更名为 **`to-tickets`**；`write-a-skill` 已移除，由 **`writing-great-skills`**（写好 skill 的参考文档）取代；
> 安装方式改为交互式，不再用 `-a <agent>` 逐个指定。`grill-me` 名称未变。
> 详见 [kage-ai.com/sdd](https://kage-ai.com/sdd/#tooling)。

skill 靠 description 字段自动触发 · 无需 `/skill` 前缀。
