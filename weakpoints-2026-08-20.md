# Weakpoints Snapshot — 2026-08-20

Previous snapshot: `weakpoints-2026-08-19.md`.

## Overall stats (as reported)
- Sample: 24 wrong-answer screenshots taken 2026-08-20 (16:16, and 22:55–23:18), app question numbers **Q659–Q691**.
- Not a full accuracy report for the day — just the screenshotted subset, same as the 8/19 batch was a sample of 281.
- All from Topic 1 (single question bank, continuing sequential numbering from the 8/19 batch which ended around Q6xx range).

## Domain distribution of this 24-question sample

| Domain | Wrong count | % of sample |
|---|---|---|
| D3 数据加载/连接 | 8 | 33% |
| D4 性能/查询/转换 | 6 | 25% |
| D2 账户管理/治理 | 5 | 21% |
| D1 架构 | 4 | 17% |
| D5 协作 | 1 | 4% |

D3 (loading/connectivity) is the standout this round — back to being the top overweighted domain, consistent with the 8/16–8/17 pattern (before D4/D2 took over on 8/19). Small sample (24), so treat as directional only.

## Recurring topic clusters

1. **三层架构归属 / Cloud Services vs Compute layer** (Q679 — Cloud Services layer handles Security + Metadata, not Query computation) — **same gap as 8/19 cluster 5, which itself was a 7/21 "resolved→reopened" recurrence. Now a 3rd occurrence across snapshots.** This is the most stubborn recurring gap in the whole tracking history — see `snowflake-progress.md` 高频错误知识点复发清单.
   → Action: this is no longer a content gap (notes already reinforced twice). Needs active recall drilling (flashcard-style, not more reading) before next quiz batch.

2. **PUT/GET/COPY mechanics** (Q664 client-side vs server-side encryption type, Q680 PUT encryption timing) — 2 hits, same family as 8/19 cluster 3 (6 hits). Still recurring.
   → Q680 repeats the *exact* same fact missed on 8/19 (PUT encrypts before leaving the user's machine) — this one specifically needs re-drilling, not new notes (already in `SnowPro_Core_Contents.html`).

3. **Specific numeric thresholds** (Q662 unload max file size to external stage = 5 GB, Q663 ACCESS_HISTORY retention = 365 days, Q669 network policies per account/user = One, Q672 recommended Parquet file size for querying external tables = 256–512 MB) — 4 hits, no shared logic, pure memorization gaps across D2–D4.
   → Action: these are guessable-format distractors (plausible-looking wrong numbers). Build a single "numbers cheat sheet" if not already present, cross-check against `SnowPro_Core_Contents.html`.

4. **Multi-select ("Choose two") distractor discipline** (Q675, Q678, Q681, Q682, Q685, Q686, Q689, Q691) — 8 of 24 wrong answers were multi-select questions, a disproportionately high share. Common failure mode: picking one correct + one plausible-but-wrong option instead of two correct ones.
   → Action: on multi-select, eliminate obviously-wrong options first, then verify each remaining candidate against the exact definition/keyword — don't pattern-match on "sounds related."

## Isolated single-hit misses (not clusters — 1 occurrence each in this sample)

- **Q659 (D3)** SnowSQL file storing connection info → `config` — chose `snowsql.cnf` (fabricated-sounding distractor)
- **Q660 (D2)** Secure vs non-secure view comparison → secure views execute slower — chose "non-secure preferred for sharing" (reversed logic)
- **Q661 (D4)** Join type listing all rows of specified table even without match → Outer join — chose Cross join
- **Q666 (D4)** 8-table join slow, Query Profile shows all partitions scanned → root cause is pruning not being performed efficiently — chose "incorrect joins"
- **Q667 (D4)** Search Optimization Service supports → tables/views not protected by row access policies — chose materialized views
- **Q674 (D1)** Which constraint is enforced in Snowflake → NOT NULL — chose FOREIGN KEY (recurring theme: only NOT NULL is truly enforced on standard tables; PK/FK/UNIQUE are informational-only)
- **Q684 (D5)** How providers share data across databases → Secure views — chose UDFs
- **Q690 (D4)** Query Profile details section can determine → total query duration — chose "source system of queried table" (fabricated capability)
- **Q691 (D3)** JSON path case-sensitivity → key names are case-sensitive (`salesPerson` ≠ `salesperson`) — chose the all-lowercase variant. **New topic, not previously covered in notes.**

## Content updates applied (2026-08-20, to `SnowPro_Core_Contents.html`)

- **① Cloud Services layer operations** — cross-referenced against existing 三层架构 note (already covered per 8/19 log); this is confirmed a **recall gap, not a content gap** — third recurrence, escalate to active-recall drilling.
- **② PUT encryption timing** — already covered per 8/19 edit; confirmed **recall gap**.
- **③ JSON path case-sensitivity (Q691)** — genuinely new, added a note near the JSON/VARIANT section: object key access via `:` colon notation is case-sensitive, must match source key casing exactly (table/column identifiers are not, but semi-structured keys are).
- **④ Numeric thresholds (Q662, Q663, Q669, Q672)** — added/confirmed a compact reference: unload max file size to stage = 5 GB; ACCESS_HISTORY retention = 365 days; network policies assignable per account/user at a time = 1; recommended Parquet file size for external table queries = 256–512 MB (distinct from the unload-recommended 100–250 MB range — flagged as an easy-to-confuse pair).
- **⑤ Search Optimization Service scope (Q667)** — added: applies to tables/views *not* protected by row access policies; does not support materialized views.

## Next snapshot
Compare against this file when the next dated batch is processed. Priority watch: does cluster 1 (三层架构/Cloud Services) recur a 4th time — if so, this needs a dedicated timed drill session, not further note edits.
