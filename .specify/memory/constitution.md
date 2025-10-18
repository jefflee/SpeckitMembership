<!--
  Sync Impact Report - Constitution v1.1.0
  ========================================
  Version Change: 1.0.0 → 1.1.0
  Rationale: MINOR version bump - Added new principle for documentation language requirements
  
  Modified Principles: N/A
  Added Sections:
    - Core Principles: V. Documentation Language (NEW)
  
  Removed Sections: N/A
  
  Templates Requiring Updates:
    ✅ plan-template.md - Constitution Check section updated with language requirement
    ✅ spec-template.md - Language requirement note added
    ✅ tasks-template.md - No changes needed (language applies to outputs, not task structure)
  
  Follow-up TODOs: None - All placeholders resolved
-->

# SpeckitMembership Constitution

## Core Principles

### I. Code Quality (NON-NEGOTIABLE)

Code MUST be maintainable, readable, and follow established standards. This principle is fundamental to project longevity.

**Standards**:
- Every component MUST have a single, clear responsibility
- Code MUST be self-documenting through clear naming and structure
- Comments are required only for complex business logic or non-obvious decisions
- Cyclomatic complexity MUST NOT exceed 10 per function
- Code duplication MUST be eliminated through appropriate abstraction
- All code MUST pass linting and formatting checks before commit
- Magic numbers and hardcoded values MUST be replaced with named constants

**Rationale**: High code quality reduces bugs, accelerates onboarding, and enables confident refactoring. Poor code quality creates compounding technical debt that slows all future work.

### II. Testing Standards (NON-NEGOTIABLE)

Comprehensive testing is mandatory. Tests define correctness and enable safe evolution.

**Requirements**:
- Test-Driven Development (TDD) MUST be followed: Write tests → Verify failure → Implement → Verify pass
- Minimum 80% code coverage required; critical paths MUST have 100% coverage
- Every user story MUST have corresponding acceptance tests
- Every API contract MUST have contract tests validating request/response schemas
- Integration tests MUST cover cross-component interactions
- Tests MUST be independent, repeatable, and fast (unit tests <100ms, integration <5s)
- Tests MUST NOT depend on external services (use mocks/stubs)
- Failing tests MUST block merges and deployments

**Test Types Required**:
- **Unit Tests**: All business logic, data transformations, calculations
- **Contract Tests**: All API endpoints, data schemas, interface boundaries
- **Integration Tests**: Component interactions, data flows, user journeys
- **Edge Case Tests**: Boundary conditions, error scenarios, validation rules

**Rationale**: Tests are executable specifications that prevent regressions and enable confident refactoring. TDD ensures code is testable by design.

### III. User Experience Consistency

User experience MUST be predictable, intuitive, and consistent across all touchpoints.

**Standards**:
- UI components MUST follow established design system and patterns
- User workflows MUST complete in ≤3 steps for primary tasks
- Error messages MUST be clear, actionable, and user-friendly (no technical jargon)
- Loading states MUST be shown for operations taking >300ms
- Success/failure feedback MUST be immediate and unambiguous
- Accessibility standards (WCAG 2.1 Level AA) MUST be met
- Mobile-first responsive design MUST be implemented
- User input MUST be validated with immediate, inline feedback
- Navigation MUST be intuitive; users should not need documentation for basic tasks

**User Story Requirements**:
- Every user story MUST define measurable success criteria
- User stories MUST be prioritized and independently testable
- Each story MUST deliver standalone value (MVP principle)
- Acceptance scenarios MUST use Given-When-Then format

**Rationale**: Consistent UX reduces cognitive load, increases user satisfaction, and decreases support burden. Poor UX drives users away regardless of functionality.

### IV. Performance Requirements

Performance is a feature. Systems MUST be responsive, scalable, and resource-efficient.

**API Performance**:
- API responses MUST complete in <200ms (p95) for CRUD operations
- API responses MUST complete in <500ms (p95) for complex queries
- API throughput MUST handle 1000 requests/second minimum
- Database queries MUST execute in <100ms (p95)
- Pagination MUST be implemented for collections >100 items

**Frontend Performance**:
- Initial page load MUST complete in <2 seconds on 3G connection
- Time to Interactive (TTI) MUST be <3 seconds
- Bundle sizes MUST be <500KB gzipped (initial load)
- Images MUST be optimized and lazy-loaded
- CSS and JavaScript MUST be minified and code-split

**Resource Efficiency**:
- Memory usage MUST NOT exceed 512MB per service instance
- CPU usage MUST NOT exceed 70% under normal load
- Database connections MUST be pooled and limited
- Caching MUST be implemented for frequently accessed data
- Background jobs MUST NOT block user-facing operations

