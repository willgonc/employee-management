# research.md

## Decisions (resolved unknowns)

### 1) Technology alignment
Decision: Use ASP.NET Core Web API backend + Blazor WebAssembly frontend.
Rationale: Matches project TechStack.md and allows C# code-sharing if needed.
Alternatives considered: Single-project Blazor Server (rejected for clearer separation of responsibilities and local dev parity with Web API patterns).

### 2) Storage approach
Decision: In-memory `List<Subscription>` behind a repository interface.
Rationale: Simplest for MVP, supports replacing with persistent storage later.
Alternatives considered: EF Core + SQLite (deferred to Extended-MVP due to scope and time).

### 3) Security defaults
Decision: Treat input as untrusted; never render raw HTML from feeds; sanitize and escape any future feed content before display.
Rationale: Minimizes XSS and unsafe rendering risks.

## Open items (none)
All clarifications needed by the spec were resolved.
