# OctoAcme — QA & Security Checklists

## Purpose

This document provides reusable checklists and templates for quality assurance and security review activities across the OctoAcme project lifecycle. Using these checklists ensures that quality and security gates are applied consistently on every feature and release, regardless of team composition or project size.

Centralizing QA and security templates here allows the QA Lead, Security Champion, and DevOps Engineer to maintain a single source of truth for these processes, and gives Developers and Product Owners clear expectations for what "done" looks like from a quality and security standpoint.

---

## QA Acceptance Testing Checklist

**Purpose:** Used by the QA Lead (and Developers) to confirm that a story or feature meets its acceptance criteria and is ready to be accepted before a sprint closes or a release is cut.

**When to use:** After development is complete and before the Product Owner acceptance walkthrough.

### Story-Level QA Checklist

- [ ] All acceptance criteria defined in the user story are verified (manually or via automated test)
- [ ] Unit tests written and passing for new logic
- [ ] Integration tests updated or added for new interactions between components
- [ ] Regression test suite passes without new failures
- [ ] Edge cases and negative paths tested (e.g., invalid inputs, boundary conditions, empty states)
- [ ] UI/UX reviewed against design specs or wireframes (if applicable)
- [ ] Accessibility requirements validated (e.g., keyboard navigation, screen reader, WCAG AA)
- [ ] Performance: no significant regression in response times for critical paths
- [ ] Defects discovered during testing are logged, triaged, and resolved or deferred with Product Owner sign-off
- [ ] Test results documented and linked to the story/issue

### Release-Level QA Checklist

Use this in addition to story-level checks before approving a release.

- [ ] All story-level QA checklists completed for stories included in this release
- [ ] Full regression suite executed in staging environment
- [ ] End-to-end smoke tests pass for the top critical user flows
- [ ] Data migration scripts (if any) tested against a production-mirror dataset
- [ ] Rollback verified: rollback procedure tested and confirmed to restore previous behavior
- [ ] Release notes reviewed for accuracy and completeness
- [ ] QA Lead has provided written sign-off for release readiness

### QA Test Plan Template

Use this template to document the test strategy for a sprint or major feature.

```
## Test Plan — [Feature / Sprint Name]

**Author:** [QA Lead name]
**Date:** [YYYY-MM-DD]
**Scope:** [What is being tested; what is explicitly out of scope]

### Test Objectives
- [What risks or acceptance criteria this plan addresses]

### Test Approach
- Unit testing: [responsibility, tooling]
- Integration testing: [responsibility, tooling]
- End-to-end / acceptance testing: [responsibility, tooling]
- Manual exploratory testing: [scope and time-box]

### Test Environments
| Environment | Purpose | Owner |
|---|---|---|
| Dev | Developer local testing | Developer |
| Staging | Pre-release regression & acceptance | QA Lead / DevOps Engineer |

### Entry Criteria
- [ ] Feature branch merged to main/release branch
- [ ] Build deployed to staging
- [ ] Acceptance criteria documented on the story

### Exit Criteria
- [ ] All acceptance criteria verified
- [ ] No open critical or high-severity defects
- [ ] Regression suite passing

### Defect Management
- Log defects as issues with labels: `bug`, severity level, and sprint milestone
- Triage daily during active test cycles; escalate blockers to Project Manager same day
```

---

## Security Review Checklist

**Purpose:** Used by the Security Champion (with support from Developers and DevOps Engineer) to ensure that security considerations are addressed at each stage — from design through deployment. This checklist is not a replacement for a formal security audit; it is a shift-left tool to catch common issues early.

**When to use:**
- During design/planning for stories touching authentication, authorization, data storage, or external integrations
- During code review for any PR that changes security-sensitive logic
- Before every production release

### Design & Planning Security Review

- [ ] Threat model reviewed or updated for new features (data flows, trust boundaries, attack surface)
- [ ] Authentication and authorization approach documented and approved
- [ ] Sensitive data identified: PII, credentials, payment data — storage and transit protections defined
- [ ] Third-party dependencies reviewed for known vulnerabilities (e.g., `npm audit`, `pip check`, Dependabot)
- [ ] Compliance requirements identified (GDPR, SOC 2, HIPAA, etc.) and addressed in the design
- [ ] Security Champion consulted and has no open blocking concerns before development starts

### Code Review Security Checklist

- [ ] No hardcoded secrets, API keys, or credentials in code (use secrets management tooling)
- [ ] Input validation applied for all external inputs (user input, API payloads, file uploads)
- [ ] Output encoding applied to prevent injection attacks (XSS, SQL injection, etc.)
- [ ] Authentication and session management follows established patterns (no custom crypto)
- [ ] Authorization checks applied at every sensitive operation (not just UI gating)
- [ ] Error handling does not leak sensitive information (stack traces, internal paths, DB errors)
- [ ] Logging captures security-relevant events without logging sensitive data (passwords, tokens, PII)
- [ ] Dependencies added in this PR have been checked for known vulnerabilities
- [ ] Security Champion review completed and approved for security-sensitive changes

