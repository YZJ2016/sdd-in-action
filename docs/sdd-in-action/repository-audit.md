# 仓库内容与落地缺口审计

日期：2026-10-12。分析对象：本地 `master`，提交 `7ccc24b38f7cae09897ace41ebae14780250ac86`。本文件记录当前材料状态；修正建议尚未应用到原案例。

## 1. 内容地图

| 范围 | 已有内容 | 如何使用 |
|---|---|---|
| [根 README](../../README.md) | 十章三阶段目录、仓库导航、书籍与行动营映射 | 定位课程结构；不等于完整书稿 |
| [book-code](../../book-code/README.md) | 团队日报 proposal/design/tasks、数据模型、3 个 ADR、2 个练习 | 主规范模板；当前目录没有 README 预告的 src/tests/templates |
| [Week 1](../../week1/README.md) | 四段模板、愿景、编码规则、三 Agent PRD/任务票、2 个 schema、Agent/Skill 描述 | 学会需求边界与协作契约；不是可直接运行的完整 Python 项目 |
| [Week 2](../../week2/README.md) | 四步 Python 流水线、LLM 重试客户端、pytest、已归档 change、主 spec、工具命令文件 | 观察 proposal→实现→测试→主规范→归档 |
| [Week 3](../../week3/README.md) | 七节点 LangGraph 工作流、Router/Supervisor 演示、成本与安全辅助模块、eval 测试、BMAD 6.6.0 安装材料 | 学运行期拓扑与开发期角色的区别；核对规范是否匹配实际代码 |
| [Week 4](../../week4/README.md) | Digest spec/deploy spec、SMTP 示例、Dockerfile/Compose | 邮件交付骨架；需补真实输入、状态和可构建依赖 |
| `book-code-snippets.zip` | 目录条目与 book-code 配套规范/练习 | zip 没有额外隐藏的 src/tests 实现 |
| `assets/` | 书籍封面 | 展示素材 |
| 根目录 briefing HTML/PNG | 工作区已有未跟踪推广材料 | 辅助参考；不是已提交书稿基线，保持原文件 |

BMAD 与 OpenSpec 的集成目录包含上游生成材料。它们说明工具安装、提示词与工作流入口，不应计入业务实现完成度。Week 3 README 提到的 metrics 完成分支没有在本次切换或拉取；当前有两个示例 metrics JSON，不能据此认定埋点已在工作流接入。

## 2. 22 篇进阶文章转成实施规则

| 来源 | 核心观点 | 建议落地动作 |
|---|---|---|
| W1 01：95/5 | 先思考、写清需求比选工具更重要 | 先完成四段式真实变更；比例是强调而非统计指标 |
| W1 02：四层金字塔 | 原子技能、上下文、框架、完整方法论分层 | 只为当前痛点升级工具 |
| W1 03：老项目逆向 | 改哪里补哪里 | 当前行为 baseline 与目标 delta 分开 |
| W1 04：粒度 | 默认功能级；条款可验证 | 一个可审查变更配一份规范，按风险调整长度 |
| W1 05：AI spec | 质疑数值、边界与验证方法 | 数字标来源；业务负责人确认；反向评审 |
| W1 06：紧急 bug | 应急流程可以简化，事后沉淀 | 最小修复记录与回归；时间经验值不当硬规则 |
| W1 07：推广 | 个人示范→同事试用→团队默认 | 用真实收益带动推广，后期再培训与门禁 |
| W2 01：命令优先级 | 学主干生命周期 | 以当前官方 profile 为准，不继承“propose 过时”说法 |
| W2 02：手写与框架 | 框架管理分层工件与历史 | 有持续维护痛点再引入；归档位置统一 |
| W2 03：Hooks | hook 要快、职责明确 | 本地只做快速检查；CI 做统一强制门禁 |
| W2 04：CI/CD | spec 管触发、失败和配置漂移 | workflow 链接 spec；配置变更也有验收 |
| W2 05：成本 | 分层预算、按比例告警、自动降级 | 统一币种和硬停止语义，调用前预留预算 |
| W3 01：角色选择 | 同时用少量必要视角 | 默认业务/架构/质量；特殊场景再增加 |
| W3 02：协作契约 | 数据、时序、失败、观测、兼容 | 用 schema 与状态契约约束交接 |
| W3 03：BMAD/OpenSpec | 多视角决策与变更生命周期互补 | 共识写入一套工件，避免平行事实来源 |
| W3 04：记忆 | 保留、清洗、失效、跨 Agent 可见性 | 单独的 memory governance 规则 |
| W3 05：退回单 Agent | 没有独立子问题时不要硬拆 | 用质量/成本/延迟数据证明复杂拓扑价值 |
| W4 01：TDD | 生产与短期原型有不同成本收益 | 核心行为/修复先测试；原型转生产前补契约 |
| W4 02：演化路径 | 每层补前一层不足 | 四周是训练路径，生产不强制四工具全装 |
| W4 03：Plugin | 工具生态变化快，方法更稳定 | 记录验证版本，弱化星标/市场背书 |
| W4 04：冲突 | 阶段负责人、目录与流程优先级 | 关键规范进 Git；忽略缓存，不能 blanket 忽略所有 AI 工件 |
| W4 05：带走什么 | 思考、多视角、测试、可追溯 | 把四点接入现有研发流程 |

