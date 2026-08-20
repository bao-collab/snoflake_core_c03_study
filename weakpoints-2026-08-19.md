# Weakpoints Snapshot — 2026-08-19

Previous snapshot: none (first snapshot). Future snapshots should link back here for comparison.

## Overall stats (as reported)
- Correct: 375 / Wrong: 281 / Accuracy: 57.00% / Total attempted: 656
- Quiz date: 2026-08-19 (reported to Claude on 2026-08-20 07:48 JST)
- Context: cumulative running total since 8/18 phone switch. vs 8/17 checkpoint (460 @ 58%) → accuracy roughly flat (−1pt) over ~196 more questions.
- 80 of the 281 wrong answers were screenshotted and analyzed below (a sample, not the full wrong-answer set).

## Domain distribution of this 80-question sample

| Domain | Wrong count | % of sample | Exam weight | Diff |
|---|---|---|---|---|
| D4 性能/查询/转换 | 23 | 28.75% | 21% | **+7.75pt 超配** |
| D2 账户管理/治理 | 22 | 27.5% | 20% | **+7.5pt 超配** |
| D3 数据加载/连接 | 18 | 22.5% | 18% | +4.5pt 超配 |
| D1 架构 | 15 | 18.75% | 31% | −12.25pt（相对强项） |
| D5 协作 | 2 | 2.5% | 10% | −7.5pt（样本仅 2 题，不下结论） |

**Shift from 8/16–8/17 pattern**: back then D3 (加载) was the sole standout-overweighted domain. In this sample, **D4 and D2 are now the two most overweighted domains**, both roughly tied. D3 is still over its weight but by less. D1 is comfortably under its weight — consistent with it being the domain worked hardest early in the sprint.

## Recurring topic clusters (ranked by frequency in this sample)

1. **Unstructured-data file URL functions & directory tables** (5 hits: file URL vs scoped URL vs pre-signed URL, `GET_RELATIVE_PATH`, directory table columns/URL type) — spans D1/D2/D3. Largest single cluster.
   → Action: build one comparison table — File URL / Scoped URL / Pre-signed URL / `GET_RELATIVE_PATH` — what each returns, which function generates it, when each is valid (only SSE stages give scoped URLs — already in notes per 8/15 log, but clearly not internalized).

2. **Query Profile reading** (5 hits: orange bar meaning, UnionAll+Aggregate operator, external function stats, definition of Query Profile itself, what stats panel shows) — D4.
   → Action: this is procedural/visual knowledge, not a fact to memorize — needs actual screen-reading practice, not more notes.

3. **PUT/GET/COPY command mechanics beyond direction** (6 hits: PUT encryption timing, `LS @~;` syntax, `FORCE` vs `LOAD_UNCERTAIN_FILES`, recommended unload target, PUT auto-actions, COPY INTO vs GET for export) — D3.
   → Broader than the previously-flagged "PUT/GET direction" mistake — this is param-level detail (encryption point, force-reload flag, syntax). Treat as a related but distinct gap.

4. **Role/privilege minimums** (5 hits: min privilege for GET via REST API, Partner Connect role, `ENABLE_ACCOUNT_DATABASE_REPLICATION` role, secure-view exposure privilege) — D2.
   → Action: build a single "minimum role/privilege required for X" cheat table — these keep being tested as isolated facts.

5. **Storage/compute layer attribution** (4 hits: micro-partitions, column compression location, Cloud Services vs Database Storage layer) — D1.
   → ⚠️ **This is the same gap flagged and marked "resolved" back on 2026-07-21** in `snowflake-progress.md`'s Weak Areas section ("Cloud Services vs Cloud Provider... resolved unless missed again"). **It recurred** — reopen that weak-area entry, don't treat as closed.

6. **Floating-point precision on unload** (3 hits: CSV/JSON truncate to ~(15,9), Parquet preserves full precision) — D3.

7. **`ACCOUNT_USAGE` vs `INFORMATION_SCHEMA`** (2 hits: latency window, dropped-object retention) — D2.

8. **Fail-safe period numbers** (2 hits: transient table = 0 days, permanent table = 7 days) — D1.

9. **Network policy IP-list mechanics** (2 hits: blocked-list precedence over allowed-list, `DESCRIBE NETWORK POLICY` vs `SHOW`) — D2.

## Full itemized list (80 questions, by domain)

