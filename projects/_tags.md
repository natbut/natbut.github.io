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
4. Add a `.project-card` entry to `../projects.html`:

```html
<a class="project-card" href="projects/<name>.html">
    <img class="card-thumb" src="img/projects/<name>/thumb.png" alt="[alt text]">
    <!-- If no thumbnail yet, use: <div class="card-thumb-placeholder"></div> -->
    <div class="card-body">
        <div class="card-title">[Project Title]</div>
        <div class="card-desc">[1–2 sentence description]</div>
        <div class="card-tags">
            <span class="tag">[tag1]</span>
            <span class="tag">[tag2]</span>
        </div>
    </div>
</a>
```
