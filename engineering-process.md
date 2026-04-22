# PR and Branching Process

## 1 Overview

This document defines the standard branching and pull request workflow for the CakeBox replatform workstream.

The goal is to keep delivery consistent, review cycles predictable, and QA handovers clear.

## 2 Main Branch Policy

- `main` is the production reference branch and must remain stable.
- No active feature development is carried out directly on `main`.
- Direct pushes to `main` are not permitted; all changes must use pull requests.
- To keep environments aligned, sync PRs are taken from `main` into `staging` after releases or urgent production hotfixes.

## 3 Branch Naming Standard

- Create all feature work from `staging`.
- Use branch format: `feature/<ticket-id>-<short-description>`
- Keep names lowercase and hyphenated.

**Example:** `feature/CB-142-add-checkout-validation`

## 4 Branching Workflow Diagram

![Branching workflow](./branching-workflow.png)

### 4.1 Legend

- **1:** Create feature branch from `staging`.
- **2:** Complete development on `feature/<ticket-id>-<desc>` and run local checks.
- **3:** Raise and merge **PR Type 1** from feature branch into `staging` after review.
- **4:** Raise and merge **PR Type 2** from `staging` into `main` after QA sign-off.

## 5 Commit Standards

We follow the **Conventional Commits** convention. This helps generate automated changelogs and keeps commit history readable.

Reference: [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)

### 5.1 Types

Use these prefixes in your commit messages to categorise changes.

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

### 5.2 Format

`<type>(<scope>): <description>`

**Example:** `feat(nav): add mobile hamburger menu`

## 6 PR Workflow

### 6.1 PR Types

- **PR Type 1 (Feature PR):** `feature/<ticket-id>-<desc>` -> `staging`
- **PR Type 2 (Release PR):** `staging` -> `main`

### 6.2 Review Model

- **Feature PR review (PR Type 1):** carried out by RAD internally for faster cycle time.
- **QA validation:** completed on `staging` after Feature PR merge.
- **Release PR review (PR Type 2):** carried out by Cake Box as the final sense check before merge.

| Step | Action | Owner | Expected Timeframe |
| :--- | :--- | :--- | :--- |
| 1 | Developer creates feature branch from `staging`, using correct naming format (`feature/<ticket-id>-<desc>`). | Developer | Before coding starts |
| 2 | Developer completes work and runs local checks: lint, build, and basic smoke test. | Developer | Before PR raised |
| 3 | Developer raises **PR Type 1 (Feature PR)** to `staging` with: JIRA ticket link, change description, screenshots or short Loom (for UI changes), and reviewer test steps. | Developer | On completion |
| 4 | PR assigned to RAD reviewer. | RAD | Within 2 hours of PR raised |
| 5 | Reviewer validates code against PR checklist (Section 7), then approves or requests changes with clear comments. | Reviewer | Within 1 business day |
| 5i | Developer addresses all requested changes and re-requests review. | Developer | Within 1 business day |
| 6 | Reviewer approves and developer merges Feature PR to `staging`. | Developer | Post-approval |
| 7 | QA validates changes on `staging`, logs defects if found, and provides sign-off or marks as failed with issues for rework. | QA | Within 1 business day of merge |
| 8 | After QA sign-off, Cake Box raises **PR Type 2 (Release PR)** from `staging` to `main`, then completes release review and merge. | Cake Box | As scheduled release window |

## 7 PR Review Criteria

### 7.1 Code Quality

- Code follows agreed naming conventions (NextJS/Hydrogen standards).
- Semantic HTML elements are used where appropriate (`header`, `nav`, `main`, `section`, `article`, `button`, etc.).
- No unused variables, debug `console.log` statements, or hardcoded credentials.
- DRY principle is applied with no obvious code duplication.
- Error handling is in place for API calls, including third-party integrations (for example: Onestock).
- Key errors/events are logged with enough context for debugging.
- Key UI elements include stable, unique identifiers (for example, dedicated class names or `data-*` attributes) to keep implementation clean, maintainable, and reliable across releases.

### 7.2 Front-End and UI

- Mobile-first implementation, tested at `375px` (iPhone SE) minimum.
- WCAG 2.2 AA accessibility compliance, including contrast ratio, alt text, and keyboard navigation.
- Cake Box brand standards are followed for typography, colours, and spacing (per RAD Google Drive guidelines).
- No layout shift on page load (CLS), and images include explicit `width` and `height` attributes.

### 7.3 Performance

- No third-party scripts are added without Cake Box sign-off.
- Images use WebP format where possible.

### 7.4 Integration

- Dependencies/config: all env vars or package changes should be documented
- API calls use agreed Onestock endpoints and payload schema.

### 7.5 Testing

- Acceptance criteria from the JIRA ticket are explicitly addressed.
- Edge cases are considered and clearly noted in the PR description.

## 8 PR Submission Checklist

Before requesting review, ensure:

- PR links to the correct JIRA ticket.
- Description clearly explains what changed and why.
- Screenshots or a short Loom are included for UI changes.
- Test steps are included so reviewers can validate quickly.
- Local lint/build/smoke checks have passed.

---

**Contributors:** Egg Free Cake Box 
**Date:** April 2026
