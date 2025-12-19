# PROVES Kit Agent

Living documentation and repo risk scanning

## Overview

This repository contains the portfolio site for **PROVES Kit Agent**, an open source MCP-backed knowledge system and repo risk scan concept.

**Live site:** https://lizo-roadtown.github.io/proveskit-agent

## What is PROVES Kit Agent?

Two linked systems:

- Living documentation library (MCP-backed, citations and excerpts only)
- IDE risk scan extension for mission-critical issues

This repository is an open source scrapbook for the concept and documentation. The working implementation will live in a separate repository.

## Core Sources

**Build knowledge**
- PROVES Kit documentation: https://docs.proveskit.space/en/latest/

**Software architecture knowledge**
- F Prime documentation: https://fprime.jpl.nasa.gov/latest/docs/

**Operational knowledge**
- Open source repos (citations and excerpts only)

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
**Client:** IDE extension

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
- Anthropic for Claude
- TeXt theme by Tian Qi
