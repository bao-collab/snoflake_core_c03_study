# Snowflake SnowPro Core (COF-C03) — Master Progress

Last updated: 2026-08-13

> ⚠️ **SUPERSEDED 2026-08-12.** The chunk-based tracking below is frozen at its July state and is no longer the live plan. Exam is booked for **2026-08-29 15:45 (offline, Pearson VUE)** and will not be rescheduled. The active plan is the 冲刺计划 pane in `SnowPro_Core.html`; daily actuals go in its 实绩表. Keep the sections below only as reference for what was covered pre-sprint. See "Sprint Log" at the bottom for current status.

> Per-session notes live in `progress-YYYY-MM-DD.md` files in this folder. This file is the master roll-up.

---

## Overall Progress

**Total chunks completed: 1/55 (2%)**

| Domain | Weight | Chunks | Status | Last Reviewed | Next Review |
|--------|--------|--------|--------|---------------|-------------|
| 1. Snowflake AI Data Cloud Features & Architecture | 31% | 1/13 (8%) | Chunk 1 done (75% quiz); Chunk 2 next | 2026-07-21 | — |
| 2. Account Management & Data Governance | 20% | 0/12 (0%) | Not started | — | — |
| 3. Data Loading, Unloading & Connectivity | 18% | 0/12 (0%) | Not started | — | — |
| 4. Performance Optimization, Querying & Transformation | 21% | 0/11 (0%) | Not started | — | — |
| 5. Data Collaboration | 10% | 0/7 (0%) | Not started | — | — |

> Weights from official COF-C03 syllabus (updated 2026-06-29). Chunk counts are the primary progress metric; hour estimates below are for rough planning only.

---

## Study Guide Updates (from official COF-C03 guide, Jan 19 2026)
- **Openflow** — marked NOT TESTED until GA; deprioritize
- **Default warehouse for Notebooks** — marked NOT TESTED until GA; deprioritize
- **Trust Center** added to Domain 2 checklist
- **Gen 1 vs Gen 2 warehouse types** added to Domain 1 checklist
- **Query Insights** (alongside Query Profile) added to Domain 4

## Restructure 2026-07-06 (aligned to official EN guide, Jan 19 2026)
All domain files + study plan reorganized to the official 1.1–5.3 objective structure:
- **Time Travel / Fail-safe / Zero-Copy Cloning** → Domain 5.1 (were in Domain 1); basics already covered as D1 Chunk 1 gap topics
- **Streams / Tasks / Dynamic tables** → Domain 3.2 (were in Domain 4)
- **Snowpark** → Domain 1.6 (was in Domain 4)
- **Resource monitors / cost monitoring** → Domain 2.3 (were in Domain 4)
- Added: DAC, securable object hierarchy, functional roles, account identifiers, logging & tracing (D2); server-side encryption, drivers vs connectors (D3); exploding joins/queuing signals, workload grouping, materialized views, unstructured data (D4); sharing & re-sharing, direct shares (D5); view types + full object hierarchy (D1)
- Removed (not in official guide): Data Exchange, compliance standards (SOC 2/HIPAA/PCI); JPN-only additions (cost center tagging, budgets) excluded per decision to follow EN guide only

## Session Log
| Date | File | Covered | Quizzed? |
|------|------|---------|----------|
| 2026-07-27 | [progress-2026-07-27.md](progress-2026-07-27.md) | Streams & Tasks/DAGs (D3 Ch 7–8), Unistore/Hybrid Tables (D1), Openflow + managed dbt (not tested) | **No — quiz pending** |

---

## Weak Areas (Flagged for Review)
> Rule: re-quiz each weak point at the next session; a study-guide video module is only warranted if it stays weak after a chunk quiz AND a spaced review.

