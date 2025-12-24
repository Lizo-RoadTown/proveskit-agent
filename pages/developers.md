---
layout: article
title: For Developers
permalink: /developers/
key: page-developers
---

# For Developers

If you build CubeSat flight software or documentation, PROVES Kit Agent helps you capture dependencies and query proven fixes through the MCP interface.

---

## Quick Start (PROVES Library)

1) Follow the setup guide: https://github.com/Lizo-RoadTown/PROVES_LIBRARY/blob/master/GETTING_STARTED.md
2) Run the curator agent with human review:

```bash
cd PROVES_LIBRARY\curator-agent
python run_with_approval.py
```

3) Track progress and verify runs:

```bash
python view_progress.py
python check_environment.py
```

---

## Use the MCP Server

Once MCP is configured, you can query the knowledge graph and docs from tools:

- VS Code extensions
- CLI utilities
- Custom agents and scripts

MCP setup guide:
https://github.com/Lizo-RoadTown/PROVES_LIBRARY/blob/master/docs/MCP_SETUP_GUIDE.md

---

## Contributing New Sources

- Add new documentation URLs to the curator maps
- Run incremental extraction with `daily_extraction.py`
- Review staged data and promote verified entries

---

## What This Enables for Teams

- Detect hidden dependencies before integration
- Trace evidence for every claim
- Share fixes across universities without manual documentation
