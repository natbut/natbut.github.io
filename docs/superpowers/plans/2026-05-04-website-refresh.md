# Website Refresh Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Refresh natbut.github.io with the "Engineering Notebook" aesthetic: design tokens in CSS, a reorganized directory structure, project card grid, and a Featured Work section on the homepage.

**Architecture:** Plain HTML + CSS, zero dependencies, no build step. All visual identity lives in CSS custom properties at the top of `css/main.css`. Directory restructure moves `pages/` content to the root level and organizes `img/` into `site/` and per-project subfolders.

**Tech Stack:** HTML5, CSS3 (custom properties), GitHub Pages static hosting. Local preview: `python -m http.server 8080` from repo root.

---

## File Map

**Moved (git mv):**
- `pages/projects.html` → `projects.html`
- `pages/publications.html` → `publications.html`
- `pages/projects/merl.html` → `projects/merl.html`
- `pages/projects/mr_drl.html` → `projects/mr_drl.html`
- `pages/projects/machine_learning.html` → `projects/machine_learning.html`
- `pages/projects/robot_control.html` → `projects/robot_control.html`
- `pages/projects/space_mining.html` → `projects/space_mining.html`
- `pages/projects/proj_temp.html` → `projects/_template.html`
- `pages/publications/hybrid-dec.html` → `publications/hybrid-dec.html`
- `img/round1.png` → `img/site/round1.png`
- `img/headshot1.png` → `img/site/headshot1.png`
- `img/beach1.JPG` → `img/site/beach1.JPG`
- `img/beach2.JPG` → `img/site/beach2.JPG`
- `img/merl_fig.png` → `img/projects/merl/merl_fig.png`
- `img/multihead_fig.png` → `img/projects/merl/multihead_fig.png`
- `img/merl_avgs.png` → `img/projects/merl/merl_avgs.png`
- `img/cnn_arch.png` → `img/projects/mr_drl/cnn_arch.png`
- `img/gnn_arch.png` → `img/projects/mr_drl/gnn_arch.png`
- `img/cnn_res.png` → `img/projects/mr_drl/cnn_res.png`
- `img/gnn_res.png` → `img/projects/mr_drl/gnn_res.png`
- `img/deep_learning_curve1.png` → `img/projects/machine_learning/deep_learning_curve1.png`
- `img/gridworld_qLearning.png` → `img/projects/machine_learning/gridworld_qLearning.png`
- `img/mission_schamatic_4.png` → `img/projects/hybrid_dec/mission_schamatic_4.png`
- `img/hybrid_dec_framework.png` → `img/projects/hybrid_dec/hybrid_dec_framework.png`
- `img/MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4` → `img/projects/hybrid_dec/MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4`

**Modified:**
- `css/main.css` — full rewrite with design tokens
- `index.html` — nav cleanup, About photo path, Featured Work section, Updates + Experience restyling
- `projects.html` — card grid layout, updated paths
- `publications.html` — left-border accents, amber venue, updated paths
- `projects/merl.html` — back-nav, image paths, button links
- `projects/mr_drl.html` — back-nav, image paths, button links
- `projects/machine_learning.html` — back-nav, image paths
- `projects/robot_control.html` — back-nav, paths
- `projects/space_mining.html` — back-nav, paths
- `publications/hybrid-dec.html` — back-nav, image paths, button links

**Created:**
- `projects/_tags.md` — canonical tag list
- `projects/_template.html` — updated template with metadata comment block

---

## Task 1: Directory Restructure

**Files:** All files listed in File Map above.

- [ ] **Step 1: Create new image subdirectories**

```powershell
mkdir img\site
mkdir img\projects\merl
mkdir img\projects\mr_drl
mkdir img\projects\machine_learning
mkdir img\projects\hybrid_dec
```

- [ ] **Step 2: Move site images**

```powershell
git mv img\round1.png img\site\round1.png
git mv img\headshot1.png img\site\headshot1.png
git mv img\beach1.JPG img\site\beach1.JPG
git mv img\beach2.JPG img\site\beach2.JPG
```

- [ ] **Step 3: Move project images — merl**

```powershell
git mv img\merl_fig.png img\projects\merl\merl_fig.png
git mv img\multihead_fig.png img\projects\merl\multihead_fig.png
git mv img\merl_avgs.png img\projects\merl\merl_avgs.png
```

- [ ] **Step 4: Move project images — mr_drl**

```powershell
git mv img\cnn_arch.png img\projects\mr_drl\cnn_arch.png
git mv img\gnn_arch.png img\projects\mr_drl\gnn_arch.png
git mv img\cnn_res.png img\projects\mr_drl\cnn_res.png
git mv img\gnn_res.png img\projects\mr_drl\gnn_res.png
```

- [ ] **Step 5: Move project images — machine_learning**

```powershell
git mv img\deep_learning_curve1.png img\projects\machine_learning\deep_learning_curve1.png
git mv img\gridworld_qLearning.png img\projects\machine_learning\gridworld_qLearning.png
```

- [ ] **Step 6: Move project images — hybrid_dec**

```powershell
git mv "img\mission_schamatic_4.png" img\projects\hybrid_dec\mission_schamatic_4.png
git mv img\hybrid_dec_framework.png img\projects\hybrid_dec\hybrid_dec_framework.png
git mv "img\MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4" "img\projects\hybrid_dec\MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4"
```

- [ ] **Step 7: Move page-level HTML files to root**

```powershell
git mv pages\projects.html projects.html
git mv pages\publications.html publications.html
```

- [ ] **Step 8: Move project detail pages**

```powershell
git mv pages\projects\merl.html projects\merl.html
git mv pages\projects\mr_drl.html projects\mr_drl.html
git mv pages\projects\machine_learning.html projects\machine_learning.html
git mv pages\projects\robot_control.html projects\robot_control.html
git mv pages\projects\space_mining.html projects\space_mining.html
git mv pages\projects\proj_temp.html projects\_template.html
```

- [ ] **Step 9: Move publication detail pages**

```powershell
git mv pages\publications\hybrid-dec.html publications\hybrid-dec.html
```

- [ ] **Step 10: Delete now-empty pages/ directory**

```powershell
git rm -r pages
```

If `git rm -r pages` fails because the directory is already empty, just run:
```powershell
Remove-Item -Recurse pages
```

- [ ] **Step 11: Update paths in index.html**

Open `index.html`. Update every path:
- `css/main.css` → unchanged (already at root)
- `img/round1.png` → `img/site/round1.png` (2 occurrences: favicon + nav img)
- `img/beach2.JPG` → `img/site/beach2.JPG`
- `pages/projects.html` → `projects.html`
- `pages/publications.html` → `publications.html`

- [ ] **Step 12: Update paths in projects.html**

Open `projects.html`. Update:
- `../css/main.css` → `css/main.css`
- `../index.html` → `index.html`
- `../img/round1.png` → `img/site/round1.png`
- `projects/machine_learning.html` → unchanged (relative path still correct)
- `projects/merl.html` → unchanged
- `projects/mr_drl.html` → unchanged
- `publications.html` → unchanged

- [ ] **Step 13: Update paths in publications.html**

Open `publications.html`. Update:
- `../css/main.css` → `css/main.css`
- `../index.html` → `index.html`
- `../img/round1.png` → `img/site/round1.png`
- `projects.html` → unchanged
- `publications/hybrid-dec.html` → unchanged

