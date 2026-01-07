# Copilot / AI Agent Instructions — Seven Seas Spa

Summary

-   Small static website (HTML/CSS only) using Bootstrap via CDN. No build, server-side code, or tests in repository.

Quick orientation

-   Entry points: `index.html`, `about.html`, `contact.html`, `thankyou.html`.
-   Static assets: `assets/css/styles.css`, `assets/images/*`.
-   External deps: Bootstrap CSS/JS and Bootstrap Icons (CDN), Google Fonts (Handlee) — see top of each HTML head.

What to expect and why

-   This project is a simple multi-page static site. Pages contain repeated header/footer markup rather than templates — prefer small, backward-compatible edits.
-   The contact form is client-side only and uses `form action="thankyou.html"` (no backend). Changing this behavior requires adding a server endpoint or JavaScript to submit to a backend/API.

Developer workflows (local testing & quick checks)

-   Preview locally:
    -   Recommended: use the VS Code Live Server extension (right-click an HTML file -> "Open with Live Server").
    -   Alternate: run a simple HTTP server from the repo root: `python -m http.server 8000` then open `http://localhost:8000`.
-   Manual checks to run after edits:
    -   Verify image paths and CSS loads (inspect `assets/images/*`, `assets/css/styles.css`).
    -   Submit the contact form and confirm it navigates to `thankyou.html`.
    -   Open browser devtools -> Console/Network for CDN or integrity errors.
    -   Run Lighthouse accessibility/SEO checks for production readiness.

Project-specific conventions & gotchas

-   Relative asset linking is strict: use `assets/...` paths from the HTML root. Example: hero background in `assets/css/styles.css` references `url("../images/hero.png")`.
-   Styling notes: headings use the Handlee font (declared in HTML head and applied in `styles.css`).
-   Navbar/footer are duplicated across pages and sometimes use different classes (e.g., `navbar-custom` present in `index.html` and `contact.html`, absent in `thankyou.html`). Be careful to keep the Nav active-state (`.nav-link.active`) consistent when editing.
-   Accessibility: pages already include ARIA attributes (social links, carousel role/aria-labels) and `tabindex` on interactive elements — preserve or improve these when changing markup.

Adding features or refactors (practical examples)

-   If adding a backend for the contact form:
    -   Replace `form action="thankyou.html"` with `action="/api/contact" method="post"` and add server-side logic or a hosted form endpoint.
-   If converting to a templating system (e.g., Jekyll, Eleventy): extract header/footer into includes/partials to remove duplication and reduce risk of inconsistent nav/branding.

Deployment notes

-   Repository contains no deployment configs. Quick option: enable GitHub Pages (Settings → Pages) and serve from the `main` branch root — supports static HTML directly.
-   Ensure any CDN integrity attributes and external links remain correct after deployment.

When in doubt (how you should act as an AI agent)

-   Make minimal, reversible changes for small fixes (update styles, fix paths, adjust ARIA). Keep changes in a single commit and include a short description.
-   For larger changes (templating, adding an API), propose a short plan and request confirmation before implementing (outline files to change and a migration strategy).

Files worth opening first

-   `index.html` — primary layout, hero, services, testimonials carousel
-   `contact.html` — contact form behavior and example of form markup
-   `assets/css/styles.css` — site-specific CSS rules (fonts, hero background, footer)

Questions for the repo owner

-   Would you prefer converting duplicated header/footer into templating/includes for maintainability?
-   Do you plan to add a server/API for the contact form, or should we keep it static?

If anything above is unclear or you'd like me to expand a section (deployment, API design, templating) tell me which part to expand and I will iterate. ✅
