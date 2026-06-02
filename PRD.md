# PRD — LeanIX Expert EA Maturity Assessment

Status: In Progress
Last Updated: 2026-06-01

---

## Project Overview

### LeanIX Expert — EA Maturity Assessment Lead Magnet

A single-page interactive assessment that asks Enterprise Architecture decision-makers 3 targeted questions about their IT landscape, scores their EA maturity level, and presents a personalized LeanIX roadmap recommendation. Visitors submit their contact info to receive a free 30-minute strategy call with the LeanIX Expert consultant.

Who it's for: CIOs, Enterprise Architects, IT Directors, and Technology Managers at mid-to-large organizations that either use LeanIX, are evaluating it, or are managing their EA practice in a suboptimal way (spreadsheets, Visio, fragmented tools).

Problem it solves: EA professionals know they have a problem but struggle to articulate it or see a path forward. This tool validates their pain, gives them a concrete maturity score, and positions the LeanIX Expert as the credible guide to fix it — converting curious visitors into qualified leads.

---

## The 3 Questions

### Question 1 — What's your biggest challenge with your IT landscape?

Multiple choice, pick one. 6 clickable cards with icons.

| Option | Icon | ID |
|---|---|---|
| Application Portfolio Bloat | 🗂️ | portfolio |
| No Visibility or Transparency | 🔍 | visibility |
| Cloud or SAP Migration | 🚀 | migration |
| Tech Debt & Risk | ⚠️ | tech_debt |
| Governance & Compliance | 🏛️ | governance |
| Poor EA Reporting | 📊 | reporting |

### Question 2 — How many business applications does your organization manage?

4 clickable cards. Drives complexity score.

| Option | Icon | ID |
|---|---|---|
| Under 100 apps | 💼 | small |
| 100–500 apps | 🏢 | mid |
| 500–2,000 apps | 🏭 | large |
| 2,000+ apps | 🌐 | enterprise |

### Question 3 — How does your team currently manage Enterprise Architecture?

4 clickable cards. Primary driver of maturity level.

| Option | Icon | ID |
|---|---|---|
| Spreadsheets & Email | 📋 | spreadsheets |
| Visio / Draw.io | 🎨 | visio |
| CMDB / ServiceNow | 🔧 | cmdb |
| LeanIX (underutilized) | ⚡ | leanix |

---

## Maturity Scoring Logic

Maturity level is derived from Q3 (tooling) and Q2 (landscape size):

```text
Tooling: spreadsheets, size: small or mid  → Foundation
Tooling: spreadsheets, size: large or ent  → Developing
Tooling: visio,        size: small or mid  → Foundation
Tooling: visio,        size: large or ent  → Developing
Tooling: cmdb,         size: small         → Developing
Tooling: cmdb,         size: mid+          → Scaling
Tooling: leanix,       size: small or mid  → Established
Tooling: leanix,       size: large or ent  → Scaling
```

### Maturity Levels

| Level | Score | Color | Recommended Service |
|---|---|---|---|
| Foundation | 3/10 | Amber | LeanIX Quick-Start Implementation |
| Developing | 5/10 | Blue | LeanIX Migration & Modernization Program |
| Established | 7/10 | Purple | LeanIX Optimization & Reporting Package |
| Scaling | 9/10 | Green | Enterprise EA Transformation Program |

### Challenge Insight (Q1 modifier)

Each challenge selection adds a one-line personalized insight below the maturity description — connecting the visitor's specific pain to a LeanIX capability.

---

## Results Screen Layout

1. Circular score badge (colored by level, e.g. "7 / 10")
2. Maturity level badge (e.g. "Established Level")
3. Headline — short punchy statement about their situation
4. Description — 2–3 sentences about what this level means
5. Green insight box — tailored sentence based on Q1 challenge
6. Recommended service box — service name + 1-sentence description
7. Divider
8. Lead capture form

---

## Lead Capture Form

Headline: "Get your personalized EA roadmap"
Subheadline: "Free 30-minute strategy call · No pressure · Reply within 1 business day"

Fields:

- First name (required)
- Last name (required)
- Work email (required, validated)
- Company (required)
- Job title (optional)

CTA button: "Book My Free Strategy Call →"

On submit: POST to Formspree with all form fields + assessment results (challenge, size, tooling, maturity level, score, recommended service). Show thank-you screen on success.

---

## Screens / Flow

```text
Intro → Q1 → Q2 → Q3 → Results + Form → Thank You
                ↑back ↑back
```

Auto-advance to next step 300ms after selection (no explicit "Next" button).
Back button on Q2 returns to Q1; back button on Q3 returns to Q2.

---

## Core Features

1. 4-screen wizard with smooth fade-in transitions
2. Progress indicator (3 step bars at top of each question screen)
3. Clickable answer cards — icon, label, description. Auto-advance on selection
4. Results screen with dynamic content driven by scoring matrix
5. Lead form with inline validation and loading state on submit
6. Sends assessment context (not just contact info) to Formspree
7. Mobile-first responsive layout

---

## Out of Scope (v1)

- Backend / database / user accounts
- Email automation sequences
- A/B testing
- Multiple languages
- Booking calendar integration (just capture contact info)
- PDF report generation

---

## Success Metrics

- [ ] All 4 × 4 × 6 = 96 question combinations produce a valid result
- [ ] Lead form submits and consultant receives an email with assessment data
- [ ] Page loads under 2 seconds on mobile (no external JS)
- [ ] Responsive at 375px, 768px, and 1280px
- [ ] No console errors on any path through the app

---

## Tech Stack

- **Frontend**: Vanilla HTML5, CSS3, JavaScript (ES6+)
- **Fonts**: Inter via Google Fonts CDN (CSS only, no JS)
- **Form submission**: Formspree (free tier — 50 submissions/month)
- **Hosting**: Netlify drag-and-drop or GitHub Pages
- **No build tool** — open index.html directly in a browser

---

## Key File Locations

```text
index.html    <- entire app (HTML + embedded CSS + JS)
PRD.md        <- this file
CLAUDE.md     <- AI development rules
SECURITY.md   <- security guidelines
README.md     <- how to configure and deploy
```

---

## Configurable Constants (top of script block in index.html)

| Constant | Purpose |
|---|---|
| BUSINESS_NAME | Displayed in header and footer |
| SITE_URL | Used in footer link back to main site |
| FORM_ACTION | Formspree endpoint URL |
| Q1, Q2, Q3 | Question option arrays |
| RESULTS | Maturity level definitions (score, color, copy, service) |
| CHALLENGE_INSIGHTS | Per-challenge insight text shown on results screen |

---

## Done When (Launch Checklist)

- [ ] Intro screen renders correctly
- [ ] All 3 question screens work with back navigation
- [ ] Results screen shows correct maturity level for every tooling+size combination
- [ ] Challenge insight line matches Q1 selection
- [ ] Lead form validates all required fields
- [ ] Form submits to Formspree with assessment metadata included
- [ ] Thank-you screen appears on successful submission
- [ ] Mobile layout verified at 375px
- [ ] No placeholder text left visible in UI
- [ ] FORM_ACTION updated from placeholder to real endpoint
