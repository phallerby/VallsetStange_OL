# Technical Plan – Vallset/Stange One‑Pager

## Overview
This site uses the existing **Ananke** Hugo theme with local overrides. We keep the theme intact and implement all design changes through:
- A custom homepage template in `layouts/index.html`.
- Custom CSS in `assets/ananke/css/custom.css`.
- Static assets in `static/images/` (logo, hero background, sponsors).

This approach keeps the theme upgradable while allowing a fully bespoke one‑page layout.

## Key Customizations
1) **Homepage override**
   - File: `layouts/index.html`
   - Implements the full one‑pager layout (hero, sections, CTAs, contact, etc.).
   - Uses anchor links for section navigation.

2) **Custom styling**
   - File: `assets/ananke/css/custom.css`
   - Uses the `custom_css` setting in `hugo.toml` to inject this stylesheet.
   - Defines typography (Outfit), color palette, spacing, buttons, and nav behavior.

3) **Transparent → white navigation**
   - A small JS snippet in `layouts/index.html` toggles the `.scrolled` class
     on the nav when the page scrolls.
   - CSS handles the visual change (transparent over hero, white after scroll).

4) **Static assets**
   - Folder: `static/images/`
   - Includes:
     - `logo.png`
     - `hero.jpg`
     - `forest.jpg`
     - `sponsors/` logo files

5) **Hugo configuration**
   - File: `hugo.toml`
   - Sets `custom_css`, `site_logo`, and disables recent posts.

## Local preview
Run locally with:
```
hugo server --baseURL http://localhost:1313/ --appendPort=false
```
Open:
```
http://localhost:1313/
```

## Deployment
The site is deployed via **GitHub Actions**. On every push to `main`, the workflow:
1) Builds the site with Hugo
2) Uploads `public/`
3) Deploys to GitHub Pages

Workflow file:
- `.github/workflows/hugo.yml`

## Files to edit for future changes
- Layout: `layouts/index.html`
- Styles: `assets/ananke/css/custom.css`
- Images: `static/images/`
- Site config: `hugo.toml`
