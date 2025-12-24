---
layout: article
title: Living Documentation Library
permalink: /living-library/
key: page-living-library
---

[Back to Home](/proveskit-agent/)

# Living Documentation Library

The PROVES Library is the living documentation layer behind PROVES Kit Agent. Entries are citation-based, artifact-linked, and queryable through MCP.

---

## The Fragmentation Problem

Knowledge fragments in predictable ways:

- Inside repos: issues, commits, tests each hold part of the story
- Across teams: fixes repeat because lessons are not shared
- Across sources: PROVES hardware guidance and F Prime docs are separated
- Across time: context fades when teams rotate or projects pause

---

## What It Is

Three knowledge layers, unified:

- Build knowledge: assembly, hardware, flight software, testing references
- Software architecture: F Prime architecture, ports, build, and GDS
- Operational knowledge: configs, issue reports, test results, fixes

MCP exposes this library to IDEs and agents without needing to know where the info originally lived.

---

## Where It Lives

The canonical library is the PROVES Library repository:

https://github.com/Lizo-RoadTown/PROVES_LIBRARY

The MCP server indexes this repo to serve structured queries.

---

## Source Policy

- Open source materials
- Citations and excerpts
- Reviewed before inclusion

---

## What Users Get

- A stable first layer of docs for onboarding
- A deeper layer that answers "what happened before?" and "where is the fix?"
- Search results that point to real artifacts (repo paths, tests, docs)

---

## Risk Scan Extension

Users can run a daily or per-commit risk scan in an IDE:

1. Query MCP for known risk patterns
2. Scan the repo for matches
3. Surface likely mission-critical issues with links to fixes
4. Contribute new lessons back to the library

---

## Lesson Entry Format (Citations)

```
Entry
- Observed context:
- Source citation(s):
- Related artifacts (component/repo/doc):
- Resolution notes (if documented):
- Verification reference:
```

---

## Why This Works

Teams get immediate value (risk scans and fixes) while the library grows over time and supports every mission.