- **Domain 1 — Metadata**: Confused it with storage layer.
  ✓ Metadata lives in Cloud Services (min/max, row counts per partition)
  Refs: [Key Concepts & Architecture](https://docs.snowflake.com/en/user-guide/intro-key-concepts) · [Micro-partitions & Data Clustering](https://docs.snowflake.com/en/user-guide/tables-clustering-micropartitions)
- **Domain 1 — Cloud Services vs Cloud Provider**: Confused the two on 2026-07-06 and 2026-07-11. **Correct on 2026-07-21 refresher re-quiz** — resolved, drop from active weak list unless missed again.
  ✓ Cloud Services is Snowflake's own brain; AWS/Azure/GCP are just the infrastructure underneath
  Refs: [Key Concepts & Architecture](https://docs.snowflake.com/en/user-guide/intro-key-concepts) · [Supported Cloud Platforms](https://docs.snowflake.com/en/user-guide/intro-cloud-platforms)
- **Domain 1 — Cloud Services layer responsibilities & caches** (added 2026-07-11, re-quiz ~3/6): didn't know result cache serves queries without a warehouse (Q2); placed micro-partition metadata in storage layer again (Q3); knew metadata answers COUNT(*) but couldn't name the layer (Q5).
  ✓ Cloud Services owns: query optimizer, metadata store, result cache, metadata cache, auth, transactions, pruning
  Refs: [Key Concepts & Architecture](https://docs.snowflake.com/en/user-guide/intro-key-concepts) · [Using Persisted Query Results](https://docs.snowflake.com/en/user-guide/querying-persisted-results)

---

## Daily Review Schedule (Spaced Repetition)
> Reset 2026-07-11 — old April schedule dropped (Domain 1 restarted from scratch). Add a row when each domain's chunks complete; intervals: Day 3 → Day 7 → Day 14.

| Domain | Completed | Review Intervals |
|--------|-----------|-----------------|
| — | — | — |

---

## Timeline Estimate
| Phase | Est. Time |
|-------|-----------|
| ~55 chunks (explain + quiz; finer-grained after 2026-07-06 restructure, ~0.5 hr each) | ~27 hours |
| 5 domain mock exams | ~2.5 hours |
| Daily spaced repetition (~15–20 min/day over ~3.5 weeks) | ~7 hours |
| Full mock exam + review | ~3 hours |
| **Total** | **~40 hours** |

### Schedule (restarted 2026-07-11)
- Weekdays: 1.5–2 hrs/day
- Weekends: 4+ hrs/day (exception: Jul 25–26 reduced to 2 hrs/day)
- ~16 hrs/week

### Milestones
| Milestone | Target |
|-----------|--------|
| All ~55 chunks done | ~Jul 22–23 (end of week 2) |
| Domain mock exams (after week 2) | Jul 24–27 |
| Full mock exam + weak-area review | Week of Jul 28 |
| **Exam** | **First week of August 2026** |

### Current Progress
- Started: 2026-04-20; resumed 2026-06-30; full restart 2026-07-11
- Chunks completed: **1/55 (2%)** (see per-domain breakdown in Overall Progress table above) + Chunk 1 gap topics covered
- Time spent so far: ~2.5 hours (Chunk 1 + gap topics + Day 14 review)
- Estimated remaining time: ~37 hours

---

## Mock Exam Scores
| Exam | Date | Score | Weak Domains |
|------|------|-------|--------------|
| — | — | — | — |

---

# Sprint Log (2026-08-12 → 08-29)

Live plan: `SnowPro_Core.html` → 冲刺计划 pane. This log records what actually happened, one line per day.
Baseline: 1452-question bank, 47% on first exposure.

| Date | Planned | Actual | Note |
|------|---------|--------|------|
| 8/12 (三) | — | ✕ 未执行 | 任务顺延至 8/13 |
| 8/13 (四) 在家 | 通读笔记全文 0.7h + Domain 1&4 精读 1.2h（2h） | ✅ 全部完成 | 无欠账带入 8/14。D1(31%)+D4(21%)=52% 已建框架 |
| 8/14 (五) 在家 WFH | D2&3 精读 1.3h + D5 0.4h + 五问自测 0.3h + 验证 App 5min（2h） | | 五问自测是进入阶段二的唯一门槛 || 8/15 (六) 阶段二第 1 天 | 第 1–200 题（4h） | **154 题，正确 92 / 错误 62，正确率 60%**；实际学习 3h10m（含早上速读 session 2–3 笔记） | 下午昏睡 1–2h。**154/200 = 完成 77%，欠 46 题**。60% vs 基线 47%，**高 13 个百分点**。晚间块 54 题、31 正确（57%），略低于白天的 61%——疲劳可见但不严重 |
| 8/16 (日) 阶段二第 2 天 | 200 题（4h） | **全天（含跨零点续做）176 题，正确 97 / 错误 79，当日正确率 55%**；累计 330 题 = 正确 189 / 错误 141（57%）。分三段：**午前 46 题 @ 48%，午后 50 题 @ 66%，晚间+夜间 80 题 @ 53%** | 未达配额（176/200）。夜间续做正确率回落（46% vs 午后 66%），符合疲劳假设。仅复盘 3 题（REFERENCE_USAGE / Egress / Revoke，均 D5），样本太小不出分布表 |
| 8/17 (一) | 130 题（不追欠，优先补 D3）（2.4h） | 累计 268/192=460 题，58%；当日新增 81 题，正确 52/错误 29（64%）。另：错题复盘单独计数，累计 11/5=16 题，69% | |

**⏰ 待复习：C03 精读①**（8/17 首读）→ 排到 **8/19 或 8/20** 二刷一次（间隔 2-3 天，防止遗忘），8/22 buffer day 前必须做完二刷。

**中途检查点（8/18 晚提前测）**：App 里实际收藏/标记数 = **39 题**，远低于计划估算的 700–900（甚至低于保守下限 500）。原因待确认：标记纪律没跟上 / 正确率明显好于 47% 起步假设。若属实且标记完整，阶段三（8/23–8/26）容量绰绰有余，不需要按原计划担心装不下。

## 高频错误知识点复发清单（持续累积，考前专项过一遍）

| 知识点 | 出错次数 | 首次 | 最近 |
|---|---|---|---|
| PUT/GET 方向（本地 ↔ Internal Stage） | 3 | 8/17 | 8/17 |
| MIN_CLUSTER_COUNT vs MAX_CLUSTER_COUNT（排队该调哪个） | 2 | 8/17 | 8/17 |
| 文件格式 vs 数据类型（JSON≠VARIANT、Avro 卸载方向） | 2 | 8/17 | 8/17 |
| 编造不存在的语法（如 `USE SECONDARY ROLES ADD <role>`） | 1 | 8/18 | 8/18 |

## 8/16 EOD 汇总（18:17 报数）

**分段对比 —— 这是今天最有价值的数据：**

| | 午前 | 午后 |
|---|---|---|
| 题量 | 46 | 50 |
| 用时 | 78 min | **55 min** |
| 速度 | **102 s/题** | **66 s/题** |
| 正确率 | **48%** | **66%** |

→ **午后更快 35%，同时正确率高 18pt。** 这否定了「慢=仔细」的假设：午前的慢不是在思考，是在**被笔记补录打断**（每题停下来复盘）。午睡 + 改成「只标记不复盘、攒批复盘」之后，两个指标同时改善。
→ **66 s/题已优于 74 s 的基线。** 按这个速度，4h 纯做题 = 218 题，200 题/天的配额可行。
→ **结论：批量复盘的做法保留，明天全天照此执行。**

**今日复盘错题的五域分布（25 道，占当日 41 道错题的 61%）：**

| 域 | 数量 | 占比 | 考试权重 |
|---|---|---|---|
| **D1 架构** | **9** | **36%** | 31% |
| **D3 加载** | **7** | **28%** | 18% ⚠️ 超配 |
| D4 性能 | 4 | 16% | 21% |
| D2 治理 | 3 | 12% | 20% |
| D5 协作 | 2 | 8% | 10% |

→ **D3 是唯一显著超配的域（28% vs 18%）**，且午前午后都在错。8/17 优先补 D3。
→ D1 绝对数最大但与权重相称，属正常暴露。

**当日错法结构（25 道）**：读题/词组重心 6 · 纯知识缺口 6 · 已有知识没调用 5 · 假术语 4 · 新花样（真指标当杠杆、同选项换轴、缩写展开错）4。
→ **知识缺口仍只占 24%**，与午前判断一致。**「读题 + 没调用」合计 44%，是最大的一块**，且这部分**不靠加笔记解决**。
→ 今天补进笔记的判据里，**最便宜的三条**（不需要知识、纯形式判断）：
① 语法搅在一起的选项直接扔（`cloud provider as a consumer account`）
② `without` ≠ `not for` —— Snowflake 说「不必」，极少说「不许」
③ 暗示停机的词（`provision` / `suspended while` / `wait for` / `downtime`）一律减分
→ **`provision` 是今天唯一重复坑到的词**（此前已错过一次）。原笔记里它只以正面用法出现，反而强化了错误印象，现已补反面。

## 8/17 EOD 域分布（约 25 道复盘）

| 域 | 数量 | 占比 | 考试权重 |
|---|---|---|---|
| D3 加载 | 9 | 36% | 18% ⚠️ 超配 |
| D1 架构 | 6 | 24% | 31% |
| D4 性能 | 4 | 16% | 21% |
| D2 治理 | 4 | 16% | 20% |
| D5 协作 | 2 | 8% | 10% |

**高危复发**（同一坑第 2/3 次）：PUT/GET 方向反了（第 3 次）、"能做 vs 最优"（MIN/MAX cluster，第 2 次）、format vs type 混淆（JSON/VARIANT，第 2 次）。

## 累计域分布（8/16 + 8/17，共 50 道）

| 域 | 数量 | 占比 | 考试权重 | 差值 |
|---|---|---|---|---|
| D3 加载 | 16 | 32% | 18% | **+14pt 超配** |
| D1 架构 | 15 | 30% | 31% | 持平 |
| D4 性能 | 8 | 16% | 21% | −5pt |
| D2 治理 | 7 | 14% | 20% | −6pt |
| D5 协作 | 4 | 8% | 10% | 持平 |

→ **D3 是两天唯一持续超配的域**，且集中在同一批命令方向题（PUT/GET/COPY INTO）反复栽。D2/D4 相对权重错得少，暂不需要额外投入。

## 8/16 晚间批（晚饭后 11 题复盘）

补进笔记的新内容：三层架构「用它≠配它」· Secure View 两个代价的因果 · 存储信息只有 DB+Stage（Pipe 不存数据）· Data Classification 支持的列类型 · Parquet 卸载压缩（LZO，不认 GZIP）· TT 三个数字按「默认/固定/上限」分类 · 加载文件大小的原理（8 线程/节点）+ 数值带逗号 · `READER_ACCOUNT_USAGE.RESOURCE_MONITORS` · federated 拆词 + Snowflake 永远是 SP · RBAC+DAC 混合模型 · SOS 双权限（表 OWNERSHIP + schema ADD SEARCH OPTIMIZATION）· VALIDATION_MODE 与转换互斥。

**晚间批的错法结构，和白天明显不同 —— 集中在两条新链上：**

**① 术语识别层（4 道）**：`federated` / `DAC` / `SCIM` / `External Function`。都不是理解不了，是**这个英文词没和已知概念挂钩**，于是正确选项读过去毫无识别度。
→ 反着用就是判据：**当一个选项你「不认识」时，它往往正是答案**。出题人不会拿生僻词当废选项，废选项都挑你眼熟的（IAM、GZIP、MODIFY）。
→ **行动：冲刺模式扫读时专门盯每条口诀里的英文术语本身，不只看中文解释。**

**② 假术语的两个变种**（这一区分是今天新建立的）：
- **凭空编**：`WAREHOUSE_USAGE` schema、`ACCOUNT_USAGE_HISTORY`
- **移植真词**：`MODIFY ON TABLE`（`MODIFY` 真存在，但只用于 warehouse / resource monitor / 账户参数）
→ **后者更难识破**，因为语感会正确地告诉你「见过这个词」。判据要升级成「我见过这个词<u>用在这个位置</u>吗」。

**③ 选项污染题干（新增，1 道）**：Fail-safe 那题五个选项四个叫 `Table`，于是把 `which objects` 自动读成了 `which tables`，漏掉 Materialized View。与「同选项换轴」同族 —— 根因都是**没回读问句**。

### 8/16 EOD 二次报数（21:07）
累计 **286 题 = 正确 166 / 错误 120，58%**。对比 18:17 的 250 题（147/103）：
- **晚间块 36 题，正确 19 / 错误 17 = 53%**
- **8/16 全天 132 题**（午前 46 @ 48% · 午后 50 @ 66% · 晚间 36 @ 53%），全天 74/58 = **56%**

**晚间块回落到 53%，比午后掉 13pt。** 但这次<u>不是节奏问题</u>——晚间块是「只标记、攒批复盘」的模式，节奏没被打断。回落的成因在错法上：晚间集中出现的是**术语识别层**和**方向翻转**（见下 ①④），都是**知识表征本身的问题**，不是状态问题。
→ 推论：**午后 66% 里有一部分是题目分布的运气**，56% 的全天值更接近真实水平。距 75% 及格线还差 19pt，8/23 模考是真正的判据。
→ 当日配额 132/200，连续两天未达标。**8/17 不加码追欠**——追欠会把错法问题埋进疲劳里。

**④ 方向翻转（新增，Clustering Key 一题两处）**：记住了「和基数有关」→ 误成「低基数适合」；记住了「和微分区数量有关」→ 误成「少的时候要用」。**相关性记住了，方向记反了**，而且同一题里翻了两次。
→ 与「术语识别层」相反：那是**没挂上钩**，这是**挂上了但接反了**。
→ **行动：笔记里每条判据都必须带一句「为什么」。**只背结论的知识点在考场上可以被出题人整个翻转（「小表本来就剪得动」这句一想起来，就不可能选「微分区少时用」）。

**已有知识没调用**仍在发生：External Table 的「见 External 就念数据不在 Snowflake 手里」、`WAREHOUSE_USAGE` 的造词套路，规则都在笔记里且写得很清楚。**这继续印证白天的结论：知识缺口不是主要矛盾。**

## 8/16 错因分析
**11 道复盘题的分类（与 8/15 相比结构变了）**：
- **纯知识缺口 2**：`MAX_FILE_SIZE` 默认 16 MB · Downloads 页面分发内容
- **读题限定词 3**：`execution **plan**` vs execution · `available with` vs `only in` · `**MOST** efficient`（"能用"≠"最优"）
- **已有知识没调用 3**：ORGADMIN 层级 · EXPLAIN vs Query Profile · masking policy 需显式配置（版本知识没用上）
- **陷阱新花样 3**：`key partitions`（词序颠倒的假术语）· `DROP FILE`（对象 vs 文件的范畴错误）· `deterministic prevents caching`（**真概念因果说反**）

→ **8/15 的主因是知识缺口，8/16 已降为次因（2/11）。** 正确率没反映出来，因为读题失误和知识缺口同样记成错。
→ **新增的三条通用判据**（均已进笔记）：
① `DROP` 的宾语必须是 `CREATE` 造得出的对象 → 挡掉 `DROP FILE` 类假命令
② **凡是「要选版本」的功能，一律需要配置** → 反过来用版本知识判"是否自动生效"
③ 看到「X 阻止 Y」的因果句，**从功能定义反推，别从词的眼熟程度判断** → 挡掉 deterministic 那类反向陷阱
→ **笔记侧同一根源已出现三次**（三层架构的"在哪一层发生"：micro-partition 元数据 · execution plan · EXPLAIN vs Profile）。已在三处交叉写入。
→ **发现一处笔记误导**：系统角色层级图把 ORGADMIN 画在树顶，视觉上诱导"ACCOUNTADMIN 继承自它"。已改为横线切出。**这是第二次"笔记的锅"**（前一次：FLATTEN "只需记 VALUE"）。

**复习节奏调整（8/17 起）**：每天做题前 10 分钟扫**考前模式**（第三档），但**不读前一晚刚补的内容**（隔一天再进复习流，避免把短期记忆误判为掌握）。**模考（8/23）前不做此复习**，以免污染基线。

## 8/15 错因分析（重要）
**知识类失分很少，失分集中在读题精度**——一天内出现 6 次同型错误：
`in lieu of` 读反 · `different times` vs `steady` · `while` vs `without completing the load` · 绝对表述（all columns）误判为陷阱 · `database objects` 理解成"数据库们" · **`most granular` 不认识词义**
→ 已全部转成笔记里可执行的动作：附录 A 限定词表扩到 12 行（新增 most granular / minimum edition / primary / first / NOT-EXCEPT）、A0 短语表、考场清单第 1 条改为「**先找限定词，再看选项**」。
→ **推论：现阶段提分最快的不是多记知识点，是读题动作。**

**速度校准（8/16 起按这个排配额）**：154 题 / 3h10m ≈ **74 s/题**（含读解析、含笔记补录），比计划假设的 65 s/题慢 14%。**4h 实际产出 ≈ 195 题**，所以 200 题/天的配额本身是对的，8/15 的缺口来自昏睡 1–2h，不是速度问题。

**晚间干扰项手法归纳（已进笔记）**：除了限定词，晚上集中出现的是**选项本身的构造手法**，共四类——
① **虚构参数**（`DATA_SHARE=TRUE`）② **真数字放错位置**（16 MB 说成源文件上限）③ **类别错位/答非所问**（问数据转换，给 Row Access Policy）④ **正确知识点+错误场景**（ORGADMIN 用于 listing 跨区）。
→ 后两类最危险：每个字单看都对。**统一识别动作：先问「它答的是不是这个问题」，再判断内容对不对。**
→ 另新增一条通用动作：**长选项要数它做了几个断言**（SSO 那题一个选项塞了两个错处）。

## Phase 1 outcome
- **Framework built for D1 + D4 first** — deliberate: they are 52% of the exam.
- Remaining for 8/14: D2 (20%), D3 (18%), D5 (10%).
- Reading order note: D1 and D4 were done as one block, so the 三层架构 ↔ warehouse sizing / caching / pruning links should be fresh. Phase 2 blocks 1–2 (8/15–8/16) will test whether that stuck.

## Open items
- [x] 8/14: verify the app — (a) does 做题模式 generate a filterable 错题本, (b) does 清空答题记录 also wipe 收藏/标记. **All of Phase 3 depends on both.**
- [x] 8/14 evening: 五问自测. Fail → 8/15 quota drops 200 → 150.

## Content gaps closed during sprint
- 2026-08-13: added to notes `n6` — Warehouse Gen1/Gen2, Privacy Policies/差分隐私, Data Lineage vs Access History vs Object Dependencies, "AI Data Cloud" wording, and an explicit **not-tested list** (Openflow, Notebooks default warehouse, Hybrid Tables/Unistore).
- 2026-08-13: added the 症状→对策 pairs the 区分口诀 was missing (查询排队 → 多集群; spilling → 加大 warehouse) and the Secondary roles gotcha (创建对象 owner 仍是 primary role).
- 2026-08-15（做题中补入 `SnowPro_Core.html`）：
  - `n1` — Editions 信号词表 + 「标准能用，企业能调」；Warehouse **服务器数/credits 八行翻倍表**（原文只有省略号，且缺服务器数）；多集群 **min≠max 隐式决定模式**；**Auto-resize 不存在**；**CREATE WAREHOUSE 参数清单**（当排除工具用）；AUTO_SUSPEND 秒/0=永不挂起/SSD 缓存 vs Result Cache
  - `n2` — RBAC **「用户只借身份，角色才是主人」** + user/role 主宾扫描判断表
  - `n3` — **加载最佳实践表**（stage 按年/月/日/小时分目录、拍平字段为新增）+ **"recommended" 类题目的 OLAP 判据**；**Snowpipe 重建 Pipe 清空 load history** + 14/64/7 天数字表
  - `n4` — **UDF vs Stored Procedure 对比表** + 语言×对象矩阵（口诀「Scala 没表」）+ 旧题库应对策略；**DML 表锁**（INSERT/COPY 不阻塞，UPDATE/DELETE/MERGE 锁表）
  - `n9` — 附录 **A0「会把句子读反的短语」**（`in lieu of` 等 9 条）
  - 反复出现的一类干扰项已抽象成通用防御：**虚构参数/视图名**（Auto-resize、编造的 storage view）→ 先怀疑它不存在，别去想"该填什么值"
- 2026-08-15 晚间续补：`n1` 三层架构**英文动词映射**（coordinates→Cloud Services）+ 三缓存归位 + 「尺寸=节点数」推导表；`n1` Editions **入口 vs 治理**分界线（修正「安全→Standard」的错误外推）+ 治理四件套；`n2` **SSO 不送密码也不送人（SCIM 才送人）**；`n2` External Tokenization vs 加密；`n3` **COPY 转换能力（逐行无状态）**、**PUT/GET/COPY 方向表**、**入六出三 XAO**、16 MB 归位；`n4` **TT vs Fail-safe 五行表**（能查/能恢复拆开）+ **克隆有里无外**（含 future grants 不克隆）+ 剪枝失效行；`n5` **Reader 能读出去**、**listing≠data 橱窗自动飞**；`n9` 附录 A 新增**软化措辞 may/at times 行**、`requires` 反向陷阱、附录 B 新增**编造参数**与**「只能用 SQL/UI」**两行。
- 2026-08-15 夜：**对照官方考纲全量审计了一遍笔记**，补齐 4 处「考纲点名但笔记零覆盖」的空洞（均标了 `考纲 X.X 点名 · 题库可能还没出到` 徽章，刷到题时优先核对/替换）：
  - `n1` 新增 **界面与工具（1.2）**：Snowsight / Snowflake CLI vs SnowSQL / IDE 集成 / **Drivers vs Connectors**
  - `n2` 新增 **Logging & Tracing / Alerts & Notifications（2.1·2.2）**：Event Table / Alert / Notification Integration + 与 Access History 的区分
  - `n3` 新增 **Directory Table & SSE（3.1）**：目录表是 stage 的文件元数据层 + 三种 URL（FILE / SCOPED / PRESIGNED）+ 只有 SSE 才能生成 scoped URL
  - `n4` 新增 **聚合函数 vs 窗口函数（4.4）**：「GROUP BY 减行，OVER 不减行」+ RANK/DENSE_RANK/LAG/LEAD + COUNT(*) vs COUNT(列)
  - 审计另一侧结论：**PrivateLink / Data Exchange / FLATTEN / LOCK_TIMEOUT / HITRUST 均不在 C03 考纲**，保留现状但**不再扩充**。
- **Still missing: Query Insights** (flagged in the July study-guide update as added to Domain 4, but it appears nowhere in `SnowPro_Core.html`). Fold into the 8/22 C03 pass or the 8/23 post-mock reread.
