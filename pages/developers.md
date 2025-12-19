---
layout: article
title: For Developers
permalink: /developers/
key: page-developers
---

# PROVES Kit Agent for F'Prime Developers

If you're building CubeSat flight software with F'Prime, the PROVES Kit Agent can accelerate your development workflow.

---

## Quick Start

### Component Generation

Describe what you need in natural language:

**Example:**
> "Create a temperature sensor component that reads telemetry every 5 seconds, has a command to trigger immediate reading, and emits an event when temperature exceeds threshold."

**Agent generates:**
- `.fpp` component definition with ports, commands, telemetry, events
- C++ implementation scaffold with TODO markers
- Unit test framework
- Component documentation

### Documentation Support

Point the agent at your component:

**Agent drafts:**
- Interface Control Document (ICD)
- Command dictionary
- Telemetry table
- Event catalog

### Code Review

Submit your component for review:

**Agent checks:**
- Port connections and types
- F'Prime coding patterns
- Thread safety in handlers
- Missing documentation

---

## Workflow Integration

### 1. Requirements to Component

```bash
# Describe your component
agent generate-component "Temperature monitor with threshold alerts"

# Review generated .fpp
# Edit C++ implementation
# Run fprime-util build
```

### 2. Component to Documentation

```bash
# Generate docs from component
agent document TempSensorComponent.fpp

# Review and refine
# Commit to repository
```

### 3. Pre-Commit Review

```bash
# Before committing
agent review TempSensorComponent.cpp

# Address findings
# Re-run review
```

### 4. Daily Risk Scan (VS Code Extension)

```bash
# Run daily scan from VS Code
# Extension queries MCP library for risk patterns
# Reports likely mission-critical issues with fixes
```

### 5. Living Documentation Library

Use the MCP-backed library to search past lessons and fixes:

- Query by component name or subsystem
- Follow links to code, docs, and tests
- Reuse verified fixes and validation steps

[Living Documentation Library](https://lizo-roadtown.github.io/proveskit-agent/living-library/)

---

## Common Use Cases

### New Component Development

**Scenario:** You need a new component for payload data handling.

**Agent assists:**
1. Draft component specification from requirements
2. Generate `.fpp` definition
3. Scaffold C++ implementation
4. Create unit test template
5. Draft interface documentation

### Topology Design

**Scenario:** Connecting components in deployment topology.

**Agent assists:**
1. Suggest port connections based on data flow
2. Validate connection types
3. Identify missing connections
4. Generate topology documentation

### Onboarding New Developers

**Scenario:** New team member needs to understand existing components.

**Agent assists:**
1. Explain component purpose and design
2. Identify key interfaces and dependencies
3. Suggest where to start modifications
4. Point to relevant F'Prime documentation

### Documentation Maintenance

**Scenario:** Component changed, docs are out of sync.

**Agent assists:**
1. Detect changes in component definition
2. Update command/telemetry tables
3. Regenerate interface documentation
4. Flag breaking changes

### Risk Scan and Lessons

**Scenario:** You want to avoid mission-critical regressions.

**Agent assists:**
1. Pull risk patterns from the MCP library
2. Scan the repo for matches
3. Link to verified fixes and tests
4. Publish new patterns when a fix is confirmed

---

## What the Agent Does NOT Do

**Important limitations:**

- **No flight certification** — Agent-generated code requires human review and testing
- **No autonomous deployment** — All generated code must be validated before flight
- **No hardware integration** — Agent doesn't configure BSP or hardware drivers
- **No mission-critical decisions** — Design choices require human oversight

The agent is a **development assistant**, not a replacement for engineering judgment.

---

## Best Practices

### 1. Iterative Refinement

Don't expect perfect output first try:
- Generate initial component
- Review and identify issues
- Refine requirements and regenerate
- Iterate until satisfactory

### 2. Human-in-the-Loop

Always review agent output:
- Verify port connections make sense
- Check command/telemetry definitions
- Validate event logic
- Review generated tests

### 3. Version Control

Commit agent-generated code separately:
- Initial generation → commit
- Human refinements → separate commit
- Makes it clear what's generated vs. manual

### 4. Documentation First

Start with clear requirements:
- What does the component do?
- What are the interfaces?
- What are the edge cases?

Better requirements → better agent output.

---

## F'Prime Resources

**Official Documentation:**
- [F'Prime User Manual](https://fprime.jpl.nasa.gov/devel/docs/user-manual/framework)
- [F'Prime Tutorials](https://fprime.jpl.nasa.gov/devel/docs/tutorials/)
- [Component Development Guide](https://fprime.jpl.nasa.gov/devel/docs/design/component-design.html)

**PROVES Kit:**
- [PROVES Kit GitHub](https://github.com/proveskit)
- Component examples and templates

---

## Getting Help

**Agent Issues:**
- File issues on the agent repository
- Include component specifications and error messages

**F'Prime Questions:**
- [F'Prime Community Forum](https://github.com/nasa/fprime/discussions)
- PROVES Kit Slack (for collaborators)

**PROVES Kit:**
- [GitHub Issues](https://github.com/proveskit)
- Contact team leads at partner universities

---

## Next Steps

Explore specific agent capabilities:

- [Component Generation →](/proveskit-agent/component-generation/)
- [Documentation Support →](/proveskit-agent/documentation/)
- [Code Review →](/proveskit-agent/code-review/)
- [Technical Architecture →](/proveskit-agent/technical/)
