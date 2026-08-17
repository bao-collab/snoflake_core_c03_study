# Snowflake SnowPro Core Certification Study Plan (COF-C03)

## Exam Overview
- **Exam code**: COF-C03 (launched Feb 16, 2026 — replaces COF-C02)
- **Format**: 100 questions (multiple choice, multiple select, interactive)
- **Duration**: 115 minutes
- **Pass Score**: 750 / 1000
- **Cost**: $175 USD
- **Certification validity**: 2 years

---

## Exam Domains

| # | Domain | Weight |
|---|--------|--------|
| 1 | Snowflake AI Data Cloud Features & Architecture | 31% |
| 2 | Account Management & Data Governance | 20% |
| 3 | Data Loading, Unloading & Connectivity | 18% |
| 4 | Performance Optimization, Querying & Transformation | 21% |
| 5 | Data Collaboration | 10% |

> Weights and topics from the **official COF-C03 study guide** (`SnowProCoreStudyGuideC03.pdf`, last updated Jan 19, 2026).

**Key changes from COF-C02:**
- 6 domains → 5 domains
- AI/ML (Cortex) is now first-class exam content
- New topics: Snowflake Cortex, Apache Iceberg tables, Snowflake Notebooks
- Governance expanded: data lineage, column masking, row-access policies
- Collaboration expanded: Marketplace, data clean rooms, native apps

---

## Study Plan

> **Study order: Domain 1 → 4 → 2 → 3 → 5.** The two heavyweight domains (1 + 4 = 52%) go first so they get the most spaced-repetition consolidation before the exam.
>
> **Session rule:** start each session with a quick re-quiz of the previous chunk (and any due spaced-repetition reviews) before advancing. Re-teach only what the re-quiz misses.
>
> **Official study-guide resources (videos/workshops) are reference, not required** — use a module only when a topic stays weak after both a chunk quiz and a spaced review. Prefer 2–3 hrs hands-on in a free Snowflake trial (Snowsight, COPY INTO, stages, RBAC) over videos.

### Domain 1 — Snowflake AI Data Cloud Features & Architecture (31%)

**1.1 Snowflake architecture**
- [ ] Cloud Services layer / Compute layer / Database Storage layer
- [ ] Snowflake editions — compare and contrast (Standard, Enterprise, Business Critical, VPS)

**1.2 Interfaces and tools**
- [ ] Snowsight
- [ ] Snowflake CLI
- [ ] IDE integrations (e.g., VS Code)

**1.3 Object hierarchy and types**
- [ ] Organization and account objects
- [ ] Database objects: stages, schemas, tables, views, UDFs, file formats, stored procedures, pipes, shares, sequences, ML models, applications
- [ ] Session/context variables — parameter hierarchy and precedence

**1.4 Virtual warehouse configuration**
- [ ] Types: Snowpark Optimized, Standard (Gen 1 vs Gen 2), ~~default warehouse for Notebooks~~ (**NOT TESTED until GA**)
- [ ] Scaling policies
- [ ] Warehouse type/config by use case: ad-hoc queries, data loading, BI & reporting
- [ ] Best practices: sizing (up/down), scaling (in/out), auto-suspend, workloads (different teams, high concurrency, complex queries)

**1.5 Storage concepts**
- [ ] Micro-partitions
- [ ] Data clustering
- [ ] Table types: permanent, temporary, transient, Apache Iceberg, external, dynamic
- [ ] View types: standard, materialized, secure

**1.6 AI/ML and application development**
- [ ] Snowflake Notebooks
- [ ] Streamlit in Snowflake
- [ ] Snowpark (Python/Java/Scala on Snowflake)
- [ ] Snowflake Cortex — AI SQL functions, Cortex Search, Cortex Analyst
- [ ] Snowflake ML

### Domain 2 — Account Management & Data Governance (20%)

**2.1 Security model and principles**
- [ ] Role-based access control (RBAC) — roles, privileges, grants
- [ ] Securable object hierarchy
- [ ] Discretionary access control (DAC)
- [ ] Network policies
- [ ] Authentication: MFA, federated authentication, SSO, OAuth, key-pair
- [ ] System-defined roles
- [ ] Functional roles: account roles, database roles, custom roles
- [ ] Secondary roles
- [ ] Account identifiers
- [ ] Logging and tracing

**2.2 Data governance features**
- [ ] Data masking — row-level security, column-level security
- [ ] Object tagging
- [ ] Privacy policies
- [ ] Trust Center — evaluate account security posture against recommendations
- [ ] Encryption key management (incl. Tri-Secret Secure / customer-managed keys)
- [ ] Alerts and notifications
- [ ] Data replication and failover
- [ ] Data lineage

**2.3 Monitoring and cost management**
- [ ] Resource monitors — cost and warehouse monitoring
- [ ] Calculating virtual warehouse credit usage
- [ ] ACCOUNT_USAGE schema

### Domain 3 — Data Loading, Unloading & Connectivity (18%)

