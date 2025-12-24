---
layout: article
title: About
permalink: /about/
key: page-about
---

# About PROVES Kit Agent

## The Vision

Enable university CubeSat teams to develop flight-qualified F'Prime software faster and more reliably through intelligent AI assistance.

---

## The Problem

### F'Prime Development is Complex

NASA's F'Prime framework provides powerful abstractions for flight software, but mastering it requires:

- Understanding component-based architecture
- Learning F'Prime Prime (FPP) modeling language
- Following specific C++ patterns for flight safety
- Maintaining extensive interface documentation
- Writing comprehensive test suites

### University Teams Face Unique Challenges

**Student rotation:** Knowledge walks out the door every semester as students graduate.

**Limited prior experience:** Most students have never written flight software before joining the team.

**Time constraints:** Deliver NASA-contracted missions while taking full course loads.

**High stakes:** Flight software failures can destroy multi-million dollar missions.

---

## The Solution

### AI Agents for F'Prime

An intelligent assistant that:

1. **Accelerates development** — Generate component boilerplate from requirements
2. **Maintains quality** — Review code for F'Prime pattern compliance
3. **Captures knowledge** — Auto-document design decisions and interfaces
4. **Supports learning** — Teach F'Prime patterns through interaction

### Human-in-the-Loop

The agent **assists**, not replaces, engineers:

- Generates initial code for human review
- Suggests improvements, doesn't autonomously commit
- Requires validation before flight qualification
- Teaches patterns through examples

---

## The Approach

### Multi-Agent Architecture

Specialized agents for different tasks:

- **Requirement Analyzer** — Extract component specs from natural language
- **Component Generator** — Create FPP definitions and C++ scaffolds
- **Documentation Agent** — Draft ICDs, tables, and specifications
- **Review Agent** — Validate F'Prime patterns and suggest improvements

### Domain Expertise

Unlike general code assistants, PROVES Kit Agent is specialized:

- Trained on F'Prime documentation and patterns
- References real PROVES Kit components
- Understands flight software constraints
- Validates against F'Prime tooling

### Research Foundation

Built on research in:

- AI for code generation
- Knowledge transfer in engineering teams
- Human-AI collaboration patterns
- Domain-specific language models

---

## The Team

### Project Lead

**Elizabeth Osborn** | Cal Poly Pomona
- PhD candidate in systems engineering
- PROVES Kit core team member
- FRAMES research platform developer

### Collaborators

**PROVES Kit Partner Universities:**
- Cal Poly Pomona (Lead)
- Columbia University
- Texas State University
- Virginia Tech
- Washington State University
- University of Illinois
- Northeastern University
- Mt. San Antonio College

### Advisors

- F'Prime community at NASA JPL
- Multi-university space mission teams
- AI for software engineering researchers

---

## Technology

### Agent Platform

**Language Model:** Claude 3.5 Sonnet (Anthropic)
- Strong code generation capabilities
- Excellent context handling for large components
- Reliable structured outputs

**Architecture:** Multi-agent orchestration
- Shared knowledge base of F'Prime patterns
- Coordinated workflows across agents
- Human approval gates at critical steps

### F'Prime Integration

**Tools:**
- FPP parser for component analysis
- F'Prime autocoder for code generation
- `fprime-util` for build/test validation

**Validation:**
- Syntax checking with `fpp-check`
- Build verification
- Pattern conformance review

---

## Research Goals

### Empirical Questions

1. **Effectiveness:** Does the agent actually accelerate F'Prime development?
2. **Quality:** Is generated code comparable to human-written code?
3. **Learning:** Do developers internalize F'Prime patterns faster?
4. **Trust:** When do developers trust vs. override agent suggestions?

### Methodological Contributions

- Validation frameworks for AI-generated flight software
- Prompt engineering for domain-specific code generation
- Human-in-the-loop architectures for safety-critical systems

### Natural Experiment

University space programs provide ideal research conditions:

- **Real stakes** — NASA missions with actual deliverables
- **Observable teams** — Small enough to fully instrument
- **Student rotation** — Natural knowledge loss experiments
- **Multi-site** — Compare across universities

---

## Relationship to FRAMES

PROVES Kit Agent extends ideas from **FRAMES** (Framework for Research & Analytics in Mission Engineering Systems):

### Shared Architecture

Both use multi-agent AI systems with specialized agents coordinated by an orchestrator.

### Different Problem Domains

**FRAMES:**
- Analyzes organizational structure
- Predicts mission risk from team interfaces
- Supports program administrators

**PROVES Kit Agent:**
- Generates flight software code
- Accelerates F'Prime development
- Supports mission engineers

### Complementary Research

**Integration potential:**
- FRAMES identifies knowledge vulnerabilities → Agent prioritizes documentation
- Agent captures technical knowledge → FRAMES maps knowledge distribution
- Combined organizational + technical mission success prediction

[Learn more about FRAMES →](https://lizo-roadtown.github.io/Portfolio/)

---

## Status & Roadmap

### Current Status (Dec 2024)

**✓ Completed:**
- Agent architecture design
- F'Prime pattern knowledge base
- Component generation prototypes
- Portfolio documentation site

**⚙ In Progress:**
- Agent orchestrator implementation
- F'Prime tooling integration
- Initial developer testing with PROVES Kit teams

**📋 Planned:**
- VSCode extension
- Documentation generation
- Code review automation
- Public release

### Future Directions

**Technical:**
- Topology design assistance
- Integration test generation
- Hardware-in-loop test support

**Research:**
- Controlled developer studies
- Long-term mission tracking
- Cross-framework generalization (ROS, etc.)

---

## Get Involved

### For Developers

Try the agent on your F'Prime project:
- [Getting Started →](/proveskit-agent/developers/)
- Provide feedback on generated components
- Share effective prompt patterns

### For Researchers

Collaborate on research questions:
- AI for code generation
- Knowledge transfer in engineering
- Human-AI collaboration
- [Research Opportunities →](/proveskit-agent/researchers/)

### For Educators

Use in CubeSat programs:
- Accelerate student onboarding
- Teach F'Prime patterns
- Capture institutional knowledge

---

## Publications

**Forthcoming:**
- Agent architecture paper (target: ICSE 2025)
- Developer study results (target: FSE 2025)
- Educational impact (target: ASEE 2025)

**Related work:**
- FRAMES organizational risk prediction
- PROVES Kit mission documentation

---

## Open Source

**Commitment:** The agent system will be open source upon stable release.

**Current access:** Available to PROVES Kit collaborators for research.

**Future release:** Public repository with documentation and examples.

---

## Contact

**Questions? Collaboration?**

Elizabeth Osborn
eosborn@cpp.edu

**Related projects:**
- [FRAMES Portfolio](https://lizo-roadtown.github.io/Portfolio/)
- [PROVES Kit GitHub](https://github.com/proveskit)
- [F'Prime Documentation](https://fprime.jpl.nasa.gov/)

---

## Acknowledgments

**NASA JPL** — F'Prime framework and community support

**PROVES Kit Partner Universities** — Multi-site collaboration and testing

**Anthropic** — Claude language model platform

**Students** — Past and present PROVES Kit team members who provide feedback and use cases

**TeXt Theme** — Jekyll theme by Tian Qi
