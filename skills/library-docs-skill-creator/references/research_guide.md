# Library Research Guide

This guide provides detailed methodology for researching library documentation and repositories when creating a new skill.

## Research Workflow

### 1. Identify the Library Ecosystem

Start by finding the main repository and related repositories:

```bash
# Find main repository
gh search repos <library-name> --limit 5 --json name,url,description,owner

# Search organization repositories
gh search repos --owner=<owner-name> --limit 20 --json name,description
```

Look for:

- **Main repository**: Core library code
- **Docs repository**: Separate documentation (e.g., `*-docs`, `documentation`)
- **Examples repository**: Official examples (e.g., `*-examples`, `*-samples`)
- **Template repository**: Starter templates (e.g., `*-template`, `*-starter`)

### 2. Explore Repository Structure

Examine the main repository's directory structure:

```bash
# Get top-level directories
gh api repos/<owner>/<repo>/contents --jq '.[] | select(.type == "dir") | .name'

# Check specific directories
gh api repos/<owner>/<repo>/contents/<dir-name> --jq '.[] | .name'
```

Common patterns to look for:

- `docs/` or `documentation/` - Documentation files
- `examples/`, `samples/`, `docs_src/` - Example code
- `tutorial/` - Tutorial content
- `src/`, `lib/`, or library name - Source code
- `tests/` - Test examples

### 3. Check for LLM-Optimized Documentation

Look for `llms.txt` files designed for LLM consumption:

```bash
# Check root directory
gh api repos/<owner>/<repo>/contents --jq '.[] | select(.name == "llms.txt") | .name'

# Check docs directory
gh api repos/<owner>/<repo>/contents/docs --jq '.[] | select(.name == "llms.txt") | .name'
```

If found, these are excellent starting points for the skill's Overview section.

### 4. Discover Documentation Structure

Explore how documentation is organized:

```bash
# List documentation directories
gh api repos/<owner>/<repo>/contents/docs --jq '.[] | select(.type == "dir") | .name'

# List markdown files
gh api repos/<owner>/<repo>/contents/docs --jq '.[] | select(.type == "file" and (.name | endswith(".md"))) | .name'
```

Common documentation structures:

- **Flat structure**: All docs in one directory
- **Topic-based**: Directories by topic (tutorial/, advanced/, api/)
- **Language-based**: Multiple language versions (en/, es/, fr/)

### 5. Locate Example Code

Find where examples are stored:

```bash
# Check for example directories
gh api repos/<owner>/<repo>/contents/examples --jq '.[] | select(.type == "dir") | .name'
gh api repos/<owner>/<repo>/contents/docs_src --jq '.[] | select(.type == "dir") | .name'
```

Examples are often:

- In an `examples/` directory at the root
- In a `docs_src/` directory parallel to `docs/`
- In a separate repository (e.g., `<library>-examples`)
- Embedded within documentation files

### 6. Identify Key Overview Files

Find the best starting points for understanding the library:

```bash
# Read first part of README
gh api repos/<owner>/<repo>/readme --jq '.content' | base64 -d | head -50

# Check for index or getting started
gh api repos/<owner>/<repo>/contents/docs --jq '.[] | select(.name | contains("index") or contains("getting-started") or contains("intro")) | .name'
```

Priority order:

1. `llms.txt` if available (optimized for LLMs)
2. `README.md` (high-level overview)
3. `docs/index.md` or `docs/README.md` (documentation entry point)
4. `docs/getting-started.md` or `docs/tutorial/index.md` (learning path)

### 7. Analyze Documentation Topics

Review the documentation to identify main topics and use cases:

```bash
# List all markdown files in docs
find docs -name "*.md" | sort

# Check directory names for topic organization
find docs -type d | sort
```

Group topics by:

- **Learning path**: Tutorial, getting started, basics
- **Features**: Core functionality, advanced features
- **How-to guides**: Task-specific instructions
- **Reference**: API documentation, configuration
- **Deployment**: Production, scaling, best practices

## Research Checklist

Use this checklist when researching a library:

### Repository Discovery

- [ ] Main repository identified
- [ ] Organization/owner confirmed
- [ ] Related repositories found (docs, examples, templates)
- [ ] Repository descriptions noted

### Structure Analysis

- [ ] Top-level directories mapped
- [ ] Documentation location identified
- [ ] Example code location identified
- [ ] Source code location noted

### Documentation Assessment

- [ ] llms.txt presence checked
- [ ] README reviewed
- [ ] Documentation structure understood
- [ ] Key topics identified
- [ ] Tutorial/learning path found

### Resource Identification

- [ ] Key overview files listed
- [ ] Example locations cataloged
- [ ] Template repositories found
- [ ] Additional resources noted

## Output Format

After research, prepare information in this format:

```
Library Name: [name]
Main Repository: [url]
Related Repositories:
  - [name]: [url] - [description]

Documentation Structure:
  - [directory]: [purpose]

Key Starting Files:
  - [file path]: [description]

Example Locations:
  - [directory or repo]

Main Topics/Sections:
  - [topic name]: [description]
```

This structured output makes it easy to fill in the skill template.
