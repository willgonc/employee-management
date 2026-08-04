<!--
Version change: uninitialized -> 1.0.0
Modified principles: Added five project-specific principles aligned to security, maintainability, and code quality
Added sections: Project Constraints, Development Workflow
Removed sections: None
Deferred items: None
-->

# RSS Feed Reader Constitution

## Core Principles

### I. Define and defend the MVP scope
The project MUST preserve the MVP boundary of subscription management only: add a feed URL and display the subscription list. Any work beyond the MVP scope requires explicit approval, a documented scope change, and a review of complexity impact.

### II. Secure by default, even in a proof-of-concept
All external input MUST be treated as untrusted. Feed URLs and UI input MUST be isolated from logging, HTML rendering, and any future persistence layer. When feed fetching is added, parse and sanitize item content before display and never execute or render unescaped payloads.

### III. Keep architecture maintainable and modular
Backend and frontend responsibilities MUST remain separated with a clear API contract. In-memory storage is acceptable for MVP only; any persistence or background-processing change MUST be introduced behind a well-defined service or repository interface.

### IV. Write code that supports quality and inspection
Changes MUST be verifiable by build, manual smoke test, or automated test coverage for core behavior. The application MUST behave correctly for the MVP user flow: adding subscriptions and showing the list immediately.

### V. Manage dependencies and code quality deliberately
Dependency changes MUST be justified in PR notes and limited to packages that solve a real need. The project MUST avoid unnecessary libraries and favor built-in ASP.NET Core/Blazor APIs for maintainability and future upgrade stability.

## Project Constraints
The app is a minimal POC that must run locally across Windows, macOS, and Linux. For the MVP:
- Data storage MUST remain in memory only.
- No feed fetching, parsing, or validation is required.
- No template demo pages from the Blazor starter project may remain if they conflict with the single-page MVP route.
- Any deviation from the MVP constraints MUST be documented and reviewed before implementation.

## Development Workflow
All work MUST include a short description of the user-visible behavior or bug fixed.
- Every PR MUST verify the app builds cleanly and the MVP flow can be exercised.
- Changes to ports, CORS, or API routes MUST be tested with a live frontend/backend run before merge.
- Dependency updates and architecture changes MUST include rationale for how they preserve security, maintainability, and code quality.

## Governance
This constitution is the authoritative project governance guide for the RSS Feed Reader. Amendments require a documented rationale, a review of the change impact, and one additional reviewer sign-off for scope or architecture changes.

- Use this constitution to evaluate every feature addition, dependency change, and architecture decision.
- The team MUST reference the current project goals, app feature scope, and tech stack documents when proposing changes.
- If a proposed change conflicts with these principles, the burden of proof is on the proposer to explain why the principle should be amended.

**Version**: 1.0.0 | **Ratified**: 2026-08-04 | **Last Amended**: 2026-08-04
