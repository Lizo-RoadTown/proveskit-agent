---
layout: article
title: System Architecture
key: page-architecture
permalink: /architecture/
---

# PROVES Kit Agent: System Architecture

This page summarizes the current agentic system as implemented in PROVES Library and exposed through PROVES Kit Agent.

---

## High-Level Architecture

```mermaid
%%{init: {'flowchart': {'defaultRenderer': 'elk'}}}%%
flowchart TB
  subgraph Query[User Query Layer]
    User[CubeSat Team]
    UI[VS Code / CLI / Web]
  end

  subgraph Orchestration[LangGraph Orchestration]
    Router[Router Agent]
    Planner[Planning Agent]
    Executor[Execution Agent]
  end

  subgraph Agents[Deep Agents]
    Curator[Curator Agent]
    Scanner[Risk Scanner]
    Builder[Builder Agent]
    Analyzer[Cascade Analyzer]
  end

  subgraph Knowledge[Knowledge Layer]
    MCP[MCP Server]
    GraphDB[(Knowledge Graph)]
    RAG[RAG + Docs]
    VectorDB[(Vector Store)]
  end

  User --> UI
  UI --> Router
  Router --> MCP
  Router --> Planner
  Planner --> Executor

  Executor --> Curator
  Executor --> Scanner
  Executor --> Builder
  Executor --> Analyzer

  Curator --> MCP
  Scanner --> MCP
  Builder --> MCP
  Analyzer --> GraphDB

  MCP --> GraphDB
  MCP --> RAG
  RAG --> VectorDB
```

---

## Theory Layer: From Systems to Graph to GNN

We layer social and organizational theory with nearly-decomposable architecture to model how interfaces, couplings, and bonds create dependency structure across three layers:

- **Organizational layer**: teams, handoffs, ownership boundaries
- **Digital layer**: software components, APIs, protocols, data flow
- **Physical layer**: hardware, power, timing, thermal constraints

That structure becomes a rich dependency graph, which is the training substrate for GNN models.

```mermaid
%%{init: {'flowchart': {'defaultRenderer': 'elk'}}}%%
flowchart TB
  subgraph Layers[Three System Layers]
    Org[Organizational Layer]
    Dig[Digital Layer]
    Phys[Physical Layer]
  end

  subgraph Theory[Theory and Structure]
    NDA[Nearly-Decomposable Architecture]
    IFC[Interfaces, Couplings, Bonds]
  end

  subgraph Graph[Dependency Graph]
    Nodes[Components and Actors]
    Edges[Relations and Evidence]
  end

  subgraph GNN[GNN Models]
    Risk[Risk Scoring]
    Cascade[Cascade Prediction]
    Outcomes[Mission Outcomes]
  end

  Org --> NDA
  Dig --> NDA
  Phys --> NDA
  NDA --> IFC
  IFC --> Nodes
  IFC --> Edges
  Nodes --> Risk
  Edges --> Risk
  Nodes --> Cascade
  Edges --> Cascade
  Risk --> Outcomes
  Cascade --> Outcomes
```

---

## MCP Query Lifecycle

```mermaid
sequenceDiagram
  participant User as CubeSat Team
  participant UI as VS Code or CLI
  participant MCP as MCP Server
  participant Graph as Truth Graph
  participant RAG as RAG Docs

  User->>UI: Ask dependency question
  UI->>MCP: Query
  MCP->>Graph: Graph lookup
  MCP->>RAG: Retrieve docs
  Graph-->>MCP: Relationships + evidence
  RAG-->>MCP: Supporting excerpts
  MCP-->>UI: Structured answer
```

---

## Truth Layer Pipeline

Only human-verified facts enter the truth graph.

```mermaid
%%{init: {'flowchart': {'defaultRenderer': 'elk'}}}%%
flowchart TB
  A[Raw Sources] --> B[Extractor Agent]
  B --> C[Validator Agent]
  C --> D[Decision Maker]
  D --> E[Human Verification]
  E --> F[Truth Graph]
  F --> G[GNN Risk Layer]
```

---

## Cascade Analysis Flow

```mermaid
%%{init: {'flowchart': {'defaultRenderer': 'elk'}}}%%
flowchart TB
  Q[User Question] --> Router[Router Agent]
  Router --> Cascade[Cascade Analyzer]
  Cascade --> Graph[(Truth Graph)]
  Graph --> Paths[Dependency Paths]
  Paths --> Evidence[Evidence Gaps]
  Evidence --> MCP[MCP Response]
```

---

## MCP Server as the Knowledge Interface

The MCP server is the single interface for:

- Graph queries and cascade paths
- Evidence tracing and citations
- RAG retrieval across docs and entries
- IDE and CLI integrations for CubeSat teams

---

## GNN Risk Layer (Proves_AI)

The GNN layer uses the verified truth graph to estimate mission risk and cascade impact:

- GraphSAGE for graph risk and cascade reasoning
- XGBoost baseline for mission success probability
- Cross-encoder reranker for retrieval quality

Repo: https://github.com/Lizo-RoadTown/Proves_AI

---

## Why This Matters

- Makes hidden dependencies queryable
- Preserves institutional memory across cohorts
- Lets teams act on risks before integration
