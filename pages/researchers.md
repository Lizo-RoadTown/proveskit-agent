---
layout: article
title: For Researchers
permalink: /researchers/
key: page-researchers
---

[← Back to Home](/proveskit-agent/)

# For Researchers

How do autonomous AI agents learn to capture and preserve engineering knowledge? This project explores that question in the context of CubeSat development.

---

## What We're Studying

### The Core Problem: Knowledge Fragmentation

When student teams build satellites, they encounter problems that other teams have already solved. But that knowledge is scattered across:

- **GitHub issues** that get closed and forgotten
- **Slack threads** that scroll away
- **Graduation** of the students who learned it
- **Documentation** that drifts from the code

**Result:** Teams waste time rediscovering solutions, or worse, repeat dangerous mistakes.

### Our Approach: Agentic Knowledge Capture

We're building AI agents that:

1. **Read** technical documents and discussions
2. **Identify** reusable patterns and relationships
3. **Validate** extracted knowledge with human experts
4. **Store** entries in a queryable knowledge graph

The goal is to study whether autonomous agents can sustainably maintain a "living library" of engineering knowledge.

---

## Research Questions

### 1. Agent Accuracy and Reliability

- How accurately do LLM-based agents extract engineering relationships from unstructured text?
- What validation strategies minimize hallucination while preserving expert insights?
- How does agent confidence scoring compare to human expert agreement?

### 2. Knowledge Graph Effectiveness

- Does a structured knowledge graph improve search over traditional keyword search?
- Which relationship types (DEPENDS_ON, CONFLICTS_WITH, etc.) are most valuable for engineers?
- How do graph queries surface non-obvious dependencies?

### 3. Human-in-the-Loop Patterns

- When should agents escalate to humans vs. act autonomously?
- How does HITL approval affect knowledge quality vs. capture speed?
- What interface designs help experts review agent extractions efficiently?

### 4. Adoption and Knowledge Reuse

- Do teams actually query the library when solving problems?
- Which entry formats are most actionable for practitioners?
- How does non-attributive contribution affect participation?

### 5. Transfer Across Domains

- Can agents trained on CubeSat documentation work on other embedded systems?
- What domain-specific prompting is required for new technical areas?
- How do we measure "knowledge transfer" between projects?

---

## System Under Study

```
┌─────────────────────────────────────────────────────────────┐
│                    CURATOR AGENT SYSTEM                     │
├─────────────────────────────────────────────────────────────┤
│                                                             │
│  Documents ──▶ [Extractor Agent] ──▶ Candidate Entries     │
│                    Claude Sonnet                            │
│                         │                                   │
│                         ▼                                   │
│               [Validator Agent] ──▶ Quality Scores          │
│                    Claude Haiku                             │
│                         │                                   │
│           ┌─────────────┼─────────────┐                     │
│           ▼             ▼             ▼                     │
│       [AUTO]       [REVIEW]      [REJECT]                   │
│     Store it    Human checks   Discard it                   │
│                         │                                   │
│                         ▼                                   │
│               [Storage Agent] ──▶ Knowledge Graph           │
│                    Claude Haiku                             │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

**Technology Stack:**
- **Orchestration:** LangGraph (Python)
- **Models:** Claude Sonnet 4.5 (extraction), Haiku 3.5 (validation/storage)
- **Database:** PostgreSQL with pgvector
- **Schema:** ERV (Engineering Relationship Vocabulary)

---

## Data Sources

| Source | Type | Status |
|--------|------|--------|
| PROVES Kit documentation | Internal | ✅ Active |
| F Prime framework docs | Open source | ✅ Active |
| CubeSat design standards | Public specs | 🔄 Planned |
| Mission post-mortems | Internal | 🔄 Planned |

All extracted knowledge includes provenance (source URL, extraction date, agent version) for reproducibility.

---

## Metrics We Track

### Agent Performance

| Metric | Description |
|--------|-------------|
| **Extraction Precision** | % of extracted relationships that experts confirm as valid |
| **Extraction Recall** | % of important relationships that agents find |
| **Hallucination Rate** | % of entries that contain fabricated information |
| **Confidence Calibration** | How well agent confidence predicts actual correctness |

### Knowledge Graph Quality

| Metric | Description |
|--------|-------------|
| **Graph Coverage** | % of known components with entries |
| **Relationship Density** | Average relationships per component |
| **Stale Entry Rate** | % of entries not updated when source changes |
| **Query Success Rate** | % of user queries that return useful results |

### User Impact

| Metric | Description |
|--------|-------------|
| **Time-to-Answer** | How long users spend finding relevant knowledge |
| **Reuse Rate** | How often existing entries solve new problems |
| **Contribution Rate** | How many users add or correct entries |

---

## Experimental Design

### Comparison Conditions

1. **Baseline:** Traditional wiki + search
2. **Treatment A:** Knowledge graph without agents (manual curation)
3. **Treatment B:** Agent-curated knowledge graph (this project)

### Hypotheses

- **H1:** Agent-curated entries have ≥80% precision vs. expert agreement
- **H2:** Graph queries return relevant results in <5 seconds
- **H3:** Teams using the library spend 30% less time on repeated problems

---

## Open Questions

We're actively exploring:

1. **Multi-agent coordination:** How should specialized agents divide work?
2. **Confidence thresholds:** What score should trigger human review?
3. **Schema evolution:** How should the knowledge graph adapt to new domains?
4. **Privacy patterns:** Can we extract lessons without exposing sensitive designs?

---

## Publications and Presentations

*Coming soon — this is an active research project.*

---

## Collaboration

We welcome collaboration from:

- **AI/ML researchers** interested in agentic systems and RAG
- **Knowledge management** researchers studying organizational learning
- **Aerospace engineers** working on similar documentation challenges
- **HCI researchers** studying human-AI collaboration

---

## Contact

**Elizabeth Osborn** | Cal Poly Pomona  
[eosborn@cpp.edu](mailto:eosborn@cpp.edu)

---

## Acknowledgments

This research is part of the PROVES (Polysat Rover Observational Vehicle for Exploration of Space) project at Cal Poly Pomona, supported by NASA and NSF educational initiatives.

---

*Updated: 2025*