- [ ] **Step 14: Update paths in projects/merl.html**

Open `projects/merl.html`. Update:
- `../../css/main.css` → `../css/main.css`
- `../../index.html` → `../index.html`
- `../projects.html` → `../projects.html` (unchanged — still one level up)
- `../../img/merl_fig.png` → `../img/projects/merl/merl_fig.png`
- `../../img/multihead_fig.png` → `../img/projects/merl/multihead_fig.png`
- `../../img/merl_avgs.png` → `../img/projects/merl/merl_avgs.png`

- [ ] **Step 15: Update paths in projects/mr_drl.html**

Open `projects/mr_drl.html`. Update:
- `../../css/main.css` → `../css/main.css`
- `../../index.html` → `../index.html`
- `../projects.html` → `../projects.html`
- `../../docs/Multi_Robot_Control_with_Deep_Reinforcement_Learning.pdf` → `../docs/Multi_Robot_Control_with_Deep_Reinforcement_Learning.pdf`
- `../../img/cnn_arch.png` → `../img/projects/mr_drl/cnn_arch.png`
- `../../img/gnn_arch.png` → `../img/projects/mr_drl/gnn_arch.png`
- `../../img/cnn_res.png` → `../img/projects/mr_drl/cnn_res.png`
- `../../img/gnn_res.png` → `../img/projects/mr_drl/gnn_res.png`

- [ ] **Step 16: Update paths in projects/machine_learning.html**

Open `projects/machine_learning.html`. Update:
- `../../css/main.css` → `../css/main.css`
- `../../index.html` → `../index.html`
- `../projects.html` → `../projects.html`
- `../../img/deep_learning_curve1.png` → `../img/projects/machine_learning/deep_learning_curve1.png`
- `../../img/gridworld_qLearning.png` → `../img/projects/machine_learning/gridworld_qLearning.png`

- [ ] **Step 17: Update paths in projects/robot_control.html and projects/space_mining.html**

For each file, update:
- `../../css/main.css` → `../css/main.css`
- `../../index.html` → `../index.html`
- `../projects.html` → `../projects.html`
- Any `../../img/` references → `../img/` equivalents (check each file for image src attributes)

- [ ] **Step 18: Update paths in publications/hybrid-dec.html**

Open `publications/hybrid-dec.html`. Update:
- `../../css/main.css` → `../css/main.css`
- `../../index.html` → `../index.html`
- `../publications.html` → `../publications.html` (unchanged — still correct)
- `../../docs/Butler_Hybrid_Decentralization_ICRA2025.pdf` → `../docs/Butler_Hybrid_Decentralization_ICRA2025.pdf`
- `../../img/mission_schamatic_4.png` → `../img/projects/hybrid_dec/mission_schamatic_4.png`
- `../../img/hybrid_dec_framework.png` → `../img/projects/hybrid_dec/hybrid_dec_framework.png`
- `../../img/MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4` → `../img/projects/hybrid_dec/MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4`

- [ ] **Step 19: Verify no broken paths**

Start a local server and check each page for broken images or links:

```powershell
python -m http.server 8080
```

Open in browser:
- `http://localhost:8080/` — logo, profile photo must load
- `http://localhost:8080/projects.html` — nav logo must load
- `http://localhost:8080/projects/merl.html` — all 3 figures must load
- `http://localhost:8080/projects/mr_drl.html` — all 4 figures must load
- `http://localhost:8080/projects/machine_learning.html` — 2 figures must load
- `http://localhost:8080/publications/hybrid-dec.html` — 3 figures must load

Stop the server (`Ctrl+C`) when done.

- [ ] **Step 20: Commit**

```powershell
git add -A
git commit -m "refactor: reorganize directory structure, flatten pages/ and sort img/ by project"
```

---

## Task 2: Rewrite css/main.css with Design Tokens

**Files:**
- Modify: `css/main.css`

- [ ] **Step 1: Replace the entire contents of css/main.css with the following**

