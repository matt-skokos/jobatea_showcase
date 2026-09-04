# JoBatea - Design Documentation Review

Reviewed: 2026-08-31
Scope: `application-flow-flowchart.md`, `architecture-class-diagram.md`, current frontend routes/components, and UI-facing API contracts. This is a documentation review only; it does not recommend changing application code in this artifact.

Note (2026-09-03): the two reviewed diagrams were retired rather than revised; see `design-changelog.md`. Their content lives on, corrected, in `deep-job-search-workflow-v1.md` and `agentic-job-search-loop-v1.md`.

## Summary

The two diagrams communicate the intended research-led product direction and the core user/job data relationships well. They are not yet reliable descriptions of the current user experience: research execution and scheduled runs are explicitly unimplemented, while several active UI surfaces and data interactions are absent.

## Findings

### 1. Separate current experience from future search automation

**Priority:** High

The application flow presents manual and scheduled research, LLM web search, ATS date verification, scoring, persistence, and result display as one continuous product flow. The current UI instead shows a disabled "Run Deep Search" control, while `researchService` and `matchScoringService` are stubs. The `Job` model also has no `postedAt` field.

**Recommendation:** Split the diagram into:

- **Current experience:** authentication, optional API key, welcome/setup wizard, resume upload or paste, guidance editing, an empty job-results state, manually created job records, applied tracking, and statistics.
- **Planned research workflow:** prerequisites, manual trigger, asynchronous progress, retry/failure handling, result review, persistence, and the planned ATS date-verification branch.

This prevents stakeholders from interpreting roadmap behavior as available interaction design.

### 2. Document the actual first-run path and prerequisite states

**Priority:** High

New users are routed to Deep Job Search after sign-up or login, not directly to the Dashboard. They may then need to provide an API key on a separate OpenAI Integration page and complete a setup wizard launched from the Profile Dashboard. The diagram does not show this route sequence, the optional-key decision, or the research-unavailable state.

**Recommendation:** Add a first-run flow with these states: account created or logged in, Deep Job Search with no criteria, Profile Dashboard, welcome acknowledgement, setup wizard, resume capture, optional API-key configuration, completed criteria, and unavailable-search messaging until the pipeline exists.

**Open product decision:** Is an OpenAI key required before search can run, or will the product provide a managed provider option? The future flow should not make the key a hard prerequisite until this is decided.

### 3. Expand the architecture diagram’s frontend and interaction coverage

**Priority:** Medium

The frontend section names Login, Dashboard, Stats, Navbar, WelcomeModal, and WizardModal, but the implemented shell is `AppShell`, not `Navbar`. It also omits the active `DeepSearch` and `OpenAiIntegration` pages, resume upload, inferred role suggestions, and the API client methods that support them.

**Recommendation:** Rename `Navbar` to `AppShell`; include `DeepSearch` and `OpenAiIntegration`; show `Dashboard` and `WizardModal` using resume upload and inferred-role endpoints; and clarify that jobs can currently be created, listed, marked applied, deleted, and summarized independently of research automation.

### 4. Mark conceptual fields and stored representations accurately

**Priority:** Medium

The architecture diagram labels several `PromptGuidance` attributes as string arrays, while the current schema stores them as JSON-encoded nullable strings. The diagram already labels `Job.postedAt` as proposed, which is helpful, but its surrounding narrative still relies on it as a delivered outcome.

**Recommendation:** Either model these fields as conceptual collections and state that explicitly, or show the storage representation. Keep proposed fields in a visually separate "planned" section to avoid ambiguity.

### 5. Add failure, partial-data, and accessibility design requirements

**Priority:** Medium

Neither diagram captures loading, API failure, missing resume content, failed resume extraction, expired download links, unsaved preference changes, disabled research, or confirmation for job removal. The current wizard also uses custom button-like toggles and modal behavior that need explicit keyboard, focus, and dialog requirements before implementation review.

**Recommendation:** Add a UI state matrix covering default, empty, loading, success, error, disabled, validation, and partial-data states for authentication, resume, guidance, research, results, and job actions. Include modal focus trapping, Escape behavior, keyboard-operable toggles/autocomplete, visible focus, error summaries, and non-color-only status indicators.

## Design Direction To Retain

- The flow correctly identifies the user’s core value: more trustworthy, better-ranked postings based on personal search criteria.
- The distinction between discovery time (`retrievedAt`) and a future authoritative posting date is a meaningful product concept worth preserving.
- Structured guidance, a reviewable setup summary, and resume-informed role suggestions are appropriate ways to reduce configuration effort.

## Recommended Documentation Sequence

1. Replace the current application flow with paired current-state and planned-state flows.
2. Update the architecture diagram to reflect current route and component ownership.
3. Add a UI requirements and state matrix for onboarding, search readiness, job results, and job management.
4. Add draft personas only after target job-seeker segments and the API-key/business model are confirmed.