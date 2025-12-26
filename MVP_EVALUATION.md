# MVP Feature Evaluation & Ranking

**Created:** December 25, 2024
**Purpose:** Evaluate and prioritize MVP features for Sleep Coach AI

---

## Evaluation Criteria

Each feature scored 1-5 on:

| Criteria | Description |
|----------|-------------|
| **Impact** | How much will this actually improve user's sleep? |
| **Differentiation** | Does this set us apart from Calm/Headspace/Sleep Cycle? |
| **Complexity** | How hard is this to build? (5 = easy, 1 = hard) |
| **User Effort** | How much work for the user? (5 = effortless, 1 = high effort) |
| **Scope Fit** | Does this align with our core mission? |

**Total Score** = Sum of all criteria (max 25)

---

## Your Idea: Bedtime Grayscale Mode

### Concept
At the user's set bedtime, the phone screen turns grayscale to reduce stimulation and eye strain, making it less appealing to keep scrolling.

### Technical Reality Check

| Platform | Feasibility | How It Would Work |
|----------|-------------|-------------------|
| **iOS** | Limited | Cannot programmatically enable grayscale. Would need to **guide users** to enable it via Settings > Accessibility > Color Filters, then use Shortcuts app to schedule it. We can send a reminder + instructions. |
| **Android** | Moderate | Requires `WRITE_SECURE_SETTINGS` permission which needs ADB command from computer. Or use AccessibilityService which requires user to grant accessibility access. Complex onboarding. |

### Verdict on Your Idea

**The concept is excellent** - it's a real stimulus control technique from CBT-I. The problem is execution:

| Approach | Pros | Cons |
|----------|------|------|
| **A: Reminder + Guide** | Easy to build, cross-platform | We don't control it, user may ignore |
| **B: Native Integration (Android only)** | Actually works | Complex setup, Android only, scary permissions |
| **C: In-App Grayscale** | We control it | Only works while in our app |

**Recommendation:** Start with **Approach A** (reminder + setup guide). If users love the concept, invest in deeper Android integration later.

### Scoring: Bedtime Grayscale Mode

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 4 | Proven technique, reduces phone appeal |
| Differentiation | 5 | No sleep app does this |
| Complexity | 2 | System-level control is hard |
| User Effort | 2 | Requires manual setup on iOS |
| Scope Fit | 4 | Stimulus control is CBT-I, fits mission |
| **Total** | **17/25** | |

---

## 5 New MVP Feature Ideas

### New MVP #1: Wind-Down Routine Builder

**Concept:** Users create a personalized 15-30 minute pre-sleep ritual with timed steps. App guides them through it each night.

**How It Works:**
```
Example Routine (User Customizes):
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━

10:00 PM - Routine Starts
├── 10:00 - Put phone on charger (not in bedroom)
├── 10:05 - Light stretching (5 min guided)
├── 10:10 - Worry dump journal (5 min)
├── 10:15 - Brush teeth, skincare
├── 10:20 - 4-7-8 breathing in bed (5 min guided)
└── 10:25 - Lights out

[Start Tonight's Routine]
```

**Why It Works:**
- Consistent routine = sleep cues for brain
- Replaces doom-scrolling with structured activity
- Combines multiple techniques into one flow

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 5 | Routines are proven to improve sleep |
| Differentiation | 5 | No app has customizable guided routines |
| Complexity | 3 | Timer + content + notifications |
| User Effort | 3 | Requires following the routine |
| Scope Fit | 5 | Core to sleep improvement |
| **Total** | **21/25** | |

---

### New MVP #2: Worry Dump Journal

**Concept:** Quick 2-minute journaling before bed to get racing thoughts out of your head. Research shows this reduces time to fall asleep.

**How It Works:**
```
Tonight's Worry Dump
━━━━━━━━━━━━━━━━━━━

What's on your mind tonight?
┌─────────────────────────────────┐
│ Work deadline Friday...         │
│ Need to call mom tomorrow...    │
│ Did I pay the electric bill?    │
│                                 │
└─────────────────────────────────┘

[These are saved. You can deal with them tomorrow.]

Optional: What are you grateful for today?
┌─────────────────────────────────┐
│ Good lunch with Sarah           │
│                                 │
└─────────────────────────────────┘

[Done - Sweet dreams 🌙]
```

