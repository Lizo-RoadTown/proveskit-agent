# PROVES Kit Agent

Living documentation and repo risk scanning for CubeSat teams

## Overview

This repository contains the portfolio site for **PROVES Kit Agent**, a public MCP-backed knowledge system and repo risk scan concept for university CubeSat teams.

**Live site:** https://lizo-roadtown.github.io/proveskit-agent

## What is PROVES Kit Agent?

Two linked systems:

- Living documentation library (MCP-backed, citations and excerpts only)
- VS Code risk scan extension for mission-critical issues

This repository is a public scrapbook for the concept and documentation. The working implementation will live in a separate repository.

## PROVES Kit Project

This agent supports the **PROVES Kit** multi-university collaboration developing open-source CubeSat payloads and bus systems using F'Prime.

**PROVES Kit GitHub:** https://github.com/proveskit

**Partner Universities:**
Cal Poly Pomona · Columbia University · Texas State University · Virginia Tech · Washington State University · University of Illinois · Northeastern University · Mt. San Antonio College

## Portfolio Structure

```
proveskit-agent/
|-- index.md                    # Homepage
|-- about.md                    # About the project
|-- pages/
|   |-- developers.md           # For developers
|   |-- researchers.md          # For researchers
|   |-- technical.md            # Architecture for MCP + risk scan
|   |-- component-generation.md # Archive concept page
|   `-- living-library.md       # Living documentation and risk scan
|-- demos/                      # Example workflows (planned)
`-- docs/                       # Research notes
```

## Technology Stack

**Site:** Jekyll with TeXt theme
**Library access:** MCP server + search index
**Client:** VS Code extension

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
| **Domain** | Organizational analysis | Knowledge transfer and risk sharing |
| **Problem** | Predict mission risk | Reduce repeated failures across teams |
| **Mechanism** | Structural diagnostics | MCP library + repo risk scan |

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
