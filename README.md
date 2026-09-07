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

## What I work with

**ML / AI** — LangGraph, hybrid retrieval (dense + BM25 + RRF), LLM evaluation and ablation design, LightGBM / XGBoost, quantile regression, MCP servers

**Engineering** — Python, FastAPI, pytest, Docker, GitHub Actions, Airflow, MLflow, Terraform, AWS, GCP

**How I work** — commit to the decision rule before running the experiment; measure the instrument's noise floor before claiming a metric moved; delete the component the numbers don't justify, even when it was the interesting part to build.

---

## GitHub

![Stats](https://github-readme-stats.vercel.app/api?username=abhirammv2000&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=default)

---

**Open to:** ML Engineer · AI Engineer · Data Scientist · MLOps roles

Best way to reach me: [LinkedIn](https://www.linkedin.com/in/abhiram-m-v-4a0413182) or [email](mailto:abhiram2000@gmail.com)