**Research Backing:**
- Study: Writing a to-do list before bed reduced sleep onset by 9 minutes
- Cognitive offloading reduces rumination
- Gratitude journaling linked to better sleep quality

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 4 | Research-backed, addresses racing mind |
| Differentiation | 4 | Reflectly does this but not sleep-focused |
| Complexity | 5 | Simple text entry + storage |
| User Effort | 4 | 2 minutes, low friction |
| Scope Fit | 5 | Cognitive therapy component of CBT-I |
| **Total** | **22/25** | |

---

### New MVP #3: Caffeine Half-Life Calculator

**Concept:** Track caffeine intake and see exactly when it will leave your system. Personalized alerts when you're approaching your "caffeine cutoff" time.

**How It Works:**
```
Your Caffeine Today
━━━━━━━━━━━━━━━━━━━

8:00 AM  ☕ Large coffee (200mg)
1:30 PM  🥤 Diet Coke (46mg)
         ─────────────────
         Total: 246mg

Caffeine in your system right now: 87mg
Estimated clear time: 11:30 PM

⚠️ For your 10:30 PM bedtime, avoid caffeine after 2:00 PM

[Log Caffeine] [Set Cutoff Alert]
```

**Science:**
- Caffeine half-life: ~5-6 hours (varies by person)
- Even 6 hours before bed, caffeine can reduce sleep by 1 hour
- Most people underestimate caffeine's duration

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 4 | Caffeine is #1 sleep disruptor |
| Differentiation | 5 | No sleep app has this |
| Complexity | 4 | Simple math + logging |
| User Effort | 3 | Requires logging each drink |
| Scope Fit | 4 | Sleep hygiene education |
| **Total** | **20/25** | |

---

### New MVP #4: Sleep Window Calculator (Sleep Restriction Lite)

**Concept:** Based on user's actual sleep (not time in bed), calculate their optimal "sleep window" to improve sleep efficiency.

**How It Works:**
```
Your Sleep Analysis
━━━━━━━━━━━━━━━━━━━

This Week's Average:
├── Time in bed: 8.5 hours
├── Actual sleep: 6.2 hours
└── Sleep efficiency: 73% ⚠️

The Problem:
You're spending 2+ hours in bed NOT sleeping.
This trains your brain that bed = awake.

Recommended Sleep Window:
━━━━━━━━━━━━━━━━━━━━━━━━

Instead of: 10:00 PM - 6:30 AM (8.5 hrs)
Try this week: 11:00 PM - 6:00 AM (7 hrs)

Why? Compressing your sleep window increases
"sleep pressure" and improves efficiency.

[Start Sleep Window Challenge] [Learn More]

Note: If you feel excessively sleepy during the
day, we'll adjust. Safety first.
```

**Research Backing:**
- Sleep restriction is the most effective CBT-I component
- Increases sleep efficiency from ~70% to 85%+
- Works by building sleep pressure

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 5 | Most effective CBT-I technique |
| Differentiation | 5 | Only clinical apps have this |
| Complexity | 3 | Calculations + recommendations + safety checks |
| User Effort | 2 | Requires behavior change |
| Scope Fit | 5 | Core CBT-I component |
| **Total** | **20/25** | |

---

### New MVP #5: Smart Bedtime Reminder System

**Concept:** Intelligent reminders that adapt based on your schedule, not just a fixed time. Knows when to nudge you to start winding down.

**How It Works:**
```
Smart Reminders
━━━━━━━━━━━━━━━

Your target bedtime: 10:30 PM
Your target wake time: 6:30 AM (8 hrs)

Reminder Schedule:
├── 9:30 PM - "1 hour to bedtime. Wrap up screens."
├── 10:00 PM - "30 min. Time to start your routine."
├── 10:15 PM - "15 min. Head to bedroom."
└── 10:30 PM - "Bedtime. Goodnight! 🌙"

Smart Features:
✓ Knows your calendar - adjusts for late meetings
✓ Weekend mode - shifts 1 hour later
✓ Detects phone activity - extra nudge if still scrolling
```