**3.1 Data loading and unloading**
- [ ] File formats: CSV, JSON, Parquet, ORC, Avro
- [ ] Stages: internal vs external (S3, Azure Blob, GCS), server-side encryption, directory tables
- [ ] COPY INTO command (load and unload / COPY INTO location)
- [ ] Error handling options: ON_ERROR, PURGE, FORCE, validation modes

**3.2 Automated data ingestion**
- [ ] Snowpipe (continuous / event-driven loading)
- [ ] Snowpipe Streaming — row-level low-latency ingestion; no COPY INTO; distinct from Snowpipe
- [ ] Streams (standard, append-only, insert-only)
- [ ] Tasks and DAGs (dependencies, scheduling)
- [ ] Dynamic tables
- [ ] ~~Openflow~~ — **NOT TESTED until GA**

**3.3 Connectors and integrations**
- [ ] Snowflake drivers (JDBC, ODBC)
- [ ] Snowflake connectors (Python connector, etc.)
- [ ] Storage integration
- [ ] API integration
- [ ] Git integration — syncing repos, versioning Snowflake code/artifacts

### Domain 4 — Performance Optimization, Querying & Transformation (21%)

**4.1 Evaluate query performance**
- [ ] Query Profile / Query Insights — bytes spilled to storage, inefficient pruning, exploding joins, queuing
- [ ] SNOWFLAKE.ACCOUNT_USAGE views — query attribution, query history
- [ ] Workload management best practices — grouping similar workloads

**4.2 Optimize query performance**
- [ ] Query Acceleration Service — offloads large scans; reduces credits for outlier queries
- [ ] Search Optimization Service — speeds up selective point lookups on large tables
- [ ] Clustering keys and automatic clustering
- [ ] Materialized views

**4.3 Snowflake caching**
- [ ] Query result cache
- [ ] Metadata cache
- [ ] Warehouse (local disk) cache

**4.4 Data transformation techniques**
- [ ] Using structured, semi-structured, and unstructured data (VARIANT, FLATTEN, PARSE_JSON)
- [ ] Aggregate functions
- [ ] Applying SQL for query optimization
- [ ] Window functions

### Domain 5 — Data Collaboration (10%)

**5.1 Data collaboration and protection**
- [ ] Data replication and failover
- [ ] Secure data sharing features
- [ ] Cloning (Zero-Copy)
- [ ] Time Travel
- [ ] Fail-safe

**5.2 Data sharing capabilities**
- [ ] Accounts: provider / consumer / reader accounts (no Snowflake license needed)
- [ ] Secure Data Sharing
- [ ] Sharing and resharing
- [ ] Direct shares
- [ ] Data clean rooms

**5.3 Marketplace and listings**
- [ ] Snowflake Marketplace
- [ ] Listings: private and public
- [ ] Native Apps

### Final Phase — Review & Practice Exams
- [ ] Review weak domains
- [ ] Take 2–3 full practice exams (target 80%+ before real exam)
- [ ] Review all missed questions and underlying concepts
- [ ] Re-read Snowflake docs for any gaps

---

## Resources

| Resource | Link |
|----------|------|
| Snowflake Official Docs | https://docs.snowflake.com/ |
| Official COF-C03 Certification Page | https://learn.snowflake.com/en/certifications/snowpro-core-c03/ |
| Snowflake Level Up (free) | https://learn.snowflake.com |
| SnowPro Practice Exams | https://learn.snowflake.com/en/certifications/snowpro-practice-exams/ |
| Udemy COF-C03 mock exams | Search "SnowPro Core COF-C03" on Udemy |

### Official study-guide recommended resources (per domain)
- **D1**: Snowflake Foundations On-Demand; Badge 1: Data Warehousing Workshop; Level Up: Key Concepts / Ecosystem / Container Hierarchy / Accounts & Assurances; Snowflake x GenAI: LLM Functions; Getting Started With Snowflake modules 1–2
- **D2**: Level Up: Resource Monitoring; FinOps for Snowflake; Getting Started module 9 (Roles, Account Admin & Account Usage); "Definitive Guide to Managing Spend in Snowflake" (white paper)
- **D3**: Level Up: Data Loading; Getting Started modules 4–5 (loading CSV / JSON); "Best Practices for Data Unloading" (article)
- **D4**: Badge 3: Data Application Builders Workshop; Level Up: Query History & Caching / Context; Getting Started module 7 (Querying, Results Cache & Cloning); articles on result caching, disk spilling, search optimization, materialized views
- **D5**: Badge 2: Collaboration, Marketplace & Cost Estimation Workshop; Level Up: Native App Development for Beginners; Getting Started modules 6, 8, 10

---

## Notes
- Hands-on experience is critical — use a free Snowflake trial account
- Focus most time on Domains 1, 4 (combined ~52% of exam) — Domain 1 alone is 31%
- Domain 3 now owns Streams/Tasks/Dynamic tables (automated ingestion) — CDC pattern questions land here
- AI/ML (Cortex Search/Analyst), Iceberg, Notebooks, Streamlit: understand positioning and use cases
- Time Travel / Fail-safe / Cloning are tested under Domain 5 (data protection), not Domain 1
- Domain 5 is only 10% — don't over-study here
