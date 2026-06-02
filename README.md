# LeanIX Expert — EA Maturity Assessment

Interactive lead magnet for [leanixexpert.com](https://leanixexpert.com). Visitors answer 3 questions about their Enterprise Architecture practice, receive a personalized maturity score and LeanIX roadmap, then submit their contact info for a free strategy call.

No build step. Open `index.html` in any browser.

---

## Quick Start

```bash
open index.html
```

Or drag `index.html` into a browser window.

---

## Configuration

All settings are constants at the top of the `<script>` block in `index.html`.

### 1. Set your Formspree endpoint

Create a free account at [formspree.io](https://formspree.io), create a new form, and copy the endpoint URL.

In `index.html`, replace:

```js
const FORM_ACTION = 'YOUR_FORMSPREE_ENDPOINT';
```

With your real endpoint:

```js
const FORM_ACTION = 'https://formspree.io/f/yourcode';
```

Each lead submission will email you: contact details + their EA challenge, landscape size, tooling, maturity level, score, and recommended service.

### 2. Optional — update business name and site URL

```js
const BUSINESS_NAME = 'LeanIX Expert';
const SITE_URL = 'https://leanixexpert.com';
```

---

## Deployment on Vercel

1. Push this repo to GitHub
2. Go to [vercel.com](https://vercel.com) → **Add New Project** → import the repo
3. Framework preset: `Other` · Build command: blank · Output directory: blank
4. Click **Deploy** — live in ~30 seconds

Custom domain: Vercel → Settings → Domains → add `leanixexpert.com`.

---

## Embedding on leanixexpert.com

The file `embed-snippet.html` contains a self-contained widget that adds a
full-width "Take the Assessment" section to your existing website. It opens
the Vercel-hosted assessment in a polished modal overlay — the user never
leaves your site.

### 3 steps

**Step 1** — Place the placeholder where you want the section to appear in
your page body (usually after your hero or services section):

```html
<div id="lx-assessment-hook"></div>
```

**Step 2** — Paste the entire contents of `embed-snippet.html` right before
your closing `</body>` tag.

**Step 3** — Replace the URL constant near the bottom of the pasted script:

```js
var ASSESSMENT_URL = 'YOUR_VERCEL_URL';
// becomes:
var ASSESSMENT_URL = 'https://leanix-expert-lead-gen.vercel.app';
```

That's it. The widget is fully self-contained — scoped CSS, no external JS,
no conflicts with your existing styles. Closes on click-outside or Escape key.

---

## Project Structure

```text
index.html          <- the full assessment app (deploy this to Vercel)
embed-snippet.html  <- drop this into leanixexpert.com to show the widget
PRD.md              <- requirements, scoring logic, question content
CLAUDE.md           <- AI-assisted development rules
SECURITY.md         <- security guidelines
README.md           <- this file
```

---

## Testing Checklist

Open `index.html` in a browser and verify:

1. Intro screen loads with "Start My Assessment →" button
2. Q1: all 6 challenge cards are selectable; auto-advances to Q2
3. Q2: all 4 size cards work; back button returns to Q1
4. Q3: all 4 tooling cards work; back button returns to Q2
5. Results: correct maturity level for the selected tooling + size combination
6. Results: insight box text matches the Q1 challenge selected
7. Form: required field validation shows errors on empty submit
8. Form: successful submit shows the thank-you screen
9. Mobile: layout is clean at 375px viewport width