**Why It's Different:**
- Most apps: Single alarm
- Us: Progressive reminders that guide behavior
- Context-aware (calendar, activity)

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 3 | Reminders help but don't solve root cause |
| Differentiation | 3 | Some apps have reminders, but not smart ones |
| Complexity | 4 | Notifications + basic calendar integration |
| User Effort | 5 | Passive, app does the work |
| Scope Fit | 4 | Supports consistency |
| **Total** | **19/25** | |

---

## Existing MVP Features (From Previous Doc)

### Existing #1: Sleep Diary

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 5 | Foundation for all personalization |
| Differentiation | 3 | Others have diaries, but we use it better |
| Complexity | 5 | Simple logging |
| User Effort | 4 | 30 seconds/day |
| Scope Fit | 5 | Core data foundation |
| **Total** | **22/25** | |

---

### Existing #2: Personalized Insights Dashboard

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 5 | Shows users what actually affects THEIR sleep |
| Differentiation | 5 | No consumer app does this |
| Complexity | 3 | Correlation analysis |
| User Effort | 5 | Passive - app generates insights |
| Scope Fit | 5 | Core differentiator |
| **Total** | **23/25** | |

---

### Existing #3: Tonight's Recommendation Engine

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 4 | Actionable advice |
| Differentiation | 5 | No app recommends based on YOUR data |
| Complexity | 3 | Rule-based initially, ML later |
| User Effort | 4 | User just follows suggestion |
| Scope Fit | 5 | Core "coach" functionality |
| **Total** | **21/25** | |

---

### Existing #4: Technique Library

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 4 | Proven techniques |
| Differentiation | 2 | Calm/Headspace have content too |
| Complexity | 4 | Content creation + audio |
| User Effort | 3 | User must engage with content |
| Scope Fit | 5 | Core sleep improvement tools |
| **Total** | **18/25** | |

---

### Existing #5: Progress Tracking

| Criteria | Score | Reasoning |
|----------|-------|-----------|
| Impact | 3 | Motivation, not direct improvement |
| Differentiation | 2 | Others have progress tracking |
| Complexity | 5 | Simple visualization |
| User Effort | 5 | Passive |
| Scope Fit | 4 | Retention feature |
| **Total** | **19/25** | |

---

## Complete MVP Ranking

### Tier 1: Must Have (Score 21+)

| Rank | Feature | Score | Type | Reasoning |
|------|---------|-------|------|-----------|
| 1 | **Personalized Insights Dashboard** | 23 | Existing | Our #1 differentiator. No one else does this. |
| 2 | **Sleep Diary** | 22 | Existing | Foundation for everything. No insights without data. |
| 3 | **Worry Dump Journal** | 22 | NEW | High impact, dead simple to build, research-backed. |
| 4 | **Tonight's Recommendation** | 21 | Existing | The "coach" that makes us different. |
| 5 | **Wind-Down Routine Builder** | 21 | NEW | Combines everything into one guided experience. |

### Tier 2: Should Have (Score 19-20)

| Rank | Feature | Score | Type | Reasoning |
|------|---------|-------|------|-----------|
| 6 | **Caffeine Half-Life Calculator** | 20 | NEW | Unique, practical, addresses top sleep disruptor. |
| 7 | **Sleep Window Calculator** | 20 | NEW | Most effective CBT-I technique, but harder to implement safely. |
| 8 | **Progress Tracking** | 19 | Existing | Retention driver, but not core functionality. |
| 9 | **Smart Bedtime Reminders** | 19 | NEW | Helpful but not differentiated. |

### Tier 3: Nice to Have (Score <19)

| Rank | Feature | Score | Type | Reasoning |
|------|---------|-------|------|-----------|
| 10 | **Technique Library** | 18 | Existing | Necessary but not differentiating. Keep lean. |
| 11 | **Bedtime Grayscale Mode** | 17 | NEW (yours) | Great concept but technical limitations reduce score. |

