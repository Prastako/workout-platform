# Competitor research: how other fitness apps solve the functions we are designing

- Research only. Nothing here is a decision until Jan approves it.
- As of 2026-09-23. Work in progress: filled app by app, pushed after each app.
- Labels on every finding:
  - **[V]** verified, with source link
  - **[U]** user reports (reviews, forums), pain points only
  - **[I]** inference, with what would confirm it
- Paraphrased throughout. No copied texts.

## Our app baseline (what the comparison is against)

- The Project docs (claude/handoff.md, claude/atlas-plan.md, claude/platform-architecture.md) were not reachable from this session. The baseline below comes from the repo (`index.html`, `master_catalog_v3.json`) plus the function list in the research brief.
- [I] The repo `index.html` may be older than the test site. Example: the brief lists a day type suggestion from history, but the repo code has no such logic. Confirm by comparing with the current test site.
- Home: Push, Pull, Legs, Full Body tiles, Catalog, Tips and Guides (with an "Ask Claude" chat), last 3 recent sessions (stored in the browser, last 10 kept).
- Configure: duration pills (45, 90, 120 min, custom 20 to 240), five option rows (Goal, Style, Volume, Pace incl. Deload and Supersets, Equipment), "+ Core / Abs" toggle, 4 emphasis chips per day type, free-text box.
- Generation: one Claude call. Catalog filtered by day type, up to 160 exercises sent, prompt rules for warm-up (3 to 4 dynamic), main block (count scales with duration), cool-down (2 to 3 static), plus coaching rules (no repeated pattern, muscle head coverage, equipment variety, compound before isolation).
- Session screen: exercises grouped by muscle, a done checkbox per exercise, "redo" per section, tap opens the exercise sheet (3D, demo, guide with steps and cues). No set, rep or weight logging, no rest timer.
- Catalog: 1,223 exercises with primary and secondary muscles, equipment, mechanic, force, level, instructions, cues, day type. Filters: day type, mechanic, equipment. No explicit movement pattern field.
- Not present: progression system, injury handling beyond free text, onboarding and profile, coach, wearables, nutrition, retention features, paid tiers.

## Section 1: Per app

_Filled app by app._

## Section 2: Per function of our app

_Filled after all apps._

## Section 3: Top 10 ideas

_Filled at the end._

## Section 4: Open questions for Jan

_Filled at the end._

## Sources

_Collected per app._
