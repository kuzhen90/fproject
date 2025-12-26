# Sleep App MVP Specification

**Document Created:** December 25, 2024
**App Name:** (TBD - working title: "Sleep Coach AI")
**Target:** Low-capital startup, small team

---

## Part 1: Competitive Gap Analysis

### What Current Apps Do Well vs. What They're Missing

| App | Strengths | Critical Gaps |
|-----|-----------|---------------|
| **Calm** | Beautiful sleep stories, celebrity narrators, relaxing content | No tracking, no personalization, $70/yr, can't filter content, same content for everyone |
| **Headspace** | Structured courses, educational, "Sleepcasts" | No tracking, overwhelming for casual users, content-heavy not results-focused |
| **Sleep Cycle** | Excellent sleep tracking, smart alarm, health integrations | Zero content to help you fall asleep, passive (tracks but doesn't improve) |
| **Sleepio** | Clinical CBT-I, evidence-based, effective | Prescription required, expensive, clinical/medical feel, not accessible |
| **CBT-I Coach (VA)** | Free, has CBT-I components | Requires clinician involvement, dated UI, not standalone |

### The Gap We're Filling

**No app combines:**
1. Sleep tracking (like Sleep Cycle)
2. Personalized content (not one-size-fits-all like Calm)
3. CBT-I techniques (clinically proven but accessible)
4. AI that learns YOUR patterns

### User Pain Points (From Research)

| Pain Point | Source | Our Solution |
|------------|--------|--------------|
| "Same content doesn't work for me" | Reddit/Reviews | AI personalization |
| "I track my sleep but don't know what to do about it" | Common complaint | Actionable insights |
| "Subscription feels expensive for what I get" | Trustpilot (1.8-2.0 stars) | Value-focused pricing |
| "Can't filter content by what I need" | Calm reviews | Smart recommendations |
| "Clinical apps require a prescription" | Sleepio limitation | Accessible CBT-I |
| "App tracks but doesn't help me improve" | Sleep Cycle gap | Active improvement focus |

---

## Part 2: MVP Feature Definition

### Core Philosophy

**"Track, Learn, Improve"**

Unlike competitors that are either:
- Passive trackers (Sleep Cycle) - tells you what happened
- Content libraries (Calm/Headspace) - gives you stuff to try
- Clinical tools (Sleepio) - requires medical involvement

We are an **active coach** that:
1. Tracks your sleep
2. Learns what affects YOUR sleep
3. Recommends what to try tonight
4. Measures if it worked
5. Adjusts recommendations

---

### MVP Features: Must Have (Week 1-8 Build)

#### 1. Sleep Diary (Core Foundation)

**What:** Quick daily logging of sleep quality and factors

**User Flow:**
```
Morning notification (9am): "How did you sleep?"

Screen 1: Sleep Quality
├── 😫 Terrible
├── 😕 Poor
├── 😐 Okay
├── 🙂 Good
└── 😴 Great

Screen 2: Quick Factors (multi-select)
├── Caffeine after 2pm
├── Alcohol
├── Exercise
├── Screen time before bed
├── Stress/Anxiety
├── Late meal
└── [Custom factor]

Screen 3: Sleep Times
├── What time did you go to bed?
├── What time did you wake up?
└── How long to fall asleep? (estimate)

→ Done! (Under 30 seconds)
```

**Why MVP:** This is the data foundation. Without this, we can't personalize.

**Technical Notes:**
- Store locally + sync to backend
- Calculate: Time in bed, sleep efficiency, trends
- Simple SQLite/Realm on device

---

#### 2. Insights Dashboard

**What:** Show users what's affecting THEIR sleep

**Displays:**
```
Your Sleep This Week
├── Average quality: 3.2/5 ⬆️ (+0.3 from last week)
├── Average duration: 6.5 hours
└── Sleep efficiency: 78%

What's Helping You
├── ✅ Exercise days: +1.2 quality points
└── ✅ No screens after 9pm: +0.8 quality points

What's Hurting You
├── ⚠️ Caffeine after 2pm: -1.5 quality points
└── ⚠️ Late meals: -0.9 quality points

This Week's Insight
"You sleep 47 minutes longer on days you exercise.
Try exercising today for better sleep tonight."
```

**Why MVP:** This is our differentiator. Calm/Headspace don't have this.

**Technical Notes:**
- Simple correlation analysis (not complex ML for MVP)
- Compare sleep quality on days with/without each factor
- Statistical significance check before showing insight

---

#### 3. Tonight's Recommendation

**What:** One personalized action to try tonight

**User Flow:**
```
Evening notification (8pm): "Ready for better sleep tonight?"

Tonight's Recommendation
━━━━━━━━━━━━━━━━━━━━━━━━
Based on your patterns, try this tonight:

🧘 4-7-8 Breathing Exercise
"You've had a stressful day. This technique
activates your parasympathetic nervous system."

[Start Exercise] [Remind me at 10pm] [Skip]

━━━━━━━━━━━━━━━━━━━━━━━━
Tomorrow, tell us if it helped!
```

**Recommendation Logic (MVP - Rule-Based):**
```
IF stress_logged_today THEN recommend: breathing_exercise
IF caffeine_after_2pm THEN recommend: extended_wind_down
IF no_exercise_3_days THEN recommend: light_stretching
IF screen_time_high THEN recommend: screen_dimming_reminder
IF new_user THEN recommend: sleep_hygiene_basics
DEFAULT: rotate through technique library
```

**Why MVP:** This is the "coach" that makes us different from trackers.

---

#### 4. Technique Library (Core Content)

**What:** Audio/text guides for sleep improvement techniques

**MVP Content (10-15 pieces, can self-produce):**

| Category | Techniques | Duration |
|----------|-----------|----------|
| **Breathing** | 4-7-8 Breathing, Box Breathing, Deep Belly Breathing | 3-5 min each |
| **Relaxation** | Progressive Muscle Relaxation, Body Scan | 10-15 min |
| **Cognitive** | Worry Dump (journaling prompt), Cognitive Shuffle | 5-10 min |
| **Wind-Down** | Screen dimming guide, Bedroom environment checklist | 2-3 min |
| **Sleep Hygiene** | Caffeine timing, Meal timing, Temperature guide | 2-3 min reads |

**Why These Specific Techniques:**
- 4-7-8 Breathing: Clinically validated, easy to teach
- Progressive Muscle Relaxation: Core CBT-I component
- Cognitive Shuffle: Disrupts racing thoughts
- Sleep Hygiene: Foundation everyone needs

**Content Production:**
- Text guides: Write ourselves
- Audio: Record with good microphone (or use AI voice for MVP)
- No need for celebrity narrators (that's Calm's game)

**Why MVP:** Users need something to DO, not just data.

---

#### 5. Progress Tracking

**What:** Show improvement over time (motivation + retention)

**Displays:**
```
Your Sleep Journey
━━━━━━━━━━━━━━━━━━

Week 1: ██░░░░░░░░ 2.1 avg
Week 2: ████░░░░░░ 2.8 avg
Week 3: █████░░░░░ 3.2 avg ← You are here
Week 4: Goal: 3.5+

🎯 You've improved 52% since starting!

Techniques That Work For You:
1. 4-7-8 Breathing (+1.2 quality)
2. No screens after 9pm (+0.8 quality)
3. Worry dump journaling (+0.6 quality)
```

**Why MVP:** Retention driver. Users need to see progress to keep logging.

---

### MVP Features: Nice to Have (Post-Launch)

| Feature | Priority | Why Defer |
|---------|----------|-----------|
| Passive sleep tracking (phone sensors) | Medium | Adds complexity, battery issues |
| Smart alarm | Medium | Sleep Cycle does this well |
| Apple Watch / Fitbit integration | Medium | API complexity |
| Social features | Low | Not core to sleep improvement |
| Sleep sounds/white noise | Low | Commoditized, not differentiating |
| AI chatbot | Low | Engineering complexity |

---

### MVP Features: Explicitly NOT Building

| Feature | Why NOT |
|---------|---------|
| Sleep stories (Calm's territory) | Content-heavy, expensive to produce, not our differentiator |
| Meditation courses | Headspace's territory, not sleep-specific |
| Clinical CBT-I program | Requires clinical validation, regulatory concerns |
| Wearable hardware | Capital-intensive, not our game |
| Community features | Distraction from core value |

---

## Part 3: CBT-I Techniques (Simplified for Consumer App)

### What We're Adapting From Clinical CBT-I

**Full CBT-I has 5 components:**

| Component | Clinical Version | Our Accessible Version |
|-----------|------------------|------------------------|
| **Sleep Restriction** | Strict time-in-bed limits set by clinician | "Sleep Window" suggestions based on efficiency |
| **Stimulus Control** | Rigid rules about bed use | Gentle reminders + education |
| **Sleep Hygiene** | Basic education | Interactive checklists + tracking |
| **Relaxation Training** | PMR, breathing exercises | Guided audio techniques |
| **Cognitive Therapy** | Challenging sleep beliefs with therapist | Journaling prompts, reframing tips |

### Sample "Accessible Sleep Restriction" Feature

**Clinical version:** "You can only be in bed from 11pm-5am. No exceptions."

**Our version:**
```
Your Sleep Window
━━━━━━━━━━━━━━━━━

Based on your logs, you spend 8 hours in bed
but only sleep 6 hours (75% efficiency).

💡 Try This Week:
Go to bed at 11:30pm instead of 10:30pm.
This can improve sleep quality by consolidating sleep.

[Set 11:30pm reminder] [Learn why this works]

Note: If you feel excessively sleepy during the day,
we'll adjust your window. You're in control.
```

**Key Difference:** We suggest, we don't prescribe. User has control.

---

## Part 4: Technical MVP Approach

### Architecture (Keep It Simple)

```
┌─────────────────────────────────────────────┐
│                 Mobile App                   │
│            (React Native / Expo)             │
│                                              │
│  ┌─────────┐ ┌─────────┐ ┌─────────────┐   │
│  │ Sleep   │ │ Insights│ │ Technique   │   │
│  │ Diary   │ │ Dashboard│ │ Library    │   │
│  └─────────┘ └─────────┘ └─────────────┘   │
│                                              │
│  ┌─────────────────────────────────────┐    │
│  │      Local Storage (Realm/SQLite)    │    │
│  └─────────────────────────────────────┘    │
└─────────────────────────────────────────────┘
                      │
                      │ Sync
                      ▼
┌─────────────────────────────────────────────┐
│                 Backend (Simple)             │
│              (Firebase / Supabase)           │
│                                              │
│  ┌─────────┐ ┌─────────┐ ┌─────────────┐   │
│  │ Auth    │ │ User    │ │ Analytics   │   │
│  │         │ │ Data    │ │             │   │
│  └─────────┘ └─────────┘ └─────────────┘   │
└─────────────────────────────────────────────┘
```

### Tech Stack Recommendation

| Layer | Choice | Why |
|-------|--------|-----|
| Mobile | React Native + Expo | Cross-platform, fast iteration, your girlfriend can test on either device |
| Backend | Supabase or Firebase | Auth, database, hosting included. Low cost at scale. |
| Audio | Local assets or CDN | Simple, no streaming complexity |
| Analytics | Mixpanel free tier | Track feature usage |
| Notifications | Expo Push + OneSignal | Critical for daily engagement |

### MVP Database Schema

```sql
-- Users
users (
  id, email, created_at, onboarding_complete,
  timezone, notification_preferences
)

-- Sleep Logs (core data)
sleep_logs (
  id, user_id, date,
  bed_time, wake_time,
  time_to_fall_asleep,
  quality_rating (1-5),
  factors (json array),
  notes,
  created_at
)

-- Technique Usage
technique_logs (
  id, user_id, date,
  technique_id,
  completed (boolean),
  helpful_rating (1-5, nullable),
  created_at
)

-- Recommendations
recommendations (
  id, user_id, date,
  technique_id,
  reason,
  was_followed (boolean),
  created_at
)
```

---

## Part 5: 8-Week Development Roadmap

### Week 1-2: Foundation
- [ ] Project setup (Expo, navigation, styling)
- [ ] Basic screens scaffolding
- [ ] Supabase/Firebase setup
- [ ] Authentication (email/password, Apple Sign-In)
- [ ] Sleep diary entry screen
- [ ] Local storage setup

### Week 3-4: Core Features
- [ ] Sleep log submission flow
- [ ] Basic insights calculation
- [ ] Insights dashboard UI
- [ ] Technique library (text content)
- [ ] Basic recommendation engine (rule-based)

### Week 5-6: Content & Polish
- [ ] Record audio for 5-10 techniques
- [ ] Audio player integration
- [ ] Progress tracking screen
- [ ] Push notifications (morning + evening)
- [ ] Onboarding flow

### Week 7: Testing
- [ ] Beta with girlfriend + friends
- [ ] Bug fixes
- [ ] Performance optimization
- [ ] App Store assets (screenshots, description)

### Week 8: Launch Prep
- [ ] App Store submission (iOS)
- [ ] Google Play submission (Android)
- [ ] Landing page update
- [ ] Soft launch to waitlist

---

## Part 6: Monetization Strategy

### Pricing Model

| Tier | Price | Features |
|------|-------|----------|
| **Free** | $0 | Sleep diary, basic insights, 3 techniques |
| **Pro** | $6.99/mo or $49.99/yr | All techniques, full insights, personalized recommendations, progress tracking |
| **Lifetime** | $99.99 | Everything forever (good for early adopters) |

### Why This Pricing

- **Cheaper than Calm ($70/yr) and Headspace ($70/yr)**
- **More expensive than Sleep Cycle ($40/yr)** - we offer more value
- **Lifetime option** reduces churn concern, good PR

### Free Tier Strategy

Free tier should be useful enough that users:
1. Build the daily logging habit
2. See enough value to want more
3. Hit the paywall naturally when they want personalization

---

## Part 7: Success Metrics

### North Star Metric
**Weekly Active Loggers (WAL):** Users who log sleep at least 4 days per week

### Supporting Metrics

| Metric | Target (Month 1) | Why It Matters |
|--------|------------------|----------------|
| Day 1 Retention | >40% | Onboarding effectiveness |
| Day 7 Retention | >25% | Core value resonating |
| Day 30 Retention | >15% | Habit formed |
| Logs per user per week | >4 | Data quality for insights |
| Technique completion rate | >30% | Content engagement |
| Free → Pro conversion | >5% | Monetization health |

---

## Part 8: Competitive Positioning

### Our Tagline Options
1. "Sleep better, not just track it"
2. "Your personal sleep coach"
3. "Finally understand YOUR sleep"

### Key Differentiators to Emphasize

| vs. Calm/Headspace | vs. Sleep Cycle | vs. Sleepio |
|-------------------|-----------------|-------------|
| We track and personalize | We help you improve, not just track | No prescription needed |
| Results-focused, not content-focused | Active coaching, not passive data | Consumer-friendly, not clinical |
| Affordable | More comprehensive | Accessible price |

### App Store Optimization Keywords
- sleep coach
- insomnia help
- sleep better
- CBT for sleep
- sleep tracker
- personalized sleep
- sleep improvement
- sleep quality

---

## Summary: What Makes Our MVP Different

| Feature | Calm | Headspace | Sleep Cycle | Us |
|---------|------|-----------|-------------|-----|
| Sleep tracking | ❌ | ❌ | ✅ | ✅ |
| Personalized insights | ❌ | ❌ | ❌ | ✅ |
| CBT-I techniques | ❌ | ❌ | ❌ | ✅ |
| Actionable recommendations | ❌ | ❌ | ❌ | ✅ |
| Progress tracking | ❌ | ✅ | ✅ | ✅ |
| Content library | ✅ | ✅ | ❌ | ✅ (focused) |
| Affordable | ❌ ($70) | ❌ ($70) | ✅ ($40) | ✅ ($50) |

**Our unique value:** We're the only app that tracks YOUR sleep, learns YOUR patterns, and tells you exactly what to try tonight - then measures if it worked.

---

## Next Steps

1. **Validate:** Talk to 10 people with sleep issues (start with your girlfriend)
2. **Name:** Decide on app name
3. **Design:** Create Figma mockups of core screens
4. **Build:** Start Week 1 of development
5. **Content:** Write/record first 5 techniques

---

## Sources

- [Sleep Foundation - CBT-I Overview](https://www.sleepfoundation.org/insomnia/treatment/cognitive-behavioral-therapy-insomnia)
- [PMC - Digital CBT-I Apps Review](https://pmc.ncbi.nlm.nih.gov/articles/PMC7999422/)
- [PMC - CBT-I Primer](https://pmc.ncbi.nlm.nih.gov/articles/PMC10002474/)
- [VA - CBT-I Coach App](https://www.ptsd.va.gov/appvid/mobile/cbticoach_app_public.asp)
- User reviews from Trustpilot, Reddit, and app stores
