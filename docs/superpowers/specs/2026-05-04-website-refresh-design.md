# Website Refresh Design Spec
**Date:** 2026-05-04  
**Project:** natbut.github.io — personal/academic portfolio for Nathan Butler, roboticist  
**Aesthetic:** "Engineering Notebook" — light warm-gray base, deep navy + amber accents, monospace used selectively for technical metadata

---

## 1. Goals

- Serve two audiences equally: industry recruiters (robotics/autonomy companies) and the academic community (conference peers, potential collaborators)
- Establish a distinctive visual identity that avoids SWE website clichés while remaining intuitive and accessible
- Make future additions (new projects, publications) as low-friction as possible
- Maintain zero dependencies: plain HTML + CSS, no build step, no JavaScript framework

---

## 2. Directory Structure

### Before → After

```
natbut.github.io/
├── index.html                        (unchanged)
├── projects.html                     ← moved from pages/projects.html
├── publications.html                 ← moved from pages/publications.html
├── css/
│   └── main.css                      (full rewrite with design tokens)
├── docs/
│   ├── NathanButler_Resume.pdf       (unchanged)
│   └── NathanButler_CV.pdf           (unchanged)
├── img/
│   ├── site/                         ← NEW: headshots, logo, profile photos
│   │   ├── round1.png
│   │   ├── headshot1.png
│   │   ├── beach1.JPG
│   │   └── beach2.JPG
│   └── projects/                     ← NEW: one subfolder per project
│       ├── merl/
│       │   ├── merl_fig.png
│       │   ├── multihead_fig.png
│       │   └── merl_avgs.png
│       ├── mr_drl/
│       │   ├── deep_learning_curve1.png
│       │   ├── gridworld_qLearning.png
│       │   ├── gnn_arch.png
│       │   ├── gnn_res.png
│       │   ├── cnn_arch.png
│       │   └── cnn_res.png
│       └── hybrid_dec/
│           ├── mission_schamatic_4.png
│           ├── hybrid_dec_framework.png
│           └── MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4
├── projects/                         ← moved from pages/projects/
│   ├── _template.html                ← renamed from proj_temp.html
│   ├── _tags.md                      ← NEW: canonical tag reference (not served)
│   ├── merl.html
│   ├── mr_drl.html
│   ├── machine_learning.html
│   ├── robot_control.html
│   └── space_mining.html
└── publications/                     ← moved from pages/publications/
    └── hybrid-dec.html
```

### Adding a new project (future workflow)
1. Copy `projects/_template.html` → `projects/<name>.html`, fill in metadata comment block
2. Add images/video to `img/projects/<name>/`
3. Add a card entry to `projects.html`

### CSS path conventions after restructure
- Root pages (`index.html`, `projects.html`, `publications.html`): `css/main.css`
- Project/publication detail pages (`projects/*.html`, `publications/*.html`): `../css/main.css`

---

## 3. Style System (Design Tokens)

All visual identity is defined as CSS custom properties in a `:root` block at the top of `css/main.css`. Every color, font, and spacing value used anywhere on the site references a variable — no hardcoded values in selectors.

```css
:root {
  /* --- Backgrounds --- */
  --bg-page:   #F4F3EF;   /* warm light gray — main page background */
  --bg-card:   #FFFFFF;   /* white — project cards */
  --bg-subtle: #ECEAE4;   /* slightly darker warm — dividers, tag chips */

  /* --- Text --- */
  --text-primary:   #1E1E1E;  /* near-black — body */
  --text-secondary: #5A5A5A;  /* medium gray — captions, metadata */
  --text-heading:   #1B3A5C;  /* deep navy — h1, h2 */

  /* --- Accents --- */
  --accent-navy:  #1B3A5C;   /* deep navy — headings, active nav, card borders */
  --accent-amber: #C97D2E;   /* amber — links, tag chips, hover states */

  /* --- Typography --- */
  --font-body: system-ui, 'Segoe UI', sans-serif;
  --font-mono: 'Courier New', monospace;  /* timestamps, tags, captions ONLY */
  --font-size-base: 18px;
  --font-size-sm:   13px;

  /* --- Spacing & Shape --- */
  --space-section:  3rem;
  --space-card-gap: 1.5rem;
  --radius-card:    6px;
  --radius-tag:     3px;
}
```

**Monospace rule:** `var(--font-mono)` is used *only* for: update timestamps, tag chip labels, and figure captions. All other text uses `var(--font-body)`.

---

## 4. Navigation

**Structure:** Single top nav row. Logo/avatar inline-left, nav links inline-right (or centered). No stacked `<br>` hacks. Nav separated from main content by a `1px solid var(--bg-subtle)` horizontal rule.

**Active state:** Persistent thin amber underline on the current page's nav link.  
**Hover state:** Amber underline appears on hover for non-active links.  
**Mobile:** Nav collapses to text links only (logo hidden). Existing responsive breakpoints retained.

