---
name: {LIBRARY_NAME}
description: Provides comprehensive context for developing with {LIBRARY_DISPLAY_NAME} by having access to the {LIBRARY_DISPLAY_NAME} codebase, official documentation, and examples
---

# {LIBRARY_DISPLAY_NAME}

<!--
INSTRUCTIONS:
1. Replace all {PLACEHOLDER} values with library-specific content
2. Remove sections that don't apply to this library
3. Add library-specific sections based on documentation structure
4. Remove these instruction comments before finalizing
-->

## Source Repositories

This skill references contents of local clones of the following {LIBRARY_DISPLAY_NAME} repositories:

- {MAIN_REPO_URL}
<!-- Add related repositories here: -->
<!-- - {DOCS_REPO_URL} -->
<!-- - {EXAMPLES_REPO_URL} -->
<!-- - {TEMPLATE_REPO_URL} -->

Before exploring, verify the repositories exist in [.repos](./.repos), clone any missing ones, pull the latest, and checkout a specific version tag if needed (e.g., `git checkout v1.2.0`).
When accessing or fetching content from these repositories, always use the local clones in [.repos](./.repos) instead of fetching from github.com.

**Important:** When exploring {LIBRARY_DISPLAY_NAME} code:
1. **Prefer checking the virtual environment first** - The installed {LIBRARY_DISPLAY_NAME} package in `.venv/` contains the actual code being used and may have local modifications or be a different version than the repository
2. **Keep repositories up-to-date** - Regularly pull the latest changes from the repositories using `git pull` to ensure you have the most current documentation and examples
3. **Explore all relevant sources** - For any request or query, explore multiple sources when it makes sense:
   - Check the actual code implementation in `.venv/` or `.repos/{MAIN_REPO_NAME}/`
   - Read the documentation in `.repos/{DOCS_LOCATION}/`
   - Find relevant examples in `.repos/{EXAMPLES_LOCATION}/` to understand usage patterns
   <!-- Add template repo reference if applicable: -->
   <!-- - Review the full-stack template in `.repos/{TEMPLATE_REPO_NAME}/` for production patterns -->

## Overview

Get an overview of {LIBRARY_DISPLAY_NAME} by reading the following files:

1. [{LIBRARY_DISPLAY_NAME} README](./.repos/{MAIN_REPO_NAME}/README.md)
<!-- Add llms.txt if available: -->
<!-- 2. [High-Level Summary](./.repos/{MAIN_REPO_NAME}/llms.txt) -->
<!-- Add documentation index: -->
<!-- 3. [Documentation Index](./.repos/{DOCS_LOCATION}/index.md) -->
<!-- Add other key overview files: -->
<!-- 4. [Features Overview](./.repos/{DOCS_LOCATION}/features.md) -->

<!--
DOCUMENTATION URLs:
When linking to external documentation sites, always use direct markdown URLs (.md suffix)
where supported. This is much more efficient for agents than HTML pages.
Example: https://docs.example.com/guide/topic.md instead of https://docs.example.com/guide/topic

SECTION CUSTOMIZATION:
Add library-specific sections below based on the documentation structure.

Examples:
- For web frameworks: Tutorial, Routing, Middleware, Testing, Deployment
- For agent frameworks: Agents, Streaming, Tools, Configuration
- For data libraries: Operations, Transformations, Performance, Integration
- For ML frameworks: Models, Training, Deployment, Optimization

Reference the google-adk and fastapi skills for patterns.
-->

## {SECTION_1_NAME}

<!-- Add section content with links to relevant documentation -->

{SECTION_1_DESCRIPTION}

- [{TOPIC_1}](./.repos/{PATH_TO_TOPIC_1})
- [{TOPIC_2}](./.repos/{PATH_TO_TOPIC_2})

## {SECTION_2_NAME}

<!-- Add section content with links to relevant documentation -->

{SECTION_2_DESCRIPTION}

- [{TOPIC_1}](./.repos/{PATH_TO_TOPIC_1})
- [{TOPIC_2}](./.repos/{PATH_TO_TOPIC_2})

## Examples

<!-- Describe where example code is located -->

Practical code examples are organized by topic in [./.repos/{EXAMPLES_LOCATION}/](./.repos/{EXAMPLES_LOCATION}/). Each subdirectory corresponds to a documentation topic and contains working {LANGUAGE} examples.

<!-- OR for separate examples repo: -->
<!-- Example code and patterns can be found in [./.repos/{EXAMPLES_REPO_NAME}/](./.repos/{EXAMPLES_REPO_NAME}/). -->

<!--
OPTIONAL SECTIONS:
Add these sections if they apply to the library
-->

<!-- For libraries with production templates:
## {TEMPLATE_NAME}

For production-ready patterns and full application structure:

- [{TEMPLATE_DISPLAY_NAME}](./.repos/{TEMPLATE_REPO_NAME}/)
  - {TEMPLATE_FEATURE_1}
  - {TEMPLATE_FEATURE_2}
  - {TEMPLATE_FEATURE_3}
-->

<!-- For libraries with well-organized documentation:
## Documentation Structure

The documentation is organized in:
- `{DIR_1}/` - {DIR_1_DESCRIPTION}
- `{DIR_2}/` - {DIR_2_DESCRIPTION}
- `{DIR_3}/` - {DIR_3_DESCRIPTION}
-->

<!--
FINAL CHECKLIST:
- [ ] All {PLACEHOLDER} values replaced
- [ ] Instruction comments removed
- [ ] Repository URLs verified
- [ ] File paths are relative and correct
- [ ] Library-specific sections added
- [ ] Unnecessary template sections removed
- [ ] Markdown links properly formatted
-->