## 3. 主要缺口与处理顺序

P0：对应能力生产使用前必须解决；P1：试点必须补齐；P2：后续增强。这些等级表示落地优先级，不是对教学仓库的漏洞评级。

### 3.1 书籍案例

| ID | 证据 | 发现 | 建议 |
|---|---|---|---|
| A01 / P0 | [ADR-003](../../book-code/specs/adrs/003-采集层返回值封装.md)、[契约](../../book-code/specs/contracts/data-models.md)、[设计](../../book-code/specs/design.md)、[任务](../../book-code/specs/tasks.md) | ADR 已采纳 CollectResult，但主契约和 design 仍返回 list；T3/T4 仍要求失败返回空列表 | 同一次变更同步四处，并写失败/空数据契约测试 |
| A02 / P0 | [proposal](../../book-code/specs/proposal.md) §3.1 / §4 | “过去24小时”和“当天00:00至执行”不是同一个采集窗口 | 确认业务时区、工作日日历与半开区间 |
| A03 / P1 | proposal §2 与 design §2 | 需求涉及 GitHub/GitLab、飞书/Jira，但设计与任务只覆盖 GitHub/飞书；讨论摘要与“不做语义理解”也需明确 | 划清一期平台；沟通部分采用关键词筛选或确认新增语义范围 |
| A04 / P0（部署前） | [book-code README](../../book-code/README.md) 与目录/zip 清单 | src/tests/templates 是渐进发布预告，当前 checkout 尚不存在 | 作为待实现项目估算，不能声称已有完整日报程序 |
| A05 / P1 | tasks 元信息与性能验收 | 3–4 小时是示例估算；mock <60s 不证明真实外部依赖下达标 | 按集成权限和实测重新估算，分别验收 mock 与真实运行 |

### 3.2 Week 1 / Week 2

| ID | 证据 | 发现 | 建议 |
|---|---|---|---|
| B01 / P0 | W1 [collector schema](../../week1/specs/schemas/collector-output.json)、[analyzer schema](../../week1/specs/schemas/analyzer-output.json)，W2 [pipeline](../../week2/code/pipeline/pipeline.py) | W1 对象封套+topics+labels；W2 写 list、source=github、summary/tags/relevance/category，无同一套 schema | 定义版本和适配；不要默认四周代码直接兼容 |
| B02 / P1 | W1 [organizer issue](../../week1/specs/issues/03-organizer.md) 与 [Agent 描述](../../week1/code/03/agents/organizer.md) | issue 按 tech 分组、stars 排序；Agent 按 innovation 分组；标签简称和 schema 字段名也不同 | 选一套排序/字段语义，同步派生配置 |
| B03 / P1 | W2 [README](../../week2/README.md)、[AGENTS](../../week2/code/AGENTS.md)、pipeline 末尾 | README 正确描述完成态，AGENTS 和 CLI 文案仍称“无retry”；AI 会接收错误现状 | 更新当前上下文，将教学起点放历史说明 |
| B04 / P1 | [归档 design](../../week2/code/openspec/changes/archive/2026-04-20-add-analyzer-retry-policy/design.md) 第35行与 [model_client](../../week2/code/pipeline/model_client.py) 第57行、主 spec | design=3 attempts；实现/主 spec=4；归档 proposal 也写3 | 明确首次和重试次数，保留勘误与最后生效版本 |
| B05 / P1 | model_client 第97–110行 | 先 min cap 再乘 jitter，参数增大时实际 sleep 可超过 max_delay；默认4次不触发这个问题 | 最终等待时间封顶；测试大 base_delay 与上限 |
| B06 / P1 | model_client get_client 与 with_retry | 自定义重试之外未显式设置 SDK 重试；实际网络尝试可能与 api_calls 指标不同 | 核查并固定 SDK 版本/重试配置，集中管总尝试与 deadline |
| B07 / P0（成本硬限场景） | [cost-budget](../../week2/specs/cost-budget.md)、[project-vision](../../week1/specs/project-vision.md)、W2 estimate_cost | 日目标 $0.50 与 $5 不同；spec 100%叫硬上限却120%才停；降级触发与验证描述也不一致；代码以人民币估计并不执行整套治理 | 明确产品版本、币种、硬限和预警；治理接入所有调用 |
| B08 / P1 | pipeline main、[pipeline spec](../../week2/specs/pipeline.md)、[ci spec](../../week2/specs/ci.md) | 实际入口 `python -m pipeline.pipeline --limit ...`；没有 spec 中 date/force/skip-to；也没有对应 __main__.py 支持 `python -m pipeline` | 给计划能力标“未实现”；用 help/CLI 测试验收 |
| B09 / P1 | W2 主 spec/归档 tasks 与 pipeline step_analyze | tags 的列表/字符串描述不一致；json.loads 后未做字段类型验证；模拟零费用调用并不是持久化成本台账 | schema 验证；独立计 attempts 与已知/未知费用；补非法字段测试 |

