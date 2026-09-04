# JoBatea - Draft User Profiles

Status: Proposal pending product-lead review and user research.

These profiles are based on the product direction documented in the README and
project discussions: job seekers, with a slight emphasis on entry- and
early-career candidates, whose searches need more nuance than conventional job
board filters support. They describe needs and contexts, not demographic
segments.

## 1. The Early-Career Signal Builder

**Context:** Has limited professional experience and is applying for entry-level
or early-career technical roles. May have projects, internships, coursework, or
adjacent experience but is unsure how employers will interpret it.

**Goals**

- Find credible roles that match current skills and a realistic next step.
- Understand why a role is a plausible match before investing time in an
  application.
- Avoid spending hours on stale, duplicate, or clearly unsuitable postings.

**Behaviors and needs**

- Benefits from guided setup, examples, and plain-language explanations of
  criteria such as seniority, work style, and must-haves.
- Starts with a resume and is open to small, targeted suggestions, but seeks a
  separate tool or workflow for substantial resume rewriting.
- Needs results to surface transferable skills and clearly distinguish stretch
  opportunities from close matches.

**Frustrations**

- Entry-level labels that conceal several years of required experience.
- Reposted or already-closed listings and repetitive job-board results.
- A blank search setup that requires knowing the right terminology up front.

**Technical comfort:** Comfortable with common web forms and job boards; may be
less comfortable deciding how search criteria affect results.

**Design implications:** Make setup resumable and progressive, show actionable
missing prerequisites on Deep Job Search, and explain match scores with concise
evidence rather than an unexplained percentage.

## 2. The Discreet Senior Specialist

**Context:** Currently employed in a senior technical or leadership role and
exploring selectively. The search may be confidential and time-constrained.

**Goals**

- Identify a small set of high-quality roles with specific scope, seniority,
  compensation, company, and work-style requirements.
- Keep research organized without broadcasting search activity or repeatedly
  recreating criteria.
- Verify source quality and posting freshness before applying.

**Behaviors and needs**

- Uses detailed preferences, must-haves, avoid lists, target companies, and
  location constraints.
- Reviews results in batches and expects a durable record of what was found,
  saved, applied to, or dismissed.
- Has a polished resume but welcomes small role-specific feedback.

**Frustrations**

- High-volume alerts dominated by loosely related roles.
- Generic filters that cannot express team scope, technical domain, or specific
  dealbreakers.
- Unclear job provenance, duplicate listings, and ambiguous dates.

**Technical comfort:** High. Expects controls to be efficient, predictable, and
easy to revise without losing prior work.

**Design implications:** Prioritize compact result comparison, transparent
criteria, reliable saved search state, and clear source/date evidence. Avoid
requiring extensive wizard repetition for routine refinements.

## 3. The Domain-Constrained Practitioner

**Context:** Works in a technical or adjacent specialist field where viable jobs
depend on nuanced domain, regulatory, clearance, certification, stack, or
location constraints.

**Goals**

- Find opportunities where multiple non-negotiable requirements intersect.
- Reduce false positives that mention relevant keywords but do not satisfy the
  actual role context.
- See why a result passed or failed key requirements.

**Behaviors and needs**

- Expresses requirements in natural language because traditional filters do not
  capture the needed nuance.
- May accept adjacent titles if the work itself is relevant.
- Needs to adjust constraints as market feedback reveals that a search is too
  broad or too narrow.

**Frustrations**

- Keyword search conflates unrelated specialties.
- Boolean-style filtering is opaque or impossible to use across job boards.
- Results do not reveal which constraint caused a weak match.

**Technical comfort:** Varies. Domain expertise is high, but search-tool fluency
is not assumed.

**Design implications:** Support structured criteria alongside free-text
guidance, present match rationales and exclusions, and make filters reviewable
and editable from the search screen.

## 4. The Intentional Career Changer

**Context:** Moving into a new technical or technical-adjacent field, often
while balancing current work, training, or personal commitments.

**Goals**

- Find roles where adjacent experience can be valuable despite a non-linear
  resume.
- Learn which target roles are realistic now versus longer-term possibilities.
- Spend effort only on opportunities that accommodate essential constraints.

**Behaviors and needs**

- Begins with broad role ideas and refines them after seeing candidate matches.
- Needs help translating prior experience into target-role language, while
  retaining control of their resume and final applications.
- May have firm requirements around remote work, location, schedule, salary, or
  junior-friendly expectations.

**Frustrations**

- Conventional job boards rank exact-title matches above credible adjacent work.
- Role recommendations feel either overconfident or too generic.
- Application advice frequently assumes a conventional career path.

**Technical comfort:** Moderate. Comfortable evaluating examples and guided
recommendations; wants understandable reasoning before trusting automation.

**Design implications:** Make inferred role suggestions selectable rather than
authoritative, distinguish close matches from stretch matches, and keep the
search setup easy to revise as the candidate learns.

## 5. The High-Constraint Opportunity Seeker

**Context:** Any career stage, but the search is governed by several constraints
that must be reconciled: geography, remote/hybrid policy, relocation, work
authorization, caregiving schedule, compensation floor, industry exclusions, or
target employers.

**Goals**

- Discover viable roles without repeatedly evaluating obvious non-starters.
- Understand tradeoffs when the combination of requirements produces few
  results.
- Maintain control over sensitive or personal constraints.

**Behaviors and needs**

- Uses strict must-haves and an avoid list, then selectively relaxes criteria
  when appropriate.
- Needs transparent indication of which constraints are confirmed, inferred, or
  unavailable from a source listing.
- May use the product intermittently during narrow windows of availability.

**Frustrations**

- Filters that treat non-negotiable requirements as soft preferences.
- A zero-results page with no explanation or next step.
- Being pressured to disclose unnecessary personal details to improve a search.

**Technical comfort:** Varies; expects privacy, accessible language, and a clear
way to correct the system.

**Design implications:** Treat constraints as first-class inputs, distinguish
missing data from a failed match, offer reversible constraint adjustments, and
never require sensitive details that are not necessary for search quality.

## Cross-Profile Design Requirements

- Deep Job Search should be the post-auth destination and show active criteria,
  readiness gaps, and a direct path to refine inputs.
- The agentic search experience must explain what it considered, what it found,
  and why results were ranked, filtered, or unavailable.
- Resume review should support concise, user-controlled micro-suggestions;
  substantial drafting belongs in a separate workflow.
- Search and result states must accommodate limited data, missing or conflicting
  job details, failures, and long-running research work.
- User research should validate these profiles before they guide prioritization
  or interface commitments.