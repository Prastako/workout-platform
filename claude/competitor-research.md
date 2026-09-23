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

### Juggernaut AI (priority)

- **What it is:** algorithmic strength programming for powerlifting and powerbuilding, designed by coach Chad Wesley Smith. No human coach in the loop. [V] [juggernautai.app](https://www.juggernautai.app/), [App Store](https://apps.apple.com/us/app/juggernautai/id1515756471)
- **Target user:** beginner to advanced powerlifters, over 250,000 users (company claim). [V] [juggernautai.app](https://www.juggernautai.app/)
- **Key systems:**
  - Onboarding: sex, age, body size, current strength, experience, goal, days per week (2 to 6), optional competition date. [V] [JTS, How it works, 2021](https://www.jtsstrength.com/how-juggernautai-works/), [juggernautai.app](https://www.juggernautai.app/)
  - Program generation: sets frequency per main lift, periodization style and volume landmarks from the inputs; picks accessories for your weak points. [V] [JTS](https://www.jtsstrength.com/how-juggernautai-works/), [App Store](https://apps.apple.com/us/app/juggernautai/id1515756471)
  - Adaptation layers: before the session, during it, session to session, week to week, block to block, program to program. [V] [JTS](https://www.jtsstrength.com/how-juggernautai-works/)
  - Readiness check-in before each session: sleep, mood, diet, recovery, bodyweight, fatigue per body part, injuries. Produces a readiness score. [V] [Garage Gym Experiment, 2022](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/). Since V3.0 the score is 0 to 100 with zones and the check-in takes half the time. [V] [V3.0 blog](https://www.juggernautai.app/blog/juggernautai-v3-0-is-here)
  - Readiness effect: a sore body part lowers the load for that session only, not the whole block. [V] as reviewer description, [Garage Gym Reviews listing snippet](https://www.garagegymreviews.com/juggernautai-review) (page itself returned 404 when opened, so treat as [U])
  - Per-set feedback: you log weight and RPE or RIR after each set; the next sets and next sessions adjust up or down. After the session you rate difficulty (5 to 10). [V] [Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/)
  - Deloads and blocks: block periodization through hypertrophy, strength and peaking phases, with built-in deloads; you can shift the schedule so deloads land well. [V] [Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/). Exact deload rules are not public. Unverified.
  - Swaps: swap an exercise for one day or for a whole block, from a list that keeps the same training purpose. Main lifts stay fixed. [V] [Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/), [AI Tools Bakery, Sep 2026](https://aitoolsbakery.com/blog/juggernautai-review/)
  - Warm-up: generated per day from that day's lifts, about 10 minutes, skippable; warm-up ramp sets with plate math. [V] [Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/), [juggernautai.app](https://www.juggernautai.app/)
  - Session screen (V3.0): full block view with past and upcoming weeks, rest timer set per lift type and shown on the phone lock screen, voice cues, beeps or silent, quick access to exercise history and lifetime maxes. [V] [V3.0 blog](https://www.juggernautai.app/blog/juggernautai-v3-0-is-here)
  - Guide: over 300 technique videos with coaching cues; custom exercises allowed. [V] [juggernautai.app](https://www.juggernautai.app/)
  - Progress views: year-long completion tracker, sleep and bodyweight trends, strength graphs, calendar grid. [V] [V3.0 blog](https://www.juggernautai.app/blog/juggernautai-v3-0-is-here)
  - Wearables: no Apple Health or Garmin sync reported. [U] [AI Tools Bakery](https://aitoolsbakery.com/blog/juggernautai-review/). Unverified on the official site.
- **Business model:** $34.99 per month or $349.99 per year, 2-week free trial. Annual plan adds a consultation with the head coach, seminars and e-books. [V] [juggernautai.app](https://www.juggernautai.app/)
- **Pain points:** [U] volume can exceed what some users recover from; honest RPE is required or loads drift; warm-up suggestions sometimes clash with readiness limits; timer notification bugs; narrow scope (big three). [App Store](https://apps.apple.com/us/app/juggernautai/id1515756471), [AI Tools Bakery](https://aitoolsbakery.com/blog/juggernautai-review/)
- **Ideas for us:**
  1. Per-set effort tap (for example easy, right, hard, or RIR 0 to 3+) that sets the next weight for that exercise. Improves progression, our biggest gap.
  2. A 10-second readiness check before generating (sleep, soreness per area, pain) that adjusts only today's session, or pre-selects "Deload". Improves configure and injury handling without adding decisions.
  3. Swap list limited to exercises with the same purpose (same pattern and muscle), for today or for good. Improves swap.
  - Watch-out: the whole system depends on honest effort ratings. Keep the input to one tap and show why the weight changed.

### Trainerize (ABC Trainerize)

- **What it is:** software for personal trainers and gyms to deliver programs, nutrition and messaging to their clients through a (brandable) client app. [V] [Pricing](https://www.trainerize.com/pricing/)
- **Target user:** coaches and studios (the payer); their clients use the app. [V] [Pricing](https://www.trainerize.com/pricing/)
- **Key systems:**
  - Programming is manual by the coach: master workouts, programs split into training phases, scheduled on a client calendar. [V] [Progressions article](https://help.trainerize.com/hc/en-us/articles/212130826-Progressing-Regressing-Workouts-with-the-Progressions-Spreadsheet)
  - Progression: a "Progressions Spreadsheet" shows every scheduled instance of one workout in a timeline; the coach edits weight, reps, rest or swaps an exercise per day, and can drag a day's targets to the next. Nothing is automatic. [V] [Progressions article](https://help.trainerize.com/hc/en-us/articles/212130826-Progressing-Regressing-Workouts-with-the-Progressions-Spreadsheet)
  - AI Workout Builder (open beta): the coach chats a prompt (or picks from a prompt library, or uploads CSV, Excel, PDF), gets a draft with exercises, sets, reps, rest, supersets and duration, refines it in chat, then confirms. One workout at a time, no programs, chat history not saved. [V] [AI builder article](https://help.trainerize.com/hc/en-us/articles/45565151151508-Using-the-AI-Workout-Builder)
  - AI context from the client is deliberately limited: age, sex, height, latest weight (last 3 months), up to 10 workouts and 10 cardio sessions from the last 3 months. Client data is not used to train the model. [V] [AI builder article](https://help.trainerize.com/hc/en-us/articles/45565151151508-Using-the-AI-Workout-Builder)
  - Client session screen: tap "Track", enter stats per set, stats save even without tapping "End", notes per workout, rest timer launches from rests the coach placed in the sequence, a separate countdown stopwatch, chime at the end. [V] [Mobile app article](https://help.trainerize.com/hc/en-us/articles/208689026-How-do-I-use-the-mobile-app-when-I-m-working-out)
  - Swap during a session: the client edits the workout (delete an exercise, insert another). A manual edit, not a suggested substitute. [V] [Mobile app article](https://help.trainerize.com/hc/en-us/articles/208689026-How-do-I-use-the-mobile-app-when-I-m-working-out)
  - Supersets and circuits: the coach selects exercises, ticks "Superset", sets rounds and rest after each exercise or round. [V] per search snippet of the help center; article page not opened, so [I] until opened.
  - Nutrition, habits and wearables: habit coaching on the free tier; meal and macro tracking and wearable integrations from Grow up; MyFitnessPal and Fitbit links for nutrition. [V] [Pricing](https://www.trainerize.com/pricing/), related article titles on the [Mobile app article](https://help.trainerize.com/hc/en-us/articles/208689026-How-do-I-use-the-mobile-app-when-I-m-working-out)
  - Retention: leaderboard and threshold challenges (Pro), custom welcome emails. [V] [Pricing](https://www.trainerize.com/pricing/)
- **Business model:** paid by the coach. Basic free (1 client, no AI), Grow $9 per month (2 clients, AI builder, nutrition, wearables), Pro from $23 per month (5 to 200 clients), Studio Plus from $248 per month. Add-ons $10 to $45 per month, branded app $169 one-time. 30-day trial without card, but the AI builder is excluded from the trial and free plan. [V] [Pricing](https://www.trainerize.com/pricing/), [AI builder article](https://help.trainerize.com/hc/en-us/articles/45565151151508-Using-the-AI-Workout-Builder)
- **Pain points:** not researched in depth; Trainerize is a coach tool, so client-side reviews are less relevant for us.
- **Ideas for us:**
  1. Send the AI only a small, fixed slice of history (for example the last 10 sessions and latest body weight), and state that personal data is not used for training. Improves generation and is a ready GDPR pattern for the platform plan.
  2. A timeline view per exercise (every past session in one row: weight, reps) as the manual fallback for progression. Improves progress views.
  3. Stats save continuously, no "Finish" required. Improves the session screen.

### Sensai (SensAI)

- **What it is:** an iOS AI personal trainer: an LLM coach plus a workout planner and tracker that reads recovery data from wearables. [V] [sensai.fit](https://www.sensai.fit/), [App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099)
- **Target user:** gym-goers who wear an Apple Watch, Garmin, Oura or WHOOP and want the plan to react to recovery. [V] company positioning, [SensAI review page, Jul 2026](https://www.sensai.fit/blog/sensai-review-2026). Note: that "review" is on SensAI's own blog, so treat its claims as company claims.
- **Key systems:**
  - Onboarding: goals, equipment, schedule, session length, training days, injuries and pain. [V] [SensAI blog](https://www.sensai.fit/blog/sensai-review-2026)
  - Generation: builds a program from scratch; regenerates it weekly from what you actually did and how you recovered, instead of rewriting every morning. [V] [sensai.fit](https://www.sensai.fit/), [SensAI blog](https://www.sensai.fit/blog/sensai-review-2026)
  - Readiness: HRV, sleep, resting heart rate and training load through Apple Health; daily recovery summary; one low reading triggers a check of the other signals, not an automatic cut. [V] [SensAI blog](https://www.sensai.fit/blog/sensai-review-2026)
  - Mid-session changes by plain language: "make it shorter", "my knee hurts, swap the lunges", "this machine is taken". The coach remembers injuries and preferences across sessions. [V] [SensAI blog](https://www.sensai.fit/blog/sensai-review-2026), [App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099)
  - Photo input: form feedback, meal evaluation, identifying gym equipment from a photo. [V] [sensai.fit](https://www.sensai.fit/)
  - Session screen: set-by-set tracking, planned vs performed sets, muscle illustrations, automatic rest timers on the lock screen, heart rate zones, works offline, full workout control from Apple Watch (added in 1.1.5). [V] [App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099), [sensai.fit](https://www.sensai.fit/)
  - Loads: remembers weights, pre-fills matching sets, estimates a starting load for new exercises. [V] [App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099)
  - Guide: over 500 exercises with animated demonstrations. [V] [App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099)
  - AI limits: stated as not diagnosing pain; no usage cap found. How chat usage is limited is unverified.
- **Business model:** $6.99 per month or $69.99 per year, 7-day full trial without card. iOS only. [V] [App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099), [SensAI blog](https://www.sensai.fit/blog/sensai-review-2026)
- **Pain points:** [U] app hangs, the AI forgets preferences between sessions, cannot log exercises outside the library; only 32 ratings so far. [App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099)
- **Ideas for us:**
  1. Pre-fill each set with the last weight used, and estimate a starting weight for a new exercise from related lifts. Improves logging and progression.
  2. Short plain-language changes during the session ("shorter", "knee hurts", "machine taken") on top of our "redo" button. Our free-text box already does this before generation; extend it to the session screen. Improves swap and injury handling.
  3. Multi-signal readiness: never cut a session because of one bad number. Relevant later if we add wearables.

### Trainwell

- **What it is:** remote 1-on-1 personal training by human trainers, with smartwatch motion tracking during workouts. Formerly named CoPilot. [V] [trainwell.net](https://www.trainwell.net/), [Sports Nerd](https://sports-nerd.com/brand/trainwell/) (former name, search listing)
- **Target user:** busy adults training at home, gym or hotel who want a person to plan and check on them. [V] [trainwell.net](https://www.trainwell.net/)
- **Key systems:**
  - Onboarding: quiz, suggested trainer matches, you choose; switch trainer any time, as often as you want. Trial starts with a 40-minute call. [V] [trainwell.net](https://www.trainwell.net/), [FAQ](https://www.trainwell.net/faq)
  - Programming: the trainer writes plans for your goals, equipment, schedule and location (home, gym, hotel). [V] [trainwell.net](https://www.trainwell.net/). A reviewer describes 4-week programs with progression, adjusted for time, intensity and focus. [V] as reviewer account, [Monica Denais, Mar 2025](https://monicadenais.com/trainwell-review)
  - Feedback loop: you give feedback after each workout and overall, and message the trainer; the trainer reviews workouts as they happen. [V] per [Trainwell blog](https://www.trainwell.net/blog/the-best-personal-trainer-app-for-working-out-at-home-and-traveling) via search listing; page not opened, so [I] until confirmed.
  - Session screen: exercise videos with how-to, the trainer's voice tells you what comes next, live feedback on pace and form. [V] [trainwell.net](https://www.trainwell.net/)
  - Watch: Apple Watch Series 5+ or WearOS 3+ tracks sets, pace and range of motion automatically. Optional. Garmin and Fitbit via Apple Health or Google Health. [V] [FAQ](https://www.trainwell.net/faq), [trainwell.net](https://www.trainwell.net/)
  - Swaps and rescheduling: a workout can be postponed one day without contacting the trainer; bigger changes go through the trainer. [U] [Monica Denais](https://monicadenais.com/trainwell-review)
  - Nutrition: habits and general tips from the trainer, no meal plans. [V] [FAQ](https://www.trainwell.net/faq)
  - Retention: workout streaks, trainer check-ins. [V] [trainwell.net](https://www.trainwell.net/)
- **Business model:** $149 per month billed quarterly, 14-day free trial, HSA/FSA eligible. [V] [FAQ](https://www.trainwell.net/faq). A 2025 reviewer paid $150 monthly or $297 per quarter. [U] [Monica Denais](https://monicadenais.com/trainwell-review)
- **Pain points:** [U] rep tracking inaccurate ([Garage Gym Reviews](https://www.garagegymreviews.com/trainwell-fitness-review), opened in a browser); outside activities like Pilates or running do not count toward the streak; limited self-service rescheduling ([Monica Denais](https://monicadenais.com/trainwell-review)).
- **Ideas for us:**
  1. A 1-question feedback after each session ("too easy, right, too hard") that the next generation reads. Improves progression with almost no friction.
  2. Streaks that count any logged training, including outside activities, so a run does not break the chain. Improves retention.
  - Watch-based rep counting is error-prone per user reports; not worth it for us early.

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

### Juggernaut AI
- https://www.juggernautai.app/
- https://www.juggernautai.app/blog/juggernautai-v3-0-is-here
- https://apps.apple.com/us/app/juggernautai/id1515756471
- https://www.jtsstrength.com/how-juggernautai-works/
- https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/
- https://aitoolsbakery.com/blog/juggernautai-review/
- https://www.garagegymreviews.com/juggernautai-review (search snippet only, page returned 404)

### Trainerize
- https://www.trainerize.com/pricing/
- https://help.trainerize.com/hc/en-us/articles/208689026-How-do-I-use-the-mobile-app-when-I-m-working-out
- https://help.trainerize.com/hc/en-us/articles/45565151151508-Using-the-AI-Workout-Builder
- https://help.trainerize.com/hc/en-us/articles/212130826-Progressing-Regressing-Workouts-with-the-Progressions-Spreadsheet

### Sensai
- https://www.sensai.fit/
- https://www.sensai.fit/blog/sensai-review-2026 (company blog)
- https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099

### Trainwell
- https://www.trainwell.net/
- https://www.trainwell.net/faq
- https://monicadenais.com/trainwell-review
- https://www.garagegymreviews.com/trainwell-fitness-review
- https://www.trainwell.net/blog/the-best-personal-trainer-app-for-working-out-at-home-and-traveling (search listing only)
- https://sports-nerd.com/brand/trainwell/ (search listing only)
