# Sleep Coach AI - Complete Project Summary

**Last Updated:** December 25, 2024
**Status:** Research & Planning Complete, Awaiting Development
**Project Manager Agent:** `@.claude/agents/sleep-app-pm.md`

---

## Executive Summary

### The Opportunity
A sleep improvement app that fills the gap between:
- **Calm/Headspace** (content but no tracking/personalization)
- **Sleep Cycle** (tracking but no improvement guidance)
- **Sleepio** (clinical CBT-I but prescription required)

### Our Unique Value Proposition
> "We're the only app that tracks YOUR sleep, learns YOUR patterns, and tells you exactly what to try tonight - then measures if it worked."

### Target User
Adults with sleep issues who:
- Have tried Calm/Headspace but didn't see lasting improvement
- Track sleep but don't know what to do with the data
- Want evidence-based techniques without clinical involvement
- Are willing to invest 30 seconds/day for personalized insights

---

## Market Research Summary

### Market Size
| Metric | Value |
|--------|-------|
| Sleep App Market (2024) | $3.98 billion |
| Projected (2033) | $17.5 billion |
| CAGR | 17.9% |
| Digital Insomnia Therapeutics | $5.16B by 2031 |

### Competitive Landscape

| App | Strengths | Weaknesses | Pricing |
|-----|-----------|------------|---------|
| **Calm** | Beautiful content, celebrity narrators, sleep stories | No tracking, no personalization, same content for everyone | $70/year |
| **Headspace** | Structured courses, educational, "Sleepcasts" | No tracking, overwhelming, content-heavy | $70/year |
| **Sleep Cycle** | Excellent tracking, smart alarm, health integrations | Zero content to help you fall asleep, passive | $40/year |
| **Sleepio** | Clinical CBT-I, evidence-based, effective | Prescription required, expensive, clinical feel | $$$ |
| **CBT-I Coach (VA)** | Free, has CBT-I components | Requires clinician, dated UI | Free |

### Key User Pain Points (From Research)
1. "Same content doesn't work for me" → Need personalization
2. "I track but don't know what to do" → Need actionable insights
3. "Subscription feels expensive" → Need better value
4. "Clinical apps need prescription" → Need accessible CBT-I
5. "Can't filter content by need" → Need smart recommendations

### The Gap We Fill
No app combines:
1. Sleep tracking (like Sleep Cycle)
2. Personalized content (not one-size-fits-all)
3. CBT-I techniques (clinically proven)
4. AI that learns YOUR patterns

---

## Technical Approach

### Recommended Tech Stack
| Layer | Technology | Reasoning |
|-------|------------|-----------|
| Mobile | React Native + Expo | Cross-platform, fast iteration |
| Backend | Supabase or Firebase | Auth, DB, hosting included, low cost |
| Audio | Local assets or CDN | Simple, no streaming complexity |
| Analytics | Mixpanel free tier | Track feature usage |
| Notifications | Expo Push + OneSignal | Critical for daily engagement |

### Database Schema (Core Tables)
```sql
users (id, email, created_at, timezone, notification_preferences)
sleep_logs (id, user_id, date, bed_time, wake_time, quality_rating, factors, notes)
technique_logs (id, user_id, date, technique_id, completed, helpful_rating)
recommendations (id, user_id, date, technique_id, reason, was_followed)
```

### Architecture
```
Mobile App (React Native/Expo)
├── Sleep Diary
├── Insights Dashboard
├── Technique Library
└── Local Storage (Realm/SQLite)
         │
         │ Sync
         ▼
Backend (Supabase/Firebase)
├── Auth
├── User Data
└── Analytics
```

---

## MVP Feature Rankings

### Tier 1: Must Have (Score 21+/25)

| Rank | Feature | Score | Description |
|------|---------|-------|-------------|
| 1 | Personalized Insights Dashboard | 23 | Shows users what affects THEIR sleep |
| 2 | Sleep Diary | 22 | 30-second daily logging foundation |
| 3 | Worry Dump Journal | 22 | 2-min brain dump before bed |
| 4 | Tonight's Recommendation | 21 | Personalized technique suggestion |
| 5 | Wind-Down Routine Builder | 21 | Customizable guided pre-sleep ritual |

### Tier 2: Should Have (Score 19-20)

| Rank | Feature | Score | Description |
|------|---------|-------|-------------|
| 6 | Caffeine Half-Life Calculator | 20 | Track when caffeine leaves system |
| 7 | Sleep Window Calculator | 20 | CBT-I sleep restriction lite |
| 8 | Progress Tracking | 19 | Visualize improvement over time |
| 9 | Smart Bedtime Reminders | 19 | Progressive wind-down notifications |

### Tier 3: Nice to Have (Score <19)