```css
/* =============================================================
   DESIGN TOKENS
   All colors, fonts, and spacing are defined here as CSS
   custom properties. To restyle the site, edit only this block.
   ============================================================= */
:root {
  /* Backgrounds */
  --bg-page:   #F4F3EF;   /* warm light gray — main page background */
  --bg-card:   #FFFFFF;   /* white — project cards */
  --bg-subtle: #ECEAE4;   /* slightly darker warm gray — dividers, tag chips */

  /* Text */
  --text-primary:   #1E1E1E;  /* near-black — body text */
  --text-secondary: #5A5A5A;  /* medium gray — captions, metadata */
  --text-heading:   #1B3A5C;  /* deep navy — h1, h2 */

  /* Accents */
  --accent-navy:  #1B3A5C;   /* deep navy — headings, active nav, card left-borders */
  --accent-amber: #C97D2E;   /* amber — links, tags, hover states */

  /* Typography */
  --font-body: system-ui, 'Segoe UI', sans-serif;
  --font-mono: 'Courier New', monospace; /* timestamps, tag chips, captions ONLY */
  --font-size-base: 18px;
  --font-size-sm:   13px;

  /* Spacing & Shape */
  --space-section:  3rem;
  --space-card-gap: 1.5rem;
  --radius-card:    6px;
  --radius-tag:     3px;
}

/* =============================================================
   BASE
   ============================================================= */
*, *::before, *::after { box-sizing: border-box; }

body {
  max-width: 860px;
  margin: 0 auto;
  padding: 0 2rem;
  font-family: var(--font-body);
  font-size: var(--font-size-base);
  background: var(--bg-page);
  color: var(--text-primary);
  line-height: 1.7;
}

@media (max-width: 1200px) { body { padding: 0 1.5rem; } }
@media (max-width: 768px)  { body { padding: 0 1rem; } }
@media (max-width: 480px)  { body { font-size: 15px; } }

h1 {
  font-size: 36px;
  font-weight: 500;
  color: var(--text-heading);
  margin: 0;
  padding: 0;
}

h2 {
  font-size: 20px;
  font-weight: normal;
  font-style: italic;
  color: var(--text-heading);
  margin: 0;
  padding-top: 1.5rem;
}

a {
  color: var(--text-primary);
  text-decoration: underline dotted var(--accent-amber) 2px;
  text-underline-offset: 3px;
}

a:hover {
  color: var(--accent-amber);
  text-decoration: none;
}

/* =============================================================
   NAVIGATION
   ============================================================= */
nav {
  display: flex;
  align-items: center;
  padding: 1.25rem 0 1rem;
  border-bottom: 1px solid var(--bg-subtle);
  margin-bottom: 2rem;
}

.nav-logo {
  margin-right: auto;
}

.nav-logo img {
  width: 44px;
  height: 44px;
  display: block;
  border-radius: 50%;
}

nav ul {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  gap: 2rem;
}

nav ul li a {
  text-decoration: none;
  color: var(--text-secondary);
}

nav ul li a:hover {
  color: var(--text-primary);
  border-bottom: 2px solid var(--accent-amber);
  padding-bottom: 2px;
}

nav ul li a.active {
  color: var(--text-primary);
  border-bottom: 2px solid var(--accent-amber);
  padding-bottom: 2px;
}

/* Back-nav on detail pages */
.back-nav {
  margin-bottom: 1.5rem;
  font-size: var(--font-size-sm);
}

.back-nav a {
  text-decoration: none;
  color: var(--text-secondary);
}

.back-nav a:hover { color: var(--accent-amber); }

/* =============================================================
   SECTION DIVIDERS (homepage only)
   ============================================================= */
.section-divider {
  border: none;
  border-top: 2px solid var(--accent-navy);
  width: 4rem;
  margin: var(--space-section) 0 2rem 0;
}

/* =============================================================
   ABOUT SECTION
   ============================================================= */
.about-grid {
  display: grid;
  grid-template-columns: 3fr 1fr;
  gap: 2rem;
  align-items: center;
  margin-top: 1.5rem;
}

.about-photo img {
  width: 100%;
  display: block;
  border-left: 6px solid var(--accent-navy);
}

.about-links {
  margin-top: 1rem;
  font-size: 0.95em;
}

.about-links a { margin-right: 0.75rem; }

@media (max-width: 768px) {
  .about-grid { grid-template-columns: 1fr; }
  .about-photo { display: none; }
}

/* =============================================================
   FEATURED WORK (homepage)
   ============================================================= */
.featured-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: var(--space-card-gap);
  margin-top: 1.5rem;
}

@media (max-width: 768px) { .featured-grid { grid-template-columns: 1fr; } }

.featured-card {
  display: block;
  text-decoration: none;
  color: var(--text-primary);
  background: var(--bg-card);
  border: 1px solid var(--bg-subtle);
  border-radius: var(--radius-card);
  overflow: hidden;
  transition: box-shadow 0.15s ease, border-left-width 0.1s ease;
}

.featured-card:hover {
  box-shadow: 0 4px 14px rgba(0,0,0,0.09);
  border-left: 4px solid var(--accent-amber);
  color: var(--text-primary);
}

.featured-card .card-thumb {
  width: 100%;
  height: 140px;
  object-fit: cover;
  display: block;
  background: var(--bg-subtle);
}

.featured-card .card-body { padding: 0.75rem 1rem 1rem; }

.featured-card .card-title {
  font-weight: bold;
  margin-bottom: 0.35rem;
}

.featured-card .card-desc {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  line-height: 1.5;
  margin-bottom: 0.75rem;
}

.featured-card .card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}

/* =============================================================
   TAG CHIPS (shared)
   ============================================================= */
.tag {
  font-family: var(--font-mono);
  font-size: var(--font-size-sm);
  background: var(--bg-subtle);
  color: var(--text-secondary);
  border-radius: var(--radius-tag);
  padding: 2px 6px;
}

/* =============================================================
   UPDATES LIST
   ============================================================= */
.updates-ul {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}

.updates-ul li { padding-bottom: 1.25rem; }

.update-date {
  font-family: var(--font-mono);
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  margin-right: 0.5rem;
}

/* =============================================================
   EXPERIENCE LIST
   ============================================================= */
.experience-ul {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}

.experience-ul li { padding-bottom: 1rem; }

.exp-date {
  font-family: var(--font-mono);
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  display: block;
  margin-bottom: 0.2rem;
}

.exp-role { color: var(--text-heading); font-weight: bold; }

/* =============================================================
   PROJECTS PAGE — CARD GRID
   ============================================================= */
.projects-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: var(--space-card-gap);
  margin-top: 1.5rem;
}

@media (max-width: 768px) { .projects-grid { grid-template-columns: 1fr; } }

.project-card {
  display: block;
  text-decoration: none;
  color: var(--text-primary);
  background: var(--bg-card);
  border: 1px solid var(--bg-subtle);
  border-radius: var(--radius-card);
  overflow: hidden;
  transition: box-shadow 0.15s ease, border-left-width 0.1s ease;
}

.project-card:hover {
  box-shadow: 0 4px 14px rgba(0,0,0,0.09);
  border-left: 4px solid var(--accent-amber);
  color: var(--text-primary);
}

.project-card .card-thumb {
  width: 100%;
  height: 180px;
  object-fit: cover;
  display: block;
}

.project-card .card-thumb-placeholder {
  width: 100%;
  height: 180px;
  background: var(--bg-subtle);
  display: block;
}

.project-card .card-body { padding: 1rem; }

.project-card .card-title {
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.project-card .card-desc {
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  line-height: 1.5;
  margin-bottom: 0.75rem;
}

.project-card .card-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.4rem;
}

/* =============================================================
   PUBLICATIONS PAGE
   ============================================================= */
.pubs-ul {
  list-style: none;
  padding: 0;
  margin-top: 1rem;
}

.pubs-ul li {
  border-left: 4px solid var(--accent-navy);
  padding: 0.75rem 0 0.75rem 1rem;
  margin-bottom: 1.5rem;
}

.pub-venue { color: var(--accent-amber); }

/* =============================================================
   DETAIL PAGES (project & publication)
   ============================================================= */
.paper-title {
  font-size: 32px;
  font-weight: 500;
  color: var(--text-heading);
  text-align: center;
  margin-bottom: 1.5rem;
  line-height: 1.3;
}

.paper-p {
  margin: 0;
  padding: 0;
  text-align: justify;
}

.btn-link {
  display: inline-block;
  padding: 4px 14px;
  border: 1px solid var(--accent-amber);
  border-radius: var(--radius-tag);
  color: var(--accent-amber);
  text-decoration: none;
  font-size: var(--font-size-sm);
  margin-right: 0.5rem;
}

.btn-link:hover {
  background: var(--accent-amber);
  color: #fff;
}

.fig-caption {
  font-family: var(--font-mono);
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
  text-align: center;
  margin-top: 0.4rem;
}

.center {
  display: block;
  margin: 1.5rem auto;
  max-width: 100%;
}

/* Monospace metadata */
#last-modified, #publish-date {
  font-family: var(--font-mono);
  font-size: var(--font-size-sm);
  color: var(--text-secondary);
}
```

- [ ] **Step 2: Verify CSS loads without errors**

Start server and open `http://localhost:8080/`. The page should now have the warm gray background (`#F4F3EF`) and navy headings. If the background is still white, hard-refresh (`Ctrl+Shift+R`).

- [ ] **Step 3: Commit**

```powershell
git add css\main.css
git commit -m "style: rewrite main.css with design tokens (Engineering Notebook aesthetic)"
```

---

## Task 3: Update index.html — Nav and About Section

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Replace the `<head>` and `<header>` blocks**

Replace the existing `<head>` with:

```html
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Nathan Butler</title>
    <link rel="stylesheet" href="css/main.css">
    <link rel="icon" type="image/x-icon" href="img/site/round1.png">
</head>
```

Replace the existing `<header>` block with:

```html
<header>
    <nav>
        <a class="nav-logo" href="index.html">
            <img src="img/site/round1.png" alt="Nathan Butler">
        </a>
        <ul>
            <li><a href="index.html" class="active">Home</a></li>
            <li><a href="projects.html">Projects</a></li>
            <li><a href="publications.html">Publications</a></li>
        </ul>
    </nav>
</header>
```

- [ ] **Step 2: Replace the About Me section**

Replace the existing `<h1>About Me</h1>` and the `<table>` below it with:

