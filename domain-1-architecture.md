# Domain 1: Snowflake AI Data Cloud Features & Architecture (31%)

Last updated: 2026-07-06 (restructured to match official COF-C03 guide, Jan 19 2026)

> Note: Time Travel / Fail-safe / Zero-Copy Cloning moved to Domain 5 (official 5.1). Snowpark is covered here (official 1.6).

---

## Chunks
- [x] Chunk 1: 3-Layer Architecture — **75%** (3/4)
- [ ] Chunk 2: Virtual Warehouses — types (Snowpark Optimized, Standard Gen 1/Gen 2), scaling policies, config by use case (ad-hoc / loading / BI), best practices (sizing, scaling, auto-suspend, workloads)
- [ ] Chunk 3: Object Hierarchy — organization/account objects; database objects (stages, schemas, tables, views, UDFs, file formats, stored procedures, pipes, shares, sequences, ML models, applications)
- [ ] Chunk 4: Editions & Multi-Cloud
- [ ] Chunk 5: [NEW COF-C03] Snowflake Cortex — AI SQL functions, Cortex Search, Cortex Analyst
- [ ] Chunk 6: [NEW COF-C03] Snowflake ML & ML models as objects
- [ ] Chunk 7: [NEW COF-C03] Apache Iceberg Tables — positioning vs native tables
- [ ] Chunk 8: [NEW COF-C03] Snowflake Notebooks — Python/SQL notebooks in Snowsight (default warehouse for Notebooks NOT TESTED until GA)
- [ ] Chunk 9: [NEW COF-C03] Streamlit in Snowflake — building data apps inside Snowflake
- [ ] Chunk 10: [NEW COF-C03] Snowpark — Python/Java/Scala on Snowflake (UDFs, DataFrames)
- [ ] Chunk 11: Interfaces — Snowsight, Snowflake CLI, IDE integrations (VS Code)
- [ ] Chunk 12: Storage — table types (permanent, temporary, transient, Iceberg, external, dynamic, **hybrid/Unistore**) + view types (standard, materialized, secure) — *Unistore/hybrid tables explained 2026-07-27 ([notes](progress-2026-07-27.md)), quiz pending*
- [ ] Chunk 13: Session/context variables — parameter hierarchy & precedence

---

## Chunk 1: 3-Layer Architecture

### Key Concepts
- **Storage Layer**: Actual data stored in cloud object storage (S3/Blob/GCS), columnar + compressed format, split into micro-partitions (50–500MB compressed)
- **Compute Layer**: Virtual Warehouses execute queries; multiple VWs read same storage independently with no contention
- **Cloud Services Layer**: Snowflake's brain — query optimization, metadata, authentication, transactions; always on, billed only if >10% of daily compute

📌 **Exam Tip**: Cloud Services is billed only when it exceeds **10% of daily compute credits** — effectively free in normal usage.
📌 **Exam Tip**: Storage and compute are **fully separated** — multiple VWs can read the same data simultaneously with no contention.

### Micro-partitions & Pruning
- Data auto-split into micro-partitions on ingestion
- Each partition stores metadata: min/max values, row counts, distinct values
- **Partition pruning**: Snowflake skips irrelevant partitions using metadata → faster queries, fewer credits

📌 **Exam Tip**: Micro-partition size = **50–500MB compressed**. Metadata lives in **Cloud Services**, not Storage.
📌 **Exam Tip**: Partition pruning is **automatic** — no configuration needed.

### Columnar Storage
- Data stored column by column (not row by row)
- Benefit: analytical queries only read needed columns, skip the rest
- Better compression: similar values grouped together

📌 **Exam Tip**: Columnar format benefits **analytics** (read only needed columns). Row format is better for transactional (OLTP) workloads.

### Billing Model
```
Total Cost = Storage (per TB/month) + Compute (credits/sec while VW runs) + Cloud Services (if >10% compute)
```

📌 **Exam Tip**: You are **not billed** for Cloud Services unless it exceeds 10% of daily compute.