W2 1/2/4 秒策略与周级 pipeline spec 的1/4/16秒、Retry-After策略不同。可能来自不同教学阶段，落地时需明确各策略的作用域和生效版本，不能自动认为它们是同一实现的约束。

### 3.3 Week 3

| ID | 证据 | 发现 | 建议 |
|---|---|---|---|
| C01 / P0 | [state-graph spec](../../week3/specs/state-graph.md)、[graph.py](../../week3/code/workflows/graph.py) | spec 是 Supervisor 调度三worker；代码是 plan→collect→analyze→review→revise/organize/human_flag | 更新工作流 spec；patterns 演示与主产品明确分开 |
| C02 / P0 | [reviewer.py](../../week3/code/workflows/reviewer.py) 第115–119行、[planning-review](../../week3/specs/planning-review.md) | Reviewer 异常自动通过；复核队列>150自动批准；都可能把未经审核内容变成正式产物 | 改 needs_review/暂停发布，溢出限流或延期，不能越过门禁 |
| C03 / P1 | reviewer.py 第61行 | 只看前5条给整批通过，没有全体条目安全性保证 | 至少全量确定性校验；按条目状态或定义有依据的抽样范围 |
| C04 / P1 | [eval_test.py](../../week3/code/tests/eval_test.py) 第109–143行与 graph 第49行 | 测试自己模拟“第3次强制通过”；真实路由达到上限进入human_flag；另外两项也未调用真实节点 | 改成真实路由/节点与有界循环测试 |
| C05 / P1 | [model_client](../../week3/code/workflows/model_client.py)、[cost_guard](../../week3/code/tests/cost_guard.py)、[security](../../week3/code/tests/security.py)，运行模块引用搜索 | 成本/安全辅助代码主要在tests；关键主流程未引用CostGuard/secure_input/secure_output；有工具不等于治理已生效 | 移到运行模块，通过统一网关接入并验证阻断 |
| C06 / P1 | [observability spec](../../week3/specs/observability.md)、workflows 与 requirements | 所需8个OTLP span未在核查的主工作流实现；main 分支metrics文件不是接入证据 | 独立实现和验收埋点；检查失败不阻塞主业务 |
| C07 / P0（真实数据使用） | [supervisor.py](../../week3/code/patterns/supervisor.py) collector_worker | 通过 prompt 请求模型“模拟采集”，不是联网采集 | 保持演示标签；生产使用真实适配器和来源验证 |
| C08 / P1 | [organizer.py](../../week3/code/workflows/organizer.py) 与 [Digest](../../week4/code/daily_digest.py) | 输出逐条JSON/index；下游读日期Markdown；缺innovation_level/difficulty等Digest字段 | 统一发布schema，从JSON渲染，避免反解析Markdown |
| C09 / P1 | organizer.py / graph.py / state-graph spec | 现代码主要用内存state和直接写文件；没有spec描述的done重跑机制；日序号ID和追加索引存在重跑语义风险 | 稳定item_id、原子写入、checkpoint与输入版本 |
| C10 / P1 | [collector.py](../../week3/code/workflows/collector.py)、[analyzer.py](../../week3/code/workflows/analyzer.py) | API失败变成ERROR条目，下游跳过；全失败可能流到“没有条目需审核”而正常结束 | 独立stage状态，全失败禁止成功/发布假象 |

Week 3 Planner 是规则策略函数，不是 LLM 自主规划。KBState 是 TypedDict，不是运行时 schema。实际 Collector 走 GitHub Search API，不是 Trending HTML；产品与数据源名称应如实记录。

### 3.4 Week 4