```html
<h1>About Me</h1>
<div class="about-grid">
    <div class="about-text">
        Hi! I'm Nathan Butler.

        I am a motivated roboticist with a background in AI and mechanical design. I believe we are
        closer than ever to achieving generalizable robotic autonomy across a wide range of real-world
        environments. With experience in autonomous planning, learning-based control, and rapid
        prototyping of field-deployable systems, I am building a career at the intersection of
        intelligent decision making and robust hardware integration.
        <br><br>
        I have recently completed my MS in Robotics in the <a
            href="https://research.engr.oregonstate.edu/rdml/home" target="_blank">Robotic Decision
            Making Lab</a>, part of the <a href="https://engineering.oregonstate.edu/CoRIS"
            target="_blank">Collaborative Robotics and Intelligent Systems (CoRIS) Institute</a> at
        Oregon State University, where I was advised by <a
            href="https://engineering.oregonstate.edu/people/geoff-hollinger">Dr. Geoff Hollinger</a>.

        My research explored the coordination challenges and possibilities presented by robotic
        mothership-passenger systems, combining centralized and distributed multi-robot coordination
        approaches with planning-based and learning-based methods to develop robust hierarchical
        teaming algorithms for uncertain and dynamic environments.
        <br><br>
        For questions related to research or potential collaborations, please reach out at <a
            href="mailto:nathanbutler.nlb@gmail.com">nathanbutler.nlb@gmail.com</a>.

        <div class="about-links">
            <a href="mailto:nathanbutler.nlb@gmail.com">Email</a>
            <a href="https://www.linkedin.com/in/nlbutler/" target="_blank">LinkedIn</a>
            <a href="https://github.com/natbut" target="_blank">GitHub</a>
            <a href="docs/NathanButler_Resume.pdf" target="_blank">Resume</a>
            <a href="docs/NathanButler_CV.pdf" target="_blank">CV</a>
        </div>
    </div>
    <div class="about-photo">
        <img src="img/site/beach2.JPG" alt="Nathan Butler">
    </div>
</div>
```

- [ ] **Step 3: Verify in browser**

Open `http://localhost:8080/`. The nav should show the avatar inline-left with nav links to the right. The about section should be a two-column grid. On a narrow window (<768px), the photo should disappear.

- [ ] **Step 4: Commit**

```powershell
git add index.html
git commit -m "feat: update index.html nav and About section"
```

---

## Task 4: Add Featured Work Section to index.html

**Files:**
- Modify: `index.html`

This section replaces the Experience list as the primary visual element on the homepage. It showcases three research projects as clickable cards. The three tiles below use the most visually-complete existing projects; adjust the content as needed.

- [ ] **Step 1: Add the Featured Work section after the About grid**

After the closing `</div>` of `.about-grid`, add:

```html
<hr class="section-divider">
<h1>Featured Work</h1>
<div class="featured-grid">

    <a class="featured-card" href="projects/merl.html">
        <img class="card-thumb" src="img/projects/merl/merl_fig.png" alt="MERL project">
        <div class="card-body">
            <div class="card-title">Multiagent Evolutionary Reinforcement Learning</div>
            <div class="card-desc">Training coordinated multi-robot policies for sparse reward environments using a hybrid EA–RL framework.</div>
            <div class="card-tags">
                <span class="tag">multi-robot</span>
                <span class="tag">reinforcement-learning</span>
                <span class="tag">simulation</span>
            </div>
        </div>
    </a>

    <a class="featured-card" href="projects/mr_drl.html">
        <img class="card-thumb" src="img/projects/mr_drl/gnn_arch.png" alt="Multi-robot DRL project">
        <div class="card-body">
            <div class="card-title">Decentralized Multi-Robot Control with DRL</div>
            <div class="card-desc">Comparing CNN and GNN policies for decentralized multi-robot motion control using MAPPO.</div>
            <div class="card-tags">
                <span class="tag">multi-robot</span>
                <span class="tag">deep-learning</span>
                <span class="tag">simulation</span>
            </div>
        </div>
    </a>

    <a class="featured-card" href="publications/hybrid-dec.html">
        <img class="card-thumb" src="img/projects/hybrid_dec/hybrid_dec_framework.png" alt="Hybrid Decentralization">
        <div class="card-body">
            <div class="card-title">Hybrid Decentralization for Mothership-Passenger Systems</div>
            <div class="card-desc">ICRA 2025 — hierarchical multi-robot orienteering combining centralized planning with decentralized execution.</div>
            <div class="card-tags">
                <span class="tag">multi-robot</span>
                <span class="tag">motion-planning</span>
                <span class="tag">underwater</span>
            </div>
        </div>
    </a>

</div>
```

- [ ] **Step 2: Verify in browser**

Open `http://localhost:8080/`. The Featured Work section should show three cards with thumbnails, titles, descriptions, and tag chips. Cards should lift on hover with an amber left-border flash. On mobile, cards stack to a single column.

- [ ] **Step 3: Commit**

```powershell
git add index.html
git commit -m "feat: add Featured Work card grid to homepage"
```

---

## Task 5: Update Updates and Experience Sections in index.html

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Replace the Updates section**

Replace the existing `<h1 id="updates">Updates</h1>` and its `<ul>` with:

```html
<hr class="section-divider">
<h1 id="updates">Updates</h1>
<ul class="updates-ul">
    <li><span class="update-date">[04/07/2026]</span> Our paper <a href="https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2026.1799672/abstract" target="_blank">Multi-Robot Coordination for Underwater Mothership-Passenger Systems</a> has been accepted for publication in Frontiers in Robotics and AI</li>
    <li><span class="update-date">[01/31/2026]</span> Submitted my first journal paper to Frontiers in Robotics and AI</li>
    <li><span class="update-date">[09/10/2025]</span> Successfully defended my MS in Robotics</li>
    <li><span class="update-date">[05/19/2025]</span> Attended &amp; presented at ICRA 2025 in Atlanta, GA</li>
    <li><span class="update-date">[01/27/2025]</span> Our paper "Hybrid Decentralization for Multi-Robot Orienteering with Mothership-Passenger Systems" has been accepted to ICRA 2025</li>
    <li><span class="update-date">[09/27/2024]</span> Started the second year of my MS</li>
    <li><span class="update-date">[09/15/2024]</span> Submitted my first paper to ICRA 2025</li>
    <li><span class="update-date">[04/26/2024]</span> Presented poster "Pseudo-Centralized Mission Planning for Under-Ice Robotic MOTHERSHIPs" at 2024 Northwest Robotics Symposium</li>
    <li><span class="update-date">[09/15/2023]</span> Started my MS in Robotics at Oregon State University</li>
</ul>
```

- [ ] **Step 2: Replace the Experience section**

Replace the existing `<h1 id="experience">Experience</h1>` and its `<ul>` with:

```html
<hr class="section-divider">
<h1 id="experience">Experience</h1>
<ul class="experience-ul">
    <li>
        <span class="exp-date">Sep. 2023 – Present</span>
        <span class="exp-role">Graduate Research Assistant</span> —
        <a href="https://research.engr.oregonstate.edu/rdml/home" target="_blank">Robotic Decision Making Lab</a>,
        <a href="https://engineering.oregonstate.edu/CoRIS" target="_blank">CoRIS Institute</a>,
        <a href="https://oregonstate.edu/" target="_blank">Oregon State University</a>
    </li>
    <li>
        <span class="exp-date">Jan. 2022 – Jul. 2023</span>
        <span class="exp-role">Undergraduate Research Assistant</span> —
        <a href="https://www.abe.iastate.edu/lietang/" target="_blank">ABE Automation and Robotics Lab</a>,
        <a href="https://www.iastate.edu/" target="_blank">Iowa State University</a>
    </li>
    <li>
        <span class="exp-date">Aug. 2021 – May 2023</span>
        <span class="exp-role">Systems Director</span> —
        <a href="https://www.stuorg.iastate.edu/spacemining" target="_blank">Cardinal Space Mining Club</a>,
        <a href="https://www.iastate.edu/" target="_blank">Iowa State University</a>
    </li>
    <li>
        <span class="exp-date">May 2021 – Dec. 2021</span>
        <span class="exp-role">Mechanical Engineer Co-Op</span> —
        Seed Technology and Innovation Team,
        <a href="https://www.corteva.com/" target="_blank">Corteva Agriscience</a>
    </li>
    <li>
        <span class="exp-date">Jan. 2021 – May 2021</span>
        <span class="exp-role">Controls Intern</span> —
        <a href="https://www.nasa.gov/mission/eap/" target="_blank">Intelligent Control and Autonomy Group</a>,
        <a href="https://www.nasa.gov/glenn/" target="_blank">NASA Glenn Research Center</a>
    </li>
    <li>
        <span class="exp-date">May 2020 – Aug. 2020</span>
        <span class="exp-role">Undergraduate Research Assistant</span> —
        <a href="https://crops.extension.iastate.edu/" target="_blank">Integrated Crop Management</a>,
        <a href="https://www.extension.iastate.edu/" target="_blank">Iowa State University Extension &amp; Outreach</a>
    </li>
    <li>
        <span class="exp-date">May 2019 – Aug. 2019</span>
        <span class="exp-role">Manufacturing Engineering Intern</span> —
        <a href="https://www.tenneco.com/" target="_blank">Tenneco Inc.</a>
    </li>
</ul>
```

- [ ] **Step 3: Verify in browser**

Open `http://localhost:8080/`. Check:
- Update timestamps are small monospace in muted gray; update text is normal body weight
- Experience entries show monospace date, navy bold role, amber org links
- Section dividers (short navy rules) appear before each `h1`

- [ ] **Step 4: Commit**

```powershell
git add index.html
git commit -m "feat: restyle Updates and Experience sections on homepage"
```

---

## Task 6: Rewrite projects.html as Card Grid

**Files:**
- Modify: `projects.html`

- [ ] **Step 1: Replace the entire contents of projects.html with the following**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Projects — Nathan Butler</title>
    <link rel="stylesheet" href="css/main.css">
    <link rel="icon" type="image/x-icon" href="img/site/round1.png">
</head>

<body>
    <header>
        <nav>
            <a class="nav-logo" href="index.html">
                <img src="img/site/round1.png" alt="Nathan Butler">
            </a>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="projects.html" class="active">Projects</a></li>
                <li><a href="publications.html">Publications</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <h1>Ongoing Projects</h1>
        <p style="color: var(--text-secondary); margin-top: 0.75rem;">Stay tuned for updates…</p>

        <hr class="section-divider">
        <h1>Past Projects</h1>

        <div class="projects-grid">

            <a class="project-card" href="projects/merl.html">
                <img class="card-thumb" src="img/projects/merl/merl_fig.png" alt="MERL">
                <div class="card-body">
                    <div class="card-title">Coordinated Underwater Exploration with Multiagent Evolutionary Reinforcement Learning</div>
                    <div class="card-desc">Training coordinated multi-robot policies for sparse-reward connectivity maintenance using a hybrid EA–RL framework.</div>
                    <div class="card-tags">
                        <span class="tag">multi-robot</span>
                        <span class="tag">reinforcement-learning</span>
                        <span class="tag">underwater</span>
                        <span class="tag">simulation</span>
                    </div>
                </div>
            </a>

            <a class="project-card" href="projects/mr_drl.html">
                <img class="card-thumb" src="img/projects/mr_drl/gnn_arch.png" alt="Multi-robot DRL">
                <div class="card-body">
                    <div class="card-title">Decentralized Multi-Robot Control with Deep Reinforcement Learning</div>
                    <div class="card-desc">Comparing CNN and GNN policies for decentralized multi-robot motion control and coordination using MAPPO.</div>
                    <div class="card-tags">
                        <span class="tag">multi-robot</span>
                        <span class="tag">deep-learning</span>
                        <span class="tag">reinforcement-learning</span>
                        <span class="tag">simulation</span>
                    </div>
                </div>
            </a>

            <a class="project-card" href="projects/machine_learning.html">
                <img class="card-thumb" src="img/projects/machine_learning/gridworld_qLearning.png" alt="Machine Learning">
                <div class="card-body">
                    <div class="card-title">Machine Learning, Evolutionary Algorithms, Reinforcement Learning</div>
                    <div class="card-desc">Class projects exploring feed-forward networks, Q-learning, DQN, and evolutionary algorithms on benchmark environments.</div>
                    <div class="card-tags">
                        <span class="tag">deep-learning</span>
                        <span class="tag">reinforcement-learning</span>
                        <span class="tag">simulation</span>
                    </div>
                </div>
            </a>

            <a class="project-card" href="projects/robot_control.html">
                <div class="card-thumb-placeholder"></div>
                <div class="card-body">
                    <div class="card-title">Robot Control</div>
                    <div class="card-desc">Robot control projects and experiments.</div>
                    <div class="card-tags">
                        <span class="tag">hardware</span>
                    </div>
                </div>
            </a>

            <a class="project-card" href="projects/space_mining.html">
                <div class="card-thumb-placeholder"></div>
                <div class="card-body">
                    <div class="card-title">Cardinal Space Mining</div>
                    <div class="card-desc">Systems Director for Iowa State's NASA Lunabotics competition team.</div>
                    <div class="card-tags">
                        <span class="tag">hardware</span>
                        <span class="tag">field-robotics</span>
                    </div>
                </div>
            </a>

        </div>
    </main>

</body>
</html>
```

Note: The `robot_control` and `space_mining` cards use `.card-thumb-placeholder` (a gray fill) because no thumbnail image exists yet. Add a thumbnail by placing an image at `img/projects/<name>/thumb.png` and replacing `<div class="card-thumb-placeholder"></div>` with `<img class="card-thumb" src="img/projects/<name>/thumb.png" alt="...">`.

- [ ] **Step 2: Verify in browser**

Open `http://localhost:8080/projects.html`. Check:
- 2-column card grid with thumbnails, descriptions, tag chips
- The two placeholder cards show a flat gray fill at the top
- Cards hover correctly (shadow + amber left-border)
- On mobile, collapses to single column

- [ ] **Step 3: Commit**

```powershell
git add projects.html
git commit -m "feat: rewrite projects.html as card grid"
```

---

## Task 7: Update publications.html

**Files:**
- Modify: `publications.html`

- [ ] **Step 1: Replace the entire contents of publications.html with the following**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Publications — Nathan Butler</title>
    <link rel="stylesheet" href="css/main.css">
    <link rel="icon" type="image/x-icon" href="img/site/round1.png">
</head>

