---
layout: article
title: For Researchers
permalink: /researchers/
key: page-researchers
---

# PROVES Kit Agent for Researchers

If you study AI for software engineering, knowledge transfer in engineering teams, or human-AI collaboration, the PROVES Kit Agent offers research opportunities.

---

## Research Questions

### 1. AI-Assisted Code Generation

**Core question:** Does AI-generated F'Prime code accelerate development and maintain quality?

**Metrics:**
- Time to functional component (human vs. AI-assisted)
- Defect rates in generated code
- Code review findings (human vs. AI-generated)
- Test coverage of generated vs. human-written code

**Experimental design:**
- Within-subjects: Same developer, some components AI-assisted, some manual
- Between-subjects: AI-assisted team vs. control team
- Natural experiment: Track PROVES Kit development over time

### 2. Knowledge Transfer & Onboarding

**Core question:** Can AI agents reduce onboarding time for new F'Prime developers?

**Metrics:**
- Time to first merged component
- Number of mentor interventions needed
- Confidence ratings in F'Prime patterns
- Knowledge retention after rotation

**Context:** University CubeSat programs have inherent knowledge transfer challenges due to student rotation—ideal natural experiment.

### 3. Human-AI Collaboration Patterns

**Core question:** How do developers interact with AI agents during flight software development?

**Observable behaviors:**
- When do developers trust agent suggestions?
- What triggers manual override?
- How do review patterns differ?
- What prompts produce best results?

**Data sources:**
- Agent interaction logs
- Git commit patterns
- Code review discussions
- Developer interviews

### 4. Domain-Specific AI Effectiveness

**Core question:** Does specialization in F'Prime improve agent performance vs. general-purpose code assistants?

