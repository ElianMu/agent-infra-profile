# Elian Mu

**AI Agent Engineer | Agent Infrastructure & LLM Systems**

M.S. Computational Design Practices · Columbia University '27  
B.Eng. Smart Building and Construction · Shanxi University '26 (GPA 89/100 · Rank 2/32)

Building reliable AI Agents, LLM workflows, and production-oriented AI infrastructure.

[LinkedIn](https://www.linkedin.com/in/elianmu3178) · [GitHub](https://github.com/ElianMu) · [Live Demo — STROLLANE · NYC](https://elianmu.github.io/streetwise/)

---

## About Me

I have a background in Architecture and Computational Design and am now focused on AI Agent Engineering and Agent Infrastructure. My work combines LLMs, tool calling, retrieval systems, real-world data, and deterministic software components into AI applications that are reliable and deployable, not just demos. I care about agent orchestration, state management, retrieval quality, safety guards, evaluation, and observability — not only generation quality.

Recent work includes a multi-agent data analysis system with a reflection loop, a Text-to-SQL platform over an enterprise data warehouse, a multi-turn customer service agent on LangGraph, a travel knowledge-base RAG system with traceable citations, and STROLLANE · NYC, a personalized city-walk platform with a 100-dataset geospatial pipeline.

---

## Featured Project

### STROLLANE · NYC
**AI-Powered Personalized City Walk & Urban Navigation Platform**

[Live Demo →](https://elianmu.github.io/streetwise/)

STROLLANE · NYC is a personalized City Walk platform that transforms natural-language walking preferences into data-informed urban routes, integrating LLM workflows, geospatial data infrastructure, route optimization, and interactive navigation. It is independently conceived, designed, and developed — product framing, system architecture, and implementation.

**LLM Workflow & Orchestration**
Built a multi-stage AI workflow integrating natural-language interpretation, geospatial retrieval, route optimization, and deterministic validation, with conversational state updates and fallback handling. The agent runtime uses LangGraph and LangChain with tool-calling, feature-flagged behind an explicit `AGENT_ENABLED` switch so the core routing service remains deterministic and dependency-free when the agent layer is off.

**Tool Integration & Reliability**
Integrated location search, urban data queries, and routing services through REST APIs; enforced route constraints and implemented structured error handling and dynamic replanning.

**Data Infrastructure**
Integrated 97 of 125 registered datasets containing 2.69M+ source records; mapped approximately 10,500 Manhattan street segments to 12 walking-experience dimensions using spatial indexing and LION–OSM matching.

**Routing & Performance**
Applied A*, Dijkstra, and 2-opt for personalized multi-stop planning; built a 13-state GPS navigation engine with 14 replayable simulation scenarios and reduced map layers from approximately 240 to 63 (74%).

| Metric | Value |
|---|---|
| Integrated Datasets | 97 / 125 |
| Source Records | 2.69M+ |
| Manhattan Street Segments | ~10,500 |
| Walking Experience Dimensions | 12 |
| GPS Navigation States | 13 |
| Navigation Simulation Scenarios | 14 |
| Map Layer Reduction | 74% |

---

## Selected Projects

### Jingwen Zhihe (景文智核) — Travel Knowledge-Base RAG System
*Independent · Oct 2026–Present · Python / FastAPI / RAG / bge / MySQL / Vue 3*

A RAG knowledge base that ingests five categories of travel guides (attractions, routes, hotels, food, transport) and serves semantic search and Q&A with source citations.

- **Layered architecture & RAG pipeline:** four-layer FastAPI architecture and a self-built RAG pipeline (load → normalize metadata → structured chunking → embed → retrieve → generate); 30 guides, 286 chunks, 768-dim vectors.
- **Structured chunking:** splits on H2/H3 heading boundaries, keeps semantic integrity first, and records each chunk's heading path so citations resolve to a specific section.
- **Metadata normalization:** maps variant source fields into one schema for content-type and region filtering, locked down by unit tests.
- **Self-built vector index:** replaced chromadb (which could not write its index under a non-ASCII path) with a numpy index — cosine similarity via dot product, metadata filtering, per-document deletion, persistence — keeping the original query interface so a move to Milvus swaps one adapter.
- **Native library conflict:** worked around a process-level torch × pymysql crash by warming the model before DB init, pinning embedding to one thread, and aligning load order across service, tests, and scripts.
- **Streaming Q&A with citations:** async httpx SSE streaming with server-side and client-side fallback to non-streaming; history-aware query rewriting; answers persist with source file and heading path.

### Zhanyu (栈语) — Multi-Turn Customer Service Agent
*Backend / AI Engineer · Sep–Nov 2026 · LangGraph / FastAPI / Vue 3 / Chroma / Neo4j*

Upgrades a single-turn Q&A bot into a multi-turn business-handling agent that survives users changing their minds, correcting inputs, and disconnecting.

- **State machine & recovery:** three-node LangGraph StateGraph with checkpoints for disconnect recovery and time travel.
- **Multi-turn flows:** declarative YAML flows plus a LIFO dialogue stack; slot correction updates only the target slot.
- **Intent drift:** fixed precedence (correction > slot filling > drift); lightweight questions answered inline, new flows pushed onto the stack and resumed.
- **Hybrid RAG & GraphRAG:** BM25 + vector + RRF with reranking and citations; Text2Cypher with EXPLAIN validation, self-correction, and user_id filtering against Cypher injection.
- **Fallback chain & tests:** four-level fallback (business flow → knowledge Q&A → graph Q&A → fallback) guarantees a non-empty response; 81 tests cover intent drift, slot correction, and disconnect recovery; new flows need only YAML.

### Shuju Tongda (数据通达) — Enterprise Text-to-SQL Q&A Platform
*Backend / AI Engineer · Jul–Sep 2026 · LangGraph / FastAPI / Vue 3 / MySQL / Qdrant / Elasticsearch / Redis*

Business users ask questions in plain language; the system handles understanding, retrieval, SQL generation, safety checks, execution, and explanation.

- **Metadata knowledge base:** declarative YAML config loaded into MySQL (relations), Qdrant (semantic vectors), and Elasticsearch (value full-text), with two-pass foreign-key backfill and idempotent rebuilds.
- **Hybrid retrieval:** vector + full-text recall fused with RRF (k=60) and reranked by bge-reranker; falls back to MySQL fuzzy matching if the vector store is down.
- **Agent orchestration & SQL safety:** 12-node LangGraph pipeline; sqlparse read-only allowlist, rewrite-on-failure (max 3), read-only account, and pre-execution re-check; SSE streaming of progress, SQL, and results.
- **Multi-turn & permissions:** checkpointer-persisted sessions with coreference resolution; table/field-level permissions removed from context before SQL generation.
- **Evaluation & observability:** gold-question eval set (accuracy, recall hit rate, execution success, latency); request_id tracing, OpenTelemetry, Langfuse, per-node timing.

### Tanyuan (探渊) — Multi-Agent Data Analysis System
*Independent · May–Jul 2026 · LangChain DeepAgents / FastAPI / Vue 3 / MySQL / Chroma*

A lead agent dispatches web-search, database, and knowledge-base sub-agents, and a plan–execute–reflect loop produces structured analysis reports, visualized live over WebSocket.

- **Multi-agent orchestration:** lead agent + three expert sub-agents on DeepAgents, decoupled via the `task` tool and `subagent_type`.
- **Reflection loop:** four programmatic hard checks (length / placeholders / PDF format / source coverage) plus an LLM soft review; failures inject correction instructions and retry (max 3 rounds).
- **Local RAG:** BGE embeddings + Chroma + recursive chunking + multi-format parsing, evaluated offline with four RAGAS metrics.
- **Security:** table-name allowlist, write blocking, and read-only account for SQL; path sanitization and boundary checks for files.
- **Async architecture:** FastAPI + WebSocket + asyncio with ContextVar session isolation and a live agent event tree in the frontend.

### Coursework — Advanced Machine Learning, Assignment 01
Classical and advanced machine learning methods in a Jupyter Notebook. [Repository](https://github.com/ElianMu/Advanced-Machine-Learning-Assignment-01)

---

## Technical Expertise

**AI Agent Engineering**
LangGraph · LangChain DeepAgents · Multi-Agent Orchestration · Tool Calling · Reflection & Self-Correction · Prompt Engineering

**RAG & Retrieval**
Hybrid Retrieval (BM25 / Vector / Full-Text + RRF) · Reranking · BGE Embeddings · Structured Chunking · GraphRAG · RAGAS Evaluation

**Text-to-Query & Dialogue**
Text-to-SQL · Text2Cypher · Slot Filling · Dialogue Stack · Coreference Resolution

**Backend & Data Stores**
Python · SQL · FastAPI · asyncio · SQLAlchemy · WebSocket / SSE · Vue 3 · Git · MySQL · Redis · Chroma · Qdrant · Elasticsearch · Neo4j

**Reliability, Security & Observability**
SQL / Cypher Injection Defense · Path-Traversal Guards · Table/Field-Level Permissions · Fallback Chains · OpenTelemetry · Langfuse · Eval-Set Regression

**Geospatial Data & Algorithms**
Geospatial Processing · Spatial Indexing · Graph Algorithms (A*, Dijkstra, 2-opt) · Data Pipelines

---

## Connect With Me

**LinkedIn:** [linkedin.com/in/elianmu3178](https://www.linkedin.com/in/elianmu3178)

**GitHub:** [github.com/ElianMu](https://github.com/ElianMu)

**Featured Project:** [elianmu.github.io/streetwise](https://elianmu.github.io/streetwise/)