---

## Deep Dive: Your Grayscale Idea

### Why It Scored Lower (But Is Still Worth Considering)

**The Good:**
- Unique - no sleep app does this
- Proven technique (stimulus control)
- Addresses real problem (phone addiction at night)
- Shows we're serious about behavior change

**The Challenges:**
- iOS: Can only guide users to settings, can't control it
- Android: Requires scary permissions or complex setup
- User might set it up once and forget
- Doesn't directly improve sleep - removes a barrier

### Recommendation: Hybrid Approach

**Phase 1 (MVP):** Simple version
- Reminder at bedtime: "Time to enable grayscale"
- One-time setup guide (screenshots for iOS/Android)
- Track if user enabled it (ask next morning)

**Phase 2 (Post-launch):** Deeper integration
- Android: Explore AccessibilityService approach
- iOS: Shortcuts integration guide
- Measure actual impact on users' sleep

### How To Reframe for Higher Score

Instead of "Bedtime Grayscale Mode", call it:

**"Digital Wind-Down Mode"**

Includes:
1. Grayscale reminder + setup guide
2. DND suggestion
3. Night Shift / blue light filter reminder
4. "Put phone in another room" challenge

This bundles multiple stimulus control techniques and makes grayscale one part of a bigger feature.

| Criteria | Original | Reframed |
|----------|----------|----------|
| Impact | 4 | 5 (multiple techniques) |
| Differentiation | 5 | 5 |
| Complexity | 2 | 3 (simpler, reminder-based) |
| User Effort | 2 | 3 (guided setup) |
| Scope Fit | 4 | 5 |
| **Total** | **17** | **21** |

---

## Recommended MVP Feature Set

### Phase 1: Core MVP (Weeks 1-8)

| Priority | Feature | Why |
|----------|---------|-----|
| P0 | Sleep Diary | Foundation - no data, no app |
| P0 | Personalized Insights | #1 differentiator |
| P0 | Tonight's Recommendation | The "coach" |
| P1 | Worry Dump Journal | Easy win, high impact |
| P1 | Technique Library (5-10 pieces) | Something to recommend |
| P2 | Progress Tracking | Retention |

### Phase 2: Quick Wins (Weeks 9-12)

| Priority | Feature | Why |
|----------|---------|-----|
| P1 | Wind-Down Routine Builder | Guided experience differentiator |
| P1 | Caffeine Calculator | Unique, practical |
| P2 | Smart Reminders | Polish |
| P2 | Digital Wind-Down Mode (your idea) | Bundle grayscale + DND + more |

### Phase 3: Advanced (Post-Launch)

| Priority | Feature | Why |
|----------|---------|-----|
| P2 | Sleep Window Calculator | Needs more data + safety considerations |
| P3 | Deep grayscale integration | Android AccessibilityService |

---

## Summary

### Top 5 Features For MVP Launch

1. **Sleep Diary** - Can't personalize without data
2. **Personalized Insights** - Our killer feature
3. **Tonight's Recommendation** - The "coach"
4. **Worry Dump Journal** - Easy, high-impact addition
5. **Technique Library** - Something to recommend

### Your Grayscale Idea: Verdict

**Keep it, but reframe it:**
- Don't make it a standalone feature
- Bundle into "Digital Wind-Down Mode"
- Start with reminder + guide approach
- Invest in deeper integration only if users love it

The concept is solid - the execution just needs to be practical for Phase 1.

---

## Sources

- [Android Police - Grayscale Setup](https://www.androidpolice.com/how-to-activate-grayscale-on-mobile/)
- [Sleep Foundation - Best Sleep Apps 2025](https://www.sleepfoundation.org/best-sleep-apps)
- [PMC - CBT-I Primer](https://pmc.ncbi.nlm.nih.gov/articles/PMC10002474/)
- [PMC - Sleep App Design Considerations](https://ncbi.nlm.nih.gov/pmc/articles/PMC9624283)