**Comparison:**
- PROVES Kit Agent (F'Prime-specialized) vs. GitHub Copilot (general)
- Task: Generate identical components
- Evaluate: Correctness, adherence to F'Prime patterns, completeness

---

## Research Methodology

### Data Collection

**Agent telemetry:**
- User prompts and requirements
- Generated outputs (code, docs, reviews)
- Edit distance from generated to final code
- Acceptance/rejection of suggestions
- Time spent per task

**Developer surveys:**
- Perceived usefulness
- Trust in generated code
- Workflow changes
- Learning outcomes

**Code analysis:**
- Defect density (AI vs. human)
- Pattern conformance (F'Prime style)
- Documentation quality
- Test coverage

**Git history:**
- Commit frequency
- Churn (lines changed post-generation)
- Review cycles
- Time to merge

### Experimental Settings

**PROVES Kit missions:**
- Multiple university teams using the agent
- Varied experience levels (novice to expert F'Prime developers)
- Real flight software with NASA deliverables
- Natural student rotation cycles

**Controlled studies:**
- Lab tasks: Generate standard components with/without agent
- Onboarding experiments: New students with/without agent support
- Code review studies: Reviewers blind to generation method

### IRB Considerations

**Human subjects:**
- Student developers using the agent
- Informed consent for data collection
- Anonymization of individual performance
- Opt-out from research participation

**Data privacy:**
- No proprietary mission data in publications
- Code samples reviewed for ITAR/EAR compliance
- Aggregated metrics only in papers

---

## Theoretical Frameworks

### 1. Simon's Bounded Rationality

**Application:** Developers have limited cognitive capacity for F'Prime's complexity.

**Hypothesis:** AI agents extend developer rationality by managing boilerplate, allowing focus on mission-critical logic.

**Measurement:**
- Cognitive load surveys during development
- Error rates in critical vs. boilerplate code
- Time allocation (creative vs. routine tasks)

### 2. Distributed Cognition

**Application:** Development is distributed across human developers, AI agents, and F'Prime tooling.

**Hypothesis:** Effective human-AI teams leverage complementary strengths—humans for judgment, AI for pattern application.

**Measurement:**
- Task allocation (what humans do vs. what agents do)
- Coordination overhead (time reviewing/correcting AI)
- Emergent workflow patterns

### 3. Learning Transfer

**Application:** Agent-assisted development teaches F'Prime patterns.

**Hypothesis:** Developers using the agent internalize patterns faster than pure documentation study.

**Measurement:**
- Pre/post knowledge tests
- Unaided performance after agent use
- Pattern recognition in novel contexts

---

## Expected Contributions

### Empirical Findings

**Quantitative:**
- Development time reduction (X% faster with agent)
- Defect rates (agent vs. human-written code)
- Onboarding time (days to productivity)
- Knowledge retention after rotation

**Qualitative:**
- Developer trust calibration
- Effective prompting strategies
- Workflow integration patterns
- Failure modes and limitations

### Methodological Contributions

**AI for domain-specific engineering:**
- Prompt engineering for flight software
- Validation strategies for generated code
- Human-in-the-loop architectures
- Knowledge base construction (F'Prime patterns)

**Natural experiments in software engineering:**
- Student rotation as controlled knowledge loss
- Multi-team comparison across universities
- Longitudinal tracking of mission success

### Theoretical Insights

**Human-AI collaboration:**
- When do developers trust AI code generators?
- What makes domain-specific AI more effective?
- How to design agents that teach, not just automate?

**Knowledge transfer:**
- Can AI mitigate institutional knowledge loss?
- What forms of tacit knowledge resist AI capture?
- How do teams adapt to AI-assisted workflows?

---

## Validation & Rigor

### Threats to Validity

**Internal validity:**
- Developer skill variance → Pair matching, random assignment
- Learning effects → Counterbalance AI vs. manual tasks
- Hawthorne effect → Long-term deployment, not just experiments

**External validity:**
- PROVES Kit specific → Replicate with other F'Prime missions
- University context → Compare with industry teams
- F'Prime specific → Test with other frameworks (ROS, etc.)

**Construct validity:**
- Measuring "code quality" → Multiple metrics (defects, coverage, review time)
- Measuring "onboarding" → Defined milestones, not just time
- Measuring "trust" → Behavioral proxies, not just surveys

### Baseline Comparisons

**Agent vs. manual development:**
- Same developers, different tasks
- Time-matched comparisons

**Agent vs. general AI assistants:**
- GitHub Copilot, ChatGPT baseline
- Task: Generate identical F'Prime component

**Current team vs. historical:**
- Compare PROVES Kit teams using agent to past teams without
- Control for mission complexity

---

## Publications & Dissemination

### Target Venues

**Software engineering:**
- ICSE (International Conference on Software Engineering)
- FSE (Foundations of Software Engineering)
- ASE (Automated Software Engineering)

**AI for code:**
- NeurIPS Workshop on ML for Systems
- ICLR Workshop on LLMs for Code

**Engineering education:**
- ASEE (American Society for Engineering Education)
- FIE (Frontiers in Education)

**Human-AI interaction:**
- CHI (Computer-Human Interaction)
- CSCW (Computer-Supported Cooperative Work)

### Research Outputs

**Datasets:**
- Annotated F'Prime component corpus
- Agent interaction logs (anonymized)
- Code evolution traces (git histories)

**Artifacts:**
- Agent system (open source)
- Prompt library for F'Prime
- Evaluation benchmarks

**Case studies:**
- PROVES Kit mission development trajectories
- Developer onboarding narratives
- Failure mode analyses

---

## Collaboration Opportunities

### Current Collaborations

**PROVES Kit partner universities:**
- Multi-site data collection
- Cross-team comparisons
- Shared evaluation metrics

**F'Prime community:**
- NASA JPL feedback on agent patterns
- Industry F'Prime users (comparison to university)

### Open Collaboration

**Seeking collaborators for:**
- **AI/ML researchers:** Improving agent architectures, prompt optimization
- **Software engineering researchers:** Code quality metrics, developer studies
- **HCI researchers:** Human-AI interaction patterns, trust calibration
- **Education researchers:** Learning outcomes, knowledge transfer

**Available resources:**
- Agent system access for research
- PROVES Kit mission data (with permissions)
- F'Prime pattern corpus

---

## Ethical Considerations

### Responsible AI in Safety-Critical Systems

**Concerns:**
- Flight software errors can destroy missions
- AI-generated code lacks accountability
- Over-reliance on AI may deskill developers

**Mitigations:**
- Human review mandatory for all generated code
- Agent presents suggestions, not autonomous commits
- Emphasize agent as learning tool, not replacement

### Impact on Engineering Workforce

**Concerns:**
- Does AI reduce need for human engineers?
- What skills become obsolete?
- How to maintain expertise?

**Perspective:**
- Agent handles boilerplate, elevates humans to system design
- Creates new skill: effective AI collaboration
- Frees cognitive capacity for mission-critical decisions

### Data Privacy & IP

**Concerns:**
- Proprietary mission data in training/prompts
- ITAR-controlled flight software

**Policies:**
- No mission-specific data in model training
- Agent uses only public F'Prime documentation
- Code examples scrubbed of sensitive info

---

## Relationship to FRAMES

### Shared Research Themes

Both PROVES Kit Agent and **FRAMES** explore:

| Theme | FRAMES | PROVES Kit Agent |
|-------|--------|------------------|
| **Knowledge transfer** | Organizational knowledge in team transitions | Technical knowledge in codebase |
| **AI for engineering** | Predict mission risk from structure | Generate flight software components |
| **University space missions** | Multi-university research platform | PROVES Kit collaboration |
| **Natural experiments** | Student rotation as knowledge loss | Same rotation as onboarding challenge |

### Complementary Insights

**FRAMES** predicts *organizational* vulnerabilities.
**PROVES Kit Agent** addresses *technical* knowledge transfer.

**Integration potential:**
- FRAMES identifies high-risk interfaces → Agent prioritizes documentation
- Agent captures design rationale → FRAMES maps knowledge distribution
- Combined: Organizational + technical mission success prediction

---

## Getting Started

### For PhD Students

**Potential dissertation topics:**
- AI-assisted flight software engineering
- Knowledge transfer in university space programs
- Human-AI collaboration in safety-critical systems
- Domain-specific code generation evaluation

**Resources:**
- Access to agent system and logs
- PROVES Kit mission data (IRB approval)
- Multi-university collaboration network

### For Faculty

**Research grants:**
- NSF CISE (AI for code, software engineering)
- NASA STTR/SBIR (Flight software tools)
- ASEE (Engineering education innovation)

**Student projects:**
- Masters theses on agent evaluation
- Undergraduate capstones on prompt engineering
- REU summer projects on data analysis

### For Industry Researchers

**Technology transfer:**
- Agent architecture for proprietary frameworks
- Validation methods for generated code
- Human-in-the-loop best practices

**Collaboration:**
- Benchmark agent on industry F'Prime missions
- Compare university vs. professional developers
- Joint publications on AI for aerospace

---

## Contact

**Research collaboration:**
Elizabeth Osborn | [eosborn@cpp.edu](mailto:eosborn@cpp.edu)

**Related research:**
- [FRAMES Research Platform](https://lizo-roadtown.github.io/Portfolio/researchers/)
- [PROVES Kit](https://github.com/proveskit)
- [F'Prime Community](https://github.com/nasa/fprime)

---

## Resources

**Agent documentation:**
- [Technical Architecture →](/proveskit-agent/technical/)
- [Component Generation →](/proveskit-agent/component-generation/)

**Research methods:**
- Multi-site case study protocols
- IRB templates for developer studies
- Data collection instruments

**Publications:**
- Forthcoming papers (preprints TBD)
- Conference presentations
- Workshop proceedings
