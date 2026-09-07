# Abhiram M V

![Header](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=180&section=header&text=Abhiram%20M%20V&fontSize=48&fontColor=ffffff&animation=fadeIn&fontAlignY=35&desc=ML%20/%20AI%20Engineer&descAlignY=55&descSize=20&fontColor=ffffff)

**ML / AI engineer.** I build retrieval and forecasting systems, then measure them hard enough to find out where they don't work.

📍 Denver, CO

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/abhiram-m-v-4a0413182/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:abhiram2000@gmail.com)


---

## Selected work

**[Citera](https://github.com/abhirammv2000/Ricoh)** — agentic RAG over 733 technical PDFs. 0.96 groundedness, 0.97 correctness, 0.94 recall@5 (n=100, bootstrap CIs). Built as a 4-stage plan→retrieve→verify→retry agent; an ablation showed the verifier earned nothing and the planner's gain didn't replicate on holdout, so both ship behind flags instead of on by default.
*Python · LangGraph · Claude · ChromaDB + BM25 + RRF · Docker*

**[Demand Forecasting & Inventory Optimization](https://github.com/abhirammv2000/walmart-forecasting)** — M5, 30,490 series. Held-out WRMSSE 0.6475 (~40% better than seasonal-naive); a newsvendor policy on forecast quantiles cut inventory cost 42% and lifted fill rate 61%→92% vs ordering the point forecast. 94 tests including a no-leakage check.
*LightGBM (Tweedie) · XGBoost quantile · Airflow · MLflow · Terraform*

**[TestForge](https://github.com/abhirammv2000/TestForge)** — turns Jira tickets into pytest/Robot Framework suites with a local LLM and **runs them for real** — pass/fail comes from an actual test run, not the model's word. Bad generations (empty files, stub asserts, repetition loops) are auto-detected and retried.
*Python · Ollama · MCP · pytest*

**[GDELT Global Events Lakehouse](https://github.com/abhirammv2000/gdelt-lakehouse)** — medallion lakehouse on a feed that publishes new world-events data every 15 minutes. Bronze→Silver (Iceberg, ACID)→Gold (dbt star schema), Kafka streaming layer with a per-event quality gate, Terraform for AWS. Runs fully local via `docker compose up`.
*PySpark · Apache Iceberg · Airflow · dbt · Kafka · Terraform*

**[Blitz](https://github.com/abhirammv2000/blitz)** *(collab)* — company URL in, full marketing package out. Six sequential LangGraph agents sharing context through ChromaDB, streamed to the browser over SSE.
*LangGraph · LiteLLM (GPT-4o/Gemini) · FastAPI · React*

**[LodgeZilla](https://github.com/abhirammv2000/LodgeZilla)** *(3-person team)* — lodging marketplace seeded from real Inside Airbnb data. FastAPI + MongoDB, JWT auth, Redis-backed activity log, full K8s deployment with HPA autoscaling.
*FastAPI · MongoDB · React · Kubernetes*

**[Ad Pulse](https://github.com/abhirammv2000/ad-pulse)** *(course project)* — ad-serving platform as 6 independent microservices: Go ad server ranking off a Redis cache, Python ad manager, Pub/Sub-driven engagement pipeline into MongoDB. Helm-deployed with per-service CI/CD.
*Go · Python/Flask · React · Kubernetes/Helm*

**[Uber Rides Medallion ETL Pipeline](https://github.com/abhirammv2000/Uber-Rides-Medallion-ETL-Pipeline)** — Databricks Bronze→Silver→Gold on synthetic ride-hailing data. Spark Structured Streaming ingestion, dbt star schema with SCD Type 2 on every dimension.
*Databricks · PySpark · Delta Lake · dbt Cloud*

**[ScaleFlow](https://github.com/abhirammv2000/scaleflow)** *(team project, CU Boulder)* — supply-chain risk platform: Airflow ETL from UN Comtrade/World Bank/Yahoo Finance, XGBoost + SHAP risk models, a LangChain/GPT-4o Q&A layer over Pinecone. Load-tested across 4 stress tiers.
*Airflow · PostgreSQL · XGBoost · LangChain · Pinecone*

---

## What I work with

`Python` `Go` `LangGraph` `LightGBM/XGBoost` `FastAPI` `Docker` `Kubernetes` `Airflow` `dbt` `Terraform` `Kafka` `AWS` `GCP` `Databricks`

**How I work** — commit to the decision rule before running the experiment; measure the noise floor before claiming a metric moved; delete the component the numbers don't justify.

---

![Stats](https://github-readme-stats.vercel.app/api?username=abhirammv2000&show_icons=true&hide_border=true&include_all_commits=true&count_private=true&theme=default)

---

**Open to:** ML Engineer · AI Engineer · Data Scientist · MLOps

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/abhiram-m-v-4a0413182/)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:abhiram2000@gmail.com)

![Footer](https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer)
