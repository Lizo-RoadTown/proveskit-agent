---
layout: article
title: Technical Architecture
permalink: /technical/
key: page-technical
---

# Technical Architecture

This system has two core products:

1) An MCP-backed living documentation library
2) A repo risk assessment extension for IDEs

---

## System Overview

```mermaid
graph TB
  subgraph Sources
    ProvesDocs[Build knowledge: assembly, hardware, flight software, testing]
    FPrimeDocs[Software architecture: ports, components, build, GDS]
    OSSRepos[Operational knowledge: configs, tests, ops notes, fixes]
  end
  ProvesDocs --> Curator[PROVES Agentic Curation System]
  FPrimeDocs --> Curator
  OSSRepos --> Curator
  Curator --> Library[Open source library repo]
  Library --> Index[Search + embeddings]
  Index --> MCP[MCP server]
  MCP --> IDE[IDE extensions]
  MCP --> AI[AI tools]
```

---

## Source Coverage (What It Really Means)

**Build knowledge (how to assemble and validate the system):**
- Assembly and integration guides
- Hardware and subsystem references
- Flight software and testing notes

**Software architecture knowledge (how the system is structured):**
- Architecture and component model
- Ports, components, and topologies
- Build system, tooling, and GDS usage

**Operational knowledge (how it behaves in the real world):**
- Configs, tests, and operational checklists
- Issue reports and fixes (as citations and excerpts)

---

## Fragmentation Map

This is the gap the MCP library closes:

- **Inside repos**: issues, commits, and tests are disconnected
- **Across teams**: the same fixes are rediscovered
- **Across sources**: PROVES build knowledge and F Prime architecture live apart

The curation system ties these fragments to a single search and citation layer.

---

## Storage Model

### Canonical Library (Open Source Repo)

- Markdown entries with small metadata blocks
- Review before merge
- Citations and excerpts only

This repo is the system of record and keeps the library transparent and open source.

### Search Index

- Built from the canonical library
- Used by the MCP server for fast retrieval
- Can be local (SQLite) or shared (Postgres with embeddings)

---

## MCP Server

The MCP server exposes:

- Search across lessons, risk patterns, and docs
- Entry retrieval with citations
- Source references to repos and docs

This makes the library interrogatable by any AI tool in an IDE.

---

## Risk Scan Extension

The IDE extension:

1) Fetches risk patterns from MCP
2) Scans the local repo for matches
3) Reports likely mission-critical issues
4) Links to fixes and verification steps

New patterns can be submitted back to the library for review.

---

## Entry Format (No Blame)

```
Issue
- What happened:
- Where it lives (component/repo/doc):
- Likely knowledge location (file/test/doc/role):
- Fix summary:
- How to verify:
```

The system owns outcomes. We log where the fix lives, not who caused the problem.

---

## Data Flow

```mermaid
sequenceDiagram
  participant Dev as Developer
  participant Ext as IDE Extension
  participant MCP as MCP Server
  participant Repo as Repo

  Dev->>Ext: Run daily scan
  Ext->>MCP: Fetch risk patterns
  Ext->>Repo: Scan for matches
  Ext->>Dev: Report risks and fixes
  Ext->>MCP: Submit new pattern (optional)
```
