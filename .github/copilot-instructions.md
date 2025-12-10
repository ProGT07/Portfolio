<!-- .github/copilot-instructions.md - Guidance for AI coding agents -->
# Repo summary

- Single-page static portfolio site. Entrypoint: `index.html` at repository root.
- Styling lives in `index.css`. Small JS behavior in `index.js`. Assets under `fonts/` and `images/`.
- No build system or dependencies detected: this is plain HTML/CSS/JS (no npm, webpack, or task runner).

# How to be productive (actions you can take)

- Edit content directly in `index.html` for text, headings, and the project blocks (`.work__box`). The `README.md` contains examples of placeholder HTML comments used for owner-specific edits.
- Update styles in `index.css`. Preserve the CSS design tokens defined in `:root` (font sizes, colors, container widths) and the `@font-face` declarations at the top (fonts reference `fonts/`).
- Update or add assets in `images/` and reference them with `./images/<name>`; keep project screenshots similar in size for layout consistency (recommended in `README.md`).
- Small interactive behavior belongs in `index.js`. Follow the existing pattern: minimal DOM API usage, attach event listeners on `window` and `document`, and avoid frameworks.

# Running / previewing locally

- This repo has no build step — open `index.html` in a browser for a quick preview.
- For a proper static server (recommended to avoid file:// path issues), use one of these from PowerShell:

```powershell
# Python (if installed):
python -m http.server 8000

# Or using Node (if you have Node):
npx serve -s . -l 5000
```

# Key patterns & notes for edits

- Semantic HTML: the page uses `header`, `main`, `section`, and `footer`. Keep these roles when refactoring to preserve accessibility.
- Accessibility pattern: `index.js` toggles a `user-is-tabbing` body class to control focus outlines. Example behavior: the first `Tab` press adds `user-is-tabbing` and mouse down removes it — follow this unobtrusive approach for new keyboard-focus features.
- Back-to-top: `index.js` contains a scroll listener and an `alterStyles` helper that toggles `.back-to-top` visibility. When adding scroll-based features, reuse the same visibility approach to keep consistent animation/timing.
- CSS variables: many layout and color tokens live in `:root`. Prefer using these variables over hardcoding values to preserve global theming.
- Fonts: `index.css` declares `@font-face` pointing to `fonts/HKGrotesk-Regular.woff` and `fonts/Jost-Regular.ttf`. If replacing fonts, update both `@font-face` and usages of `--font-stack`.

# Files to inspect for examples

- `index.html` — entrypoint; see `.work__box` blocks (project entries) and HTML comments in `README.md` describing where to edit.
- `index.css` — large centralized stylesheet using CSS variables and responsive media queries (root font-size scaling technique: `html { font-size: 62.5%; }`).
- `index.js` — small vanilla JS for keyboard focus and back-to-top behavior. New JS should follow this minimal, dependency-free style.
- `README.md` — contains editing instructions and markup examples; consult it for copy/content conventions (project image sizing, placeholder comments).

# What we did NOT find (so mention when adding features)

- No tests, linters, or CI workflows present. If you add build tooling, tests, or formatting/linting, also add a README section and CI config files so future agents can detect them.
- No `.github/` templates or Issue/PR templates — keep PRs small and descriptive until templates are added.

# Integration & external dependencies

- No external API integrations are present in code. Some content references (e.g., resume PDF and external links) are static.
- Be careful when adding dependencies: this repository is intentionally dependency-free. If Node/npm is added, update `README.md` with install and run commands.

# Guidance for changes & PRs

- Small, focused commits. When modifying layout or global variables, include a short preview instruction in the PR description (how to preview locally using `python -m http.server 8000`).
- When changing asset paths, update usages across `index.html`, `index.css`, and any inline `src` attributes.

# If something is unclear

- Ask for clarification and indicate which file and line-range you need help with (e.g., "index.css top @font-face block").
- If proposing a build system or major restructuring, provide a migration plan and keep the existing static site runnable during the transition.

-- End of guidance

If you want I can refine any section (add examples of `work__box`, show the exact `index.js` snippet to copy-pattern, or include PR templates). Please tell me which parts need more detail.