<details>
<summary>D1 Architecture (15)</summary>

- Unstructured data table type → Directory (chose Permanent)
- Retrieving unstructured data from storage → SQL functions build URLs (chose result cache)
- UDF unqualified object name resolution → only UDF's own schema (chose current+previous schema)
- Storage unit for efficient query processing → Micro-partitions (chose Blobs)
- How table data stored (2 correct) → columnar format + micro-partitions (chose text format+uncompressed)
- FLOAT synonyms (2 correct) → DOUBLE, REAL (wrongly included NUMERIC)
- Functions to share unstructured data via secure view (2 correct) → BUILD_SCOPED_FILE_URL, GET_PRESIGNED_URL (wrongly included GET_RELATIVE_PATH)
- Max VARIANT record size → 128 MB (chose 16 MB)
- How table data compressed → per-column within micro-partition (chose "cloud storage handles it")
- Fail-safe period, transient table → 0 days (chose 1 day)
- Snowflake architecture description → hybrid shared-disk/shared-nothing (chose shared-disk/shared-everything)
- ALTER WAREHOUSE property to confirm compute fully provisioned → WAIT_FOR_COMPLETION (chose SCALING_POLICY)
- Fail-safe period, permanent table → 7 days (chose 1 day)
- Layer that reorganizes data into internal columnar format → Database Storage (chose Cloud Services)
- View + same-name temp table in same schema → returns temp table data, name resolution precedence (chose permanent table)

</details>

<details>
<summary>D2 Governance (22)</summary>

- Tag DDL commands (2 correct) → ALTER TAG, DROP TAG (wrongly included GRANT TAG)
- Governance control embedded in Snowflake → attribute-based access control (chose network policies)
- Account usage vs information schema (2 correct) → dropped objects retained + differing retention (chose latency+retention)
- Database clone privilege behavior → replicates child-object privileges (chose "retains none")
- Constraint causing error → NULL into NOT NULL column (chose duplicate PK — not enforced by default)
- Min privilege on external stage for GET via REST API → USAGE (chose READ)
- Partner Connect role requirement → ACCOUNTADMIN (chose SECURITYADMIN)
- User property requiring Support to set → MINS_TO_BYPASS_NETWORK_POLICY (chose MFA bypass var)
- ALLOW_CLIENT_MFA_CACHING token validity → 4 hours (chose 8)
- ALLOWED_VALUES tag property max values → 256 (chose 10)
- Role characteristic → privileges can be granted/revoked to role (chose "roles can't be granted to roles")
- Directory table URL type → File (chose Pre-signed)
- Network policy IP precedence → blocked list applied first (chose allowed first)
- Column-level security features (2 correct) → Dynamic Data Masking, External Tokenization (missed one)
- SAML_IDENTITY_PROVIDER valid values (2 correct) → AD FS, Okta (wrongly included OAuth)
- How to enable MFA → user self-enrolls via web UI (chose "sign up with Duo Mobile")
- ACCOUNT_USAGE view characteristics (2 correct) → latency 45min–3hr + includes dropped objects (wrong retention window)
- Privilege to expose a secure view → OWNERSHIP (chose IMPORT SHARE)
- Directory table output columns (2 correct) → LAST_MODIFIED, RELATIVE_PATH (wrongly included FILE_NAME, STAGE_NAME)
- Command to view network policy IP lists → DESCRIBE NETWORK POLICY (chose SHOW NETWORK POLICIES)
- Min role for ENABLE_ACCOUNT_DATABASE_REPLICATION → ORGADMIN (chose SYSADMIN)
- Query for Snowflake-hosted file URL via directory table → `SELECT * FROM DIRECTORY(@stage)` (chose METADATA$FILENAME variant)

</details>

<details>
<summary>D3 Data Loading/Connectivity (18)</summary>

