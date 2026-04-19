# Tech Stack & Constraints

This file is the source of truth for architectural constraints. All plans and edits must respect these.

## Deployment
- **Host:** GitHub Pages, served from the `main` branch of `yhenryli.github.io`.
- **Custom domain:** configured via `CNAME` at repo root.
- **No build step.** The site is served as-is — no bundler, no transpiler, no CI build. What's in the repo is what ships.

## Code shape
- **Single-file site:** the entire portfolio lives in `index.html` at the repo root. HTML, CSS (inline `<style>`), and JS (inline `<script>`) are all in that one file.
  - Do **not** split into separate `.css` / `.js` files without an explicit decision logged in `./.team-brain/decisions/changelog.md`.
- **Assets:** static images live at repo root (e.g., `hl_profile_pic.png`).
- **No framework:** vanilla HTML/CSS/JS only. No React, Vue, Svelte, jQuery, Tailwind, etc.
- **External deps:** limited to CDN-loaded Google Fonts (`Manrope`, `Inter`). Do not add npm packages or script CDNs without approval.

## Design system
- Named "Kinetic Euphoria" — warm-cream background with leaf-green / wildflower-violet / sun-gold accents, animated mesh-gradient backdrop, glassmorphic pills.
- CSS custom properties defined in `:root` at the top of the `<style>` block are the canonical design tokens. Reuse them; don't introduce ad-hoc colors.

## Internationalization
- **Client-side i18n** inside the single `index.html`. No per-language HTML files, no URL subpaths.
- Translatable elements carry a `data-i18n="section.key"` attribute.
- Translations live in a nested `I18N` object inside the inline `<script>`.
- Supported languages: English (`en`), French (`fr`), Chinese Simplified (`zh`), Finnish (`fi`).
- Language switcher: floating glass pill (top-right) with `EN / FR / 中文 / SUOMI` buttons.
- Preference persisted in `localStorage['site-lang']`. Initial resolution: saved preference → `navigator.language` prefix match → `en`.
- **Do not translate:** proper nouns (names, institutions, companies, journals) or the titles of linked publications in "Selected Work" (the links point to English articles).

## Content ownership
- Site owner: Henry Li — Statistician / Data Scientist / AI Engineer.
- Sections: About, Industry, Academic, Selected Work, Contact.
- Tone is personal and professional — match existing copy when adding new sections.
