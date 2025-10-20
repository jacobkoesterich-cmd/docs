# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Mintlify documentation site. Mintlify is a documentation framework that uses MDX files for content and a `docs.json` configuration file for site structure and theming.

## Development Commands

### Local Development
```bash
# Install the Mintlify CLI globally (required for development)
npm i -g mint

# Start local development server (runs on http://localhost:3000)
mint dev

# Run on custom port
mint dev --port 3333

# Update CLI to latest version
mint update

# Validate all links in documentation
mint broken-links
```

### Prerequisites
- Node.js version 19 or higher
- Mintlify CLI installed globally

## Architecture and Structure

### Configuration
- **docs.json**: Central configuration file that defines:
  - Site metadata (name, colors, theme)
  - Navigation structure (tabs, groups, pages)
  - Logo paths for light/dark modes
  - Footer and social links
  - Contextual menu options

### Content Organization
- **MDX files**: All documentation content is written in MDX (Markdown with JSX)
- **Snippets**: Reusable content stored in `/snippets/` directory
  - Snippet files are NOT rendered as standalone pages
  - Import snippets using: `import MySnippet from '/snippets/path/to/snippet.mdx'`
  - Snippets can export variables, components, or default content

### Directory Structure
```
.
├── docs.json              # Main configuration
├── index.mdx              # Homepage
├── quickstart.mdx         # Quickstart guide
├── development.mdx        # Development instructions
├── ai-tools/              # AI tools documentation
├── api-reference/         # API documentation
├── essentials/            # Core documentation guides
├── snippets/              # Reusable content snippets
├── images/                # Image assets
└── logo/                  # Logo files (light/dark)
```

### Navigation System
Navigation is defined in `docs.json` under the `navigation` key:
- Pages are referenced by their file path without the `.mdx` extension
- Navigation uses a tabs → groups → pages hierarchy
- Adding a new page requires:
  1. Creating the `.mdx` file
  2. Adding the page path to the appropriate group in `docs.json`

## Working with Content

### MDX Components
Mintlify provides custom MDX components including:
- `<Card>`: Links with icons
- `<Columns>`: Multi-column layouts
- `<Steps>`, `<Step>`: Step-by-step guides
- `<Info>`, `<Warning>`, `<Note>`: Callout boxes
- `<Accordion>`, `<AccordionGroup>`: Collapsible content
- `<Frame>`: Image containers

### Reusable Snippets
- Snippets support three patterns:
  1. **Default export**: Entire snippet as a component with props
  2. **Named exports**: Export variables or objects
  3. **Arrow function components**: Export reusable components (HTML only, no MDX)

## Deployment

Changes are automatically deployed to production when pushed to the default branch (main) if the GitHub app is installed from the Mintlify dashboard.

## Troubleshooting

If the dev server fails to start:
- Ensure Node.js v19+ is installed
- Delete `~/.mintlify` folder and retry
- Run `mint update` to get the latest CLI version
- Verify you're in a directory with a valid `docs.json` file