- JS stored proc delimiters (2 correct) → single quote + `$$` (chose double quotes + `//`)
- PUT command auto-actions (2 correct) → GZIP compress + encrypt in transit (wrongly included "uses last stage created")
- File format preserving float precision on unload → Parquet (chose CSV)
- COPY INTO param that hurts perf on large file counts → PATTERN (chose FILE_FORMAT)
- Function to unload relational data to JSON → OBJECT_CONSTRUCT (chose PARSE_JSON)
- Stored proc vs UDF → SPs can execute DB ops, UDFs cannot (chose wrong claim re: multiple calls)
- Command to export/unload data → COPY INTO @stage (chose GET @stage)
- PUT encryption timing → before leaving user's machine (chose "at micro-partition stage")
- Abbreviated LS for current-user stage → `LS @~;` (chose `LIST @~;`)
- COPY option to force-reload regardless of status → FORCE=TRUE (chose LOAD_UNCERTAIN_FILES=TRUE)
- Query syntax to reference directory table → `SELECT * FROM DIRECTORY(@stage)` (chose wrong variant)
- Unload float precision truncation → ~(15,9) (chose (12,2))
- Non-deterministic file functions (2 correct) → BUILD_SCOPED_FILE_URL, GET_PRESIGNED_URL (wrongly included GET_RELATIVE_PATH)
- File format preventing float truncation → Parquet (chose CSV)
- Stream type for external tables → Insert-only (chose "External")
- Recommended unload approach → directly to cloud storage location (chose "via user stage then upload")
- REST API for unstructured data → `GET /api/files/` (chose insertFiles)
- COPY INTO [location] supported unload formats (2 correct) → JSON, Parquet (wrongly included XML)

</details>

<details>
<summary>D4 Performance/Querying (23)</summary>

