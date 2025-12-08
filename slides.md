---
marp: true
theme: custom
paginate: true
class: lead
---

<!--
  slides.md - Marp product documentation presentation
  Author: Technical writer (template)
  Contact: 22f3001731@ds.study.iitm.ac.in

  Notes for maintainability:
  - Keep the file in git (Markdown is diff-friendly).
  - Place large images under `assets/` and reference with relative paths.
  - Convert using marp-cli: `npx @marp-team/marp-cli slides.md -o slides.pdf`
  - Theme and CSS are inline here for single-file portability; consider moving to a separate `.css` when the style stabilizes.
-->

<!-- Custom theme / styling (Marp accepts inline <style>) -->
<style>
:root{
  --bg: #0b1220;
  --card: rgba(255,255,255,0.03);
  --primary: #0b5cff;
  --accent: #f97316;
  --muted: rgba(255,255,255,0.65);
  --mono: "Fira Code", "SFMono-Regular", Menlo, monospace;
}

/* Apply fonts and page background */
section {
  font-family: Inter, "Helvetica Neue", Arial, sans-serif;
  background: linear-gradient(180deg, rgba(11,18,32,1) 0%, rgba(6,9,20,1) 100%);
  color: var(--muted);
  padding: 40px;
}

/* Card (content) */
.card {
  background: var(--card);
  border-radius: 12px;
  padding: 18px;
  box-shadow: 0 6px 18px rgba(3,6,12,0.6);
}

/* Title */
h1 {
  color: var(--primary);
  margin-bottom: 6px;
}
h2 { color: #9ad0ff; }

/* Footer / page numbers (Marp generates .marp-footer when paginate: true) */
.marp-footer {
  position: absolute;
  right: 20px;
  bottom: 16px;
  font-size: 12px;
  color: rgba(255,255,255,0.55);
}

/* Code and monospace */
code, pre {
  font-family: var(--mono);
  background: rgba(255,255,255,0.02);
  padding: 6px 8px;
  border-radius: 6px;
}

/* Emphasize important badges */
.badge {
  display:inline-block;
  background: var(--accent);
  color: white;
  padding: 6px 10px;
  border-radius: 999px;
  font-weight: 600;
  font-size: 12px;
}

/* Background image slide tweaks */
.bg-cover {
  background-size: cover !important;
  background-position: center !important;
  color: white !important;
  text-shadow: 0 2px 10px rgba(0,0,0,0.6);
}
</style>

<!-- Slide 1: Title -->
# Product Documentation
### Maintainable Marp source + conversion workflow
22f3001731@ds.study.iitm.ac.in

<div class="card" style="margin-top:18px;">
- Version-controlled Markdown (diff-friendly)  
- Convert with `marp-cli` or Marp for VS Code  
- Put large assets in `assets/` and reference relatively (e.g., `assets/bg.png`)  
</div>

---

<!-- Slide 2: Overview with custom styling -->
## Documentation goals
<div class="card">
- Lightweight, single-file source for easy diffs and reviews.  
- Exportable to PDF / PPTX / HTML using Marp tooling.  
- Themeable and brandable via CSS (see the inline theme at top).
</div>

---

<!-- Slide 3: Background image slide -->
<!-- Using an external image here for demo; in prod move to `assets/` and reference relatively. -->
<section class="bg-cover" style="background-image: url('https://images.unsplash.com/photo-1505238680356-667803448bb6?auto=format&fit=crop&w=1350&q=80');">
  
# Product: Analyze — Key Features

<div style="margin-top:18px; font-size:16px;">
- Interactive data pipelines  
- Extensible plugin architecture  
- Built for reproducible research
</div>

</section>

---

<!-- Slide 4: Architecture diagram (ASCII / small) -->
## Architecture (high level)
<div class="card" markdown="1">

- **Ingest** → **Transform** → **Analyze** → **Report**
- Each stage is versioned; configs are stored in `config/`.
- Artifacts (models, datasets) stored under `artifacts/` with checksums.

</div>

---

<!-- Slide 5: Algorithms & complexity (mathematical equations) -->
## Algorithmic Complexity

The primary sort-and-merge pipeline has time complexity:

\[
T(n) = O(n \log n) + O(m)
\]

Where:
- \(n\) = number of records to sort  
- \(m\) = number of merge operations

If merges are done in parallel across \(p\) workers, approximate wall time reduces to:

\[
T_{wall}(n) \approx \frac{O(n \log n)}{p} + O\!\left(\frac{m}{p}\right)
\]

(KaTeX/LaTeX math blocks are supported by Marp when building HTML/PDF with marp-cli.)

---

<!-- Slide 6: Example usage & commands -->
## Build / Export Commands

<div class="card">
- Preview locally (VS Code + Marp extension)  
- Export PDF:  
`npx @marp-team/marp-cli slides.md -o slides.pdf --pdf-options.printBackground`  
- Export PPTX (experimental):  
`npx @marp-team/marp-cli slides.md -o slides.pptx`
</div>

---

<!-- Slide 7: Styling tips & maintainability notes -->
## Style & Maintenance

- Keep global theme variables in the top `<style>` block; this keeps color/brand changes minimal.  
- Prefer relative paths for images/assets so the presentation builds in CI.  
- Use small modular slides: each slide should cover one idea — easier to review in PRs.

---

<!-- Slide 8: Closing / Contact -->
## Questions / Contact
22f3001731@ds.study.iitm.ac.in

<div class="badge">Version control friendly</div>
<div style="margin-top:10px;">Convert to PDF/PPTX/HTML via `marp-cli` in CI. See top comments for commands.</div>
