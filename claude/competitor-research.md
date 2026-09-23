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

### Shred

- **What it is:** coach-built strength programs personalized by AI, plus studio classes (HIIT, yoga, dance cardio). [V] [shred.app](https://www.shred.app/)
- **Target user:** gym and home lifters from beginner up, with separate programs for men and women. [V] [shred.app](https://www.shred.app/)
- **Key systems:**
  - Onboarding: short assessment of goals, equipment, gym size (large, medium, small, hotel, home) and preferences. [V] [shred.app](https://www.shred.app/)
  - Generation: human coaches write base programs (hypertrophy, strength, powerlifting, bodyweight, sculpting); AI fits them to schedule, space and goal. [V] [shred.app](https://www.shred.app/), [App Store](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)
  - Equipment switch: one tap rebuilds the workout for dumbbells, barbell, bands or bodyweight. [V] [shred.app](https://www.shred.app/). Users say saved equipment is not applied automatically and alternatives must be picked by hand. [U] [App Store](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)
  - Swaps: exercise alternates rebuilt on muscle-level metadata and training logic; saved alternates in training settings; a "Build Your Own" mode with filtering and swapping. [V] [App Store version history](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)
  - Warm-up: dynamic warm-ups added in a recent version. [V] [App Store version history](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)
  - Progression: suggested weight and tempo per set, automatic rest timing, weekly adjustment from strength or body changes. [V] [shred.app](https://www.shred.app/). Reviewers confirm starting suggestions for reps and weight. [V] per review snippet, [Garage Gym Reviews](https://www.garagegymreviews.com/shred-app-review) (page not readable here, so [U])
  - Session screen: coach audio cues and form cues, videos, heart rate from Apple Watch or AirPods Pro with audio announcements. [V] [App Store](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)
  - After the session: AI-written workout summary. [V] [App Store version history](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)
  - Progress and social: charts for weight, reps and records, comparison with other users, friend challenges, gym leaderboards, a live feed of friends' sessions, partner workouts. [V] [shred.app](https://www.shred.app/)
- **Business model:** limited free tier; premium $12.99 per month (7-day trial), $99.99 per year, also a $9.99 weekly option. [V] [App Store](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095). Third-party figures ($19.99 month, $119.99 year) differ. [I] prices vary by region or offer; confirm in the app.
- **Pain points:** [U] videos need internet, stretching only as video classes, fixed 5-minute finisher. [App Store](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)
- **Ideas for us:**
  1. Alternates chosen by muscle-level metadata (same target muscle and pattern), and remembered once picked ("saved alternates"). Improves swap and uses the atlas data we already have.
  2. One tap "I only have dumbbells today" that rebuilds the session. We have an Equipment row; this puts it on the session screen. Improves swap.
  3. A short auto-written summary after the session (what improved, what next time). Improves retention and progression.

### Caliber

- **What it is:** a strength training app with a free logger, a paid plans tier with a Strength Score, and a premium human coaching tier. [V] [App Store](https://apps.apple.com/us/app/caliber-strength-training/id1482405410), [caliberstrong.com](https://caliberstrong.com/)
- **Target user:** people who want to get stronger and improve body composition, from self-guided lifters to those paying for a coach. [V] [caliberstrong.com](https://caliberstrong.com/)
- **Key systems:**
  - Free tier: unlimited custom workouts, over 800 exercises with tutorials, training with friends, Apple Health sync. [V] [App Store](https://apps.apple.com/us/app/caliber-strength-training/id1482405410)
  - AI connection: an MCP server (added in version 5.15.0) lets users connect their Caliber training data to ChatGPT or Claude. Free. [V] [App Store](https://apps.apple.com/us/app/caliber-strength-training/id1482405410). Caliber's own AI coaching inside the app was not found. Unverified.
  - Strength Score (paid): estimated 1RM per exercise, multiplied by a bodyweight factor, scored per muscle group (legs split into quad and hamstring work; chest, back, shoulders, arms), weighted by body mass, adjusted for age and sex, levels from Beginner (100) to Elite (600). Recomputed weekly. [V] [Strength Score guide](https://caliberstrong.freshdesk.com/support/solutions/articles/48001257574-strength-score-user-guide)
  - Strength Balance: shows whether muscle groups develop evenly; coaching members aim for 90%+. [V] [caliberstrong.com](https://caliberstrong.com/), [Strength Score guide](https://caliberstrong.freshdesk.com/support/solutions/articles/48001257574-strength-score-user-guide)
  - Honest score explanations: a help article explains why the score can dip when you add weight (fewer reps lower the estimate) and tells you to watch the trend. [V] [Score drop article](https://caliberstrong.freshdesk.com/support/solutions/articles/48001225489-why-did-my-muscle-group-strength-score-drop-even-though-i-increased-weight-on-an-exercise-)
  - Plus tier: over 120 coach-designed plans, nutrition lessons, custom exercises and supersets, progress photos. [V] [App Store](https://apps.apple.com/us/app/caliber-strength-training/id1482405410)
  - Premium coaching: assessment, a coach plans strength, cardio, nutrition and habits; video form reviews, daily messaging, weekly reviews; money back if body composition does not improve 20% in 12 weeks. [V] [App Store](https://apps.apple.com/us/app/caliber-strength-training/id1482405410), [caliberstrong.com](https://caliberstrong.com/)
  - Progress views: redesigned charts per activity type, progress photo gallery with comparisons. [V] [App Store version history](https://apps.apple.com/us/app/caliber-strength-training/id1482405410)
- **Business model:** Free forever; Plus $9 to $12 per month or $36 to $72 per year; a $3 "Supporter" option; Premium coaching about $200 per month. [V] [App Store](https://apps.apple.com/us/app/caliber-strength-training/id1482405410), [Athletech, Feb 2026](https://athletechnews.com/age-of-ai-human-personal-trainers-might-become-a-luxury-future-caliber/)
- **Pain points:** [U] score accuracy could be better; few complaints visible. [App Store](https://apps.apple.com/us/app/caliber-strength-training/id1482405410)
- **Ideas for us:**
  1. A per-muscle strength and balance view built from logged sets (estimated 1RM per exercise, grouped by muscle). Fits the atlas muscle map directly. Improves progress views.
  2. Instead of paying for AI calls, let users connect their own AI assistant to their data (Caliber's MCP route). Relevant to the platform plan and to AI cost limits.
  3. Explain metric dips in plain words inside the app. Improves trust in progression.

### NordicTrack (iFIT software and programs)

- **What it is:** NordicTrack machines run on iFIT, a class and program platform with over 10,000 trainer-led workouts, an AI coach, and a newer standalone phone app (iFIT Personal Trainer) for strength, HIIT, yoga and more without machines. [V] [AI Coach release notes, Sep 2024](https://www3.ifit.com/blog/connect/ai-coach-beta-release-notes), [App Store](https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504)
- **Target user:** home exercisers, many of them NordicTrack or ProForm owners. [V] [AI Coach release notes](https://www3.ifit.com/blog/connect/ai-coach-beta-release-notes)
- **Key systems:**
  - AI Coach (beta, 2024): sets goals with you, builds a plan mixing iFIT series, schedules workouts to the calendar, reminds you the night before, flags missed workouts, weekly check-ins, celebrates milestones. Ran over SMS, US members with iFIT equipment only. [V] [AI Coach release notes](https://www3.ifit.com/blog/connect/ai-coach-beta-release-notes)
  - Tailor (current app): AI builds a daily and weekly plan from goals, level, health data, history, available equipment and time; pulls Apple Health and MyFitnessPal data. [V] [App Store](https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504)
  - Recent app features: choose the AI trainer's personality, improved warm-ups, streak credit for workouts done outside iFIT, 1-rep-max tracking, outdoor running coach. [V] [App Store version history](https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504)
  - SmartAdjust: intensity for a workout is set from your past iFIT history; when you override speed or incline, the system learns your pattern. [V] [Connect The Watts, Mar 2021](https://connectthewatts.com/2021/03/16/ifit-details-smartadjust-and-activepulse-features-to-automate-your-workouts/)
  - ActivePulse: live heart rate keeps you in a target zone by changing speed, incline or resistance automatically. Machine feature, noted only for its logic. [V] [Connect The Watts](https://connectthewatts.com/2021/03/16/ifit-details-smartadjust-and-activepulse-features-to-automate-your-workouts/)
  - Guide: visual movement demonstrations, 180+ trainers. [V] [App Store](https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504)
- **Business model:** iFIT Train about $15 per month (1 user), iFIT Pro about $39 per month (up to 5 users, needed for touchscreen machines). [U] third-party figures via search, the official membership page blocked reading. The new app sells Tailor+ at $19.99 per month and Train and Tailor+ at $24.99; Train and Pro members get it included. [V] [App Store](https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504)
- **Pain points:** [U] Apple Watch sync failures, chat history not shown, no pause button in workouts. [App Store](https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504)
- **Ideas for us:**
  1. Learn from overrides: when a user changes a suggested weight or swaps an exercise, store it and bias the next generation. Improves progression and generation without asking questions.
  2. Night-before reminder with tomorrow's suggested day type. Improves retention and the day type suggestion.
  3. Streak credit for training logged outside the app. Improves retention (same point as Trainwell's pain point).

### Peloton (app, classes, Strength+)

- **What it is:** instructor-led classes plus two self-guided layers: Personalized Plans (weekly class suggestions) and Strength+ (a separate gym app with a workout generator and weight logging). AI features are grouped as Peloton IQ. [V] [Plans blog](https://www.onepeloton.com/blog/personalized-workout-plan), [Strength+](https://www.onepeloton.com/strength-plus-app), [Peloton IQ](https://www.onepeloton.com/peloton-iq)
- **Target user:** Peloton members and app users who want guidance, from beginner to advanced. [V] [Plans blog](https://www.onepeloton.com/blog/personalized-workout-plan)
- **Key systems:**
  - Plan onboarding: goal (stronger, weight, cardio, longevity), preferred activities, 1 to 6 days per week, preferred durations, experience level. [V] [Plans blog](https://www.onepeloton.com/blog/personalized-workout-plan)
  - Weekly plan: new suggestions every Monday from preferences and class history (down to music and instructor). Days can be moved, classes swapped or skipped without penalty; tracker workouts from outside count. Beta Sep 2024, now for all App and All-Access members. [V] [Plans blog](https://www.onepeloton.com/blog/personalized-workout-plan)
  - Strength+ generator: pick muscle focus or full body, length, level and available equipment (cables, racks, bench, free weights). [V] [Strength+](https://www.onepeloton.com/strength-plus-app)
  - Strength+ programs: multi-week, self-paced, led by instructors (for example 4 weeks, 3 to 5 sessions a week). [V] [Strength+](https://www.onepeloton.com/strength-plus-app)
  - Strength+ session: a movement breakdown video at the start of each block, coach demo during every exercise, audio technique cues, swap any exercise for a similar one, weight and rep logging, Apple Watch with rest timer and heart rate. [V] [Strength+](https://www.onepeloton.com/strength-plus-app), [App Store](https://apps.apple.com/us/app/peloton-strength/id6476712925)
  - Weight recommendations: after several sessions in the same range or with rising reps, the app prompts during class to go heavier; you accept or defer; needs consistent logging. Session-trend based, not per set. [V] [Peloton Buddy, Jul 2025](https://www.pelobuddy.com/personalized-weight-strength-plus/)
  - Peloton IQ (on newer hardware): camera counts reps and gives form tips, suggested weights, performance estimates from history, weekly summaries, data from Apple Health, Garmin or Fitbit. Included in All-Access at no extra charge. [V] [Peloton IQ](https://www.onepeloton.com/peloton-iq)
- **Business model:** App Free, App One $12.99 per month (floor workouts incl. strength), App+ $28.99 per month (adds equipment classes), All-Access for hardware owners. Strength+ alone $9.99 per month with 14-day trial, included in App+ and All-Access, not in App One. [V] [Peloton Buddy, Dec 2025](https://www.pelobuddy.com/new-year-app-2026/), [Strength+](https://www.onepeloton.com/strength-plus-app)
- **Pain points:** [U] a user reports previous weights and reps disappearing so they could not see what they did last time. [MWM listing of App Store reviews](https://mwm.ai/apps/peloton-strength/6476712925) (via search summary; not opened)
- **Ideas for us:**
  1. Weight increase suggestion shown during the session with "accept" or "not today", triggered when the same weight was hit for the target reps in recent sessions. Improves progression with a clear, reversible rule.
  2. A short movement breakdown at the start of each block, then the demo during the set. Maps to the atlas: open the guide at block start, not only on tap. Improves the guide.
  3. A weekly plan that simply suggests, and moving or skipping a day costs nothing. Fits our day type suggestion.

### Centr

- **What it is:** a training, meal planning and mindfulness app founded by Chris Hemsworth, now also selling home gym equipment and official HYROX programs. [V] [App Store](https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817), [centr.com](https://centr.com/)
- **Target user:** general fitness users at home or in the gym who want training and meals in one plan. [V] [App Store](https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817)
- **Key systems:**
  - Onboarding (3 to 5 minutes): goal (lose weight, build muscle, get fit), level, meal preference (regular, pescatarian, vegetarian, vegan), sex. [V] as reviewer account, [GymBird, 2023](https://www.gymbird.com/fitness-apps/centr-app-review)
  - Planner home: today's workout, breakfast, lunch, dinner, optional snack and a wellness tip, all from the quiz. Meals and workouts can be swapped in advance. [V] [GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)
  - Workouts: 5 to 60 minutes; two formats: self-guided move by move, or a continuous coached video; demos show beginner to advanced versions; filter by body part or equipment. [V] [App Store](https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817), [GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)
  - Weights tracker: in self-guided workouts you log weight and reps, and see your last three performances. [V] [GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)
  - Nutrition: dietary styles (plant-based, high-protein and more), recipes with nutrition data, automatic shopping list from the week's meals. Calorie or macro targets not confirmed. [V] [App Store](https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817), [GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)
  - Centr Coach: a newer guided strength and conditioning app tied to their equipment. Details not public beyond the product page. [V] [centr.com](https://centr.com/)
  - Devices: TV casting, Apple Watch tracking. [V] [App Store](https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817)
- **Business model:** 7-day trial, then about $29.99 per month, $59.99 per quarter or $119.99 per year (App Store shows ranges from $15.99 per month to $89.99 per year by offer). [V] [App Store](https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817), [GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)
- **Pain points:** [U] workouts feel repetitive over time; users want voice coaching through all videos. [App Store](https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817). [U] interface can overwhelm people who want a simple routine. [GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)
- **Ideas for us:**
  1. Show the last three performances of an exercise while logging. Cheap and useful. Improves logging and progression.
  2. For NutriLog later: one planner screen that shows today's session and today's meals together, with a shopping list. Improves the nutrition link.
  - Watch-out: repetition complaints. Our generator already varies sessions; keep that as a selling point.

### th.fit (TRAIN HARD by Jason Khalipa)

- **What it is:** a men's training brand by former CrossFit Games champion Jason Khalipa: a training app with fixed daily programming, local in-person "men's clubs", a podcast and a shop. The app runs on a white-label coaching platform (Playbook; at launch it was SugarWOD). [V] [th.fit](https://th.fit/), [Workouts page](https://th.fit/pages/workouts), [checkout](https://my.playbookapp.io/trainhard/checkout), [SugarWOD, Dec 2023](https://www.sugarwod.com/2023/12/train-hard-app-launch-jason-khalipa/)
- **Target user:** busy men who want strength, conditioning and a community to show up for. [V] [Workouts page](https://th.fit/pages/workouts)
- **Key systems:**
  - Programming: one coach-written program for everyone, TRAIN HARD DAILY, 45 minutes start to finish, new workout every day, AMRAP and EMOM formats. [V] [Workouts page](https://th.fit/pages/workouts). Weekly blueprint of 2 full-body strength days, 2 mixed days, 1 aerobic, 1 anaerobic, 1 rest. [V] per search listing of the [TH Daily program page](https://my.playbookapp.io/trainhard/programs/th-daily/29843); page not opened, so [I] until confirmed.
  - Equipment variants: each workout comes in a barbell version and a dumbbell version, with a clear equipment list. [V] [Workouts page](https://th.fit/pages/workouts)
  - Earlier tracks: FORCE (strength and conditioning), FLEX (bodybuilding-style), EMOM (efficient); 5 training days, 2 rest days, weekly "hero" workouts. [V] [SugarWOD](https://www.sugarwod.com/2023/12/train-hard-app-launch-jason-khalipa/)
  - Personalization: none found beyond choosing a program and equipment variant. [I] no generation or adaptation; confirm with a trial.
  - Community: free weekly in-person club sessions, money-back promise. [V] [th.fit](https://th.fit/), [Workouts page](https://th.fit/pages/workouts)
  - Logging, videos, nutrition: described by third-party listings (stream workouts, movement videos, log lifts, nutrition guidance, challenges, weekly calls). [U] [Garage Gym Reviews listing](https://www.garagegymreviews.com/train-hard-app-review), search summary only.
- **Business model:** $29.99 per month or $199 per year, 7-day free trial. Checkout shows 4.9 from about 32,000 ratings. [V] [checkout](https://my.playbookapp.io/trainhard/checkout)
- **Ideas for us:**
  1. Zero-decision mode: one "today's session" button that needs no configuration at all. Their whole product is this. Improves the core idea directly (1 tap instead of 2 or 3).
  2. Two equipment variants of the same session (barbell or dumbbells) instead of a new generation. Improves swap.
  - Their retention comes from people (clubs, brotherhood), not features. Not something we can copy in the app.

### Extra platforms

- Picked by how relevant their system is to our app, not by fame. Researched lighter than the listed apps: the mechanism that matters for us, pricing, one to three ideas.

#### Fitbod (personalized plans; picked because it is the closest match: it generates each gym session itself)

- **What it is:** an app that generates every gym workout from your profile, your logged history and a per-muscle recovery model. Over 1,600 exercises with HD demo videos. [V] [Help: How Fitbod creates your workout](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)
- **Key systems:**
  - Profile ("My Plan"): goal, experience, equipment (gym profiles), split (Full Body, Upper/Lower, Push/Pull/Legs), duration, warm-ups and cool-downs on or off, cardio, exercise variability, supersets or circuits. [V] [Help](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)
  - Selection: effectiveness data from millions of logged workouts, filtered by equipment and recovery; user feedback per exercise: "recommend more", "recommend less", "exclude". It also learns silently from skips, replacements, deletions and manual additions. [V] [Help](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)
  - Duration: the number of exercises follows the chosen length (4 exercises about 27 to 51 min, 6 about 39 to 63 min). [V] [Help](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)
  - Recovery model: each muscle group has a recovery percentage (0 to 100), full recovery up to 7 days, shown as a body heat map; fresher muscles are preferred; you can override a percentage; cardio from Apple Health or Strava counts. [V] [Help](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)
  - Load: easy completion raises load or reps, a struggle lowers them; intensity and volume are deliberately varied between sessions (heavy and light days); estimated strength per exercise, periodic "max effort days", optional reps-in-reserve logging; lighter weights after a break. New users get conservative starting loads from population data. [V] [Help](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)
  - In-app answer to "why less weight than last time?": planned light day, muscle still recovering, or return from a break. [V] [Help](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)
- **Business model:** limited free workouts, then $12.99 to $15.99 per month or $79.99 to $95.99 per year. [V] [App Store](https://apps.apple.com/us/app/fitbod-gym-fitness-planner/id1041517543)
- **Pain points:** [U] navigation during an active workout is limited. [App Store](https://apps.apple.com/us/app/fitbod-gym-fitness-planner/id1041517543)
- **Ideas for us:**
  1. Per-muscle recovery from logged sessions, shown on the atlas body model as a heat map, and used by the day type suggestion. Improves day type suggestion and fits the 3D model we already have.
  2. Three-way feedback on any exercise (more, less, never) plus silent learning from swaps and skips. Improves generation.
  3. Explain every lower recommendation in one line. Improves trust in progression.

#### Dr. Muscle (personalized plans; picked for fully automatic progression and deloads)

- **What it is:** an AI trainer app that recalculates weights, reps and sets after every workout, with automatic deloads. [V] [App Store](https://apps.apple.com/us/app/dr-muscle-ai-personal-trainer/id1073943857)
- **Key systems (all company descriptions):**
  - Rep ranges change every session (daily undulating periodization); weights are computed from past results, aiming for 2 to 3% increases. [V] [Dr. Muscle features page, Apr 2026](https://dr-muscle.com/what-makes-dr-muscle-different/)
  - Rest-pause sets are the default set style to save time. [V] [features page](https://dr-muscle.com/what-makes-dr-muscle-different/)
  - Automatic deload per exercise: when estimated 1RM drops and a plateau is detected, sets are cut by half and weight by about 10%. [V] [features page](https://dr-muscle.com/what-makes-dr-muscle-different/)
  - Breaks: after 10+ days off, the next sessions are automatically light; longer breaks cut load more. [V] [features page](https://dr-muscle.com/what-makes-dr-muscle-different/)
  - Neglected areas: a body part not trained for 5+ days gets more volume. [V] [features page](https://dr-muscle.com/what-makes-dr-muscle-different/)
  - Effort input: RIR or RPE guidance after sets. [V] [features page](https://dr-muscle.com/what-makes-dr-muscle-different/)
- **Business model:** free trial with all features; $48.99 per month or $399.99 per year; meal plan add-on $18.99 per month. [V] [App Store](https://apps.apple.com/us/app/dr-muscle-ai-personal-trainer/id1073943857). A third party reports a free plan with one AI recommendation per day. [U] [AI Tools Bakery](https://aitoolsbakery.com/blog/dr-muscle-review/), search summary only.
- **Ideas for us:**
  1. Simple, explainable auto-deload rule per exercise (estimated strength drops two sessions in a row: half the sets, 10% less weight for one session). Improves progression.
  2. Return-from-break rule: after X days off, the next session is generated lighter automatically. Improves progression and injury prevention with no user input.

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

### Shred
- https://www.shred.app/
- https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095
- https://www.garagegymreviews.com/shred-app-review (search snippet only)

### Caliber
- https://caliberstrong.com/
- https://apps.apple.com/us/app/caliber-strength-training/id1482405410
- https://caliberstrong.freshdesk.com/support/solutions/articles/48001257574-strength-score-user-guide
- https://caliberstrong.freshdesk.com/support/solutions/articles/48001225489-why-did-my-muscle-group-strength-score-drop-even-though-i-increased-weight-on-an-exercise-
- https://athletechnews.com/age-of-ai-human-personal-trainers-might-become-a-luxury-future-caliber/

### NordicTrack (iFIT)
- https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504
- https://www3.ifit.com/blog/connect/ai-coach-beta-release-notes
- https://connectthewatts.com/2021/03/16/ifit-details-smartadjust-and-activepulse-features-to-automate-your-workouts/
- https://www.ifit.com/membership (blocked, not read)

### Peloton
- https://www.onepeloton.com/blog/personalized-workout-plan
- https://www.onepeloton.com/strength-plus-app
- https://www.onepeloton.com/peloton-iq
- https://apps.apple.com/us/app/peloton-strength/id6476712925
- https://www.pelobuddy.com/personalized-weight-strength-plus/
- https://www.pelobuddy.com/new-year-app-2026/
- https://mwm.ai/apps/peloton-strength/6476712925 (search summary only)

### Centr
- https://centr.com/
- https://apps.apple.com/us/app/centr-fitness-workout-plans/id1382530817
- https://www.gymbird.com/fitness-apps/centr-app-review
- https://help.centr.com/en-US

### th.fit
- https://th.fit/
- https://th.fit/pages/workouts
- https://my.playbookapp.io/trainhard/checkout
- https://www.sugarwod.com/2023/12/train-hard-app-launch-jason-khalipa/
- https://my.playbookapp.io/trainhard/programs/th-daily/29843 (search listing only)
- https://www.garagegymreviews.com/train-hard-app-review (search listing only)

### Fitbod
- https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout
- https://apps.apple.com/us/app/fitbod-gym-fitness-planner/id1041517543

### Dr. Muscle
- https://dr-muscle.com/what-makes-dr-muscle-different/ (company page)
- https://apps.apple.com/us/app/dr-muscle-ai-personal-trainer/id1073943857
- https://aitoolsbakery.com/blog/dr-muscle-review/ (search summary only)
