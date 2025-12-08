---
marp: true
theme: custom
paginate: true
class: lead
---

<!--
  slides.md - Marp product documentation presentation
  Author: Technical writer
  Contact: 22f3001731@ds.study.iitm.ac.in
-->

<style>
:root{
  --bg: #0b1220;
  --card: rgba(255,255,255,0.03);
  --primary: #0b5cff;
  --accent: #f97316;
  --muted: rgba(255,255,255,0.65);
  --mono: "Fira Code", monospace;
}

section {
  font-family: Inter, "Helvetica Neue", Arial, sans-serif;
  background: linear-gradient(180deg, rgba(11,18,32,1) 0%, rgba(6,9,20,1) 100%);
  color: var(--muted);
  padding: 40px;
}

.card {
  background: var(--card);
  border-radius: 12px;
  padding: 18px;
  box-shadow: 0 6px 18px rgba(3,6,12,0.6);
}

h1 { color: var(--primary); margin-bottom: 6px; }
h2 { color: #9ad0ff; }

.marp-footer {
  position: absolute;
  right: 20px;
  bottom: 16px;
  font-size: 12px;
  color: rgba(255,255,255,0.55);
}

code, pre {
  font-family: var(--mono);
  background: rgba(255,255,255,0.02);
  padding: 6px 8px;
  border-radius: 6px;
}

.badge {
  display:inline-block;
  background: var(--accent);
  color: white;
  padding: 6px 10px;
  border-radius: 999px;
  font-weight: 600;
  font-size: 12px;
}
</style>

---

# Product Documentation
### Maintainable Marp source + conversion workflow
22f3001731@ds.study.iitm.ac.in

<div class="card" style="margin-top:18px;">
- Version-controlled Markdown (diff-friendly)  
- Convert with `marp-cli` or Marp for VS Code  
- Put large assets in `assets/` and reference relatively (e.g., `assets/bg.png`)  
</div>

---

## Documentation goals
<div class="card">
- Lightweight, single-file source for easy diffs and reviews.  
- Exportable to PDF / PPTX / HTML using Marp tooling.  
- Themeable and brandable via CSS (see the inline theme at top).
</div>

---

---
background-image: url('assets/bg.png')
background-size: cover
background-position: center
---

# Product: Analyze — Key Features

- Interactive data pipelines  
- Extensible plugin architecture  
- Built for reproducible research


# Product: Analyze — Key Features

- Interactive data pipelines  
- Extensible plugin architecture  
- Built for reproducible research

---

## Architecture (high level)
<div class="card" markdown="1">
- **Ingest** → **Transform** → **Analyze** → **Report**  
- Each stage is versioned; configs are stored in `config/`.  
- Artifacts (models, datasets) stored under `artifacts/` with checksums.
</div>

---

## Algorithmic Complexity

The primary sort-and-merge pipeline has time complexity:

\[
T(n) = O(n \log n) + O(m)
\]

Where:
- \(n\) = number of records to sort  
- \(m\) = number of merge operations

Parallel execution across \(p\) workers reduces wall time:

\[
T_{wall}(n) \approx \frac{O(n \log n)}{p} + O\!\left(\frac{m}{p}\right)
\]

---

## Build / Export Commands
<div class="card">
- Preview locally (VS Code + Marp extension)  
- Export PDF:  
`npx @marp-team/marp-cli slides.md -o slides.pdf --pdf-options.printBackground`  
- Export PPTX (experimental):  
`npx @marp-team/marp-cli slides.md -o slides.pptx`
</div>

---

## Style & Maintenance
- Keep global theme variables in the top `<style>` block; change colors/brand easily.  
- Prefer relative paths for images/assets for CI builds.  
- One idea per slide for easier PR review.

---

## Questions / Contact
22f3001731@ds.study.iitm.ac.in

<div class="badge">Version control friendly</div>
<div style="margin-top:10px;">Convert to PDF/PPTX/HTML via `marp-cli` in CI. See top comments for commands.</div>

