# Abhiram M V

**ML / AI engineer.** I build retrieval and forecasting systems, then measure them hard enough to find out where they don't work.

Most of what's below is a link to a repo where the numbers, the ablation, and the failure modes are written down. Where a result was wrong, the README says so.

📍 Boulder, CO · [LinkedIn](https://www.linkedin.com/in/abhiram-m-v-4a0413182/) · [Email](mailto:abhiram2000@gmail.com)

---

## Selected work

### [Citera](https://github.com/abhirammv2000/Ricoh) — agentic RAG for technical support

Retrieval-augmented assistant over 733 product-documentation PDFs. Answers with page-level citations, or refuses when the corpus doesn't contain the answer.

| | |
|---|---|
| **Result** | 0.96 groundedness, 0.97 correctness, 1.00 citation precision, 0.94 retrieval recall@5 — n=100, 70/30 dev/holdout, bootstrap CIs |
| **The interesting part** | It was built as a plan → retrieve → verify → retry agent, and an ablation removed most of it. The verifier earned nothing; the planner helped on dev and not on holdout, so it ships behind a flag instead of on by default. |
| **Also** | Judge is a different model from the agent (self-grading is indefensible). Judge noise floor measured before any metric claim is made. One earlier README claim was withdrawn and the correction is kept in the repo. |
| **Stack** | Python · LangGraph · Claude · ChromaDB + BM25 + Reciprocal Rank Fusion · Streamlit · pytest + GitHub Actions · Docker |

---

### [Demand Forecasting & Inventory Optimization](https://github.com/abhirammv2000/walmart-forecasting) — M5, 30,490 series

Forecasting through to the actual stocking decision, with cost measured against held-out demand.

| | |
|---|---|
| **Result** | Held-out WRMSSE 0.6475 (~40% better than seasonal naive). Newsvendor policy on forecast quantiles cut total cost 42% vs ordering the point forecast, and lifted fill rate 61% → 92%. |
| **The interesting part** | 68% of series-days are zero. A model that minimises average error learns to predict ~0, which is useless for stocking — so the demand *distribution* is carried all the way to the order quantity. The empirical cost-minimising service level (0.900) lands on the theoretical critical ratio (0.909). |
| **Engineering** | 94 tests including a no-leakage test, pinned deps, rolling-origin CV (never random splits), held-out window touched once. Airflow DAG, MLflow registry, Terraform for the AWS core, PSI drift check, CI. |
| **Stack** | LightGBM (Tweedie) · XGBoost multi-quantile · Docker · Airflow · MLflow · Terraform · GitHub Actions |

---

### [TestForge](https://github.com/abhirammv2000/TestForge) — Jira tickets → runnable test suites

Reads a plain-text ticket, pulls the source under test, generates pytest and Robot Framework files with a local LLM, **runs them for real**, and publishes a report. Jira, Bitbucket and Confluence all reached through an MCP server.

| | |
|---|---|
| **The interesting part** | Pass/fail counts come from an actual test run, not the model claiming success. Tests that run but fail are reported as-is rather than rewritten until green — otherwise the tool hides real bugs. |
| **Getting usable output from a 7B model** | Generated files are rejected on specific smells (empty, `pass` stub, leftover code fence, repetition loop) and retried. The model sees the signature and docstring plus known I/O examples, not the implementation, so it can't copy the answer back. |
| **Stack** | Python · Ollama (qwen2.5-coder) · MCP · pytest · Robot Framework |

---

### [Blitz](https://github.com/abhirammv2000/blitz) — multi-agent marketing pipeline *(collaboration)*

A company URL in, a full marketing package out: research dossier, brand profile, audience segments, content plan, sales sequences, ad creatives. Six sequential LangGraph agents sharing context through ChromaDB, streaming results to the browser over SSE.

**Stack:** LangGraph · LiteLLM (GPT-4o with Gemini fallback) · FastAPI · ChromaDB · React + TypeScript · Tavily / Firecrawl · ElevenLabs

---

### [GDELT Global Events Lakehouse](https://github.com/abhirammv2000/gdelt-lakehouse) — streaming data engineering, 7 phases

A medallion-architecture lakehouse ingesting the GDELT global-events feed, which publishes a new batch of world news events every 15 minutes: 61 raw columns, no headers, real schema drift.

| | |
|---|---|
| **Pipeline** | Bronze (raw, MinIO/S3) → Silver (typed, deduped, Apache Iceberg, ACID + time travel) → Gold (dbt star schema: fact + 4 dimensions) |
| **Built** | Idempotent ingestion with MD5 verification and checkpointing (re-running a batch is a no-op — verified by test), a schema-drift quarantine for non-conformant rows, a Kafka/Redpanda streaming layer with a per-event data-quality gate, and Terraform for the AWS path (S3 + Glue Iceberg + IAM) |
| **Runs entirely locally** | `docker compose up` — no cloud account needed — and switches to AWS with one env flag |
| **Stack** | PySpark · Apache Iceberg · Apache Airflow · dbt · Kafka/Redpanda · Terraform · GitHub Actions CI (ruff, mypy --strict, pytest) |

Built as a systems-design demonstration rather than in response to a live production need — a good signal of stack depth (streaming, lakehouse table formats, orchestration, IaC all in one place), not a business outcome.

---

### [LodgeZilla](https://github.com/abhirammv2000/LodgeZilla) — property listing & booking marketplace *(3-person team project)*

Short-term lodging marketplace: hosts list properties, tourists search by destination and date range and reserve what's free.

| | |
|---|---|
| **Built** | FastAPI + MongoDB backend, React frontend, JWT auth, a Redis-backed activity-log queue with a dedicated worker consuming it |
| **Deployment** | Full Kubernetes manifests — Deployments, Services, Ingress, HPA autoscaling 1→5 pods at 50% CPU |
| **Data** | Seeded from real Inside Airbnb city exports, not synthetic data |
| **Stack** | FastAPI · MongoDB · React · Redis · Kubernetes |

---

### [Ad Pulse](https://github.com/abhirammv2000/ad-pulse) — ad-serving platform, 6 microservices *(CSCI5828 course project)*

An ad manager, a real-time ad server, and a click/render analytics pipeline, built as independently deployable services rather than a monolith.

| | |
|---|---|
| **Built** | Ad server (Go/Gin) ranks and bids off a Redis cache kept warm by a dedicated refresh service; engagement pipeline (Go → Pub/Sub → Python subscriber) aggregates clicks/renders into MongoDB reports |
| **Ops** | Kubernetes/Helm chart deploying all six services; GitHub Actions CI/CD builds, tags and deploys per-service on every push |
| **Stack** | Python/Flask · Go/Gin · React · Redis · MongoDB · Postgres · Kubernetes/Helm |

---

### [GDELT Global Events Lakehouse](https://github.com/abhirammv2000/gdelt-lakehouse) — streaming data engineering, 7 phases

A medallion-architecture lakehouse ingesting the GDELT global-events feed, which publishes a new batch of world news events every 15 minutes: 61 raw columns, no headers, real schema drift.

| | |
|---|---|
| **Pipeline** | Bronze (raw, MinIO/S3) → Silver (typed, deduped, Apache Iceberg, ACID + time travel) → Gold (dbt star schema: fact + 4 dimensions) |
| **Built** | Idempotent ingestion with MD5 verification and checkpointing (re-running a batch is a no-op — verified by test), a schema-drift quarantine for non-conformant rows, a Kafka/Redpanda streaming layer with a per-event data-quality gate, and Terraform for the AWS path (S3 + Glue Iceberg + IAM) |
| **Runs entirely locally** | `docker compose up` — no cloud account needed — and switches to AWS with one env flag |
| **Stack** | PySpark · Apache Iceberg · Apache Airflow · dbt · Kafka/Redpanda · Terraform · GitHub Actions CI |

---

### [Uber Rides Medallion ETL Pipeline](https://github.com/abhirammv2000/Uber-Rides-Medallion-ETL-Pipeline) — Databricks Bronze→Silver→Gold

A Databricks pipeline over six related ride-hailing entities, built as a focused exercise in the medallion pattern on synthetic data.

| | |
|---|---|
| **Built** | Spark Structured Streaming ingestion (per-entity checkpoints, `trigger(once=True)` for scheduled batch runs), PySpark cleaning/dedup/upsert layer, dbt-managed star schema with SCD Type 2 history on every dimension and an incremental fact table |
| **Stack** | Databricks · PySpark · Delta Lake · dbt Cloud · Unity Catalog |

---

### [ScaleFlow](https://github.com/abhirammv2000/scaleflow) — supply-chain risk prediction *(CSCI-6502 team project, CU Boulder)*

A platform combining economic/trade/financial data ingestion with ML risk models and a real-time LLM Q&A interface.

| | |
|---|---|
| **Built** | Airflow-orchestrated ETL from UN Comtrade, World Bank, and Yahoo Finance (6,000+ tickers); XGBoost risk models with SHAP explainability; a LangChain/GPT-4o Q&A service retrieving over Pinecone + Supabase with streamed, cited responses |
| **Load-tested** | Ingestion and Postgres aggregation benchmarked across four stress tiers (`super_light` → `heavy`) |
| **Stack** | Apache Airflow · PostgreSQL · XGBoost · LangChain · Pinecone · Supabase · Next.js |

---

## What I work with

**ML / AI** — LangGraph, hybrid retrieval (dense + BM25 + RRF), LLM evaluation and ablation design, LightGBM / XGBoost, quantile regression, MCP servers

**Engineering** — Python, Go, FastAPI, pytest, Docker, Kubernetes, GitHub Actions, Airflow, dbt, MLflow, Terraform, Kafka, AWS, GCP, Databricks

**How I work** — commit to the decision rule before running the experiment; measure the instrument's noise floor before claiming a metric moved; delete the component the numbers don't justify, even when it was the interesting part to build.

---

## GitHub

![Stats](https://github-readme-stats.vercel.app/api?username=abhirammv2000&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=default)

---

**Open to:** ML Engineer · AI Engineer · Data Scientist · MLOps roles

Best way to reach me: [LinkedIn](https://www.linkedin.com/in/abhiram-m-v-4a0413182/) or [email](mailto:abhiram2000@gmail.com)
