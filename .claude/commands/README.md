# Pythia Cookbook Custom Agents

This directory contains specialized Claude Code agent definitions for developing and maintaining the "Ciencia de Datos Hidrometeorológicos con Python" Project Pythia Cookbook.

## How These Work

These agents are invoked conversationally when working with Claude Code:

```
You: "Review notebooks/3.Aplicaciones/3.1.ENSO.ipynb with pythia-compliance, grammar-reviewer, and flow-reviewer agents"

Claude: I'll run all three agents in parallel to review the ENSO notebook...
```

Claude Code automatically:
1. Runs the specified agents concurrently
2. Collects their detailed reports
3. Synthesizes findings into actionable improvements
4. Shows you a plan before making changes (if requested)

## Available Agents

### Content Creation

**content-creator** - Content Creator Expert
- Creates new educational Jupyter notebooks
- Follows Pythia template structure
- Ensures Spanish language and Latin American context
- Manages learning objectives and prerequisites
- Use when: Creating new notebooks from scratch

### Review & Quality Assurance

**grammar-reviewer** - Grammar & Typo Reviewer
- Reviews Spanish grammar, spelling, and technical terminology
- Checks markdown formatting and citations
- Ensures consistent Spanish technical terms
- Use when: Proofreading notebooks or fixing language issues

**flow-reviewer** - Flow & Simplicity Reviewer
- Evaluates pedagogical flow and educational clarity
- Assesses appropriate complexity for target audience
- Checks learning objectives alignment
- Reviews cognitive load and pacing
- Use when: Ensuring effective teaching progression

**data-validator** - Data Management Validator
- Validates data access methods (remote, local, generated)
- Checks file sizes against <50MB guideline
- Verifies data licensing and documentation
- Ensures reproducibility of data access
- Use when: Adding data sources or reviewing data practices

**pythia-compliance** - Pythia Standards Compliance Checker
- Validates notebook template structure
- Checks required sections (Overview, Prerequisites, Summary, etc.)
- Verifies heading hierarchy and formatting
- Ensures myst.yml TOC integration
- Use when: Final check before publishing or merging

**science-reviewer** - Scientific Accuracy Reviewer
- Validates atmospheric/climate science concepts
- Checks data analysis methodology
- Reviews visualization appropriateness
- Verifies regional context (Colombian/Latin American)
- Use when: Ensuring scientific correctness

**code-quality** - Code Quality & Reproducibility Checker
- Tests notebook executability (Restart & Run All)
- Validates dependencies and environment.yml
- Checks code style and best practices
- Ensures Binder compatibility
- Use when: Testing notebook reliability and reproducibility

**accessibility-reviewer** - Accessibility & Inclusivity Reviewer
- Checks alt text for images
- Validates colorblind-friendly visualizations
- Reviews language clarity and inclusivity
- Ensures cultural and regional appropriateness
- Use when: Making content accessible to all learners

**metadata-validator** - Metadata & Citation Validator
- Validates CITATION.cff, myst.yml, _gallery_info.yml
- Checks data source citations and attributions
- Verifies DOI and Zenodo integration
- Ensures proper licensing information
- Use when: Updating repository metadata or citations

**bilingual-coordinator** - Bilingual Content Coordinator
- Manages Spanish/English terminology consistency
- Reviews code/narrative language balance
- Validates external link language indicators
- Ensures smooth bilingual integration
- Use when: Managing bilingual technical content

## Usage Patterns

### Creating a New Notebook

Ask Claude Code to run agents in sequence:

```
You: "I need to create a new notebook about Colombian precipitation patterns.
Use the content-creator agent to help me set it up."

You: "Now review it with pythia-compliance and grammar-reviewer agents."

You: "Test the code with code-quality agent."

You: "Check the pedagogical flow with flow-reviewer agent."

You: "Final accessibility check with accessibility-reviewer agent."
```

### Reviewing an Existing Notebook

```
You: "Review notebooks/3.Aplicaciones/3.1.ENSO.ipynb with pythia-compliance agent"

You: "Run a comprehensive review of notebooks/2.acceso-datos/2.3.GFS.ipynb with
grammar-reviewer, science-reviewer, code-quality, and accessibility-reviewer agents"
```

