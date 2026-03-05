# CLAUDE.md

This file provides context for Claude Code when working with this repository.

## Project Overview

A demo repository that renders a simple static web page using plain HTML and GitHub's Primer CSS design system. There is no build step or JavaScript framework — just static HTML served directly.

## Repository Structure

```
.
├── index.html              # Main (and only) web page
├── package.json            # Node.js dependencies (Primer CSS)
├── package-lock.json       # Dependency lock file
├── CLAUDE.md               # This file — context for Claude Code
├── .cursor/rules/          # Cursor AI skill/rules files
│   ├── general.mdc         # General project conventions
│   ├── html.mdc            # HTML-specific rules
│   └── github-actions.mdc  # GitHub Actions rules
├── .husky/                 # Git hooks (via Husky)
│   ├── pre-commit          # Validates HTML, blocks .env files, checks for conflict markers
│   └── commit-msg          # Enforces Conventional Commits format
└── .github/workflows/      # CI/CD
    ├── auto-assign.yml     # Auto-assigns issues/PRs to maintainers
    └── proof-html.yml      # Validates HTML on push
```

## Tech Stack

- **HTML** — static markup, no templating
- **Primer CSS** (`@primer/css@17.0.1`) — GitHub's design system for styling
- **Husky** — Git hooks management
- **GitHub Actions** — CI workflows for HTML validation and issue assignment

## Commands

```bash
# Install dependencies
npm install

# Initialize Husky hooks (runs automatically via `prepare` script)
npm run prepare
```

## Conventions

- **Commit messages**: Follow [Conventional Commits](https://www.conventionalcommits.org/) (`feat:`, `fix:`, `docs:`, `chore:`, etc.). Enforced by the `commit-msg` hook.
- **File naming**: Use kebab-case for all file names.
- **HTML**: Use semantic elements, include `<!DOCTYPE html>`, and follow accessibility best practices.
- **GitHub Actions**: Pin action versions to specific tags/SHAs, declare minimum permissions, and never hard-code secrets.
- **No build step**: This project intentionally has no bundler or transpiler. Keep it simple.

## Workflow

1. Install dependencies with `npm install`.
2. Edit `index.html` directly.
3. Commit with a Conventional Commits message.
4. Push to trigger CI checks (HTML validation via `proof-html` workflow).

## Important Notes

- The `pre-commit` hook will block commits containing `.env` files or merge conflict markers.
- The `proof-html` workflow validates HTML on every push using `anishathalye/proof-html`.
- Primer CSS is installed as an npm dependency but linked/used via CDN or local reference in HTML — there is no CSS build pipeline.
