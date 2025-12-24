# PROVES Kit Agent

Agentic knowledge capture for CubeSat missions, backed by PROVES Library.

**Live site:** https://lizo-roadtown.github.io/proveskit-agent

## What is PROVES Kit Agent?

This repository hosts the portfolio site for the PROVES Kit Agent system. The live implementation and knowledge graph live in PROVES Library.

Key capabilities:

- Curator agent for dependency extraction
- Human-in-the-loop truth layer
- MCP server for graph and evidence queries
- GNN risk modeling scaffold (Proves_AI)

## Core Repos

- PROVES Library: https://github.com/Lizo-RoadTown/PROVES_LIBRARY
- Proves_AI (GNN stack): https://github.com/Lizo-RoadTown/Proves_AI

## Portfolio Structure

```
proveskit-agent/
  index.md                 # Homepage
  pages/
    about.md               # Vision and relationships
    living-library.md      # PROVES Library overview
    architecture.md        # System architecture
    technical.md           # Technical details
    developers.md          # Developer guide
    researchers.md         # Research guide
```

## Technology Stack

**Site:** Jekyll with TeXt theme
**Backend:** LangGraph agents, Neon PostgreSQL, MCP server
**ML Stack:** GraphSAGE, XGBoost, reranker (in Proves_AI)

## Local Development

```bash
bundle install
bundle exec jekyll serve
```

View at http://localhost:4000/proveskit-agent

## Relationship to FRAMES

PROVES Kit Agent shares architectural patterns with FRAMES (Framework for Research and Analytics in Mission Engineering Systems):

- FRAMES focuses on organizational risk modeling
- PROVES Kit Agent focuses on dependency capture and mission risk mitigation

FRAMES portfolio: https://lizo-roadtown.github.io/Portfolio

## Contact

Elizabeth Osborn
Cal Poly Pomona
[eosborn@cpp.edu](mailto:eosborn@cpp.edu)

## License

Portfolio content: CC-BY-NC-4.0