- HyperLogLog for approx distinct count → correct func (chose MD5)
- Query Profile UnionAll+Aggregate meaning → UNION without ALL (chose "inefficient pruning")
- Multi-cluster warehouse max clusters → 10 (chose 100)
- View to detect frequent row updates/deletes → TABLE_STORAGE_METRICS (chose STORAGE_DAILY_HISTORY)
- Search optimization service benefit → equality searches (chose range searches)
- Query Profile definition → graphical plan representation (chose "collapsible node-time panel")
- SAMPLE returning empty result → sample(0) (chose sample())
- Query Profile display info (2 correct) → overall stats + graphical plan (wrongly included clustering keys)
- Optimize repeated query on small, rarely-changing subset → materialized view (chose query acceleration service)
- Bernoulli sampling meaning → samples every row independently (chose "sampling blocks" — that's system/block method)
- Min table size before considering clustering key → 1 TB (chose 1 GB)
- Default Warehouse Activity graph window in Snowsight → 2 weeks (chose 1 month)
- Result cache requirement → identical SQL text (chose "identical query profile")
- Query Profile orange bar meaning → fraction of time operator consumed (chose "progress measure")
- Query result cache max retention reset → 31 days (chose 1 day)
- Recursive query commands when depth unknown (2 correct) → CONNECT BY, WITH (chose LISTAGG, QUALIFY)
- TABLESAMPLE(100) on a table → returns entire table (chose "random 100 rows")
- Query Profile stat specific to external functions → total invocations (chose bytes sent over network)
- Loop type iterating until condition true → REPEAT (chose WHILE)
- average_overlaps in SYSTEM$CLUSTERING_INFORMATION → avg micro-partitions w/ overlapping value ranges (chose "physically same location")
- Object to evaluate warehouse perf under query queuing → ACCOUNT_USAGE.QUERY_HISTORY (chose WAREHOUSE_METERING_HISTORY)
- Tabular UDF return clause keyword → TABLE (chose VALUES)
- Set operator for values present in both tables → INTERSECT (chose MINUS)

</details>

<details>
<summary>D5 Collaboration (2)</summary>

- Recommended URL type for sharing unstructured data via share → Scoped (chose Pre-signed)
- Command to share data via my_share with account xy12345 → `ALTER SHARE my_share ADD ACCOUNTS = xy12345;` (chose GRANT SELECT ON SHARE...)

</details>

## Verbatim English appendix — 34 questions from the 9 recurring clusters

Pulled directly from screenshots (app question number, verbatim question/options/correct/your answer) to check whether mistakes were English misreads vs real knowledge gaps.

**Verdict: mostly knowledge/terminology gaps, not misreads.** Only one clear case (Q576) was a missed qualifier word ("abbreviated form"). `GET_RELATIVE_PATH` was picked wrong twice (Q557, Q636) — a repeatable terminology confusion, not a one-off. Q574 (orange bar: "progress" vs "fraction of time consumed") is the closest to a genuine wording trap.

### ① Storage/compute layer (reopened gap)
- **Q527** — What unit of storage supports efficient query processing in Snowflake? A. Blobs / B. JSON / C. Block storage / D. Micro-partitions → Correct: **D** · You chose: A
- **Q535** — How does Snowflake store a table's underlying data? (choose 2) A. Columnar file format / B. Micro-partitions / C. Text file format / D. Uncompressed / E. User-defined partitions → Correct: **A, B** · You chose: C, D
- **Q598** — How is table data compressed in Snowflake? A. Each column is compressed as it is stored in a micro-partition / B. Each micro-partition is compressed as it is written into cloud storage using GZIP / C. The micro-partitions are stored in compressed cloud storage and the cloud storage handles compression / D. The text data in a micro-partition is compressed with GZIP but other types are not compressed → Correct: **A** · You chose: C
- **Q651** — In which Snowflake layer does Snowflake reorganize data into its internal optimized, compressed, columnar format? A. Cloud Services / B. Database Storage / C. Query Processing / D. Metadata Management → Correct: **B** · You chose: A

### ② Unstructured-data URL functions
- **Q529** — Which URL type does Snowflake recommend to use when providing unstructured data to other accounts through a share? A. File / B. Pre-signed / C. Scoped / D. Staged → Correct: **C** · You chose: B
- **Q557** — Which functions can be used to share unstructured data through a secure view? (choose 2) A. BUILD_SCOPED_FILE_URL / B. BUILD_STAGE_FILE_URL / C. GET_ABSOLUTE_PATH / D. GET_PRESIGNED_URL / E. GET_RELATIVE_PATH → Correct: **A, D** · You chose: A, E
- **Q569** — Which Snowflake URL type is used by directory tables? A. File / B. Pre-signed / C. Scoped / D. Virtual-hosted style → Correct: **A** · You chose: B
- **Q636** — Which file functions are non-deterministic? (choose 2) [same options as Q557] → Correct: **A, D** · You chose: A, E
- **Q649** — Which query contains a Snowflake hosted file URL in a directory table for a stage named bronzestage? A. `list @bronzestage;` / B. `select * from directory(@bronzestage);` / C. `select metadata$filename from @bronzestage;` / D. `select * from table(information_schema.stage_directory_file_registration_history(stage_name=>'bronzestage'));` → Correct: **B** · You chose: C

### ③ Query Profile reading
- **Q488** — A Query Profile shows a UnionAll operator with an extra Aggregate operator on top. What does this signify? A. Exploding joins / B. Inefficient pruning / C. UNION without ALL / D. Queries too large to fit in memory → Correct: **C** · You chose: B
- **Q509** — What does a Query Profile provide in Snowflake? A. A multi-step query that displays each processing step in the same panel / B. A pre-computed data set derived from a query specification and stored for later use / C. A graphical representation of the main components of the processing plan for a query / D. A collapsible panel in the operator tree pane that lists nodes by execution time in descending order for a query → Correct: **C** · You chose: D
- **Q539** — What information is included in the display in the Query Profile? (choose 2) A. Index hints used in query / B. Credit usage details / C. Clustering keys details / D. Details and statistics for the overall query / E. Graphical representation of the query processing plan → Correct: **D, E** · You chose: C, D
- **Q574** — What does the orange bar on an operator represent when reviewing the Query Profile? A. A measure of progress of the operator's execution / B. The fraction of time that this operator consumed within the query step / C. The cost of the operator in terms of virtual warehouse CPU utilization / D. The fraction of data scanned from cache versus remote disk for the operator → Correct: **B** · You chose: A
- **Q613** — Which statistic displayed in a Query Profile is specific to external functions? A. Bytes written / B. Total invocations / C. Partitions scanned / D. Bytes sent over the network → Correct: **B** · You chose: D

### ④ PUT/GET/COPY mechanics
- **Q490** — What actions does the use of the PUT command do automatically? (choose 2) A. It creates a file format object / B. It uses the last stage created / C. It compresses all files using GZIP / D. It encrypts the file data in transit / E. It creates an empty target table → Correct: **C, D** · You chose: B, D
- **Q532** — What command is used to export or unload data from Snowflake? A. `PUT @mystage` / B. `GET @mystage` / C. `Copy INTO @mystage` / D. `INSERT @mystage` → Correct: **C** · You chose: B
- **Q570** — At which point is data encrypted when using a PUT command? A. When it reaches the virtual warehouse / B. When it gets micro-partitioned / C. Before it is sent from the user's machine / D. After it reaches the internal stage → Correct: **C** · You chose: B
- **Q576** — What is the abbreviated form to get all the files in the stage for the current user? A. `LIST @~;` / B. `LS @~;` / C. `LS @usr;` / D. `SHOW @%;` → Correct: **B** · You chose: A ⚠️ *missed the qualifier "abbreviated"*
- **Q587** — Which command can be added to the COPY command to make it load all files, whether or not the load status of the files is known? A. `FORCE = TRUE` / B. `FORCE = FALSE` / C. `LOAD_UNCERTAIN_FILES = TRUE` / D. `LOAD_UNCERTAIN_FILES = FALSE` → Correct: **A** · You chose: C
- **Q644** — What is the recommended approach for unloading data to a cloud storage location from Snowflake? A. Use a third-party tool / B. Unload directly to the cloud storage location / C. Unload to a local file system, then upload / D. Unload to a user stage, then upload → Correct: **B** · You chose: D

### ⑤ Role/privilege minimums
- **Q508** — What happens when a database is cloned? A. It does not retain any privileges granted on the source object / B. It replicates all granted privileges on the corresponding source objects / C. It replicates all granted privileges on the corresponding child objects / D. It replicates all granted privileges on the corresponding child schema objects → Correct: **C** · You chose: A
- **Q524** — What MINIMUM privilege is required on the external stage for any role in the GET REST API to access unstructured data files using a file URL? A. READ / B. OWNERSHIP / C. USAGE / D. WRITE → Correct: **C** · You chose: A
- **Q526** — Snowflake Partner Connect is limited to users with a verified email address and which role? A. SYSADMIN / B. SECURITYADMIN / C. ACCOUNTADMIN / D. USERADMIN → Correct: **C** · You chose: B
- **Q628** — By definition, a secure view is exposed only to users with what privilege? A. IMPORT SHARE / B. OWNERSHIP / C. REFERENCES / D. USAGE → Correct: **B** · You chose: A
- **Q638** — What is the MINIMUM role required to set the value for the parameter ENABLE_ACCOUNT_DATABASE_REPLICATION? A. ACCOUNTADMIN / B. SECURITYADMIN / C. SYSADMIN / D. ORGADMIN → Correct: **D** · You chose: C

### ⑥ Floating-point precision on unload
- **Q495** — When unloading data, which file format preserves the data values for floating-point number columns? A. Avro / B. CSV / C. JSON / D. Parquet → Correct: **D** · You chose: B
- **Q627** — When floating-point number columns are unloaded to CSV or JSON files, Snowflake truncates the values to approximately what? A. (12,2) / B. (10,4) / C. (14,8) / D. (15,9) → Correct: **D** · You chose: A
- **Q639** — Which file format will keep floating-point numbers from being truncated when data is unloaded? A. CSV / B. JSON / C. ORC / D. Parquet → Correct: **D** · You chose: A

### ⑦ ACCOUNT_USAGE vs INFORMATION_SCHEMA
- **Q499** — What are the main differences between the account usage views and the information schema views? (choose 2) A. No active warehouse is needed to query account usage views but one is needed to query information schema views / B. Account usage views do not contain data about tables but information schema views do / C. Account usage views contain dropped objects but information schema views do not / D. Data retention for account usage views is 1 year but is 7 days to 6 months for information schema views, depending on the view / E. Information schema views are read-only but account usage views are not → Correct: **C, D** · You chose: B, C
- **Q617** — What are the key characteristics of ACCOUNT_USAGE views? (choose 2) A. There is no data latency / B. The data latency can vary from 45 minutes to 3 hours / C. The historical data is not retained / D. The historical data can be retained from 7 days to 6 months / E. Records for dropped objects are included in each view → Correct: **B, E** · You chose: B, D

### ⑧ Fail-safe periods
- **Q606** — What is the Fail-safe period for a transient table in the Snowflake Enterprise edition and higher? A. 0 days / B. 1 day / C. 7 days / D. 14 days → Correct: **A** · You chose: B
- **Q624** — How long is the Fail-safe period for recovering historical data from permanent tables? A. 1 day / B. 3 days / C. 7 days / D. 14 days → Correct: **C** · You chose: A

### ⑨ Network Policy
- **Q573** — What happens when the values for both an ALLOWED_IP_LIST and a BLOCKED_IP_LIST are used in a network policy? A. Snowflake ignores the BLOCKED_IP_LIST first / B. Snowflake applies the BLOCKED_IP_LIST first / C. Snowflake applies the ALLOWED_IP_LIST first / D. Snowflake ignores the ALLOWED_IP_LIST first → Correct: **B** · You chose: C
- **Q635** — Which command can be used to view the allowed and blocked IP list of a network policy? A. ALTER NETWORK POLICY / B. CREATE NETWORK POLICY / C. DESCRIBE NETWORK POLICY / D. SHOW NETWORK POLICIES → Correct: **C** · You chose: D

## Isolated single-hit misses (not clusters — 1 occurrence each in this sample)

Flagged separately so they're visible instead of buried in the raw domain list. Per the promotion rule in `snowflake-progress.md`, these stay off the permanent recurring-mistake table unless they recur in a future batch — but content was added for all of them since they were true content gaps (nothing existed in the notes), not recall gaps.

- **#2 (D4)** HyperLogLog for approx distinct count on huge tables — chose MD5 instead
- **#33 (D4)** Bernoulli sampling meaning (samples every row independently) — chose "system/block" definition instead
- **#36 (D4)** Min table size before considering a clustering key (1 TB) — chose 1 GB
- **#51 (D4)** Recursive query syntax when hierarchy depth is unknown (`CONNECT BY` / `WITH RECURSIVE`) — chose `LISTAGG`/`QUALIFY`
- **#61 (D4)** Loop that iterates until a condition becomes true (`REPEAT`) — chose `WHILE`
- **#75 (D4)** Tabular UDF return clause keyword (`RETURNS TABLE`) — chose `VALUES`
- **#79 (D4)** Set operator for values in both tables (`INTERSECT`) — chose `MINUS`
- **#64 (D4)** `average_overlaps` in `SYSTEM$CLUSTERING_INFORMATION` (avg micro-partitions with overlapping value ranges) — chose "physically stored in same location"

## Content updates applied (2026-08-20, to `SnowPro_Core_Contents.html`)

All 9 recurring clusters + the isolated misses above were checked against the notes file; gaps were patched:

- **① 存储/计算层归属** — added a pointed reinforcement note in the 三层架构 section tied to the exact recurring wrong answers (Blobs vs Micro-partitions, Cloud Services vs Database Storage, "cloud storage handles compression" myth). Content already existed here in general form — this confirms it's a **recall/rehearsal gap**, not a missing-notes gap; re-quiz to verify.
- **② Unstructured URL functions** — added `GET_RELATIVE_PATH` clarification + Directory Table output columns list
- **③ Query Profile reading** — added Query Profile definition, orange bar meaning, UnionAll+Aggregate signal, external-function stat
- **④ PUT/GET/COPY mechanics** — added PUT encryption timing, `LS @~` syntax
- **⑤ Role/privilege minimums** — added secure view `OWNERSHIP` vs `IMPORT SHARE`
- **⑥ Float precision on unload** — added `(15,9)` truncation number, direct-to-cloud-storage recommendation
- **⑦ ACCOUNT_USAGE vs INFORMATION_SCHEMA** — already well-covered, no edit needed (recall gap)
- **⑧ Fail-safe periods** — already well-covered, no edit needed (recall gap)
- **⑨ Network Policy** — added `DESCRIBE` vs `SHOW` distinction, `ALLOW_CLIENT_MFA_CACHING` 4hr number
- **Isolated misses** — added new "SQL 杂项速记" block (HyperLogLog, Bernoulli/System sampling, `SAMPLE(0)`/`SAMPLE(100)`, recursive query syntax, `REPEAT` vs `WHILE`, `INTERSECT`/`MINUS`, `RETURNS TABLE`) + clustering-key 1TB threshold + `average_overlaps` definition

## Next snapshot
Compare against this file once the next wrong-answer batch is processed. Watch specifically: does cluster 5 (storage/compute layer attribution) resolve this time, given it already "recurred" once before? Watch clusters 1, 3, 4 (unstructured-data URLs, PUT/GET/COPY mechanics, role/privilege minimums) for repeat appearances — 2+ hits next time promotes them into the permanent recurring-mistake table in `snowflake-progress.md`.
