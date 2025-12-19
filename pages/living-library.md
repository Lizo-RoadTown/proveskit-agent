---
layout: article
title: Living Documentation Library
permalink: /living-library/
key: page-living-library
---

# Living Documentation Library

The PROVES Kit Agent now includes a deeper layer of "living" documentation that users can interrogate beyond the first-layer docs.

The core idea is simple: the structure owns outcomes, not individuals. The library stores citations and excerpts, not attribution or fault.

---

## The Fragmentation Problem

Knowledge is fragmented in predictable ways:

- **Inside repos**: issues, commits, and tests each hold part of the story.
- **Across teams**: the same failures repeat because fixes are not shared.
- **Across sources**: PROVES hardware guidance, F Prime architecture, and ops fixes are separated.
- **Across time**: context fades when teams rotate or projects pause.

The library is built to make those fragments interrogatable as one system.

---

## What It Is

Think of it as three types of knowledge, unified:

- **Build knowledge**: assembly, hardware, flight software, and testing references
- **Software architecture knowledge**: F Prime architecture, ports, build, and GDS
- **Operational knowledge**: configs, test results, issue reports, and fixes

The library is exposed through an MCP server so any AI system in IDEs can query it without needing to know where the information originally lived.

---

## Where the Library Lives

The canonical library is an open source repository that stores reviewed entries in plain text (Markdown with small metadata blocks).

The MCP server builds its search index from that repo.

The implementation will live in its own repository (TBD), separate from this scrapbook site.

---

## Source Policy

- Open source materials only
- Citations and excerpts only
- Reviewed before inclusion

This keeps the library open, verifiable, and safe to share.

---

## What Users Get

- A stable first layer of docs for onboarding
- A deeper layer that answers "what happened before?" and "where is the fix?"
- Search results that point to real artifacts (repo paths, tests, components, or docs)

---

## Risk Scan Extension

Users can run a daily or per-commit risk scan in an IDE:

1. The extension queries the MCP library for known risk patterns.
2. It scans the repo for matches.
3. It surfaces likely mission-critical issues with links to fixes.
4. It can contribute new patterns or lessons back to the library.

No attribution. Only cited knowledge.

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

Users get immediate value (risk scans and fixes), while the library grows over time and supports every team.

This makes knowledge sharing safer and more useful, which is the best incentive to participate.
