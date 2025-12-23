# Project Guidance: sifat-ahmed.github.io

## Overview
This is a static personal website hosted on GitHub Pages. It is built from plain HTML, CSS, and JavaScript, with shared navbar/footer includes and a Unity WebGL game page. There is no build system or package manager. Changes are made by editing files directly in the repository.

## Site Structure
- Root HTML pages:
  - `index.html`: About page and landing content.
  - `research.html`: Publications and research list.
  - `projects.html`: Projects portfolio with images and links.
  - `activities.html`: Timeline of activities and milestones.
  - `vitae.html`: Embedded CV content (currently includes a OneDrive embed).
  - `game.html`: Unity WebGL player page.
- Shared includes:
  - `navbar.html`: Primary navigation links.
  - `footer.html`: Footer and social links.
- Assets:
  - `css/main.css`: Global styling and layout rules.
  - `css/teaching-panels.css`: Panel styles used by activities content.
  - `js/main.js`: UI behavior (top button, read-more toggle, tooltips).
  - `js/w3data.js`: HTML include helper for navbar/footer.
  - `img/`: Images, GIFs, and a PDF CV.
  - `favicons/`: Site icons and manifest files.
- Unity WebGL build:
  - `Build/`: Unity build artifacts (loader, data, wasm, json).
  - `TemplateData/`: Unity WebGL template assets and CSS.

## Shared Layout Pattern
All main pages include:
- External libraries (Bootstrap 3.4.1, jQuery 3.3.1, jQuery UI theme).
- Google fonts (Open Sans, Montserrat), Font Awesome, Academicons.
- `css/main.css` for site-wide styling.
- `js/w3data.js` and `w3IncludeHTML()` to load `navbar.html` and `footer.html`.
- `js/main.js` for common UI interactions.

When adding new pages, follow the same pattern to keep styling and navigation consistent.

## Navigation and Page Activation
- Navbar is defined in `navbar.html`.
- Each page highlights its active nav item using a jQuery snippet in the page body. Example:
  - `index.html` adds classes to `li#about a`.
  - `projects.html` adds classes to `li#projects a`.
- If you add a new page, update `navbar.html` and add a similar active state snippet.

## Content Update Guide
### About (index.html)
- Update bio text, education, and skills directly in the HTML.
- The read-more section is toggled by `#badge-more` in `js/main.js`.

### Research (research.html)
- Update publication lists in the `ul.publications` sections.
- Keep the same list structure for consistent styling.

### Projects (projects.html)
- Each project is an `li` with an image and tool list.
- Images referenced from `img/` or external URLs.
- Keep image sizes reasonable to avoid layout overflow.

### Activities (activities.html)
- Timeline entries are grouped by year with repeated `ul` blocks.
- Uses `css/teaching-panels.css` for panel styling.

### Vitae (vitae.html)
- Currently includes a OneDrive embed for the CV.
- There is a garbled text line in the file; consider removing or fixing it if not intentional.
- A PDF exists at `img/cv_sifat_ahmed.pdf` if you want to embed locally.

### Game (game.html)
- Unity WebGL player loads `Build/New folder.json` via `UnityLoader.js`.
- If you rebuild the Unity game, replace the files in `Build/` and `TemplateData/`.

## Styling Notes
- Global typography and colors live in `css/main.css`.
- Many elements use the Montserrat font by default.
- Body text and layout are tuned for a narrow container on larger screens.
- Activity lists use `list-style: circle` from `main.css`.

## SEO and Hosting
- `CNAME` points the site to `sifat-ahmed.com` for GitHub Pages.
- `robots.txt` allows all crawlers and links to the sitemap.
- `sitemap.xml` currently lists only the homepage and is outdated.
  - Update it if you add pages or want accurate indexing.
- `.htaccess` enforces HTTPS on servers that support it (not used by GitHub Pages).

## External Dependencies
These are loaded from CDNs on each page:
- Bootstrap 3.4.1 CSS and JS.
- jQuery 3.3.1.
- jQuery UI theme CSS.
- Font Awesome 5.8.1.
- Academicons.
- Google Fonts.

If you need offline hosting, download these assets and update the references.

## Common Tasks
### Add a new page
1. Copy the structure from an existing page (head, navbar include, footer include, scripts).
2. Add a nav item to `navbar.html`.
3. Add an active state script block for the new nav item.
4. Add the page to `sitemap.xml`.

### Update images
- Place new images in `img/`.
- Reference them with relative paths (example: `img/new-image.png`).

### Update the Unity game
- Replace `Build/` files and `TemplateData/` assets with the new Unity WebGL build.
- Keep `game.html` pointing at the correct build JSON file.

## Known Issues and Checks
- `vitae.html` contains a line of unreadable characters; confirm if this is intentional.
- `sitemap.xml` is outdated (lastmod 2019). Consider updating.
- Mixed use of absolute (`/android-icon-192x192.png`) and relative favicon paths across pages. Keep consistent if you edit.

## Quick Reference
- Main styles: `css/main.css`
- UI behavior: `js/main.js`
- Navbar: `navbar.html`
- Footer: `footer.html`
- Game build: `Build/` + `TemplateData/`
- Images: `img/`