# Long Beach Institute — Site Briefing for Claude Code

## Overview
Single-file static website for the Long Beach Institute, a computational sociology research institute founded in 2016 in Long Beach, NY. The site is deployed on GitHub Pages.

**Repository:** https://github.com/jackcs99/longbeachinstitute.github.io  
**Live URL:** https://jackcs99.github.io/longbeachinstitute.github.io/  
**Contact:** jcs@alumni.caltech.edu  
**Files:** `index.html` (entire site), `socialOptPres.pdf` (linked presentation)

---

## Tech Stack
- Single `index.html` — all CSS and JS are embedded inline, no external files except Google Fonts
- Logo is embedded as a base64 PNG data URI (no separate image file)
- No build system, no npm, no frameworks — plain HTML/CSS/JS only
- Deployed via GitHub Pages from the `main` branch, root folder

## Deploying Changes
```bash
git add .
git commit -m "describe your change"
git push
```
GitHub Pages rebuilds automatically within ~1 minute.

---

## Design System

**Color palette:**
- `--warm-bg: #f5f2eb` — main background (warm paper)
- `--warm-mid: #ede9e0` — alternate section background
- `--ink: #2a2520` — primary text
- `--accent: #4a7ab5` — steel blue (matches logo)
- `--muted: #8a8278` — secondary text

**Typography:**
- Serif: `'Playfair Display'` (headings, quotes)
- Sans: `'IBM Plex Sans'` (body)
- Mono: `'IBM Plex Mono'` (labels, tags, attributions)

**Animations:**
- Cards use `.fade-up` class (opacity 0, translateY 24px)
- Made visible by IntersectionObserver JS at bottom of file adding `.visible` class
- If cards appear blank, check the IntersectionObserver script is present and not duplicated

---

## Page Structure (in order)

1. **`<nav>`** — Static nav with base64 logo (280px), tagline quote, and anchor links
2. **`<section class="hero">`** — Title, mission statement, "View our research" CTA button
3. **Dark pullquote band** — Two JFK quotes, single Rice 1963 citation
4. **`<section id="publications">`** — 01 / Selected Publications
5. **`<section id="presentations">`** — 02 / Presentations (links to socialOptPres.pdf)
6. **`<section id="quotes">`** — 03 / Perspectives (quote cards)
7. **`<section id="about">`** — 04 / Our Mission (research pillars)
8. **`<footer>`** — contact email

**Nav anchor links** use `onclick` JS smooth scroll (not plain href) so they work in all environments:
```html
onclick="event.preventDefault(); document.getElementById('sectionid').scrollIntoView({behavior:'smooth'});"
```

---

## Content

**Tagline:** "Society, simply simulated. Explained."

**Mission statement:**
"We apply the new science of computation — agent based models, genetic programming, and minimal models of systems using the mathematical principles of biology, genetics and ecology — to provide explanations for the complex adaptive behaviors of society."

**Nav quote (no attribution):**
"Optimizing social systems by and for 'We the people'"

**Dark banner quotes:**
"We set sail on this new sea because there is new knowledge to be gained, and new rights to be won, and they must be won and used for the progress of all people. We do these things not because they are easy but because they are hard."
— John F. Kennedy, Rice University, 1963

**Perspectives quotes:**
1. William Lloyd, *Two Lectures on the Checks to Population*, 1833
2. E. O. Wilson, *Sociobiology*, 2000
3. Albert Einstein, *Out of My Later Years*, 2011

**Research pillars (in About section):**
1. Wealth Inequality
2. Legislative Governance
3. Computational Methods
4. Policy & Society

---

## Publications (12 total, newest first)

| Year | Title | Link |
|------|-------|------|
| 2025 | Death Taxes and Inequality | https://doi.org/10.1007/978-3-031-91782-0_35 |
| 2025 | Low Total Fertility in Simple Economic Systems | https://arxiv.org/abs/2406.13816 |
| 2024 | Local Sharing and Sociality Effects on Wealth Inequality | https://arxiv.org/abs/2305.17177 |
| 2023 | The Struggle for Existence: Time, Memory and Bloat | https://arxiv.org/abs/2302.03096 |
| 2023 | Competitive Exclusion in an Artificial Foraging Ecosystem | https://arxiv.org/abs/2203.02814 |
| 2023 | Towards Eusociality Using an Inverse Agent Based Model | https://arxiv.org/abs/2206.00116 |
| 2022 | Dynamics of Wealth Inequality in Simple Artificial Societies | https://arxiv.org/abs/2108.11892 |
| 2022 | Agentization of Two Population-Driven Models of Mathematical Biology | https://arxiv.org/abs/2101.09817 |
| 2021 | Population and Inequality Dynamics in Simple Economies | https://arxiv.org/abs/2101.09817 |
| 2016 | The Value of Millisecond Expiry Options in Spot Foreign Exchange Markets | — |
| 2008 | Options Embedded in Physical Money | https://ssrn.com/abstract=1313665 |
| 1990 | Autonomous Landing on Mars | — |

Tags used: `Inequality`, `Agent-Based Modelling`, `Evolutionary Computation`, `Artificial Life`, `Finance`, `Aerospace`

---

## Presentations

| Year | Title | File |
|------|-------|------|
| 2024 | Economics and Complexity Seminar, CEIICH-CEPHCIS-UNAM | socialOptPres.pdf |

---

## Common Tasks

**Add a new publication:**
Find the `<div class="pub-grid">` inside `#publications` and add a new `.pub-card` at the top following the existing pattern. Wrap in `<a>` tag if there is a URL.

**Update the logo:**
The logo is a base64-encoded PNG in the `<img>` tag inside `<nav>`. Convert the new PNG to base64 and replace the data URI value.

**Add a new presentation:**
Find the `<div class="pub-grid">` inside `#presentations` and add a card. Upload the PDF to the repo root alongside `index.html`.

**Change quote text:**
Search for the quote text directly — all content is inline in the HTML.
