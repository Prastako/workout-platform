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

### Future (priority)

- **What it is:** remote 1-on-1 personal training through an app. A human coach writes your plan. [V] [future.co](https://future.co/)
- **Target user:** adults who want a plan and accountability made for them and will pay a premium. [I] from price and positioning; confirm with Future's own audience data.
- **Key systems:**
  - Onboarding: survey, coach match, kickoff call in the app about goals, schedule, equipment and limitations. [V] [future.co](https://future.co/), [FAQ coach](https://faq.future.co/en/articles/12073321-what-should-i-expect-from-my-future-pro-coach)
  - Programming: the coach builds a weekly plan, refines it week by week from feedback, and rewrites it for travel or illness (for example hotel bodyweight days). [V] [FAQ coach](https://faq.future.co/en/articles/12073321-what-should-i-expect-from-my-future-pro-coach)
  - Library and guide: over 2,000 exercises, video demos, the coach's voice opens the session, audio form cues during it. [V] [FAQ workout](https://faq.future.co/en/articles/12073331-what-should-i-expect-from-a-future-pro-workout)
  - Session screen: report reps, adjust and log weight, exercise history with past weights and reps, a flag that swaps an exercise instantly, form video recording sent to the coach. [V] [FAQ workout](https://faq.future.co/en/articles/12073331-what-should-i-expect-from-a-future-pro-workout)
  - Rest timers: not described in any source found. Unverified.
  - Wearables: Apple Watch Series 4+ or WearOS 3+. Heart rate during workouts and daily activity go to the coach. [V] [FAQ smartwatch](https://faq.future.co/en/articles/12073347-do-i-need-a-smartwatch-to-use-future-pro). One tap on the watch advances to the next exercise. [V] [Better Living review, Jan 2026](https://onbetterliving.com/future-app/)
  - Injuries: medical clearance required, the coach excludes movements that do not suit you and adapts the plan over time. [V] [FAQ injury](https://faq.future.co/en/articles/12073374-what-if-i-have-an-injury-or-special-needs). A strongly disliked exercise is simply left out by the coach. [V] [Better Living](https://onbetterliving.com/future-app/)
  - Nutrition: general tips, recipes, food logs can be shared with the coach. No meal plans, no calorie or macro targets. [V] [FAQ nutrition](https://faq.future.co/en/articles/12240765-does-future-pro-include-nutrition)
  - Retention: daily accountability messages, the coach is notified of each completed workout. [V] [Better Living](https://onbetterliving.com/future-app/). Company claim: most members more consistent within 4 weeks. [V] as a claim, [future.co](https://future.co/)
  - AI: a free AI tier launched in February 2026 (engine built on their coaching data, selectable coach voice personalities). [V] [Athletech, Feb 2026](https://athletechnews.com/age-of-ai-human-personal-trainers-might-become-a-luxury-future-caliber/). It was scrapped in June 2026 to focus on human coaches. [V] [Athletech, Jun 2026](https://athletechnews.com/future-pulls-the-plug-on-ai-personal-training-commits-to-human-coaches/)
- **Business model:** $199 per month, first month $50, refund within 30 days. Longer plans: $179, $169, $149 per month for 3, 6, 12 months. [V] [FAQ pricing](https://faq.future.co/en/articles/12073382-membership-plans-pricing), [future.co](https://future.co/)
  - Conflict: the June 2026 article mentions a Core tier ($129) and a Premium tier ($399) with DEXA scans and lab tests. Not in the FAQ pricing article. [I] New tiers may be rolling out; confirm on Future's current sign-up flow.
- **Pain points:** [U] a coach not expert enough for injury changes, workouts that felt templated, coaches short on time ([App Store](https://apps.apple.com/us/app/future-pro-personal-training/id1288178982)). [U] coaches carry many clients ([Better Living](https://onbetterliving.com/future-app/)).
- **Ideas for us:**
  1. One-tap "flag" swap on an exercise during the session, replaced instantly. Improves our swap function.
  2. Show the last weight and reps for an exercise right where you log it (exercise history). Improves logging and is the base for progression.
  3. A personal "never give me this" list that generation respects. Improves generation and injury handling.
  - Lesson: Future's AI-only tier did not last. Their value is accountability and a person; ours is speed and no decisions. Do not copy the coach model, copy the low-friction session mechanics.

## Section 2: Per function of our app

_Filled after all apps._

## Section 3: Top 10 ideas

_Filled at the end._

## Section 4: Open questions for Jan

_Filled at the end._

## Sources

### Future
- https://future.co/
- https://faq.future.co/en/collections/18317406-future-pro
- https://faq.future.co/en/articles/12073321-what-should-i-expect-from-my-future-pro-coach
- https://faq.future.co/en/articles/12073331-what-should-i-expect-from-a-future-pro-workout
- https://faq.future.co/en/articles/12073347-do-i-need-a-smartwatch-to-use-future-pro
- https://faq.future.co/en/articles/12073374-what-if-i-have-an-injury-or-special-needs
- https://faq.future.co/en/articles/12240765-does-future-pro-include-nutrition
- https://faq.future.co/en/articles/12073382-membership-plans-pricing
- https://apps.apple.com/us/app/future-pro-personal-training/id1288178982
- https://onbetterliving.com/future-app/
- https://athletechnews.com/age-of-ai-human-personal-trainers-might-become-a-luxury-future-caliber/
- https://athletechnews.com/future-pulls-the-plug-on-ai-personal-training-commits-to-human-coaches/