| Rank | Feature | Score | Description |
|------|---------|-------|-------------|
| 10 | Technique Library | 18 | Audio/text guides for techniques |
| 11 | Digital Wind-Down Mode | 17 | Grayscale + DND bundle (reframed from original idea) |

### Features Explicitly NOT Building
- Sleep stories (Calm's territory)
- Meditation courses (Headspace's territory)
- Passive phone tracking (complexity)
- Wearable integration (defer to v2)
- Clinical CBT-I program (regulatory concerns)

---

## CBT-I Techniques to Include

### Core Techniques (MVP)
| Technique | Type | Duration | Description |
|-----------|------|----------|-------------|
| 4-7-8 Breathing | Breathing | 3-5 min | Activates parasympathetic system |
| Box Breathing | Breathing | 3-5 min | Calming square pattern |
| Progressive Muscle Relaxation | Relaxation | 10-15 min | Tense and release muscle groups |
| Body Scan | Relaxation | 10-15 min | Mental scan from head to toe |
| Cognitive Shuffle | Cognitive | 5-10 min | Random word visualization to disrupt racing thoughts |
| Worry Dump | Cognitive | 5 min | Journaling to offload thoughts |
| Sleep Hygiene Checklist | Education | 2-3 min | Environment optimization |

### CBT-I Components Adapted for Consumer App
| Clinical Component | Our Accessible Version |
|--------------------|------------------------|
| Sleep Restriction | "Sleep Window" suggestions |
| Stimulus Control | Gentle reminders + education |
| Sleep Hygiene | Interactive checklists + tracking |
| Relaxation Training | Guided audio techniques |
| Cognitive Therapy | Journaling prompts, reframing tips |

---

## Monetization Strategy

### Pricing Tiers
| Tier | Price | Features |
|------|-------|----------|
| Free | $0 | Sleep diary, basic insights, 3 techniques |
| Pro | $6.99/mo or $49.99/yr | All techniques, full insights, personalized recommendations |
| Lifetime | $99.99 | Everything forever (early adopter offer) |

### Positioning
- Cheaper than Calm/Headspace ($70/yr)
- More value than Sleep Cycle ($40/yr)
- Accessible alternative to clinical CBT-I

---

## Development Roadmap

### Phase 1: Core MVP (Weeks 1-8)
| Week | Focus |
|------|-------|
| 1-2 | Project setup, auth, sleep diary, storage |
| 3-4 | Insights calculation, dashboard UI, recommendations |
| 5-6 | Content creation, audio recording, notifications |
| 7 | Beta testing with girlfriend + friends |
| 8 | App Store submission |

### Phase 2: Quick Wins (Weeks 9-12)
- Wind-Down Routine Builder
- Caffeine Calculator
- Smart Reminders
- Digital Wind-Down Mode

### Phase 3: Advanced (Post-Launch)
- Sleep Window Calculator (with safety checks)
- Deeper Android integrations
- Apple Watch/Health integrations

---

## Success Metrics

### North Star Metric
**Weekly Active Loggers (WAL):** Users who log sleep at least 4 days/week

### Supporting Metrics
| Metric | Target (Month 1) |
|--------|------------------|
| Day 1 Retention | >40% |
| Day 7 Retention | >25% |
| Day 30 Retention | >15% |
| Logs per user per week | >4 |
| Technique completion rate | >30% |
| Free → Pro conversion | >5% |

---

## Key Decisions Made

1. **Personalization over content volume** - We won't compete with Calm on content quantity
2. **Accessible CBT-I** - Clinical techniques without prescription requirement
3. **Rule-based recommendations first** - ML/AI can come later
4. **React Native + Expo** - Cross-platform, fast iteration
5. **Supabase/Firebase backend** - Low cost, managed infrastructure
6. **Subscription model** - Recurring revenue, investor-friendly

---

## Open Questions (For Future PM)

1. **App name** - Still TBD (working title: "Sleep Coach AI")
2. **Content production** - Self-record or hire voice talent?
3. **Beta strategy** - How many users before public launch?
4. **Launch market** - US first or global?
5. **MVP feature cuts** - If timeline slips, what gets cut first?

---

## Research Documents

All detailed research is available in:
- `MARKET_RESEARCH.md` - B2B SaaS market analysis
- `B2C_market_research.md` - Consumer app market analysis
- `APP_IDEAS_DETAILED.md` - Detailed app concepts
- `SLEEP_APP_MVP.md` - Full MVP specification
- `MVP_EVALUATION.md` - Feature evaluation and ranking

---

## Current Status

**Phase:** Research & Planning Complete
**Next Step:** Wireframing and development
**Blocker:** Need to decide if MVPs are compelling enough or pivot approach
**Note:** User feedback indicates current MVP features "not very compelling" - may need to revisit differentiation strategy

---

*This document should be updated as the project progresses.*
