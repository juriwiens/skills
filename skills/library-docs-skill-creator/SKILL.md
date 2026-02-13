---
name: library-docs-skill-creator
description: Automated workflow for creating library documentation skills by researching GitHub repositories and generating structured skill files. Use this skill when the user wants to create a new skill for a library or framework, needs to research a library's documentation structure, or wants to generate a skill file that provides comprehensive context through official code, documentation, and examples.
---

# Library Documentation Skill Creator

This skill automates the creation of library documentation skills by researching official GitHub repositories and generating structured skill files following established patterns.

## Overview

This skill helps create library documentation skills. It automates:

1. **Research**: Discovering official repositories, documentation, and examples
2. **Organization**: Structuring findings into a standardized skill format
3. **Generation**: Creating a complete skill file ready for use

## Quick Start

When the user asks to create a skill for a library:

1. **Identify the library**: Get the library name or GitHub URL
2. **Research sources**: Use Task tool (Explore agent) to discover repositories, documentation structure, and examples
3. **Review findings**: Present discovered resources to the user for confirmation
4. **Generate skill**: Use the template from `references/skill_template.md`
5. **Customize**: Add library-specific sections based on documentation structure

## Research Process

Use the Task tool with `subagent_type=Explore` to adaptively explore the library's GitHub repositories. This handles any repository structure, including:

- Non-standard directory layouts
- Multi-language documentation
- Complex monorepo structures
- Documentation on external sites
- Nested or unconventional organizations

For detailed guidance on what to look for during research, see [references/research_guide.md](references/research_guide.md).

## Skill Structure

Generated skills follow this standard structure:

### 1. Frontmatter

```yaml
---
name: library-name
description: Provides comprehensive context for developing with [Library] by having access to the codebase, official documentation, and examples
---
```

### 2. Source Repositories

List of GitHub repositories with `.repos/` directory instructions.

Create a `.repos/.gitignore` file with self-contained ignore rules:

```
*
!.gitignore
```

This pattern keeps the `.repos/` directory self-contained - it manages its own ignoring, the skill root stays clean, and the directory is tracked via the .gitignore file itself.

### 3. Important Guidelines (Standard)

Three key guidelines for all library skills:

- Prefer checking virtual environment first for code sources
- Keep repositories up-to-date
- Explore all relevant sources (code, docs, examples)

### 4. Overview Section

Links to key starting files (README, llms.txt, index.md, etc.)

### 5. Library-Specific Sections

Organized by the library's main use cases and documentation structure

Examples:

- Tutorial sections for learning paths
- Advanced topics for complex features
- Examples directory references
- Template repositories for production patterns

### 6. Documentation Structure

Summary of how documentation is organized

## Template Usage

Use `references/skill_template.md` as the base template. It contains:

- Standard frontmatter with placeholders
- Common sections with placeholders
- Library-specific section examples
- Guidance comments (remove before finalizing)

## Best Practices

### Research Thoroughness

Explore multiple sources when researching:

- **Main repository**: Core library code and often documentation
- **Separate docs repo**: Some projects maintain dedicated documentation repos
- **Examples/samples repos**: Official example code and patterns
- **Template repos**: Full-stack or starter templates

### Documentation Discovery

Look for these common patterns:

- `docs/` or `documentation/` directories
- `examples/`, `samples/`, or `docs_src/` for code examples
- `tutorial/` or `getting-started/` for learning paths
- `llms.txt` files optimized for LLM consumption
- `README.md` as the primary overview

### Documentation URL Format

When linking to external documentation sites, **always prefer direct markdown URLs** (`.md` suffix) over human-readable HTML URLs. Many documentation sites (e.g., docs.langchain.com, mkdocs-based sites) serve raw markdown when you request the `.md` file directly. This is much more efficient for agents -- raw markdown instead of parsing HTML.

Example:
- **Prefer**: `https://docs.langchain.com/oss/javascript/deepagents/overview.md`
- **Avoid**: `https://docs.langchain.com/oss/javascript/deepagents/overview`

Check the site's `llms.txt` if available -- it typically lists URLs in the `.md` format already.

### Skill Customization

Tailor the skill to the library's domain:

- **Web frameworks** (FastAPI, Flask): Focus on routing, middleware, testing
- **Agent frameworks** (ADK, LangChain): Focus on agents, streaming, tools
- **Data libraries** (Pandas, Polars): Focus on operations, transformations
- **ML frameworks** (PyTorch, TensorFlow): Focus on models, training, deployment

### Progressive Disclosure

Keep SKILL.md concise by:

- Linking to comprehensive guides in `references/`
- Using directory references instead of listing all files
- Providing navigation hints rather than full content
- Organizing by use case for targeted loading

## Output Location

Create new skills at:

```
.claude/skills/<library-name>/
├── SKILL.md
└── .repos/
    └── .gitignore    # Contains: *\n!.gitignore
```

Always create the `.repos/.gitignore` file immediately when generating the skill, before any repositories are cloned.

## Example Workflow

User asks: "Create a skill for Pydantic"

1. **Research**: Use Task tool (Explore agent) to explore pydantic/pydantic repository
   - Find main repo and any related repos (docs, examples)
   - Discover documentation structure (docs/, tests/ with examples)
   - Identify key files (README, llms.txt if present)
   - Locate example code and tutorials

2. **Review findings**: Present discovered structure to user

3. **Generate skill**:
   - Copy `references/skill_template.md` to `.claude/skills/pydantic/SKILL.md`
   - Fill in placeholders with Pydantic-specific information
   - Add sections for validation, models, settings based on discovered structure

4. **Customize**:
   - Add overview links to key docs
   - Organize tutorial topics
   - Reference example locations

5. **Deliver**: Present the completed skill to the user

## Validation

Before considering a skill complete, verify:

- [ ] Frontmatter has comprehensive description with triggers
- [ ] Source repositories are listed with GitHub URLs
- [ ] Standard "Important" guidelines are included
- [ ] Overview section links to key starting files
- [ ] Library-specific sections match documentation structure
- [ ] All file paths are relative and correct
- [ ] Markdown links are properly formatted

## Related Skills

- **skill-creator**: General guide for creating any type of skill