| ID | 证据 | 发现 | 建议 |
|---|---|---|---|
| D01 / P0 | [daily_digest.py](../../week4/code/daily_digest.py) 第38–47行 | 只检查文件存在，随后返回5个mock项目，未解析和排序 | 实现真实结构化输入，拒绝发送占位条目 |
| D02 / P0 | daily_digest 第79、84–98行与 digest/deploy spec | 取消订阅token占位；SMTP无显式timeout/重试；无持久化发送状态 | 完成取消订阅链路、超时、账本、失败与不确定状态 |
| D03 / P0 | [Dockerfile](../../week4/code/Dockerfile) 第10–11行与目录 | COPY requirements.txt，但week4/code未提供此文件；缺配置/subscribers样例 | 加入构建输入和配置校验，实际构建验收 |
| D04 / P1 | Dockerfile 第17–21行 | tail未预创建日志；首次cron运行前可能因文件不存在退出；cron的Python路径/env需要验证 | 明确运行环境，可靠启动日志，端到端验证cron |
| D05 / P1 | [Compose](../../week4/code/docker-compose.yml) healthcheck | pgrep需核查镜像是否有对应程序；检查cron存活也不等于邮件成功 | 实际镜像验证命令；增加业务完成时间指标 |
| D06 / P1 | Compose volumes 与 deploy spec | knowledge只读挂载；发送标记需要另设可写持久化位置；当前无发送ledger | 明确可写state volume与跨重启唯一键 |
| D07 / P1 | daily_digest load_subscribers/main | YAML结构和邮箱未校验；总发送失败仍可正常退出；dry-run也累加sent | 输入错误可诊断；输出simulated/sent/failed分别统计；失败退出语义 |
| D08 / P2 | digest spec 与代码 | 取关率停推、p99、<500人5分钟均缺实现或测量；主题固定5条；description未强制50字 | 指标接入业务数据；基于数量渲染；压测后确定容量 |

## 4. 文档和工具时效

- `/opsx:onboard`：仓库自带 [命令文件](../../week2/code/.claude/commands/opsx/onboard.md) 描述完整首次变更教学；advance 将它描述为模块逆向baseline工具，含义不一致。
- OpenSpec 实际归档是 `changes/archive`；部分文章写 `openspec/archive`。
- 现行 OpenSpec 官方入门支持propose快速路径与profile配置，不应把仓库的旧版说明直接当现行操作规程。[官方入门](https://github.com/Fission-AI/OpenSpec/blob/main/docs/getting-started.md)
- BMAD本地manifest是6.6.0；文章中的 `.bmad-core` 与当前 `_bmad` 实物不同。目录与命令应跟验证版本走。
- “工具生成目录全部加入gitignore”过于宽泛：规范、ADR、可复用项目规则应版本管理；缓存、临时会话和秘密才按内容忽略。
- 根briefing材料强调会议/分享/培训，W1推广文章反对早期强推。可按推广阶段协调：个人试点先证明收益，团队/组织阶段再正式培训。

## 5. 核查方法与限制

已做：目录与隐藏集成入口清点；book-code zip清单；公开规范和22篇进阶文档梳理；代码图索引、符号读取、build_graph关系检查；关键源码回读；工具官方资料核查。

代码图对LangGraph节点回调的调用边不完整：build_graph的图trace未返回节点调用链，但source明确注册节点。本文据真实图构建源码描述拓扑，没有以图中缺少CALLS边判断节点不可达。

coverage检查对关键路径报告metadata_changed；已回读所依赖源码，图关系只辅助定位。Dockerfile第7–20行partial已直接读。排除的命令目录通过直接读取入口核查；媒体资源没有当业务行为证据。

运行核查结果：

| 检查 | 实际结果 | 结论边界 |
|---|---|---|
| Python环境探测 | Python 3.12.5；pytest/openai/httpx/langgraph/yaml缺失，dotenv存在 | 当前环境不能直接执行案例完整测试 |
| 应用与测试源码AST解析 | 25个Python文件解析通过（W2 pipeline/tests，W3 workflows/patterns/tests，W4源码；不含BMAD生成脚本） | 仅证明语法可解析，不证明依赖、运行、类型或行为正确 |
| 实际route_after_review函数 | AST隔离执行：通过→organize；未通过且未达上限→revise；达到上限→human_flag，3分支断言通过 | 使用源码原函数，未加载LangGraph，不是集成测试 |
| 实际review_node故障注入 | AST隔离执行，chat_json替身抛RuntimeError，结果review_passed=True | 复现C02现有放行行为；没有修改它 |
| 新文档本地链接/代码块 | 3个Markdown文件本地链接存在，围栏成对 | 基础文档完整性通过 |

未运行整套pytest、Docker构建、真实外部服务或付费模型评估；不能将静态可解析、离线路由结果推断为生产可用。
