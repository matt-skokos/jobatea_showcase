# Jobatea - Visual Design System and Flagship Screen v1

Status: Tentative high-fidelity direction for review.
Updated: 2026-08-31
Scope: Desktop flagship Deep Job Search screen. Functional behavior remains
defined in `deep-job-search-workflow-v1.md`.

## Direction

**Moss + Mineral** is the v1 direction: a calm career workspace with a subtle
field-research character. The batea reference appears in the app mark, thin
contour lines, and rare mineral-gold emphasis, not as literal mining decoration.
The intended feeling is relief from search noise and confidence in a capable,
detail-oriented partner.

### Alternate Palettes

- **Slate + Gold:** a cool blue-gray workspace with graphite and muted brass;
  strong future contender for a more technical, quietly premium tone.
- **Ink + Copper:** cool off-white, near-black navy, oxidized copper, and pale
  aqua; strong future contender for a more distinctive workshop character.

## Tokens

| Role | Token | Value |
| --- | --- | --- |
| Canvas | `--canvas` | `#F4F6F2` |
| Surface | `--surface` | `#FFFFFF` |
| Raised surface | `--surface-raised` | `#FBFCFA` |
| Primary ink | `--ink` | `#18302A` |
| Secondary ink | `--ink-muted` | `#60736A` |
| Moss primary | `--moss-700` | `#17634F` |
| Moss hover | `--moss-800` | `#10503F` |
| Moss soft | `--moss-50` | `#E7F1EB` |
| Mineral line | `--mineral-200` | `#D8E1DB` |
| Mineral panel | `--mineral-100` | `#EEF2EF` |
| Gold accent | `--gold-500` | `#C49332` |
| Gold soft/warning | `--gold-50` | `#FFF6E5` |
| Success | `--success-700` | `#287A5D` |
| Error | `--error-700` | `#B54436` |
| Focus | `--focus` | `#17634F` |

Light theme ships in v1. Token names intentionally support a future dark theme;
do not hard-code these values in components.

## Typography and Geometry

- UI type: humanist sans-serif, proposed `Source Sans 3`; implementation must
  provide a suitable fallback stack.
- Technical metadata: `IBM Plex Mono` at 11-12 px only for timestamps, source
  evidence, run IDs, and generated-sheet status.
- Page title: 28 px / 34 px, semibold. Section title: 16 px / 22 px, semibold.
  Body: 14 px / 20 px. Metadata: 12 px / 16 px.
- Spacing scale: 4, 8, 12, 16, 24, 32, 48 px. Operational components use 8 px
  radius; pills use full radius only for compact tags.
- Desktop reference: 1440 px wide. Sidebar 248 px; main max width 1184 px;
  content padding 40 px; 24 px grid gaps.

## Flagship Deep Job Search Screen

- A 64 px top bar holds the wordmark, a quiet current-workspace label, and an
  account menu. The icon uses `jobatea-batea-mark.svg`; wordmark casing is
  `Jobatea`.
- The sidebar is deep moss, with line icons and clear active state. It contains
  Deep Job Search, Profile and Criteria, Search History, Statistics, and
  account settings.
- The first content row states the current search scope and presents one
  primary `Start deep search` action.
- The compact Search Profile button is a 48 px donut paired with `85% complete`.
  Hover and focus open an accessible popover containing completed inputs,
  next-best improvement, and `Refine profile`.
- The generated Prompt Guidance Sheet has its own flat surface, a technical
  "saved guidance" status, readable grouped content, and an explicit review
  action. It is not styled as a text editor.
- Recent searches appears below, constrained to three rows. A current returned
  result count and source-verification cues make research state clear without
  turning the page into a dashboard.
- A small running-search placeholder occupies the result area while research is
  active: named phases, elapsed time, and confirmation that navigation is safe.

## Interaction and Accessibility

- Primary actions use `--moss-700`; hover uses `--moss-800`; focus is a
  2 px visible outline with 2 px offset. Target size is at least 40 px.
- The Search Profile control is a native button. Its popover supports keyboard
  focus, `aria-expanded`, Escape close, and focus return to the trigger.
- Status always combines text and color. The donut’s percentage and the search
  phase are available to assistive technology.
- Source dates use text labels such as `Verified employer date`, `Source date`,
  or `Date unavailable`; color alone never conveys reliability.
- Respect reduced motion. The running state may use a static phase indicator in
  place of animation.

## Handoff Boundaries

The visual screen is a target for the Frontend SWE after the active workflow
requirements. Search-run history, generated guidance snapshots, canonical
posting identity, and research states require the backend/data contracts listed
in `deep-job-search-workflow-v1.md`.