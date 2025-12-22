---
layout: article
title: For Developers
permalink: /developers/
key: page-developers
aside:
  toc: true
---

[← Back to Home](/proveskit-agent/)

# PROVES Library for Developers

Whether you're building a CubeSat, contributing to the library, or learning about agentic AI systems, this page will help you get started.

---

## Quick Start

### Set Up in 15 Minutes

```bash
# 1. Clone the repository
git clone https://github.com/Lizo-RoadTown/PROVES_LIBRARY.git
cd PROVES_LIBRARY

# 2. Create virtual environment
python -m venv .venv
.venv\Scripts\activate  # Windows
# source .venv/bin/activate  # macOS/Linux

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure environment
cp .env.example .env
# Edit .env with your API keys (see below)

# 5. Initialize database
python scripts/apply_schema.py
python scripts/setup_checkpointer.py

# 6. Run the curator agent
cd curator-agent
python run_with_approval.py
```

### API Keys You'll Need

| Service | Purpose | Get it at |
|---------|---------|-----------|
| **Anthropic** | Claude AI models | [console.anthropic.com](https://console.anthropic.com/) |
| **Neon** | PostgreSQL database | [neon.tech](https://neon.tech/) |
| **LangSmith** (optional) | Tracing & debugging | [smith.langchain.com](https://smith.langchain.com/) |

**Free tiers available for all services!**

---

## Repository Structure

```
PROVES_LIBRARY/
├── curator-agent/           # The main AI agent
│   ├── src/curator/
│   │   ├── agent.py         # Curator orchestration
│   │   └── subagents/       # Extractor, Validator, Storage
│   ├── run_with_approval.py # CLI entry point
│   └── test_agent.py        # Basic tests
│
├── scripts/                 # Database utilities
│   ├── apply_schema.py      # Initialize schema
│   ├── db_connector.py      # Connection pooling
│   ├── graph_manager.py     # CRUD for nodes/edges
│   └── library_indexer.py   # Markdown processing
│
├── docs/                    # Technical documentation
│   ├── AGENTIC_ARCHITECTURE.md
│   ├── KNOWLEDGE_GRAPH_SCHEMA.md
│   └── ...
│
├── trial_docs/              # Sample documents for testing
├── archive/                 # Historical work (reference only)
│
├── GETTING_STARTED.md       # Full setup guide
├── CANON.md                 # Core design principles
└── FOLDER_STRUCTURE.md      # Detailed organization
```

---

## Common Tasks

### Run the Curator Agent

The curator agent extracts dependencies from documentation:

```bash
cd curator-agent
python run_with_approval.py
```

**What happens:**
1. Agent reads a document
2. Extractor finds dependencies
3. Validator checks quality
4. HIGH criticality items prompt for approval
5. Approved items stored to database

### Work with the Knowledge Graph

```python
from scripts.graph_manager import GraphManager

# Initialize
gm = GraphManager()

# Create a node
node_id = gm.create_node(
    name="ImuManager",
    node_type="component",
    description="Manages IMU sensor readings",
    properties={"fprime_component": True}
)

# Create a relationship
gm.create_relationship(
    source_id=node_id,
    target_id=i2c_driver_id,
    relationship_type="depends_on",
    criticality="HIGH",
    evidence="ImuManager.cpp lines 45-67"
)

# Query relationships
deps = gm.get_dependencies("ImuManager")
```

### Process a Document

```python
from scripts.library_indexer import LibraryIndexer

indexer = LibraryIndexer()

# Parse markdown with YAML frontmatter
entry = indexer.parse_file("trial_docs/fprime_i2c_driver.md")

print(f"Title: {entry.title}")
print(f"Tags: {entry.tags}")
print(f"Sources: {entry.sources}")
```

---

## How to Contribute

### 1. Add Documentation

Found useful documentation? Add it to `library/`:

```markdown
---
title: "Power System Design Guidelines"
type: guide
domain: hardware
tags: [power, battery, solar]
sources:
  - "PROVES Kit Hardware Guide v2.1"
---

## Overview
Guidelines for designing CubeSat power systems...
```

### 2. Improve the Agents

The sub-agents are in `curator-agent/src/curator/subagents/`:

- **extractor.py** — Reads docs, finds dependencies
- **validator.py** — Checks quality, finds duplicates
- **storage.py** — Saves to database

Each uses Claude with specific prompts and tools.

### 3. Extend the Schema

The knowledge graph schema is in `archive/design-docs/mcp-server/schema/`:

```sql
-- Add a new relationship type
ALTER TYPE relationship_type ADD VALUE 'validates';

-- Add a new node property
ALTER TABLE kg_nodes ADD COLUMN mission_phase text;
```

### 4. Write Tests

```python
# tests/test_extraction.py
def test_extracts_depends_on():
    """Test that depends_on relationships are extracted."""
    doc = """
    The ImuManager component requires LinuxI2cDriver
    for all sensor communications.
    """
    
    deps = extract_dependencies(doc)
    
    assert len(deps) == 1
    assert deps[0].source == "ImuManager"
    assert deps[0].target == "LinuxI2cDriver"
    assert deps[0].relationship == "depends_on"
```

---

## Understanding the Codebase

### Key Design Decisions

| Decision | Why |
|----------|-----|
| **Sub-agents as tools** | Context isolation, cost optimization |
| **Haiku for simple tasks** | 90% cheaper than Sonnet |
| **HITL for HIGH criticality** | Human oversight for mission-critical items |
| **Deferred storage** | Ensures reliable tool pairing with LangGraph |

### Core Principles (from CANON.md)

1. **Autonomous intelligence, not automation** — Give goals, not instructions
2. **Criticality is metadata, not a gate** — Store everything, filter at query time
3. **Rich context + clear goals** — Better inputs → better agent decisions
4. **Transparency at every layer** — Console, checkpoints, logs, database

### The ERV Schema

Engineering Relationship Vocabulary defines 6 relationship types:

| Type | Example |
|------|---------|
| `depends_on` | ImuManager → LinuxI2cDriver |
| `requires` | Component → Toolchain |
| `enables` | LoadSwitch → SensorPower |
| `conflicts_with` | UARTDebug ↔ RadioTX |
| `mitigates` | Watchdog → InfiniteLoop |
| `causes` | Brownout → StateCorruption |

---

## Debugging Tips

### Agent Not Running?

```bash
# Check environment variables
python -c "import os; print(os.getenv('ANTHROPIC_API_KEY', 'NOT SET'))"

# Test database connection
python scripts/db_connector.py

# Check for schema
python scripts/apply_schema.py --check
```

### LangSmith Tracing

Enable for debugging agent workflows:

```bash
# .env
LANGCHAIN_TRACING_V2=true
LANGCHAIN_API_KEY=lsv2_pt_...
```

Then visit [smith.langchain.com](https://smith.langchain.com/) to see traces.

### Common Issues

| Issue | Solution |
|-------|----------|
| "Anthropic API key invalid" | Check key starts with `sk-ant-api03-` |
| "Database connection failed" | Verify Neon connection string format |
| "LangSmith 403 error" | Use personal API key, not org-scoped |
| "No module found" | Activate virtual environment |

---

## Resources

### Documentation

- **[GETTING_STARTED.md](https://github.com/Lizo-RoadTown/PROVES_LIBRARY/blob/master/GETTING_STARTED.md)** — Full setup guide
- **[CANON.md](https://github.com/Lizo-RoadTown/PROVES_LIBRARY/blob/master/CANON.md)** — Core design principles
- **[FOLDER_STRUCTURE.md](https://github.com/Lizo-RoadTown/PROVES_LIBRARY/blob/master/FOLDER_STRUCTURE.md)** — Repository organization

### External

- **[LangGraph Documentation](https://python.langchain.com/docs/langgraph)** — Agent framework
- **[Anthropic API Docs](https://docs.anthropic.com/)** — Claude models
- **[Neon Documentation](https://neon.tech/docs)** — Serverless PostgreSQL

### CubeSat Resources

- **[F´ Framework](https://fprime.jpl.nasa.gov/)** — NASA/JPL flight software
- **[PROVES Kit](https://github.com/proveskit)** — Cal Poly CubeSat hardware
- **[PySquared](https://pysquared.org/)** — STEM flight computers

---

## Getting Help

- **GitHub Issues** — [PROVES_LIBRARY Issues](https://github.com/Lizo-RoadTown/PROVES_LIBRARY/issues)
- **Email** — [eosborn@cpp.edu](mailto:eosborn@cpp.edu)

[← Back to Home](/proveskit-agent/)
