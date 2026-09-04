# Design Changelog

| Date | Artifact | Summary |
| --- | --- | --- |
| 2026-09-03 | `application-flow-flowchart.md`, `architecture-class-diagram.md` | Retired the early application-flow and architecture-class diagrams once their content was superseded by `deep-job-search-workflow-v1.md` and `agentic-job-search-loop-v1.md`. |
| 2026-08-31 | `agentic-job-search-loop-v1.md` | Defined the initial deterministic scoring model: user-policy gates, normalized weights, explainable category evidence, 70-point preference threshold, and lower-confidence fallback selection. |
| 2026-08-31 | `agentic-job-search-loop-v1.md` | Selected Greenhouse's public structured job endpoint as the first posting-verification adapter; it verifies canonical job identity but does not claim its update timestamp is an authoritative posting date. |
| 2026-08-31 | `agentic-job-search-loop-v1.md` | Selected Tavily as the initial development discovery provider, with a default cap of five results and a hard cap of 10 per planned query; direct ATS/employer verification remains a separate stage. |
| 2026-08-31 | `agentic-job-search-loop-v1.md` | Recorded v1 execution policy: user-selected $k$ capped at 10, $3k$-minute hard runtime, $150k$ all-page fetch budget, token cap, threshold/fallback selection, freshness constraints, and promotable cold leads. |
| 2026-08-31 | `agentic-job-search-loop-v1.md` | Defined the planned seven-stage, bounded research loop for returning up to $k$ verified, unique, ranked job postings, including provider boundaries, lifecycle states, and implementation decisions. |
| 2026-08-31 | `design-review-2026-08-31.md` | Recorded gaps between the existing diagrams and the current UI, data model, and planned research workflow. |
| 2026-08-31 | `user_profiles/job-seeker-profiles.md` | Added five draft profiles for nuanced technical and constraint-heavy job searches. |
| 2026-08-31 | `archive/ui-requirements.md` | Archived general UI requirements after consolidation into the active v1 workflow handoff. |
| 2026-08-31 | `archive/onboarding-search-readiness-spec.md` | Archived readiness specification after consolidation into the active v1 workflow handoff. |
| 2026-08-31 | `archive/onboarding-search-readiness-low-fi.svg` | Added editable low-fidelity desktop references for missing-resume, broad-search, and refined-profile states. Superseded by the consolidated v1 workflow. |
| 2026-08-31 | `archive/onboarding-search-history-v1-spec.md` | Archived v1 guidance/history specification after consolidation into the active workflow handoff. |
| 2026-08-31 | `archive/onboarding-search-history-v1-low-fi.svg` | Added editable low-fidelity Deep Search and Search History screen references. Superseded by the consolidated v1 workflow. |
| 2026-08-31 | `deep-job-search-workflow-v1-low-fi.svg` | Consolidated the tentative v1 desktop workflow from resume setup through returned results and history. |
| 2026-08-31 | `deep-job-search-workflow-v1.md` | Added the v1 screen inventory, approved decisions, primary flow, and engineering handoff. |
| 2026-08-31 | `jobatea-batea-mark.svg` | Added the minimalist v1 Jobatea batea logo mark. |
| 2026-08-31 | `deep-job-search-hifi-v1.md` | Defined the Moss and Mineral visual system and flagship-screen specifications. |
| 2026-08-31 | `deep-job-search-hifi-v1.svg` | Added the polished desktop Deep Job Search flagship visual reference. |