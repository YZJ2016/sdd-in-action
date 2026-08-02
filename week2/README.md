# Week 2

## 代码在哪

`code/` 目录是 `add-analyzer-retry-policy` 这个 change **做完之后**的状态，retry 已经落在 `pipeline/model_client.py` 的 `with_retry()` 装饰器上。

跟着实操文档动手时，对照关系是这样：

| 文档里说的 | 仓库里的位置 |
|:--|:--|
| change 的 proposal / design / spec / tasks | `code/openspec/changes/archive/2026-04-20-add-analyzer-retry-policy/`（已 archive） |
| 合并后的主规范 | `code/openspec/specs/analyzer-retry-policy/spec.md` |
| retry 实现 | `code/pipeline/model_client.py` — `with_retry()` 与 `@with_retry()` 装饰的 `chat()` |
| 验收测试 | `code/tests/test_retry.py` |

文档里 `/opsx:archive` 之前的路径（`openspec/changes/add-analyzer-retry-policy/`）在仓库里已经归档，这是 OpenSpec 的正常生命周期，不是文件丢了。

实操文档是流水账，代码块给的是命令与关键片段，完整源码以本仓库为准。

## 文章

- [OpenSpec 的 7+ 命令哪个最值得学](./advance/01-OpenSpec命令优先级.md)
- [/opsx:new 和手写 spec 的区别](./advance/02-opsx-new和手写的区别.md)
- [Hooks 什么时候不用写](./advance/03-Hooks什么时候不用写.md)
- [CI/CD 里 spec 的角色](./advance/04-CI-CD里spec的角色.md)
- [成本超标的 spec 应该长什么样](./advance/05-成本超标spec长什么样.md)

## 工具

Week 2 装 OpenSpec（Week 1 的 skill 保留）：

```bash
npm install -g @fission-ai/openspec@latest
cd your-project && openspec init

# 关键 · 启用 expanded 命令（默认 core 只有 4 条）
# v1.3.0 暂无预设 · 直接改 ~/.config/openspec/config.json 的 workflows 数组：
# ["propose","explore","apply","archive","new","continue","ff","verify","sync","bulk-archive","onboard"]
openspec update
```

改完重启 IDE。本周用到 7 个 `/opsx:*` 命令：`new · ff · apply · verify · sync · archive · onboard`（默认 core 只有 `propose · explore · apply · archive` 四条，不够用）。