### Quiz Results
| Q | Summary | Result | Notes |
|---|---------|--------|-------|
| Q1 | Name and describe 3 layers | Partial | Confused metadata with storage; Cloud provider vs Cloud Services layer |
| Q2 | Do separate VWs compete for resources? | Correct | |
| Q3 | Why is columnar better for analytics? | Correct | |
| Q4 | When is Cloud Services billed? | Correct | >10% of daily compute |
| Q5 | Where is data physically stored? | Correct | Storage layer, AWS/Azure/GCP |
| Q6 | Can two VWs access same data simultaneously? | Correct | Yes, storage is shared; compute is isolated |
| Q7 | Difference between auto-suspend and auto-resume? | Correct | Auto-suspend = shutdown after idle; auto-resume = start when query arrives |
| Q8 | What is partition pruning and why is it faster? | Correct | Labels on micro-partitions; fetch only relevant partitions → faster + cheaper |

**Chunk 1 Score: 7/8 (88%)**

### Editions (covered in Chunk 1 extra questions)
| Edition | Key Features |
|---------|-------------|
| Standard | Core features, 1-day Time Travel |
| Enterprise | 90-day Time Travel, multi-cluster warehouses (max 10), materialized views |
| Business Critical | HIPAA/PCI compliance, private link, Tri-Secret Secure |
| Virtual Private (VPS) | Dedicated metadata store, highest isolation |

📌 **Exam Tip**: Multi-cluster warehouses are **Enterprise+ only**, max **10 clusters**.
📌 **Exam Tip**: Time Travel — Standard = **1 day**, Enterprise+ = up to **90 days**.
📌 **Exam Tip**: Multi-cluster scales **out** (more clusters, same size) — not up. All clusters are the same size as the VW.
📌 **Exam Tip**: Multi-cluster prevents **query queuing** during concurrency spikes — not about per-query performance.

### Clarifications & Additional Questions
- **Metadata** — clarified: data about data (min/max, row counts per partition), lives in Cloud Services
- **Partition pruning** — clarified: skipping irrelevant micro-partitions using metadata labels
- **Cloud Services vs Cloud Provider** — Cloud Services is Snowflake's own layer running on top of AWS/Azure/GCP
- **Columnar format** — clarified: data stored column by column; better for analytics (read only needed columns) and compression
- **Billing** — confirmed: Storage + Compute + Cloud Services (if >10% of daily compute credits)
- **10% compute threshold** — clarified: if Cloud Services credits > 10% of VW credits used that day, excess is billed
- **Shared VW vs separate VWs** — clarified: same VW = queries compete and queue; separate VWs = full isolation, no contention
- **Multi-cluster** — clarified: scales out (more clusters, same size); max 10 clusters; prevents queuing during concurrency spikes; Enterprise+ only
- **Materialized views** — clarified: pre-computed stored results; read-only; no joins allowed; auto-refreshed by Snowflake (costs credits); Enterprise+ only
- **HIPAA/PCI** — clarified: HIPAA = health data, PCI = payment data; both require Business Critical+
- **Private Link** — clarified: direct private connection inside cloud provider network, no public internet; Business Critical+
- **Tri-Secret Secure** — clarified: customer holds part of encryption key; even Snowflake cannot access data; Business Critical+
- **VPS** — clarified: dedicated metadata store + single-tenant environment; physically isolated; for strictest compliance needs

---

## ⏭️ Resume Here Next
**Date**: 2026-05-04
**Start with**: Chunk 2: Virtual Warehouses

### Chunk 1 Gaps (exam-likely topics not yet covered)
- [x] **Fail-safe** — 7-day recovery after Time Travel expires; Snowflake-managed only; cannot be queried
- [x] **Zero-Copy Cloning** — instant copy, no data duplication; only new changes cost storage; can clone databases/schemas/tables
- [x] **Time Travel on transient/temporary tables** — Transient/Temporary = up to 1 day Time Travel, no Fail-safe; Permanent = up to 90 days + 7-day Fail-safe
- [x] **Clustering keys** — when to use, cost implications, automatic clustering
- [x] **Secure Views** — hides view definition; required for Data Sharing; slight perf tradeoff

---

## Chunk 2: Virtual Warehouses
*(Not started)*

---

## Chunk 3: Object Hierarchy
*(Not started)*

> Time Travel / Fail-safe / Zero-Copy Cloning: some basics already covered under Chunk 1 gaps above; full coverage now lives in Domain 5.

---

## Chunk 4: Editions & Multi-Cloud
*(Not started)*
