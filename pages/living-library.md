---
layout: article
title: Living Documentation Library
permalink: /living-library/
key: page-living-library
---

# Living Documentation Library

The PROVES Kit Agent now includes a deeper layer of "living" documentation that students can interrogate beyond the first-layer docs.

The core idea is simple: the structure owns outcomes, not individuals. We log where the fix lives, not who caused it.

---

## What It Is

A shared, continuously updated library that combines:

- PROVES Kit docs and flight software guides
- F'Prime documentation and patterns
- Lessons learned with links to source artifacts
- Risk patterns that can be checked against a repo

The library is exposed through an MCP server so any AI system in VS Code can query it.

---

## What Students Get

- A stable first layer of docs for onboarding
- A deeper layer that answers "what happened before?" and "where is the fix?"
- Search results that point to real artifacts (repo paths, tests, components, or docs)

---

## Risk Scan Extension

Students can run a daily or per-commit risk scan in VS Code:

1. The extension queries the MCP library for known risk patterns.
2. It scans the repo for matches.
3. It surfaces likely mission-critical issues with links to fixes.
4. It can contribute new patterns or lessons back to the library.

No names. No blame. Only system knowledge.

---

## Lesson Entry Format (No Blame)

```
Issue
- What happened:
- Where it lives (component/repo/doc):
- Likely knowledge location (file/test/doc/role):
- Fix summary:
- How to verify:
```

---

## Why This Works

Students get immediate value (risk scans and fixes), while the library grows over time and supports every team.

This makes knowledge sharing safer and more useful, which is the best incentive to participate.