<body>
    <header>
        <nav>
            <a class="nav-logo" href="index.html">
                <img src="img/site/round1.png" alt="Nathan Butler">
            </a>
            <ul>
                <li><a href="index.html">Home</a></li>
                <li><a href="projects.html">Projects</a></li>
                <li><a href="publications.html" class="active">Publications</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <h1>Publications</h1>

        <ul class="pubs-ul">
            <li>
                N. Butler and G. Hollinger, "<a href="publications/hybrid-dec.html">Hybrid
                Decentralization for Multi-Robot Orienteering with Mothership-Passenger
                Systems</a>," in <span class="pub-venue">Proc. of the 42<sup>nd</sup> IEEE
                International Conference on Robotics and Automation (ICRA)</span>, Atlanta,
                GA, May 2025.
            </li>
            <li>
                N. Butler, G. Hollinger, J. Garwood, Y. Si, and A. Stewart,
                "Pseudo-Centralized Mission Planning for Under-Ice Robotic MOTHERSHIPs"
                [Poster]. <span class="pub-venue">2<sup>nd</sup> Northwest Robotics
                Symposium</span>, Corvallis, OR, April 2024.
            </li>
        </ul>
    </main>

</body>
</html>
```

- [ ] **Step 2: Verify in browser**

Open `http://localhost:8080/publications.html`. Check:
- Each citation has a navy left-border accent
- Venue names render in amber
- Nav shows "Publications" as active link

- [ ] **Step 3: Commit**

```powershell
git add publications.html
git commit -m "feat: update publications.html with left-border accents and amber venue"
```

---

## Task 8: Update Project Detail Pages

**Files:**
- Modify: `projects/merl.html`, `projects/mr_drl.html`, `projects/machine_learning.html`

Apply the same set of changes to each file: back-nav, updated image paths, PDF links as `.btn-link` buttons. Steps below show `merl.html` in full; repeat the pattern for the other two.

- [ ] **Step 1: Replace projects/merl.html**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Coordinated Underwater Exploration with MERL</title>
    <link rel="stylesheet" href="../css/main.css">
</head>

<body>
    <header>
        <nav>
            <a class="nav-logo" href="../index.html">
                <img src="../img/site/round1.png" alt="Nathan Butler">
            </a>
            <ul>
                <li><a href="../index.html">Home</a></li>
                <li><a href="../projects.html" class="active">Projects</a></li>
                <li><a href="../publications.html">Publications</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <p class="back-nav"><a href="../projects.html">← Projects</a></p>

        <h1 class="paper-title">Coordinated Underwater Exploration with Multiagent Evolutionary Reinforcement Learning</h1>

        <div style="text-align: center; margin-bottom: 1.5rem;">
            Class Project for Robotics 538: Multiagent Systems<br><br>
            <a class="btn-link" href="../docs/ROB538_ProjectPaper_ButlerOhWells.pdf" target="_blank">PDF</a>
        </div>

        <h2>Overview</h2>
        <p class="paper-p">
            In this class project, we explored multiagent evolutionary reinforcement learning (MERL) frameworks for training multiple policies in sparse reward environments. This work was inspired by connectivity maintenance problems for multi-robot teams. We define a simple sparse reward environment where a subset of the multiagent team must position themselves as intermediate communication relays in order for maximum rewards to be obtained from task locations. Using MERL, we are able to iteratively evolve and refine a set of policies that results in coordinated behaviors for this environment.
        </p>

        <h2>MERL Framework</h2>
        <p class="paper-p">
            MERL addresses sparse reward settings by training polices in a manner that iterates between reinforcement learning (RL) and an evolutionary algorithm (EA). The EA initializes a diverse population of team policies. We perform multiple policy rollouts in our training environment to evaluate the fitness of each (max performance). Next, the best-performing policy is applied in an RL setting to receive refined, dense training feedback before being returned to the EA population pool. This cycle repeats until convergence.
        </p>

        <img src="../img/projects/merl/merl_fig.png" alt="MERL Framework" class="center">

        <h2>Multi-Headed Policy</h2>
        <p class="paper-p">
            We configure our team policy as a multi-headed policy in which each agent uses a shared trunk. The output of the trunk is provided to each agent's individual policy head. This structure allows the trunk to perform general, high-level environment processing before each agent's head provides fine-grained, unique behaviors. In training, the EA adjusts the weights of each aspect of the network while the RL loop refines only each agent's head.
        </p>

        <img src="../img/projects/merl/multihead_fig.png" alt="Multi-headed policy architecture" style="max-width: 80%;" class="center">

        <h2>Training Evaluations</h2>
        <p class="paper-p">
            We trained our policy with two dense RL reward functions to address the sparse environmental feedback. Our L1 reward function motivates agents to optimize their spacing between other agents and a central communication location. L2 rewards agents for moving towards incomplete tasks. While neither reward is directly aligned with the problem's overall global reward, our results show that the RL loop guides policies to higher rewards faster than the EA-only loop.
        </p>

        <img src="../img/projects/merl/merl_avgs.png" alt="Training results" style="max-width: 80%;" class="center">
    </main>

</body>
</html>
```

- [ ] **Step 2: Replace projects/mr_drl.html**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Decentralized Multi-Robot Control with DRL</title>
    <link rel="stylesheet" href="../css/main.css">
</head>

<body>
    <header>
        <nav>
            <a class="nav-logo" href="../index.html">
                <img src="../img/site/round1.png" alt="Nathan Butler">
            </a>
            <ul>
                <li><a href="../index.html">Home</a></li>
                <li><a href="../projects.html" class="active">Projects</a></li>
                <li><a href="../publications.html">Publications</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <p class="back-nav"><a href="../projects.html">← Projects</a></p>

        <h1 class="paper-title">Decentralized Multi-Robot Control with Deep Reinforcement Learning</h1>

        <div style="text-align: center; margin-bottom: 1.5rem;">
            Class Project for AI 535: Deep Learning<br><br>
            <a class="btn-link" href="../docs/Multi_Robot_Control_with_Deep_Reinforcement_Learning.pdf" target="_blank">PDF</a>
            <a class="btn-link" href="https://github.com/natbut/multi-robot-DRL/tree/main" target="_blank">GitHub</a>
        </div>

        <h2>Overview</h2>
        <p class="paper-p">
            Multi-robot systems require both task allocation and motion control to operate efficiently in cluttered environments. Deep Reinforcement Learning (DRL) has shown promise, with Convolutional Neural Networks (CNNs) excelling in motion control and Graph Neural Networks (GNNs) enabling coordination through message passing.
            <br><br>
            This project evaluated CNN- and GNN-based DRL policies for decentralized multi-robot control, assessing whether CNNs can implicitly develop coordination from local sensor inputs and whether GNNs offer advantages through explicit communication.
        </p>

        <h2>Network Architectures</h2>
        <p class="paper-p">
            We evaluated each architecture in a simulated multi-agent training environment where multiple agents must move towards task locations while avoiding obstacles. The figure below presents the high-level CNN architecture.
        </p>

        <img src="../img/projects/mr_drl/cnn_arch.png" alt="CNN architecture" class="center">

        <p class="paper-p">
            For the GNN, each agent receives a summary of its local observations rather than image data. The GNN architecture exchanges information between neighboring agents through message passing layers, enabling coordinated decision-making based on shared knowledge of the environment and other agents' states.
        </p>

        <img src="../img/projects/mr_drl/gnn_arch.png" alt="GNN architecture" class="center">

        <p class="paper-p">Both policies were trained using Multi-Agent Proximal Policy Optimization (MAPPO).</p>

        <h2>Training Performance</h2>
        <p class="paper-p">
            We evaluated training performance based on average episode rewards over training. The figure below presents experimental results for RL minibatch iterations, sizes, and learning rates for the CNN. Larger minibatch sizes and smaller learning rates yield the most stable learning outcomes.
        </p>

        <img src="../img/projects/mr_drl/cnn_res.png" alt="CNN training results" class="center">

        <p class="paper-p">
            We also evaluated multiple GNN aggregation functions, finding that the Transformer method yields the best performance.
        </p>

        <img src="../img/projects/mr_drl/gnn_res.png" alt="GNN training results" style="max-width: 80%;" class="center">

        <p class="paper-p">
            Ultimately, while training performance shows that these policies can learn useful control inputs, qualitative analysis of the resulting trajectories indicates limited support for coordinated actions.
        </p>
    </main>

</body>
</html>
```

