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

#### RP Hypertrophy (muscle gain; picked for volume per muscle driven by soreness and pump feedback)

- **What it is:** a hypertrophy programming app by Renaissance Periodization built on mesocycles (training blocks of several weeks) with planned deloads. [V] [RP app page](https://rpstrength.com/pages/hypertrophy-app)
- **Key systems:**
  - Setup: 45+ templates or a "Meso Builder" where you pick target muscle groups. [V] [RP app page](https://rpstrength.com/pages/hypertrophy-app)
  - Feedback per muscle: pump, soreness and workload (plus, per third-party descriptions, joint pain and general fatigue); the app changes next week's sets and loads from the answers. Low pump points to more volume, extreme pump to too much. [V] [RP app page](https://rpstrength.com/pages/hypertrophy-app); pump scale per [Dr. Muscle article, Apr 2025](https://dr-muscle.com/rp-hypertrophy-app-beginners/) (a competitor, so [U])
  - Exact weights and rep targets each week; system-managed deload weeks; exercises can be changed on the fly. [V] [RP app page](https://rpstrength.com/pages/hypertrophy-app)
  - Guide: 250+ technique videos. [V] [RP app page](https://rpstrength.com/pages/hypertrophy-app)
- **Business model:** $34.99 per month or $299.99 per year, 30-day money-back; separate diet app at a discount. [V] [RP app page](https://rpstrength.com/pages/hypertrophy-app), [App Store](https://apps.apple.com/us/app/rp-hypertrophy/id1555614554)
- **Pain points:** [U] no built-in rest timer, no separate logging per limb, no cardio tracking. [App Store](https://apps.apple.com/us/app/rp-hypertrophy/id1555614554)
- **Ideas for us:**
  1. After the session, one question per trained muscle: "pump: low, good, too much" and at the next session "still sore? yes, no". Feeds volume per muscle. Improves progression and soreness handling. Watch-out: it adds taps, so keep it optional.

#### Alpha Progression (muscle gain; picked for set-by-set weight and rep recommendations)

- **What it is:** a German gym tracker with a plan generator and per-set progression recommendations, focused on hypertrophy. [V] [alphaprogression.com](https://alphaprogression.com/en)
- **Key systems:**
  - Plan generator: goal, equipment (several gym profiles), frequency, duration, muscle priorities, split. [V] [alphaprogression.com](https://alphaprogression.com/en)
  - Recommendations: before each set it shows weight and reps, from past sessions and from the sets already done today (set 3 is not set 1), rounded to the gym's weight steps. RIR is optional, in half steps. [V] [Guide, Sep 2026](https://alphaprogression.com/en/blog/alpha-progression-guide), [RIR glossary](https://alphaprogression.com/en/glossary/reps-in-reserve)
  - Exercise evaluations (Pro): each exercise rated for muscle-building suitability by range of motion and stability. [V] [Guide](https://alphaprogression.com/en/blog/alpha-progression-guide)
  - Weekly sets per muscle chart. [V] [Guide](https://alphaprogression.com/en/blog/alpha-progression-guide)
  - Deloads: at the end of a plan, or mark any single workout as a deload and the recommendations adjust. [V] [Guide](https://alphaprogression.com/en/blog/alpha-progression-guide)
  - Swaps: "similar exercises" list; history carries over into new plans. [V] [Guide](https://alphaprogression.com/en/blog/alpha-progression-guide)
  - Session tools: supersets, dropsets with automatic weight reduction, rest timer per exercise type that keeps counting past zero, lock screen display, warm-up calculator from first working set and available plates. [V] [Guide](https://alphaprogression.com/en/blog/alpha-progression-guide)
  - Guide: 795 exercises with gym-filmed videos, setup, execution cues, common mistakes; lower-resolution videos available offline. [V] [alphaprogression.com](https://alphaprogression.com/en)
- **Business model:** free: unlimited logging, manual plans, videos, measurements, CSV export. Pro: $12.99 per month or $79.99 per year, 14-day trial. [V] [alphaprogression.com](https://alphaprogression.com/en)
- **Ideas for us:**
  1. Within-session adjustment: if set 1 was hard, lower set 2's suggestion. Improves the session screen and progression.
  2. "Mark today as deload" as a single switch that lowers all suggestions. We have "Deload" in Pace; this is the same idea, confirmed.
  3. Weekly sets per muscle, drawn on the atlas body. Improves progress views.
  4. A free tier that keeps logging and videos free and charges for the smart parts. A clear split for our paid tiers.

#### MacroFactor (weight loss; picked for adaptive nutrition targets and a separate linked workout app, the closest model for NutriLog)

- **What it is:** a nutrition coach app with an adaptive calorie algorithm, plus MacroFactor Workouts (launched January 2026) as a separate app. [V] [macrofactor.com](https://macrofactor.com/), [Workouts page](https://macrofactor.com/workouts/)
- **Key systems:**
  - Nutrition: an algorithm learns your real energy expenditure from your food logs and weight trend, and recalibrates calorie targets at regular check-ins; "adherence-neutral" (missed days are not punished). [V] [macrofactor.com](https://macrofactor.com/)
  - Fast logging: barcode, AI food photo, receipt photo, voice. [V] [macrofactor.com](https://macrofactor.com/)
  - Workouts: program from goal (strength or hypertrophy), experience, equipment, gym locations, schedule; rule-based auto-progression from RIR (explicitly not AI); smart substitutes; supersets, myoreps, partials, left/right weights; plate calculator; 900+ exercises with multi-angle videos by Jeff Nippard. [V] [Workouts page](https://macrofactor.com/workouts/)
  - Link between the apps: body metrics, scale weight, progress photos, some habits and period tracking sync; no automatic training changes from nutrition yet, by choice. Data can be exported or deleted from either app. [V] [Workouts page](https://macrofactor.com/workouts/)
- **Business model:** Workouts $11.99 per month, $7.99 per month for 6 months, $5.99 per month yearly, bundle discount with Nutrition, 7-day trial. [V] [Workouts page](https://macrofactor.com/workouts/)
- **Ideas for us (NutriLog):**
  1. Two separate apps that share only body data (weight, photos, measurements), with no automatic cross-effects at first. A low-risk model for the NutriLog link and for GDPR scope (each app holds only what it needs).
  2. Rule-based, explainable progression instead of AI for load changes; AI stays for session design. Keeps AI costs down and results predictable.

#### Noom (weight loss; picked for behavior change and retention mechanics)

- **What it is:** a psychology-first weight loss program with a food tracker, now also a telehealth provider for GLP-1 weight loss drugs (Noom Med). [V] [Noom pricing article, Sep 2026](https://www.noom.com/blog/weight-management/noom-cost-2/)
- **Key systems:**
  - Daily short lessons based on cognitive behavioral therapy, as articles and quizzes. [V] [Noom pricing article](https://www.noom.com/blog/weight-management/noom-cost-2/), [calorie-trackers.com, Apr 2026](https://calorie-trackers.com/reviews/noom/)
  - Color system: every food is green, yellow or red by calorie density and nutrition; aim for mostly green and yellow. A simple rule instead of numbers. [V] [calorie-trackers.com](https://calorie-trackers.com/reviews/noom/)
  - Coaching: weekly check-ins with a human goal specialist by message, peer groups with a coach. [V] [calorie-trackers.com](https://calorie-trackers.com/reviews/noom/)
  - GLP-1 companion: protein tools, muscle-preservation workouts, side-effect management. [V] [Noom pricing article](https://www.noom.com/blog/weight-management/noom-cost-2/)
- **Business model:** Noom Weight $169 for 4 months, $179 for 6, $209 for 12, 7-day trial; Noom Med GLP-1 plans $179 to $299 per month. [V] [Noom pricing article](https://www.noom.com/blog/weight-management/noom-cost-2/)
- **Pain points:** [U] aggressive upselling during onboarding, less accurate calorie data, expensive. [calorie-trackers.com](https://calorie-trackers.com/reviews/noom/)
- **Ideas for us:**
  1. For NutriLog: a 3-color food rule as the simple mode, with numbers only for those who want them. Same "no decision paralysis" idea applied to food.
  2. Muscle-preservation training for people losing weight (including GLP-1 users) as a goal option. A possible profile goal later.
  - Watch-out: upselling in onboarding is a top complaint. Keep our onboarding free of sales pressure.

#### Hevy (gym logging; picked as the reference logging screen with a generous free tier)

- **What it is:** a social workout logger with routines, a plan generator ("Hevy Trainer") and a coach product (Hevy Coach). [V] [Hevy features](https://www.hevyapp.com/features/)
- **Key systems:**
  - Logging: set types, RPE, supersets that auto-scroll to the next exercise after a set, automatic rest timer (per exercise, default for new routines), percentage-based warm-up set calculator, plate calculator, live PR notification, lock screen live activity, Apple Watch. [V] [Hevy features](https://www.hevyapp.com/features/), [Hevy help: workout settings](https://help.hevyapp.com/hc/en-us/articles/33882110558743-Workout-Settings-Preferences-Timer-Warm-up-calculator-Plate-Calculator-Smart-Superset-Scrolling) (search listing)
  - "Previous" values: you choose whether the previous value shown is from the last time you did the exercise anywhere, or the last time within this routine. [V] per search listing of the [Hevy help center](https://help.hevyapp.com/hc/en-us/articles/33882110558743-Workout-Settings-Preferences-Timer-Warm-up-calculator-Plate-Calculator-Smart-Superset-Scrolling); page not opened, so [I] until confirmed.
  - Progress: charts, muscle distribution chart, measurements, progress photos, monthly and yearly reviews. Social feed, likes, comments, leaderboards. [V] [Hevy features](https://www.hevyapp.com/features/)
  - AI: a Hevy plugin for ChatGPT. [V] [Hevy features](https://www.hevyapp.com/features/)
- **Business model:** free with limits (4 routines, 7 custom exercises, 3 months of stats history); Pro about $2.99 to $3.99 per month, $23.99 per year, $74.99 lifetime. [U] third-party review, [AI Tools Bakery, Sep 2026](https://aitoolsbakery.com/blog/hevy-review/); the official pricing page was not reachable.
- **Pain points:** [U] social feed cannot be removed; no Garmin. [AI Tools Bakery](https://aitoolsbakery.com/blog/hevy-review/)
- **Ideas for us:**
  1. Superset auto-scroll: after logging a set, jump to the partner exercise. Improves supersets (we already offer "Supersets" in Pace).
  2. Rest timer that starts itself when a set is ticked, with per-exercise defaults (longer for compounds). Improves the session screen.

#### Strong (gym logging; picked as the minimal logger many apps copy)

- **What it is:** a long-running, minimal workout logger; free forever with a Pro tier. [V] [strong.app](https://www.strong.app/)
- **Key systems:** custom exercises, supersets, warm-up calculator, RPE, custom timers, scheduling, muscle heat map, charts, best sets, estimated 1RM records, measurements, CSV export, Apple Health, Siri Shortcuts, Apple Watch. [V] [strong.app](https://www.strong.app/)
- **Business model:** free tier; Pro for advanced progress views; price not shown on the site. Unverified.
- **Idea for us:** a muscle heat map of what you trained this week on the body model. Same as the Fitbod idea; two apps confirm it.

#### MuscleWiki (exercise guides; picked because its muscle-map-first browser is the closest match to the atlas)

- **What it is:** a free exercise library and app where you tap a muscle on a body map (male or female) and get exercises, filtered by equipment category (barbell, dumbbells, cables, machine, kettlebells, bands, TRX, stretches, recovery and more); also a "Joints" view, a workout generator and routine builder. [V] [musclewiki.com](https://musclewiki.com/) (opened in a browser)
- **Exercise page structure:** difficulty level, 3 short numbered steps, then a detailed how-to (setup, torso, grip, performing the lift), then a coach's tips section. [V] [Bench press page](https://musclewiki.com/exercise/barbell-bench-press) (opened in a browser)
- **Business model:** free with ads; premium about $49.99 per year with 7-day trial: unlimited routines, AI workout generation, progress analytics, advanced filters, no ads. [U] via search summary of the [App Store listing](https://apps.apple.com/us/app/musclewiki-workout-fitness/id1096827640) and [premium page](https://musclewiki.com/gopremium); not opened. The site also links a public API. [V] [musclewiki.com](https://musclewiki.com/)
- **Ideas for us:**
  1. Guide layout in two depths: 3 short steps first (readable between sets), full detail and expert tips below. Improves the exercise guide.
  2. Body map as an entry point to the catalog (tap a muscle, see exercises). The atlas already has the model; this confirms the pattern.

#### Muscle & Motion (exercise guides; picked for 3D anatomy videos per exercise, close to our 3D tab)

- **What it is:** 3D anatomy and kinesiology apps (strength training, anatomy, yoga, posture) for trainers, therapists, students and gym-goers. [V] [muscleandmotion.com](https://www.muscleandmotion.com/)
- **Presentation:** 3D animations of each movement with the active muscles highlighted, common mistakes, variations by level. [V] [muscleandmotion.com](https://www.muscleandmotion.com/)
- **Business model:** not shown on the home page. Unverified.
- **Idea for us:** in the 3D tab, highlight the working muscles and add a "common mistakes" block. Improves the guide and uses the atlas model.

#### ExRx.net (exercise guides; picked for its long-standing exercise classification)

- **What it is:** a large reference site of exercises and kinesiology. [V] [ExRx bench press page](https://exrx.net/WeightExercises/PectoralSternal/BBBenchPress) (opened in a browser)
- **Classification per exercise:** Utility (basic or auxiliary), Mechanics (compound or isolation), Force (push or pull); muscles split into Target, Synergists and Dynamic Stabilizers, with muscle heads named (for example pectoralis major sternal vs clavicular). Instructions in Preparation, Execution, Comments. [V] [ExRx bench press page](https://exrx.net/WeightExercises/PectoralSternal/BBBenchPress)
- **Idea for us:** add "target vs synergist vs stabilizer" and a muscle head field to the catalog, and a movement pattern field. Our generation rules already talk about muscle heads and patterns, but the catalog has no field for them. Improves catalog structure and generation.

#### Freeletics (fitness in general; picked because its AI coach changes the next session from post-workout feedback)

- **What it is:** an AI coach app for bodyweight HIIT, weights, gym machines and running, with 700+ exercises combined into generated sessions. [V] [App Store](https://apps.apple.com/app/id654810212), [freeletics.com](https://www.freeletics.com/en/)
- **Key systems:**
  - Onboarding: goals, fitness level, training days and time, location (home, gym, outdoor) and equipment. [V] [freeletics.com](https://www.freeletics.com/en/)
  - Post-workout feedback: a five-step scale from too easy to too hard, plus which movements worked and whether form held or needed changes. [V] [Freeletics blog](https://www.freeletics.com/en/blog/posts/what-is-the-purpose-of-the-feedback-i-am-asked-to-give-after-each-workout/)
  - Use of feedback: short term decides whether the next session scales back or pushes; long term sets training load. [V] [Freeletics blog](https://www.freeletics.com/en/blog/posts/what-is-the-purpose-of-the-feedback-i-am-asked-to-give-after-each-workout/)
- **Business model:** free: 34 bodyweight workouts, 100+ exercises, community. Paid Coach or Coach plus Nutrition bundle, about $35 to $50 for 3 months, $75 to $90 for 12 months; 14-day money-back. [V] [App Store](https://apps.apple.com/app/id654810212)
- **Pain points:** [U] no swapping single exercises or changing reps in a plan; rest too long in strength sessions; exercise order jumps between standing, seated and lying positions; quitting mid-workout loses the session. [App Store](https://apps.apple.com/app/id654810212)
- **Ideas for us:**
  1. One post-session rating (5 steps from too easy to too hard) that sets the next session's volume and load. Same point as Trainwell and Juggernaut; three apps confirm it.
  2. Generation rule: group exercises by station and body position to cut walking and getting up and down. Improves generation (a coaching rule we do not have yet).
  3. Save partial sessions automatically. Improves the session screen.

#### Apple Fitness+ (fitness in general; picked for building a whole plan in a few taps)

- **What it is:** Apple's trainer-led video workout and meditation service, with Custom Plans. [V] [Apple Support: Custom Plans](https://support.apple.com/guide/fitness-plus/use-custom-plans-apdf222051d8/ios)
- **Key systems:**
  - Build your own plan: tap workout days, pick time per day, plan length, up to five activity types, trainer and music preferences, start date. [V] [Apple Support](https://support.apple.com/guide/fitness-plus/use-custom-plans-apdf222051d8/ios)
  - Premade plans with no setup: "Stay Consistent" (built from your history: favorite activities, durations, trainers, music, usual days), "Push Further" (same but longer), "Get Started" (from your first choices). [V] [Apple Support](https://support.apple.com/guide/fitness-plus/use-custom-plans-apdf222051d8/ios)
  - Missed days: you can go back and do earlier workouts of the plan; a finished plan can be repeated with the same or refreshed content. [V] [Apple Support](https://support.apple.com/guide/fitness-plus/use-custom-plans-apdf222051d8/ios)
- **Business model:** subscription; price not checked in this session. Unverified.
- **Ideas for us:**
  1. A premade "keep doing what I do" option built only from history, next to the configurable path. Improves the day type suggestion and configure screen (zero-decision default).
  2. A "push further" variant that is the same session, slightly longer or harder. Improves progression without new settings.

#### Ladder (fitness in general; picked because the session is simply given to you, a direct answer to decision paralysis)

- **What it is:** a strength app where a 2-minute quiz places you on a "team" run by a human coach who publishes a new 7-day plan every week. [V] [joinladder.com](https://www.joinladder.com/)
- **Key systems:**
  - You follow the coach's plan; you do not assemble workouts. Audio cues handle pacing, reps and rest; videos for every movement; you log reps and weight as you go. [V] [joinladder.com](https://www.joinladder.com/)
  - Blocks of about 5 to 6 weeks that get harder; the weight you used last time is pre-filled; team chat, awards, coach messaging; sessions about 30 to 40 minutes. [U] via search summary of reviews ([Bustle](https://www.bustle.com/wellness/ladder-app-review), [Garage Gym Reviews](https://www.garagegymreviews.com/ladder-app-review)); not opened.
- **Business model:** free trial without card. [V] [joinladder.com](https://www.joinladder.com/). About $29.99 per month or $179.99 per year. [U] search summary only.
- **Ideas for us:**
  1. Pre-filled last weight (again; now confirmed across Sensai, Centr, Ladder). Improves logging.
  2. Audio cue for rest end and next exercise, so the phone can stay in the pocket. Improves the session screen.

## Section 2: Per function of our app

- Effort scale: **S** = up to a day, **M** = a few days, **L** = weeks. Rough estimates for a single developer working with Claude.
- Platform impact is judged without the platform plan doc (not reachable here). It names what each idea would need: **server** (a server function or sync), **GDPR** (personal data stored or sent), **tiers** (fits a paid tier).
- [I] Several ideas touch health-related data (injuries, body weight, readiness). Under GDPR these are likely "data concerning health" (Article 9, needs explicit consent). This is an inference; confirm with a legal source before building.

### 1. Day type suggestion from history

- **Others:**
  - Fitbod keeps a recovery % per muscle from logged sets and prefers fresh muscles. ([Fitbod](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout))
  - Dr. Muscle adds volume to a body part untrained for 5+ days. ([Dr. Muscle](https://dr-muscle.com/what-makes-dr-muscle-different/))
  - Apple Fitness+ builds a "Stay Consistent" plan purely from history. ([Apple](https://support.apple.com/guide/fitness-plus/use-custom-plans-apdf222051d8/ios))
  - Peloton sends a new weekly plan every Monday. ([Peloton](https://www.onepeloton.com/blog/personalized-workout-plan))
  - iFIT reminds you the night before. ([iFIT](https://www3.ifit.com/blog/connect/ai-coach-beta-release-notes))
- **Ours:** next day in the Push, Pull, Legs rotation after the last logged day (per the brief; not in the repo code).
- **Difference:** ours looks at the last label only; the others look at what each muscle actually did and how recently.
- **Verdict: adapt.** Keep the rotation as the default. Add a recovery check: if the suggested muscles were trained in the last 48 hours (for example a Full Body yesterday), suggest the next fresh option and say why in one line.
  - Benefit: fewer wrong suggestions, still 1 tap.
  - Effort: S once sessions store their muscles; M with a per-muscle recovery model.
  - Platform: GDPR (training history). Server only if history syncs across devices.

### 2. Configure screen

- **Others:**
  - Peloton Strength+ generator: muscle focus, length, level, equipment. ([Peloton](https://www.onepeloton.com/strength-plus-app))
  - Fitbod stores all of this once in a "My Plan" profile. ([Fitbod](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout))
  - Shred rebuilds with one tap for other equipment. ([Shred](https://www.shred.app/))
  - Juggernaut asks a short readiness check first. ([V3 blog](https://www.juggernautai.app/blog/juggernautai-v3-0-is-here))
  - th.fit and Ladder have no configuration at all. ([th.fit](https://th.fit/pages/workouts), [Ladder](https://www.joinladder.com/))
- **Ours:** duration, five option rows, "+ Core / Abs", emphasis chips and free text, reset to defaults each time (repo: duration resets to 90).
- **Difference:** ours is richer per session but forgets choices. The best "no decision" apps either remember or skip configuration.
- **Verdict: adapt.** Remember the last choices per day type (or profile defaults) so "Generate" works as the second tap. Keep the options one tap away. Optionally add a 10-second readiness row (sleep, sore areas) that can pre-select "Deload".
  - Benefit: protects the 2-to-3-tap promise.
  - Effort: S.
  - Platform: none if stored on the device; server for multi-device.

### 3. Session generation

- **Others:**
  - Fitbod: effectiveness data, equipment, recovery; exercise count from duration; deliberate heavy and light days; learns from skips and swaps; "more, less, exclude" per exercise. ([Fitbod](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout))
  - Juggernaut: accessories picked for weak points; warm-up built from the day's lifts with ramp sets. ([JTS](https://www.jtsstrength.com/how-juggernautai-works/), [Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/))
  - Trainerize AI: gets a small, fixed slice of client history (last 10 workouts, latest weight). ([Trainerize](https://help.trainerize.com/hc/en-us/articles/45565151151508-Using-the-AI-Workout-Builder))
  - Shred: coaches write base programs and AI fits them. ([Shred](https://www.shred.app/))
  - Freeletics users complain about exercise order that jumps between standing, seated and lying. ([App Store](https://apps.apple.com/app/id654810212))
- **Ours:** one Claude call per session from a shuffled catalog subset, with strong coaching rules (no repeated pattern, muscle head coverage, equipment variety, compound first). No history, no preferences.
- **Difference:** our rules are more explicit about anatomy than most. What we lack is memory: nothing from past sessions or user preferences reaches the prompt.
- **Verdict: adapt.** Add three things to the prompt:
  1. A short history slice (last few sessions: exercises and loads).
  2. The user's "never" list and limitations.
  3. A rule to group exercises by station and body position.
  - Also: warm-up built from the first main lifts, with lighter ramp sets.
  - Benefit: sessions that follow on from each other.
  - Effort: M.
  - Platform: server (hold the API key and meter usage instead of a browser key), GDPR (history sent to the AI provider; state that it is not used for training, as Trainerize does), tiers (generation count).

### 4. Swap or regenerate one exercise or one section

- **Others:**
  - Future: a flag swaps instantly. ([FAQ](https://faq.future.co/en/articles/12073331-what-should-i-expect-from-a-future-pro-workout))
  - Juggernaut: swap for today or the whole block, from a same-purpose list. ([Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/))
  - Shred: alternates from muscle-level metadata, saved alternates. ([App Store](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095))
  - Alpha Progression: "similar exercises" list; history carries over. ([Guide](https://alphaprogression.com/en/blog/alpha-progression-guide))
  - Sensai: plain-language changes mid-session. ([SensAI](https://www.sensai.fit/blog/sensai-review-2026))
  - Trainerize: only a manual edit. Freeletics users complain there is no swap at all.
- **Ours:** "redo" per section by a new AI call (repo). Per-exercise swap is listed in the brief but not in the repo code.
- **Difference:** the others swap single exercises instantly from a list with no AI call. Ours regenerates with AI, which is slower and costs money.
- **Verdict: adapt.** Per-exercise swap from a deterministic list (same pattern, same primary muscle, available equipment), with "just today" or "always". Keep the AI "redo" for whole sections and add a "only dumbbells today" rebuild.
  - Benefit: instant, free, predictable.
  - Effort: S to M (needs the pattern field, see function 9).
  - Platform: none; the "always" choice is a user preference (GDPR light).

### 5. Session screen: logging, rest timers, supersets

- **Others:**
  - Previous values pre-filled: Sensai, Ladder; Centr shows the last 3; Hevy lets you choose last time anywhere or in this routine. ([App Store](https://apps.apple.com/us/app/sensai-fitness-sensei/id6738963099), [GymBird](https://www.gymbird.com/fitness-apps/centr-app-review), [Hevy](https://www.hevyapp.com/features/))
  - Rest timer: starts by itself, set per lift type, shown on the lock screen (Juggernaut V3, Alpha Progression, Sensai). ([V3 blog](https://www.juggernautai.app/blog/juggernautai-v3-0-is-here), [Alpha guide](https://alphaprogression.com/en/blog/alpha-progression-guide))
  - Supersets: Hevy scrolls to the partner exercise after each set. ([Hevy](https://www.hevyapp.com/features/))
  - Autosave: Trainerize saves stats without "Finish"; Freeletics users lose unsaved sessions. ([Trainerize](https://help.trainerize.com/hc/en-us/articles/208689026-How-do-I-use-the-mobile-app-when-I-m-working-out))
  - Audio cues for next move and rest end: Ladder, Future, Juggernaut. ([Ladder](https://www.joinladder.com/))
- **Ours:** a done checkbox per exercise. No sets, weights or timers.
- **Difference:** every tracker-type app logs sets. It is the base for progression.
- **Verdict: adopt.** Set rows with pre-filled last weight and reps, an automatic rest timer (longer for compounds), superset auto-scroll, autosave.
  - Benefit: large; also unlocks functions 6 and 14.
  - Effort: M.
  - [I] A web app cannot show iOS lock-screen live timers; sound or vibration and notifications are the likely limit. Confirm with a PWA test on iPhone.
  - Platform: GDPR (training logs), server for sync. Keep logging free (the Alpha Progression and Hevy model).

### 6. Progression between sessions

- **Others:**
  - Per set: Juggernaut RPE or RIR moves the next sets and sessions ([Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/)); Alpha Progression adjusts within the session ([Guide](https://alphaprogression.com/en/blog/alpha-progression-guide)).
  - Session trend: Peloton prompts "go heavier" after stable sessions, which you accept or defer ([Peloton Buddy](https://www.pelobuddy.com/personalized-weight-strength-plus/)); Fitbod raises after easy sessions, lowers after struggles, alternates heavy and light days ([Fitbod](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)).
  - Post-session rating: Freeletics 5 steps, Trainwell feedback, Juggernaut difficulty 5 to 10 ([Freeletics](https://www.freeletics.com/en/blog/posts/what-is-the-purpose-of-the-feedback-i-am-asked-to-give-after-each-workout/)).
  - Deloads and breaks: Dr. Muscle halves the sets and takes about 10% off the weight when estimated 1RM drops, and runs light sessions after 10+ days off ([Dr. Muscle](https://dr-muscle.com/what-makes-dr-muscle-different/)); RP plans deload weeks and sets weekly volume from pump and soreness ([RP](https://rpstrength.com/pages/hypertrophy-app)).
  - Rules, not AI: MacroFactor keeps progression rule-based on purpose ([MacroFactor](https://macrofactor.com/workouts/)).
- **Ours:** none.
- **Verdict: adopt, in two stages.**
  - Stage 1 (rule-based, no AI):
    - pre-fill the last weight;
    - if all sets hit the top of the rep range, suggest the next weight step, with "accept" or "not today";
    - one 5-step rating after the session;
    - one line explaining every change.
  - Stage 2:
    - optional RIR per set;
    - auto-deload rule;
    - return-from-break rule;
    - within-session adjustment.
  - Benefit: fills the biggest gap and removes the "what weight?" decision.
  - Effort: M (stage 1), M to L (stage 2).
  - Platform: rules can run on the device; no AI cost. GDPR (logs). Tiers: the smart suggestions could be paid while logging stays free.

### 7. Injuries, soreness and limitations

- **Others:**
  - Future: medical clearance, the coach excludes movements ([FAQ](https://faq.future.co/en/articles/12073374-what-if-i-have-an-injury-or-special-needs)).
  - Juggernaut: readiness asks about injuries and soreness per body part and lowers load for that session only ([Garage Gym Experiment](https://garagegymexperiment.com/2022/04/24/juggernaut-ai-review-from-non-powerlifters/)).
  - Sensai: remembers injuries, "knee hurts, swap lunges" mid-session, says it cannot diagnose ([SensAI](https://www.sensai.fit/blog/sensai-review-2026)).
  - Fitbod: exclude an exercise, override recovery ([Fitbod](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)).
  - RP: asks about soreness and joint pain ([RP](https://rpstrength.com/pages/hypertrophy-app)).
- **Ours:** the free-text box before generation (for example "left knee sore").
- **Difference:** ours works per session only and must be typed each time.
- **Verdict: adapt.**
  - A saved limitations list (area plus movements to avoid) applied to every generation.
  - A "never" list.
  - Quick "sore today" chips.
  - A plain disclaimer that the app does not diagnose.
  - Benefit: safer sessions without typing.
  - Effort: S to M.
  - Platform: GDPR high: injury data is likely health data [I]. Prefer keeping it on the device, or ask explicit consent.

### 8. Exercise guides

- **Others:**
  - Future and Ladder: video plus a coach's voice with form cues ([FAQ](https://faq.future.co/en/articles/12073331-what-should-i-expect-from-a-future-pro-workout)).
  - Peloton Strength+: a movement breakdown at the start of each block, then a demo during every exercise ([Peloton](https://www.onepeloton.com/strength-plus-app)).
  - MuscleWiki: 3 short steps, then the full how-to, then expert tips ([MuscleWiki](https://musclewiki.com/exercise/barbell-bench-press)).
  - Muscle & Motion: 3D with active muscles highlighted and common mistakes ([M&M](https://www.muscleandmotion.com/)).
  - Alpha Progression: setup, cues and common mistakes, low-resolution videos offline ([Alpha](https://alphaprogression.com/en)).
  - Centr: demos show beginner to advanced versions ([GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)).
  - Reached from the session: tap the exercise, same as ours.
- **Ours:** exercise sheet with 3D, demo and guide tabs (steps and cues), from the atlas.
- **Verdict: already have (core); adapt the details.**
  - Put 3 short steps first (readable between sets), then the full atlas detail.
  - Add a "common mistakes" block.
  - Highlight the working muscles on the 3D model.
  - Optionally open the guide automatically at the start of a new block.
  - Benefit: the atlas becomes the "more information" layer at the right moment.
  - Effort: S to M.
  - Platform: none. Content must stay our own.

### 9. Exercise catalog structure

- **Others:**
  - ExRx: Utility (basic or auxiliary), Mechanics, Force; muscles split into target, synergists and stabilizers, with muscle heads ([ExRx](https://exrx.net/WeightExercises/PectoralSternal/BBBenchPress)).
  - MuscleWiki: body map plus equipment categories and a joints view ([MuscleWiki](https://musclewiki.com/)).
  - Shred: muscle-level metadata drives alternates ([App Store](https://apps.apple.com/us/app/shred-gym-home-workouts/id1439828095)).
  - Alpha Progression: rates exercises by range of motion and stability ([Guide](https://alphaprogression.com/en/blog/alpha-progression-guide)).
  - Fitbod: uses effectiveness data from logs ([Fitbod](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)).
- **Ours:** primary and secondary muscles, equipment, mechanic, force, level, day type. No movement pattern, no muscle role or head, no station or position.
- **Difference:** our generation rules talk about patterns and heads, but the catalog does not store them, so the AI has to guess.
- **Verdict: adapt.** Add these fields:
  - movement pattern (for example horizontal push, hinge);
  - muscle role (target, synergist, stabilizer);
  - muscle head or region;
  - station or body position.
  - Benefit: enables the instant swap (function 4), the station grouping rule (function 3) and better atlas filters.
  - Effort: M (fill 1,223 entries with AI help, then review).
  - Platform: none.

### 10. Onboarding and user profile

- **Others:**
  - Peloton: goal, activities, days, durations, level ([Peloton](https://www.onepeloton.com/blog/personalized-workout-plan)).
  - Centr: 3 to 5 minutes, goal, level, diet, sex ([GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)).
  - Juggernaut: detailed, including current strength ([JTS](https://www.jtsstrength.com/how-juggernautai-works/)).
  - Fitbod: "My Plan" plus conservative first loads from population data ([Fitbod](https://help.fitbod.me/hc/en-us/articles/360004429814-How-Fitbod-Creates-Your-Workout)).
  - Future and Trainwell: quiz plus a call with a coach.
  - Noom's onboarding upselling is a top complaint ([calorie-trackers.com](https://calorie-trackers.com/reviews/noom/)).
- **Ours:** none (only the API key screen in the repo).
- **Verdict: adapt.** A 4 to 5 question, fully skippable onboarding: goal, experience, where you train and equipment, days per week, limitations. The answers become the configure defaults. No sales pressure.
  - Benefit: first session fits without configuring.
  - Effort: S to M.
  - Platform: GDPR (profile); server only with accounts.

### 11. Human coach vs AI vs hybrid

- **Others:**
  - Human: Future ($149 to $199 per month), Trainwell ($149), Caliber Premium (about $200), Ladder (coach publishes weekly plans).
  - Coach tools with AI help: Trainerize.
  - Algorithms: Juggernaut, Fitbod, Dr. Muscle, Alpha Progression, RP.
  - LLM coaches: Sensai, iFIT Tailor.
  - Instructors plus algorithms: Peloton, Centr.
  - Signal: Future launched a free AI tier in February 2026 and scrapped it in June 2026 to focus on humans ([Athletech](https://athletechnews.com/future-pulls-the-plug-on-ai-personal-training-commits-to-human-coaches/)). The same source cites a Les Mills survey where only about 10% prefer AI guidance over a human.
- **Ours:** AI designs the session; "Ask Claude" chat in Tips.
- **Verdict: skip human coaching for now.** Keep the hybrid "AI designs, rules progress" model (as MacroFactor does).
  - [I] People may trust AI more when it explains itself in plain words. Confirm with user testing.

### 12. Wearables, readiness and recovery data

- **Others:**
  - Sensai: HRV, sleep and resting heart rate, judged together, never one number alone ([SensAI](https://www.sensai.fit/blog/sensai-review-2026)).
  - Future and Trainwell: heart rate goes to the coach ([FAQ](https://faq.future.co/en/articles/12073347-do-i-need-a-smartwatch-to-use-future-pro)).
  - Peloton IQ: camera rep counting ([Peloton IQ](https://www.onepeloton.com/peloton-iq)).
  - Fitbod: counts cardio from Apple Health in recovery.
  - Trainwell: watch rep counting, which users call inaccurate.
  - Juggernaut: purely subjective readiness.
- **Ours:** none.
- **Verdict: skip for now, adopt subjective readiness instead** (see functions 2 and 7).
  - [I] A web app cannot read Apple Health directly; that needs a native app. Confirm against the platform plan.

### 13. Nutrition, body weight and the link to training

- **Others:**
  - MacroFactor: adaptive calorie targets from food logs and the weight trend; the workout app is separate and shares only body data, with no automatic cross-effects yet ([MacroFactor](https://macrofactor.com/workouts/)).
  - Noom: green, yellow, red food colors ([calorie-trackers.com](https://calorie-trackers.com/reviews/noom/)).
  - Centr: meals and today's workout on one planner screen, plus a shopping list ([GymBird](https://www.gymbird.com/fitness-apps/centr-app-review)).
  - Future and Trainwell: tips only, no meal plans.
  - Juggernaut V3: shows the bodyweight trend on the dashboard ([V3 blog](https://www.juggernautai.app/blog/juggernautai-v3-0-is-here)).
  - Caliber: uses body weight for relative strength ([Caliber](https://caliberstrong.freshdesk.com/support/solutions/articles/48001257574-strength-score-user-guide)).
- **Ours:** none; NutriLog later.
- **Verdict: adapt later.** Start with shared body data only: weight, measurements, photos. Use body weight in progress views. Consider a color-rule "simple mode" in NutriLog.
  - Effort: M (NutriLog side).
  - Platform: server (shared account), GDPR (body weight, likely health data [I]).

### 14. Motivation and retention

- **Others:**
  - Streaks: Trainwell; Alpha Progression with badges. iFIT gives streak credit for outside workouts; Trainwell users complain that outside activities don't count ([App Store](https://apps.apple.com/us/app/ifit-personal-trainer/id6756594504), [Monica Denais](https://monicadenais.com/trainwell-review)).
  - Reminders: iFIT sends night-before reminders and missed-workout alerts ([iFIT](https://www3.ifit.com/blog/connect/ai-coach-beta-release-notes)).
  - Summaries: weekly (Peloton IQ), monthly and yearly (Hevy), AI summary after each workout (Shred).
  - Records: live PR alerts (Hevy); a per-muscle Strength Score (Caliber).
  - Social: feeds and leaderboards (Hevy, Shred).
  - People: daily accountability messages from a person (Future).
- **Ours:** last 3 sessions on the home screen.
- **Verdict: adapt.**
  - A streak that counts any logged training.
  - A short summary after each session (what went up, what next time).
  - A weekly view with sets per muscle on the atlas body.
  - PR highlights.
  - Skip social feeds for now. Reminders later (they need notifications).
  - Effort: S to M.
  - Platform: server for push notifications. GDPR light.

### 15. Business model

- **Prices seen (per month unless noted):**
  - Human coaching: Future $149 to $199; Trainwell $149; Caliber Premium about $200.
  - Programming apps: Juggernaut $34.99; RP $34.99; Dr. Muscle $48.99.
  - AI and tracker apps: Sensai $6.99; Shred $12.99; Fitbod $12.99 to $15.99; Alpha Progression $12.99; MacroFactor Workouts $5.99 to $11.99; Hevy Pro about $3; Peloton App One $12.99, Strength+ $9.99.
  - Content apps: Centr up to $29.99; th.fit $29.99.
  - Trials: mostly 7 or 14 days.
- **Patterns:**
  - Logging free, smart features paid: Alpha Progression, Hevy, Caliber, Strong.
  - AI only on paid plans: Trainerize.
  - Free AI capped (one recommendation per day): Dr. Muscle [U].
  - Bring your own AI assistant through an MCP server: Caliber.
  - A free AI tier that did not last: Future.
- **Ours:** the user pastes their own Anthropic API key (repo).
- **Verdict: adapt.**
  - Free: catalog, atlas, logging, a small number of generations per week.
  - Paid: unlimited generation plus smart progression.
  - Keep "bring your own AI" as an option for power users.
  - Platform: server (usage metering, key custody), tiers.

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

### RP Hypertrophy
- https://rpstrength.com/pages/hypertrophy-app
- https://apps.apple.com/us/app/rp-hypertrophy/id1555614554
- https://dr-muscle.com/rp-hypertrophy-app-beginners/ (competitor article)

### Alpha Progression
- https://alphaprogression.com/en
- https://alphaprogression.com/en/blog/alpha-progression-guide
- https://alphaprogression.com/en/glossary/reps-in-reserve (search listing)

### MacroFactor
- https://macrofactor.com/
- https://macrofactor.com/workouts/

### Noom
- https://www.noom.com/blog/weight-management/noom-cost-2/
- https://calorie-trackers.com/reviews/noom/

### Hevy
- https://www.hevyapp.com/features/
- https://help.hevyapp.com/hc/en-us/articles/33882110558743-Workout-Settings-Preferences-Timer-Warm-up-calculator-Plate-Calculator-Smart-Superset-Scrolling (search listing)
- https://aitoolsbakery.com/blog/hevy-review/

### Strong
- https://www.strong.app/

### MuscleWiki
- https://musclewiki.com/
- https://musclewiki.com/exercise/barbell-bench-press
- https://apps.apple.com/us/app/musclewiki-workout-fitness/id1096827640 (search summary only)
- https://musclewiki.com/gopremium (search summary only)

### Muscle & Motion
- https://www.muscleandmotion.com/

### ExRx.net
- https://exrx.net/WeightExercises/PectoralSternal/BBBenchPress

### Freeletics
- https://www.freeletics.com/en/
- https://www.freeletics.com/en/blog/posts/what-is-the-purpose-of-the-feedback-i-am-asked-to-give-after-each-workout/
- https://apps.apple.com/app/id654810212

### Apple Fitness+
- https://support.apple.com/guide/fitness-plus/use-custom-plans-apdf222051d8/ios

### Ladder
- https://www.joinladder.com/
- https://www.bustle.com/wellness/ladder-app-review (search summary only)
- https://www.garagegymreviews.com/ladder-app-review (search summary only)