### Pre-Publication Checklist

Before publishing, ask Claude to run all reviewers:

```
You: "Run the full pre-publication checklist on notebooks/3.Aplicaciones/3.5.QPE.ipynb:
- pythia-compliance for structure
- grammar-reviewer for language quality
- science-reviewer for scientific accuracy
- code-quality for execution
- data-validator for data practices
- accessibility-reviewer for accessibility
- metadata-validator for citations
- bilingual-coordinator for terminology consistency"
```

### Repository Maintenance

```
You: "Use metadata-validator agent to check CITATION.cff, myst.yml, and _gallery_info.yml"

You: "Run data-validator agent on all files in notebooks/data/"

You: "Review notebooks/3.Aplicaciones/3.1.ENSO.ipynb with flow-reviewer agent"
```

## Agent Priorities

### High Priority (Use Frequently)
1. **content-creator** - Creating new notebooks
2. **pythia-compliance** - Ensuring standards
3. **code-quality** - Testing execution
4. **grammar-reviewer** - Language quality

### Medium Priority (Use Regularly)
5. **flow-reviewer** - Educational effectiveness
6. **data-validator** - Data management
7. **science-reviewer** - Scientific accuracy

### Nice to Have (Use When Relevant)
8. **accessibility-reviewer** - Accessibility audit
9. **metadata-validator** - Citations/metadata
10. **bilingual-coordinator** - Bilingual coordination

## Tips for Effective Use

### 1. Iterative Review
Don't try to fix everything at once. Run reviewers iteratively:
- First pass: Structure and executability
- Second pass: Content quality and accuracy
- Third pass: Polish and accessibility

### 2. Combine Reviewers
For comprehensive review, invoke multiple agents:
```
You: "Review the notebook with pythia-compliance, code-quality, and grammar-reviewer agents"
```

### 3. Focus on Specific Issues
Be specific about what you want reviewed:
```
You: "Use grammar-reviewer agent to focus on terminology consistency"
You: "Run data-validator agent to check only the data citations"
```

### 4. Document Decisions
If a reviewer flags something you intentionally chose, document why:
```markdown
<!-- Pythia compliance note: Using custom structure here because... -->
```

## Customization

Each agent file (`.md`) can be edited to adjust:
- Review criteria
- Output format
- Severity thresholds
- Domain-specific checks

Located in: `.claude/commands/[agent-name].md`

## Contributing

To add a new agent:

1. Create `.claude/commands/your-agent.md`
2. Define role, input requirements, and review areas
3. Specify output format
4. Document in this README
5. Test with sample notebooks

## Workflow Integration

### With Git Workflow

```
You: "Before I commit, run code-quality and grammar-reviewer agents on
notebooks/3.Aplicaciones/3.1.ENSO.ipynb"

You: "Before creating PR, check all notebooks with pythia-compliance agent
and validate repository metadata with metadata-validator agent"
```

### With Binder

```
You: "Before pushing to Binder, simulate execution with code-quality agent
and check data file sizes with data-validator agent"
```

## Support

For questions about:
- **Agent functionality**: Check individual agent `.md` file
- **Pythia standards**: See https://projectpythia.org/cookbook-guide/
- **Repository structure**: See `/CLAUDE.md`

## Quick Reference

| Agent | Primary Use | Output |
|-------|-------------|--------|
| content-creator | Create notebooks | New .ipynb file |
| grammar-reviewer | Language quality | Issue list |
| flow-reviewer | Educational flow | Section analysis |
| data-validator | Data management | Data sources report |
| pythia-compliance | Structure check | Compliance report |
| science-reviewer | Scientific accuracy | Accuracy assessment |
| code-quality | Execution test | Quality report |
| accessibility-reviewer | Accessibility | A11y checklist |
| metadata-validator | Citations/metadata | Metadata report |
| bilingual-coordinator | Spanish/English | Terminology report |

---

**Remember:** These agents are tools to help maintain quality. Use your judgment on which recommendations to implement based on context and priorities.
