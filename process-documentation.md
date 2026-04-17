# Process Documentation:

## Overview

This document establishes a standardised approach for all contributors committing and working our codebase.

Its purpose is to maintain consistency, reduce defects, and ensure confidence in each release; whilst providing stakeholders with a clear, shared framework.

## Branching Strategy:

We use a **Feature Branch** workflow to ensure the `main` branch remains stable and deployable at all times.

### Branch Types:

- **`main`**: Production-ready code. No one commits directly to `main`.
- **`feature/`**: New functionality or migration tasks (e.g., `feature/navigation-mega-menu`).
- **`fix/`**: Bug fixes for existing features.
- **`refactor/`**: Code changes that neither fix a bug nor add a feature.

### Workflow: 

1. Pull the latest from `main`.
2. Create a new branch: `git checkout -b feature/short-description`.
3. Work and commit locally.
4. Push to origin and open a Pull Request (PR).
5. Once approved and CI passes, **Squash and Merge** into `main`.

## Commit Standards:

We follow the **Conventional Commits** convention. This helps in generating automated changelogs and makes the history readable.

### Types:

Use these prefixes in your commit messages to categorise the changes you are making.

| Type | Purpose | Example |
| :--- | :--- | :--- |
| **feat** | A new feature or functionality. | `feat(pdp): add product image zoom` |
| **fix** | A bug fix. | `fix(cart): resolve quantity update error` |
| **docs** | Documentation only changes. | `docs: update branching strategy guide` |
| **style** | Formatting and UI polish (no logic changes). | `style: fix button alignment on mobile` |
| **refactor** | Code changes that neither fix a bug nor add a feature. | `refactor: clean up liquid loop logic` |
| **perf** | A code change that improves performance. | `perf: lazy load collection images` |
| **test** | Adding missing tests or correcting existing ones. | `test: add checkout flow validation` |
| **build** | Changes to build tools or external dependencies. | `build: update shopify-cli version` |
| **ci** | Changes to CI configuration files and scripts. | `ci: fix github action syntax` |
| **chore** | Routine tasks (updating `.gitignore`, housekeeping). | `chore: remove unused assets folder` |
| **revert** | Undoing a previous commit. | `revert: feat: add experimental filter` |

### Format:

`<type>(<scope>): <description>`
*Example:* `feat(nav): add mobile hamburger menu`

---
**Contributors:** Helen Goatly & Moses Sangobiyi  
**Date:** April 2026
