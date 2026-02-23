# OctoAcme Personas

This document defines typical roles and responsibilities used in OctoAcme project docs and exercises. Understanding each persona helps teams establish clear ownership, minimize handoff friction, and ensure that every stage of the project lifecycle has a named accountable party.

---

## Developers

### Role Summary
Developers design, build, test, and deliver software components. They collaborate with product and project leads to implement features that meet acceptance criteria and quality standards.

### Responsibilities
- Implement features and fixes to meet acceptance criteria
- Write and maintain tests and documentation
- Participate in design and code reviews
- Assist in estimating and planning work
- Help identify technical risks and propose mitigations

### Goals
- Deliver reliable, maintainable code
- Reduce cycle time from idea to production
- Maintain high test coverage and observability

### Typical Communication
- Daily standups and sprint planning
- PR descriptions and code review comments
- Technical design docs when needed

### Interaction Points
- Works closely with QA Lead to clarify acceptance criteria and resolve test failures
- Coordinates with DevOps Engineer on CI/CD pipeline requirements and environment configuration
- Partners with Security Champion to address security findings before merge
- Receives prioritized work from Product Owner and Business Analyst

---

## Product Managers

### Role Summary
Product Managers define what should be built to deliver customer and business value. They own the product vision, prioritize the backlog, and measure outcomes.

### Responsibilities
- Define problem statements and success metrics
- Prioritize the roadmap and backlog
- Collaborate with stakeholders and engineering on trade-offs
- Validate solutions through user research and metrics

### Goals
- Maximize customer value and impact
- Make clear, data-driven prioritization decisions
- Ensure product-market fit and usability

### Typical Communication
- Weekly alignment with PM and engineering leads
- Roadmap updates and stakeholder briefings
- Acceptance criteria and feature specs

### Interaction Points
- Aligns with Business Analyst to translate business requirements into product stories
- Coordinates with Project Manager on timelines, milestones, and risk trade-offs
- Reviews QA acceptance results to confirm release readiness

---

## Project Managers

### Role Summary
Project Managers coordinate delivery activities, manage schedules, risks, and communications. They enable the team to deliver on commitments efficiently.

### Responsibilities
- Create and maintain project plans and timelines
- Manage risks, dependencies, and resource constraints
- Facilitate meetings (kickoff, planning, retrospectives)
- Ensure consistent project documentation and status reporting
- Coordinate cross-team and stakeholder communication

### Goals
- Deliver projects on time and within scope
- Minimize unplanned work and escalations
- Maintain transparency and alignment across stakeholders

### Typical Communication
- Weekly status updates and stakeholder reports
- Risk registers and decision logs
- Coordination via project boards and meeting facilitation

### Interaction Points
- Escalates technical blockers to DevOps Engineer or Security Champion as needed
- Works with Business Analyst to ensure requirements are understood and scoped
- Partners with QA Lead to track test progress and manage release gates

---

## QA Lead

### Role Summary
The QA Lead owns the quality strategy for the project. They define testing standards, review acceptance criteria, coordinate test execution across sprints, and act as the quality gate before releases go to production. This role ensures that what ships meets both functional requirements and user expectations.

### Responsibilities
- Define and maintain the overall test strategy and Definition of Done for quality
- Create and maintain test plans, test cases, and acceptance checklists
- Coordinate manual and automated testing across sprints
- Triage, prioritize, and track defects through resolution
- Approve release readiness from a quality perspective
- Collaborate with Developers to ensure testability is built into features

### Goals
- Prevent defect leakage to production
- Shift quality left by involving QA early in planning and design
- Build a repeatable, low-maintenance automated test suite

### Typical Communication
- Sprint planning and backlog grooming to review acceptance criteria
- QA status reports before each release
- Defect triage sessions with Developers and Project Manager

### Interaction Points
- Reviews acceptance criteria with Product Owner and Business Analyst during backlog grooming
- Works with Developers to resolve test failures and clarify expected behavior
- Coordinates with DevOps Engineer to ensure test environments mirror production
- Provides release sign-off to Project Manager and Product Manager
- Collaborates with Security Champion on security test cases and vulnerability validation

---

## DevOps Engineer

### Role Summary
DevOps Engineers design, build, and maintain the pipelines, infrastructure, and tooling that enable the team to deliver software reliably and repeatably. They bridge the gap between development and operations, reducing manual toil and improving deployment confidence.

### Responsibilities
- Design and maintain CI/CD pipelines (build, test, deploy)
- Manage infrastructure-as-code (IaC) and environment configurations
- Implement and monitor observability tooling (logging, metrics, alerting)
- Support automated security and compliance scanning in the pipeline
- Define and enforce deployment runbooks and rollback procedures
- Collaborate on environment provisioning for development, staging, and production

### Goals
- Achieve fast, safe, and repeatable deployments
- Reduce mean time to recovery (MTTR) for production incidents
- Increase developer productivity by minimizing infrastructure friction