- [ ] **Step 3: Replace projects/machine_learning.html**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Machine Learning Projects</title>
    <link rel="stylesheet" href="../css/main.css">
</head>

<body>
    <header>
        <nav>
            <a class="nav-logo" href="../index.html">
                <img src="../img/site/round1.png" alt="Nathan Butler">
            </a>
            <ul>
                <li><a href="../index.html">Home</a></li>
                <li><a href="../projects.html" class="active">Projects</a></li>
                <li><a href="../publications.html">Publications</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <p class="back-nav"><a href="../projects.html">← Projects</a></p>

        <h1 class="paper-title">Experimenting with Machine Learning</h1>

        <p class="paper-p">
            Through class assignments and projects I have had the opportunity to explore multiple facets of machine learning, including network architectures, training configurations, data augmentation, and more.
        </p>

        <h2>Image Classification &amp; Feed Forward Neural Network Tuning</h2>
        <p class="paper-p">
            In a class assignment for AI 535: Deep Learning, I implemented a feed forward neural network for the CIFAR-10 image dataset capable of achieving ~80% validation accuracy. The network uses ReLU activation for hidden layers and a sigmoid activation for the binary output class. I experimented with batch sizes, learning rates, hidden layer widths, and numbers of hidden layers.
            <br><br>
            <a class="btn-link" href="https://github.com/natbut/deep-learning/tree/main/hw1_image_classification_FCNN" target="_blank">GitHub</a>
        </p>

        <img src="../img/projects/machine_learning/deep_learning_curve1.png" alt="Training curve" class="center">

        <h2>Reinforcement Learning with Gridworld</h2>
        <p class="paper-p">
            The objective of this assignment for ROB 537: Learning-Based Control was to implement Q-Learning and SARSA agents to solve a simple gridworld environment. The environment consists of a 5×10 grid with a fixed goal location and a wall. The agent receives a reward of −1 when in any cell other than the goal cell.
            <br><br>
            <a class="btn-link" href="https://github.com/natbut/learning-based-control/tree/main/hw3" target="_blank">GitHub</a>
        </p>

        <img src="../img/projects/machine_learning/gridworld_qLearning.png" alt="Q-learning gridworld results" class="center">

        <h2>DQN &amp; EA for Cartpole Environment</h2>
        <p class="paper-p">
            In another assignment for ROB 537: Learning-Based Control, I implemented a Deep Q-Network (DQN) agent and an Evolutionary Algorithm (EA) agent to solve the Gym Cartpole environment. The DQN uses two feed-forward networks (policy and target); the EA iteratively evolves a population of candidate Q-Network policies through selection, crossover, and mutation.
            <br><br>
            <a class="btn-link" href="https://github.com/natbut/learning-based-control/tree/main/hw4" target="_blank">GitHub</a>
        </p>
    </main>

</body>
</html>
```

- [ ] **Step 4: Update nav in projects/robot_control.html and projects/space_mining.html**

For each of these files, open it and replace the existing `<header>` with the standard nav block:

```html
<header>
    <nav>
        <a class="nav-logo" href="../index.html">
            <img src="../img/site/round1.png" alt="Nathan Butler">
        </a>
        <ul>
            <li><a href="../index.html">Home</a></li>
            <li><a href="../projects.html" class="active">Projects</a></li>
            <li><a href="../publications.html">Publications</a></li>
        </ul>
    </nav>
</header>
```

Also add the back-nav line immediately after `<main>`:
```html
<p class="back-nav"><a href="../projects.html">← Projects</a></p>
```

Update any `../../css/main.css` references to `../css/main.css` and any `../../img/` references to `../img/`.

- [ ] **Step 5: Verify in browser**

Open each project detail page:
- `http://localhost:8080/projects/merl.html` — back-nav, all figures load, PDF button styled
- `http://localhost:8080/projects/mr_drl.html` — back-nav, all figures load, PDF + GitHub buttons
- `http://localhost:8080/projects/machine_learning.html` — back-nav, 2 figures load, GitHub buttons
- Click "← Projects" on each — should return to `projects.html`

- [ ] **Step 6: Commit**

```powershell
git add projects\merl.html projects\mr_drl.html projects\machine_learning.html projects\robot_control.html projects\space_mining.html
git commit -m "feat: update project detail pages with back-nav, btn-link, and new image paths"
```

---

## Task 9: Update publications/hybrid-dec.html

**Files:**
- Modify: `publications/hybrid-dec.html`

Note: The existing file has the correct ICRA 2025 content. This step preserves that content and applies only nav, path, and styling updates.

- [ ] **Step 1: Replace the entire contents of publications/hybrid-dec.html**

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Hybrid Decentralization for Multi-Robot Orienteering with Mothership-Passenger Systems</title>
    <link rel="stylesheet" href="../css/main.css">
</head>