**Monitoring Requirements**:
- All performance metrics MUST be instrumented and monitored
- Performance regressions MUST trigger alerts
- Load testing MUST be performed before production deployment
- Performance budgets MUST be defined and enforced in CI/CD

**Rationale**: Users expect instant responses. Slow systems frustrate users, waste resources, and limit scalability. Performance issues compound under load.

### V. Documentation Language (NON-NEGOTIABLE)

All specifications, plans, and user-facing documentation MUST be written in Traditional Chinese (zh-TW). This ensures consistency and accessibility for the target user base.

**Requirements**:
- Feature specifications (spec.md) MUST be in Traditional Chinese
- Implementation plans (plan.md) MUST be in Traditional Chinese
- User-facing documentation (README, quickstart guides, help text) MUST be in Traditional Chinese
- API documentation for end-users MUST be in Traditional Chinese
- Error messages shown to users MUST be in Traditional Chinese
- UI text and labels MUST be in Traditional Chinese

**Exceptions** (English permitted):
- Code (variable names, function names, comments within source code)
- Technical internal documentation for developers (if team preference)
- Commit messages and pull request descriptions (if team preference)
- Log messages and internal debugging output

**Rationale**: Consistent language in user-facing materials eliminates confusion, improves accessibility for the target audience, and demonstrates cultural respect. Technical documentation in the users' native language significantly reduces support burden and improves user satisfaction.

## Performance Standards

Performance targets define acceptable system behavior under normal and peak load.

**Response Time Targets**:
- Simple reads: <100ms (p95)
- Simple writes: <200ms (p95)
- Complex operations: <500ms (p95)
- Batch operations: <2s (p95)

**Scalability Targets**:
- Horizontal scaling MUST be supported
- Services MUST be stateless (session state in external store)
- Database reads MUST be scalable via read replicas
- Heavy operations MUST be async with job queues

**Degradation Behavior**:
- System MUST degrade gracefully under overload
- Non-critical features MUST be circuit-breakered
- Rate limiting MUST protect from abuse
- Health checks MUST enable automatic failover

## Development Workflow

Development workflow ensures quality, consistency, and team alignment.

**Branch Strategy**:
- Feature branches named: `###-feature-name`
- All work MUST be in feature branches (no direct commits to main)
- Branches MUST be short-lived (<3 days ideal, 1 week maximum)

**Quality Gates** (All MUST pass before merge):
1. All tests pass (unit, contract, integration)
2. Code coverage meets minimums (80% overall, 100% critical paths)
3. Linting and formatting checks pass
4. Code review approved by at least one team member
5. Constitution compliance verified (via checklist)
6. Performance benchmarks meet targets (if applicable)
7. Documentation updated (README, API docs, etc.)

**Code Review Standards**:
- Reviews MUST check for constitution compliance
- Reviews MUST verify test quality and coverage
- Reviews MUST validate error handling and edge cases
- Reviews MUST assess performance implications
- Reviewers MUST verify code meets single responsibility principle

**Commit Standards**:
- Commits MUST be atomic and focused
- Commit messages MUST follow conventional commit format
- Commits MUST reference issue/story numbers

**Documentation Requirements**:
- API changes MUST update contract documentation
- New features MUST update README and quickstart guides
- Breaking changes MUST include migration guides
- Complex logic MUST have inline explanations
- All user-facing documentation MUST be in Traditional Chinese (zh-TW)
- Error messages and UI text MUST be in Traditional Chinese (zh-TW)

## Governance

This constitution supersedes all other development practices and policies.

**Amendment Process**:
- Amendments require documented rationale and team consensus
- Version MUST be incremented per semantic versioning:
  - MAJOR: Breaking governance changes or principle removals
  - MINOR: New principles added or material expansions
  - PATCH: Clarifications, wording improvements, typo fixes
- Amendments MUST be propagated to all affected templates and documentation

**Compliance**:
- All pull requests MUST verify constitution compliance
- Constitution violations MUST be justified in Complexity Tracking section
- Regular constitution audits MUST be performed quarterly
- Non-compliance discovered post-merge MUST be tracked as technical debt

**Enforcement**:
- Automated checks MUST enforce what can be automated (tests, coverage, linting)
- Manual review MUST verify what cannot be automated (design, UX, architecture)
- Violations without justification MUST block merge

**Version**: 1.1.0 | **Ratified**: 2025-10-18 | **Last Amended**: 2025-10-18
