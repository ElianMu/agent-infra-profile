# Elian Mu

**AI Agent Engineer | Agent Infrastructure & LLM Systems**

M.S. Computational Design Practices · Columbia University '27

Building reliable AI Agents, LLM workflows, and production-oriented AI infrastructure.

[LinkedIn](https://www.linkedin.com/in/elianmu3178) · [GitHub](https://github.com/ElianMu) · [Live Demo — STROLLANE · NYC](https://elianmu.github.io/streetwise/)

---

## About Me

I have a background in Architecture and Computational Design and am now focused on AI Agent Engineering and Agent Infrastructure. My work centers on combining LLMs, tool calling, real-world data, retrieval systems, and deterministic software components into AI applications that are reliable and deployable, not just demos. I care about agent system architecture, tool integration, data infrastructure, evaluation, and production-oriented engineering — not only generation quality. My largest project, STROLLANE · NYC, reflects this: a multi-stage agent workflow, a 100+ dataset geospatial data pipeline, and a tested navigation/routing engine, built end to end.

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

## Other Selected Projects

### Advanced Machine Learning — Assignment 01
Coursework applying classical and advanced machine learning methods in a Jupyter Notebook.

**Technical Focus:** Python, Machine Learning, Jupyter, Data Analysis

[Repository](https://github.com/ElianMu/Advanced-Machine-Learning-Assignment-01)

---

## Technical Expertise

**AI Agent Engineering**
Agent Architecture · LangGraph · LangChain · Tool Calling · Workflow Orchestration · Agent Evaluation

**LLM & Retrieval Systems**
Large Language Models · Retrieval-Augmented Generation · Structured Retrieval · Context Management

**Backend & Agent Infrastructure**
Python · REST APIs · SQLite · Git · GitHub Actions · Docker · Deployment & Monitoring

**Data Engineering & Algorithms**
Geospatial Processing · Spatial Indexing · Graph Algorithms (A*, Dijkstra) · Route Optimization · Data Pipelines

---

## Connect With Me

**LinkedIn:** [linkedin.com/in/elianmu3178](https://www.linkedin.com/in/elianmu3178)

**GitHub:** [github.com/ElianMu](https://github.com/ElianMu)

**Featured Project:** [elianmu.github.io/streetwise](https://elianmu.github.io/streetwise/)