### Pre-Release Security Checklist

- [ ] Automated SAST (static analysis) scan completed and findings reviewed
- [ ] Dependency vulnerability scan (SCA) completed and critical/high findings resolved
- [ ] Secrets scanner run; no secrets detected in repository history or build artifacts
- [ ] Container/image scan completed (if applicable) and critical findings resolved
- [ ] DAST (dynamic analysis) scan run against staging environment (if applicable)
- [ ] Penetration test findings (if any) triaged and critical items resolved or formally accepted
- [ ] Security Champion has provided written sign-off for release readiness
- [ ] Incident response runbook updated if new components or infrastructure were added

### Security Incident Response Template

Use this template when a security incident or critical vulnerability is identified.

```
## Security Incident Report — [Short Title]

**Reported by:** [Name / Role]
**Date/Time discovered:** [YYYY-MM-DD HH:MM UTC]
**Severity:** [Critical / High / Medium / Low]

### Summary
[1–3 sentence description of the incident or vulnerability]

### Impact Assessment
- Systems/data affected:
- Users affected (estimated):
- Exploitability (internal/external, authentication required):

### Immediate Actions Taken
- [Action 1 — Owner — Timestamp]
- [Action 2 — Owner — Timestamp]

### Root Cause (preliminary)
[Known or suspected root cause; update as investigation continues]

### Remediation Plan
- [ ] [Fix / mitigation action] — Owner: [Name] — Due: [Date]
- [ ] Deploy fix to production — Owner: [DevOps Engineer] — Due: [Date]
- [ ] Notify affected parties (if required) — Owner: [Project Manager] — Due: [Date]

### Post-Incident Review
- Scheduled blameless retrospective: [Date]
- Action items to prevent recurrence: [Link to issues/backlog]
```

---

## DevOps Deployment-Readiness Checklist

**Purpose:** Used by the DevOps Engineer and Project Manager to confirm that infrastructure, pipelines, and operational readiness criteria are met before deploying to production. This reduces deployment risk and ensures the team is prepared to respond quickly if issues arise.

**When to use:** Before every production deployment (major, minor, or patch).

### Pipeline & Build Readiness

- [ ] CI pipeline passing on the release branch (all tests, linting, and scans green)
- [ ] Build artifacts versioned and stored in the artifact registry (no local or ad-hoc builds deployed)
- [ ] Container images or deployment packages scanned for vulnerabilities (no critical findings unresolved)
- [ ] Infrastructure-as-code (IaC) changes reviewed and applied to staging without errors
- [ ] Environment-specific configuration (env vars, secrets) verified for the target environment

### Deployment Execution Readiness

- [ ] Deployment window confirmed with Project Manager and stakeholders (change management approval if required)
- [ ] Rollback procedure documented and tested in staging
- [ ] Database migration scripts (if any) tested on staging with production-size dataset; rollback script ready
- [ ] Feature flags configured correctly for the target environment (flags off for unreleased features)
- [ ] On-call rotation confirmed and aware of the deployment; escalation contacts documented

### Observability & Monitoring

- [ ] Dashboards and alerts updated to reflect new components or changed metrics
- [ ] Log aggregation confirmed for new services or endpoints
- [ ] Synthetic monitors or uptime checks configured for new user-facing flows
- [ ] Alerting thresholds reviewed and tuned for expected traffic patterns post-release

### Post-Deployment Verification

- [ ] Deployment completed without errors (pipeline or manual steps)
- [ ] Smoke tests executed and passing in production
- [ ] Key metrics (error rate, latency, throughput) are within normal bounds
- [ ] Stakeholders and support team notified of successful deployment
- [ ] Deployment log and release notes linked in the project's release record

### Deployment Runbook Template

Use this template to document the step-by-step deployment procedure for each release.

```
## Deployment Runbook — [Release Name / Version]

**Release type:** [Patch / Minor / Major]
**Deploy date/time:** [YYYY-MM-DD HH:MM UTC]
**Deploy owner:** [DevOps Engineer name]
**Approvers:** [QA Lead, Security Champion, Project Manager]

### Pre-Deployment Steps
1. [Step description] — Owner: [Name] — ETA: [X min]
2. ...

### Deployment Steps
1. Trigger pipeline / run deployment script: `[command or link]`
2. Monitor pipeline progress at: [link]
3. Confirm deployment succeeded in: [dashboard/log link]

### Post-Deployment Verification Steps
1. Run smoke tests: [link or command]
2. Check error rate dashboard: [link]
3. Confirm feature flags are in expected state

### Rollback Procedure
Trigger if: [define rollback criteria, e.g., error rate > X%, smoke tests fail]
1. [Step 1]
2. [Step 2]
Rollback owner: [DevOps Engineer] | Notify: [Project Manager, QA Lead]

### Communication
- Deployment start: notify [#channel or distribution list]
- Deployment complete: update [project board / status page]
- Incident (if triggered): follow [link to incident response doc]
```