<body>
    <header>
        <nav>
            <a class="nav-logo" href="../index.html">
                <img src="../img/site/round1.png" alt="Nathan Butler">
            </a>
            <ul>
                <li><a href="../index.html">Home</a></li>
                <li><a href="../projects.html">Projects</a></li>
                <li><a href="../publications.html" class="active">Publications</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <p class="back-nav"><a href="../publications.html">← Publications</a></p>

        <h1 class="paper-title">Hybrid Decentralization for Multi-Robot Orienteering with Mothership-Passenger Systems</h1>

        <div style="text-align: center; margin-bottom: 1.5rem;">
            <span style="color: var(--text-secondary);">Nathan L. Butler and Geoffrey A. Hollinger</span><br>
            <span class="pub-venue">ICRA 2025 — 42<sup>nd</sup> IEEE International Conference on Robotics and Automation</span>
            <br><br>
            <a class="btn-link" href="../docs/Butler_Hybrid_Decentralization_ICRA2025.pdf" target="_blank">PDF</a>
            <a class="btn-link" href="https://www.frontiersin.org/journals/robotics-and-ai/articles/10.3389/frobt.2026.1799672/abstract" target="_blank">Journal</a>
        </div>

        <img src="../img/projects/hybrid_dec/mission_schamatic_4.png" alt="Mission schematic" style="max-width: 75%;" class="center">

        <h2>Overview</h2>
        <p class="paper-p">We present a hybrid centralized-decentralized planning algorithm for a multi-robot system consisting of a Mothership robot and multiple Passenger robots. In this system, the Passenger robots execute tasks while the Mothership provides support. This paper addresses the challenge of planning Passenger robot movements, framing it as a Stochastic Multi-Agent Orienteering Problem (SMOP) complicated by factors like stochastic operational efforts and disruptive events. We optimize the task completion efficiency of the system by combining centralized solutions from the Mothership with local plans from Passengers to enhance system resilience. Our contributions include defining the SMOP, developing a solution using Decentralized Monte Carlo Tree Search, presenting a hybrid algorithm that integrates centralized plans into the distributed framework, and evaluating the algorithm's performance in a simulated environment. Our results show that our hybrid approaches outperform fully centralized and fully distributed algorithms in highly-dynamic scenarios with up to a 26.6% increase in task completion efficiency over baseline methods.</p>

        <h2>Hybrid Decentralized Mission Planning</h2>
        <p class="paper-p">Our hybrid planning algorithm equips the mothership and passengers to each solve solutions to the SMOP using the unique observations available to each robot. The mothership uses a centralized planner to solve joint multi-robot solutions to a centralized variant of the SMOP, which are then shared with connected passengers. The plans produced by the mothership are informed by information that it has aggregated from connected passengers during runtime. However, as communication links between the mothership and passengers are not guaranteed, we also equip each passenger robot with a local decentralized planner. Using local observations and sets of candidate plans received from neighboring robots, each passenger plans routes that are well-informed by their local neighborhood. Meanwhile, plans sent by the mothership guide global coordination.</p>

        <img src="../img/projects/hybrid_dec/hybrid_dec_framework.png" alt="Hybrid decentralization framework" style="max-width: 75%;" class="center">

        <p class="paper-p">During operations, passengers store a history of high-value plans that they have both received from the mothership and developed locally, which they then compare against any new local plans. By referencing a history of past plans, even passengers that have lost communication with the mothership or neighboring robots can take informed, coordinated actions. Altogether, this framework supports hybrid centralized-decentralized replanning, even with asynchronous communications.</p>

        <h2>Video Walkthrough &amp; Simulations</h2>
        <video controls class="center" style="max-width: 75%;">
            <source src="../img/projects/hybrid_dec/MOTHERSHIP_ICRA25_SupplVid_Sims_480p_2.mp4" type="video/mp4">
            Your browser does not support the video tag.
        </video>
    </main>

</body>
</html>
```

- [ ] **Step 2: Verify in browser**

Open `http://localhost:8080/publications/hybrid-dec.html`. Check:
- Back-nav "← Publications" present and functional
- ICRA venue name in amber
- Both figures load
- Video player renders and plays
- Journal button styled correctly

- [ ] **Step 3: Commit**

```powershell
git add publications\hybrid-dec.html
git commit -m "feat: update hybrid-dec publication detail page with new nav and image paths"
```

---

## Task 10: Create _template.html and _tags.md

**Files:**
- Modify: `projects/_template.html`
- Create: `projects/_tags.md`

- [ ] **Step 1: Replace the entire contents of projects/_template.html**

```html
<!--
  METADATA (fill in before publishing — not rendered in browser)
  title:       [Project Title]
  date:        [YYYY-MM or YYYY]
  status:      [ongoing | past]
  tags:        [tag1, tag2]  — use canonical tags from _tags.md
  thumbnail:   ../img/projects/[name]/thumb.png
  description: [1–2 sentence summary for the projects.html card]
-->
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>[Project Title]</title>
    <link rel="stylesheet" href="../css/main.css">
</head>

<body>
    <header>
        <nav>
            <a class="nav-logo" href="../index.html">
                <img src="../img/site/round1.png" alt="Nathan Butler">
            </a>
            <ul>
                <li><a href="../index.html">Home</a></li>
                <li><a href="../projects.html" class="active">Projects</a></li>
                <li><a href="../publications.html">Publications</a></li>
            </ul>
        </nav>
    </header>

    <main>
        <p class="back-nav"><a href="../projects.html">← Projects</a></p>

        <h1 class="paper-title">[Project Title]</h1>

        <div style="text-align: center; margin-bottom: 1.5rem;">
            [Course or context, e.g. "Class Project for ROB 537"]<br><br>
            <!-- Add links as needed: -->
            <a class="btn-link" href="../docs/[filename].pdf" target="_blank">PDF</a>
            <a class="btn-link" href="https://github.com/natbut/[repo]" target="_blank">GitHub</a>
        </div>

        <h2>Overview</h2>
        <p class="paper-p">
            [Project overview paragraph]
        </p>

        <!-- Repeat h2 + p.paper-p + img.center blocks as needed -->
        <h2>[Section Title]</h2>
        <p class="paper-p">
            [Section content]
        </p>

        <img src="../img/projects/[name]/[figure.png]" alt="[description]" class="center">
        <p class="fig-caption">[Optional caption]</p>

    </main>

</body>
</html>
```

- [ ] **Step 2: Create projects/_tags.md**

```markdown
# Canonical Tag List

Use these tags in project metadata and card HTML to keep naming consistent.
Add new tags freely — just update this file when you do.

## Research Areas
- `multi-robot`
- `motion-planning`
- `reinforcement-learning`
- `deep-learning`
- `field-robotics`
- `underwater`

## Methods
- `simulation`
- `hardware`
- `learning-based-control`
- `evolutionary-algorithms`

## Adding a new project
1. Copy `_template.html` → `<name>.html`
2. Fill in the metadata comment block at the top
3. Add images to `../img/projects/<name>/`
4. Add a `.project-card` entry to `../projects.html`
```

- [ ] **Step 3: Verify template renders without errors**

Open `http://localhost:8080/projects/_template.html`. The page should load the nav, back-nav, and placeholder content without CSS errors. (Broken image links for placeholder paths are expected.)

- [ ] **Step 4: Commit**

```powershell
git add projects\_template.html projects\_tags.md
git commit -m "docs: add project _template.html with metadata block and _tags.md"
```

---

## Task 11: Final Review Pass

- [ ] **Step 1: Full site walkthrough in browser**

Start `python -m http.server 8080` and check every page:

| Page | Check |
|---|---|
| `index.html` | Nav inline logo+links, warm gray bg, two-column about, 3 Featured Work cards, monospace timestamps, compact experience list |
| `projects.html` | 2-col card grid, amber left-border on hover, placeholder cards for robot_control + space_mining |
| `publications.html` | Navy left-border per citation, amber venue names |
| `projects/merl.html` | Back-nav, paper-title, btn-link PDF, all 3 figures |
| `projects/mr_drl.html` | Back-nav, btn-link PDF + GitHub, all 4 figures |
| `projects/machine_learning.html` | Back-nav, btn-link GitHub links, 2 figures |
| `publications/hybrid-dec.html` | Back-nav, amber venue, 2 figures, video player |
| Mobile (resize to <768px) | About photo hides, grids go to 1 column, nav text-only |

- [ ] **Step 2: Check for any remaining `pages/` references**

```powershell
Select-String -Path "*.html", "**\*.html" -Pattern "pages/" -Recurse
```

Expected output: no results. If any appear, fix the path in that file.

- [ ] **Step 3: Final commit**

```powershell
git add -A
git commit -m "chore: final review pass — fix any remaining path or style issues"
```