---

## 5. Section Dividers

Between homepage sections (About, Featured Work, Updates, Experience): `var(--space-section)` vertical gap plus a `4rem`-wide, `2px` navy horizontal rule, left-aligned. Evokes an engineering notebook margin marker. Used on the homepage only — detail pages use standard heading hierarchy.

---

## 6. Homepage (`index.html`)

### 6a. About Me
- Two-column layout retained: bio text left (75%), photo right (25%)
- Profile photo: add a `6px solid var(--accent-navy)` left-border accent
- Bio text unchanged
- Links row (Email / LinkedIn / GitHub / Resume / CV): styled as small amber-underlined inline links, slightly larger than body text
- Mobile: photo hidden, single column (existing behavior retained)

### 6b. Featured Work (replaces Experience list)
A 2–3 column responsive grid of clickable tiles. Each tile links directly to a project detail page.

**Tile anatomy:**
- Thumbnail image (fixed height ~160px, `object-fit: cover`)
- Bold project label (e.g., "Multi-Robot Coordination")
- 1-sentence description in `var(--text-secondary)` small text
- 1–3 tag chips along the bottom (monospace, amber-tinted)

**Hover state:** Slight box-shadow lift + `4px solid var(--accent-amber)` left-border flash.

**Mobile:** Collapses to single column.

### 6c. Updates
- Retains `<ul>` list structure
- Timestamps: `var(--font-mono)`, `var(--font-size-sm)`, `var(--text-secondary)` — reads like a log
- Update text: `var(--font-body)`, `var(--text-primary)`

### 6d. Experience
- Moves below Featured Work, stays on homepage
- Compact list: role title in navy, org name as amber link, date range in monospace
- Reduced visual footprint vs current bullet list

---

## 7. Projects Page (`projects.html`)

**Layout:** 2-column card grid on desktop, 1-column on mobile.

**Card anatomy:**
- `var(--bg-card)` background, `1px solid var(--bg-subtle)` border, `var(--radius-card)` corners
- Thumbnail image fills card top (fixed height, `object-fit: cover`)
- Below image: bold title, 1–2 sentence description, tag chips at bottom
- Entire card is an `<a>` link
- Hover: shadow lift + amber left-border

**Sections:** "Ongoing Projects" and "Past Projects" separated by the navy section-marker rule.  
**Ongoing cards without images:** Placeholder style (solid `var(--bg-subtle)` fill) keeps grid intact.

**Tag chips:** `var(--font-mono)`, `var(--font-size-sm)`, `var(--bg-subtle)` background, `var(--text-secondary)` text, `var(--radius-tag)` corners.

---

## 8. Project Detail Pages (`projects/*.html`)

Structure largely unchanged. Updates:

- Back nav: `← Projects` link, left-aligned, `var(--text-secondary)`
- PDF/code/video links: styled as small amber-bordered inline buttons (not plain text)
- Figure captions (optional): `var(--font-mono)`, `var(--font-size-sm)`, `var(--text-secondary)`, centered below image
- Metadata comment block at top of each file (see Section 10)

---

## 9. Publications Page (`publications.html`)

- Retains academic citation format
- Each `<li>` gets a `4px solid var(--accent-navy)` left-border accent
- Venue/conference name: `var(--accent-amber)`
- Links (paper title, PDF, project page): amber-underlined
- Optional: 1-line abstract or summary in `var(--text-secondary)` below citation

**Publication detail pages (`publications/*.html`):** Same updates as project detail pages (back-nav, button links, caption style).

---

## 10. Template & Tag Conventions

### `projects/_template.html` metadata comment block (top of file)
```html
<!--
  title:       [Project Title]
  date:        [YYYY-MM or YYYY]
  status:      [ongoing | past]
  tags:        [tag1, tag2, tag3]  — use canonical tags from _tags.md
  thumbnail:   ../img/projects/[name]/[thumb.png]
  description: [1-2 sentence summary for the projects listing card]
-->
```

### `projects/_tags.md` (canonical tag list — not served, author reference only)
Maintained manually. Examples:
- `multi-robot`
- `reinforcement-learning`
- `motion-planning`
- `field-robotics`
- `hardware`
- `deep-learning`
- `underwater`
- `simulation`

New tags can be added freely; the goal is consistency across pages, not exhaustiveness.

---

## 11. What Does NOT Change

| Element | Reason |
|---|---|
| Responsive CSS breakpoints | Already well-tuned |
| Two-column bio layout | Works and is conventional |
| Academic citation format on publications page | Credibility with academic audience |
| Content of bio, updates, experience | Out of scope |
| `docs/` folder and PDF paths | Stable external references |
| Zero-dependency constraint | Intentional — no JS frameworks, no build step |
