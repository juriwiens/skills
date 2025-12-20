# Skills

Personal skills collection by Juri Wiens.

This repository contains custom skills that extend Claude Code's capabilities for specialized tasks. Each skill is self-contained in its own folder with a `SKILL.md` file containing the instructions and metadata that Claude uses.

## Installation

### Step 1: Add the marketplace

First, register this repository as a plugin marketplace:

```bash
/plugin marketplace add juriwiens/skills
```

### Step 2: Install the skill

Then install the specific skill from the marketplace:

```bash
/plugin install library-docs-skill-creator@juri-wiens-skills
```

**Note:** The marketplace name `juri-wiens-skills` comes from the `name` field in `.claude-plugin/marketplace.json`.

## Available Skills

### library-docs-skill-creator

Automated workflow for creating library documentation skills by researching GitHub repositories and generating structured skill files.

**What it does:**
1. Uses AI exploration to discover repository structure
2. Identifies documentation, examples, and key files
3. Generates a complete SKILL.md following established patterns
4. Provides templates and research guidelines

**Usage triggers:**
- "Create a skill for [library name]"
- "Make a skill for [framework]"
- "Generate documentation context for [library]"
- "Research [library] docs structure"

**Features:**
- Automated repository discovery and analysis
- Documentation structure exploration
- Template-based skill file generation
- Support for multi-repo libraries (main, docs, examples, templates)
- Adaptive to any repository structure

## Repository Structure

- `.claude-plugin/` - Marketplace configuration
- `skills/` - Individual skill directories, each with a `SKILL.md`

## Creating Your Own Skills

To create a new skill:
1. Create a new directory under `skills/`
2. Add a `SKILL.md` file with frontmatter and instructions
3. Optionally add supporting files in `references/`, `scripts/`, or other subdirectories
4. Add the skill to `.claude-plugin/marketplace.json`

See [skills/library-docs-skill-creator](skills/library-docs-skill-creator) for a complete example.

## References

- [Agent Skills Standard](https://agentskills.io) - The open standard for AI agent skills
- [agentskills/agentskills](https://github.com/agentskills/agentskills) - GitHub repository for the standard
- [anthropics/skills](https://github.com/anthropics/skills) - Example skills from Anthropic

## License

MIT