### Typical Communication
- Sprint planning to identify infrastructure needs for upcoming features
- Pipeline failure notifications and incident bridge calls
- Deployment runbooks and post-mortem write-ups

### Interaction Points
- Partners with Developers to support branching strategies and pipeline requirements
- Works with Security Champion to integrate security scanning steps into pipelines
- Coordinates with Project Manager on deployment window scheduling and change management
- Supports QA Lead by provisioning and maintaining test environments
- Collaborates with Business Analyst to understand deployment constraints from compliance or SLA requirements

---

## Security Champion

### Role Summary
The Security Champion is an embedded advocate for secure engineering practices within the project team. This role does not replace a dedicated security team, but ensures that security is considered at every stage—from design through deployment—and that the team is equipped to identify and address common risks proactively.

### Responsibilities
- Promote and apply secure coding practices and OWASP guidelines within the team
- Conduct or facilitate threat modeling exercises during design and planning
- Review code and architecture changes for security implications
- Track and triage security findings from automated scanners and penetration tests
- Maintain and communicate the project's security checklist and review gates
- Escalate critical security issues to the appropriate security team or on-call rotation
- Coordinate vulnerability remediation with Developers and DevOps Engineer

### Goals
- Reduce the number of security vulnerabilities that reach production
- Build security awareness and a security-first culture within the team
- Ensure compliance with applicable security policies and standards

### Typical Communication
- Threat modeling sessions during planning or major feature design
- Security findings reviews and remediation tracking
- Escalation communications for critical vulnerabilities

### Interaction Points
- Collaborates with Developers during code review to flag and remediate security issues
- Works with DevOps Engineer to configure and tune security scanning tools in CI/CD
- Coordinates with QA Lead to validate that security test cases are included in test plans
- Engages Product Owner and Business Analyst to communicate security trade-offs and compliance constraints
- Provides security sign-off to Project Manager before production releases

---

## Product Owner

### Role Summary
The Product Owner (PO) represents the voice of the customer and business within the delivery team. They own the product backlog, clarify requirements, and make prioritization decisions to maximize the value delivered in each sprint. The PO is distinct from the Product Manager in that they operate at the sprint and story level rather than the strategic roadmap level.

### Responsibilities
- Own and maintain a well-groomed, prioritized product backlog
- Write and refine user stories with clear acceptance criteria
- Attend sprint planning to answer questions and confirm priorities
- Accept or reject completed work based on acceptance criteria
- Make real-time trade-off decisions when scope or design questions arise during development
- Maintain alignment between stakeholder expectations and team delivery

### Goals
- Maximize value delivered each sprint
- Ensure team always has a clear, ready-to-pull backlog
- Bridge the gap between business intent and technical implementation

### Typical Communication
- Sprint planning and backlog refinement sessions
- Daily availability (Slack or equivalent) for clarifying story requirements
- Sprint review acceptance walkthroughs

### Interaction Points
- Works with Business Analyst to translate business requirements into user stories
- Collaborates with Product Manager to align sprint goals with the strategic roadmap
- Reviews acceptance criteria with QA Lead before stories are scheduled for testing
- Provides real-time decisions to Developers and Project Manager when requirements are ambiguous
- Coordinates with Security Champion and DevOps Engineer when stories have security or infrastructure implications

---

## Business Analyst

### Role Summary
Business Analysts (BAs) bridge the gap between business stakeholders and the delivery team. They gather, document, and validate business requirements, translating them into structured specifications that Developers, QA, and Product Owners can act on. BAs ensure that solutions address the underlying business need and that nothing is lost in translation from concept to delivery.

### Responsibilities
- Elicit, document, and validate business and functional requirements
- Create process models, data flows, and use cases as needed
- Support backlog refinement by helping the Product Owner write clear user stories
- Facilitate requirements workshops with business stakeholders and the delivery team
- Analyze and document current-state and future-state processes
- Track requirement changes and ensure impacts are communicated to all stakeholders

### Goals
- Ensure requirements are complete, unambiguous, and agreed upon before development begins
- Reduce rework caused by misunderstood or incomplete requirements
- Accelerate onboarding of new team members by maintaining comprehensive requirement documentation

### Typical Communication
- Requirements workshops and stakeholder interviews
- Written specifications, acceptance criteria, and process diagrams
- Backlog grooming sessions with Product Owner and delivery team

### Interaction Points
- Collaborates with Product Owner to translate business needs into actionable user stories
- Engages stakeholders (business, operations, compliance) to gather and validate requirements
- Works with QA Lead to ensure test cases cover documented business requirements
- Provides context to Developers when implementation questions arise about intent or edge cases
- Coordinates with Security Champion and DevOps Engineer to document compliance, data governance, or operational requirements

---

## How these personas are used in the exercise
- Use these persona definitions to frame scenarios and sample interactions in the Skills Exercise.
- Each persona can be used as a persona prompt for Copilot Spaces to shape role-specific guidance.
- Reference the **Interaction Points** for each role to understand how responsibilities hand off across team members at each project stage.

