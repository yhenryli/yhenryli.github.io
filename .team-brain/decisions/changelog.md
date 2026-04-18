# Changelog

## 2026-04-18 — Multilingual site support (EN / FR / ZH / FI)

**Context:** User requested adding French, Chinese (Simplified), and Finnish language versions alongside the existing English site. No prior architectural plan from Antigravity existed in `/.team-brain/plans/` for i18n, so Claude Code made the design decision independently and is logging it here for Antigravity's awareness.

**Approach chosen:** Client-side i18n in a single `index.html`, not separate per-language HTML files or URL subpaths.

- Language keys stored as `data-i18n="section.key"` attributes on translatable elements.
- Translations live in a nested `I18N` object inside the existing `<script>` block (no build step, no external JSON fetch — matches the "single-file static site hosted on GitHub Pages" shape).
- Floating glass pill at top-right with buttons for `EN / FR / 中文 / SUOMI`.
- Preference persisted to `localStorage['site-lang']`.
- Initial language resolution: saved preference → `navigator.language` prefix match → `en`.
- Script also updates `<html lang="...">` and `<title>` to match the active language.

**Tradeoffs / limitations to flag:**

1. **No separate URLs per language.** A future SEO-oriented rewrite may want `/fr/`, `/zh/`, `/fi/` subpaths with `hreflang` tags so crawlers index each language. Deferred — portfolio reach is not primarily organic search.
2. **Publication list entries in "Selected Work" are intentionally left in English.** The links point to English articles (Uber Eng blog, Bigeye blog, PLOS, AoAS, VentureBeat, etc.), so translating their titles would misrepresent what the user will land on. Group/section headings around them *are* translated.
3. **Proper nouns kept in original form** across all languages: "Henry Li", institution names (Stanford, UC Berkeley, LBNL), company names (Uber, Bigeye, Nova AI, JB Hi-Fi, Zoom, Confluent, Instacart), professor names, journal names. Standard academic convention.
4. **Brief FOUC on first paint** for non-English users: HTML ships with English text, JS swaps it on `DOMContentLoaded`. Acceptable for a portfolio; a `<script>` in `<head>` could eliminate it if needed.

**Files touched:**
- `index.html` — added `data-i18n` attributes, lang-switcher pill markup + CSS, and the `I18N` translations object + switcher logic in the existing `<script>`.

If Antigravity later drafts a canonical i18n plan (e.g., moving to per-locale files, adding RTL languages, or restructuring translations as extracted JSON), the current implementation can be refactored from a single well-scoped location.
