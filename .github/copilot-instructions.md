# Copilot / AI Agent Instructions — GEO-Physics

Purpose: Short actionable guidance to help an AI assistant be productive immediately in this repository (static Arabic educational website).

## Quick snapshot
- Single-page HTML files and simple multi-page static site (no build system). Key files: `index.html`, `GEO.html`, `physics.html`, `bagGeo.html`, `bagphysics.html`, `exams.html`, `examsphysics.html`.
- Assets: `image/` (images), `pdf/` (document resources). Many filenames contain Arabic characters and spaces.
- External libraries are used via CDN (Google Fonts - `Cairo`, FontAwesome, Three.js).

## How to run locally (fast checks) ✅
- Serve static files over HTTP (recommended to avoid local-file CORS issues):
  - Python: `python -m http.server 8000` (run from repo root) then open `http://localhost:8000`
  - Or use VS Code Live Server extension / other static-server tools.
- No npm, no `package.json`, no build step — editing HTML/CSS/JS and refreshing browser is the main dev loop.

## Architecture & important patterns 🔧
- Pages are pure HTML with inline `<style>` and small scripts at the bottom of each file. Prefer adding styles inline when matching current style.
- Interactive/visual effects use Three.js via CDN (e.g., star fields in `GEO.html`, `bagphysics.html` and meteor animation in `index.html`). When modifying visual code, reuse existing CDN version and patterns.
- Navigation is manual (relative links between files). Keep links relative and update them when adding/removing pages.
- Right-to-left (RTL) & Arabic content: pages use `lang="ar"` and some use `dir="rtl"` (e.g., `index.html`). Ensure `lang` and `dir` are set appropriately for new pages.

## Project-specific conventions 📝
- Font: use Google Font `Cairo` to maintain consistent typography.
- Icon and libraries: use CDN-hosted FontAwesome and Three.js (consistent with existing code).
- Styling: current codebase prefers component-level inline `<style>` blocks rather than separate CSS files — follow that pattern for small pages. If adding a shared stylesheet, document it in this file and update all pages.
- Filenames: many assets and PDFs use Arabic names and spaces. Avoid renaming files unless you update every relative link; prefer adding new files with ascii-safe names if you expect external tooling to process filenames.
- Accessibility: keep `alt` attributes on images (existing pages include them) and titles on links/buttons.

## Editing / PR checklist ✅
- Run the site locally and verify changes in a browser (use localhost server above).
- Check that relative links to `image/` and `pdf/` work and open files in a browser.
- Ensure `lang="ar"` and `dir="rtl"` present where appropriate and text direction looks correct.
- Keep CDNs consistent (use the existing versions unless there is a clear reason to upgrade).
- If adding JS visual effects, test on a low-power machine and mobile (Three.js scenes can be heavy); use `requestAnimationFrame` throttling or smaller geometry counts where necessary.
- Add only discoverable changes in PR description — mention files changed and the manual verification steps used.

## Deployment & CI notes ⚠️
- There is no CI or Actions currently. For simple publish, GitHub Pages (branch `main` or `gh-pages`) is suitable for hosting this static site.
- If you add automated checks (link check, HTML linter), document them in this repo and update this file.

## When you're unsure / feedback
- If changes require renaming assets or introducing new tooling, open a PR and describe the rationale and the exact manual steps to verify.

---
If anything in this guidance is unclear or incomplete, tell me which sections you'd like expanded or give examples of changes you plan to make and I'll update this file accordingly.