# CLAUDE.md — LeanIX Expert Lead Generator

## About This Project

- **Name**: LeanIX Expert — EA Maturity Assessment (Lead Magnet)
- **Type**: Static Web Page (single `index.html`)
- **Primary Tech**: Vanilla HTML + CSS + JavaScript (ES6+, no framework, no build step)
- **Key Purpose**: A 3-question interactive EA Maturity Assessment that scores visitors on their Enterprise Architecture practice and captures contact info as a warm lead for LeanIX consulting engagements.
- **Live Site**: leanixexpert.com

---

## Security

- No backend, no database, no secrets in source.
- If a form submission service (Formspree) is used, the endpoint URL is a constant at the top of the `<script>` block — not hardcoded deep in logic, and never committed with a real key until the user is ready.
- Sanitize any user-provided strings before rendering them into the DOM (XSS).

---

## Before Any Feature Work — Read These First

- **`PRD.md`** — the 3 questions, scoring matrix, maturity levels, lead form spec, and launch checklist.
- **`README.md`** — how to open, configure Formspree, and deploy.

---

## Project Rules

- **Code style**: Vanilla JS only — no jQuery, React, or build tool.
- **Single file**: All HTML, CSS, and JS lives in `index.html`.
- **No comments** explaining what code does — only comments for non-obvious WHY.
- **Naming**: camelCase JS, kebab-case CSS classes, UPPER_SNAKE JS constants at the top of `<script>`.
- **Testing**: Open `index.html` in a browser; manually step through every question combination before marking anything done.
- **Critical constants** (ask before changing): `FORM_ACTION`, `RESULTS` scoring matrix, `BUSINESS_NAME`.

---

## Workflow

- Solo project — no PRs, no CI.
- Verify every change by opening `index.html` in a browser.
- Golden-path test: complete all 3 questions → see the results screen → submit the lead form → see the confirmation.
- Edge-case test: try every answer combination; back button from each step.
