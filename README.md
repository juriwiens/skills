# Claude Code Plugins

Personal marketplace for Claude Code plugins by Juri Wiens.

This repository serves as both:
1. A **Claude Code plugin marketplace** for distributing plugins
2. A **plugin** containing the library-docs-skill-creator skill

## Installation

### Add the marketplace

```bash
/plugin marketplace add juriwiens/claude-plugins
```

### Install plugins from this marketplace

```bash
/plugin install library-docs-skill-creator@claude-plugins
```

Or install directly from this repository:

```bash
/plugin install juriwiens/claude-plugins
```

## Available Plugins

### library-docs-skill-creator

Automated workflow for creating library documentation skills by researching GitHub repositories and generating structured skill files.

**Features:**
- Automated repository discovery and analysis
- Documentation structure exploration
- Template-based skill file generation
- Support for multi-repo libraries (main, docs, examples, templates)
- Adaptive to any repository structure

**Usage triggers:**
- "Create a skill for [library name]"
- "Make a skill for [framework]"
- "Generate documentation context for [library]"
- "Research [library] docs structure"

**What it does:**
1. Uses AI exploration to discover repository structure
2. Identifies documentation, examples, and key files
3. Generates a complete SKILL.md following established patterns
4. Provides templates and research guidelines

## Repository Structure

```
claude-plugins/
├── .claude-plugin/
│   ├── marketplace.json    # Marketplace definition
│   └── plugin.json         # Plugin manifest
├── skills/
│   └── library-docs-skill-creator/
│       ├── SKILL.md        # Main skill file
│       ├── .gitignore      # Excludes .repos/
│       └── references/
│           ├── skill_template.md    # Template for new skills
│           └── research_guide.md    # Research methodology
├── LICENSE
└── README.md
```

## License

MIT
