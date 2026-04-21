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

## 5 PR Workflow

### 5.1 PR Types

- **PR Type 1 (Feature PR):** `feature/<ticket-id>-<desc>` -> `staging`
- **PR Type 2 (Release PR):** `staging` -> `main`

### 5.2 Review Model

- **Feature PR review:** normal code review by reviewers.
- **QA validation:** completed on `staging` after Feature PR merge.
- **Release PR review:** release review and merge by release owner.

| Step | Action | Owner | Expected Timeframe |
| :--- | :--- | :--- | :--- |
| 1 | Developer creates feature branch from `staging`, using correct naming format (`feature/<ticket-id>-<desc>`). | Developer | Before coding starts |
| 2 | Developer completes work and runs local checks: lint, build, and basic smoke test. | Developer | Before PR raised |
| 3 | Developer raises **PR Type 1 (Feature PR)** to `staging` with: JIRA ticket link, change description, screenshots or short Loom (for UI changes), and reviewer test steps. | Developer | On completion |
| 4 | PR assigned to developer reviewer. | Cake Box | Within 2 hours of PR raised |
| 5 | Reviewer validates code against PR checklist (Section 6), then approves or requests changes with clear comments. | Reviewer | Within 1 business day |
| 5i | Developer addresses all requested changes and re-requests review. | Developer | Within 1 business day |
| 6 | Reviewer approves and developer merges Feature PR to `staging`. | Developer | Post-approval |
| 7 | QA validates changes on `staging`, logs defects if found, and provides sign-off or marks as failed with issues for rework. | QA | Within 1 business day of merge |
| 8 | After QA sign-off, release owner raises **PR Type 2 (Release PR)** from `staging` to `main`, then completes release review and merge. | Release Owner | As scheduled release window |

## 6 PR Review Criteria

### 6.1 Code Quality

- Code follows agreed naming conventions (NextJS/Hydrogen standards).
- No unused variables, debug `console.log` statements, or hardcoded credentials.
- DRY principle is applied with no obvious code duplication.
- Error handling is in place for API calls, including third-party integrations (for example: Onestock and WorldPay).
- Key errors/events are logged with enough context for debugging

### 6.2 Front-End and UI

- Mobile-first implementation, tested at `375px` (iPhone SE) minimum.
- WCAG 2.2 AA accessibility compliance, including contrast ratio, alt text, and keyboard navigation.
- Cake Box brand standards are followed for typography, colours, and spacing (per RAD Google Drive guidelines).
- No layout shift on page load (CLS), and images include explicit `width` and `height` attributes.

### 6.3 Performance

- No third-party scripts are added without Cake Box sign-off.
- Images use WebP format where possible.

### 6.4 Integration

- Dependencies/config: all env vars or package changes should be documented
- API calls use agreed Onestock endpoints and payload schema.
- Payment integration (Worldpay/Cybersource or Ryftpay) follows the agreed specification.

### 6.5 Testing

- Acceptance criteria from the JIRA ticket are explicitly addressed.
- Edge cases are considered and clearly noted in the PR description.

## 7 PR Submission Checklist

Before requesting review, ensure:

- PR links to the correct JIRA ticket.
- Description clearly explains what changed and why.
- Screenshots or a short Loom are included for UI changes.
- Test steps are included so reviewers can validate quickly.
- Local lint/build/smoke checks have passed.

---

**Contributors:** Helen Goatly & Moses Sangobiyi  
**Date:** April 2026
