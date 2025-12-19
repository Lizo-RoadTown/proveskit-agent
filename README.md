# PROVES Kit Agent

Agentic AI for F'Prime Flight Software Development

## Overview

This repository contains the portfolio site for **PROVES Kit Agent**, an intelligent assistant system designed to support CubeSat mission engineers working with NASA's F'Prime flight software framework.

**Live site:** https://lizo-roadtown.github.io/proveskit-agent

## What is PROVES Kit Agent?

An AI agent system that helps F'Prime developers:

- Generate F'Prime components from natural language requirements
- Auto-draft interface control documents and command/telemetry tables
- Review code for F'Prime pattern compliance
- Capture design knowledge for team transitions
- Provide a living documentation library and repo risk scans via MCP and VS Code

## PROVES Kit Project

This agent supports the **PROVES Kit** multi-university collaboration developing open-source CubeSat payloads and bus systems using F'Prime.

**PROVES Kit GitHub:** https://github.com/proveskit

**Partner Universities:**
Cal Poly Pomona · Columbia University · Texas State University · Virginia Tech · Washington State University · University of Illinois · Northeastern University · Mt. San Antonio College

## Portfolio Structure

```
proveskit-agent/
|-- index.md                    # Homepage
|-- pages/
|   |-- developers.md           # For F'Prime developers
|   |-- researchers.md          # For AI/SE researchers
|   |-- technical.md            # Agent architecture
|   |-- component-generation.md # Component generation details
|   |-- documentation.md        # Documentation capabilities
|   |-- code-review.md          # Code review features
|   `-- living-library.md       # Living documentation and risk scan
|-- demos/                      # Example workflows (planned)
`-- docs/                       # Technical documentation (planned)
```

## Technology Stack

**Site:** Jekyll with TeXt theme
**Agent:** Claude 3.5 Sonnet (Anthropic)
**Integration:** F'Prime autocoding toolchain

## Local Development

### Prerequisites

- Ruby 2.7+
- Bundler

### Setup

```bash
# Install dependencies
bundle install

# Run local server
bundle exec jekyll serve

# View at http://localhost:4000/proveskit-agent
```

### Build

```bash
bundle exec jekyll build
```

## Relationship to FRAMES

PROVES Kit Agent shares architectural patterns with **FRAMES** (Framework for Research & Analytics in Mission Engineering Systems):

| | FRAMES | PROVES Kit Agent |
|---|--------|------------------|
| **Domain** | Organizational analysis | Flight software development |
| **Problem** | Predict mission risk | Accelerate F'Prime workflows |
| **Agents** | Map vulnerabilities | Generate components, docs |

**FRAMES Portfolio:** https://lizo-roadtown.github.io/Portfolio

## Contributing

This portfolio is actively being developed. Contributions welcome:

- Documentation improvements
- Example workflows
- Use case studies
- Research findings

## Contact

**Elizabeth Osborn**
Cal Poly Pomona
eosborn@cpp.edu

## License

Portfolio content: CC-BY-NC-4.0
Agent code: TBD (will be open source)

## Acknowledgments

- NASA JPL for F'Prime
- PROVES Kit partner universities
- Anthropic for Claude
- TeXt theme by Tian Qi
