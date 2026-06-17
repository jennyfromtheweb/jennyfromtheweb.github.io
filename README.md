# Jenny Li — UX Research Portfolio

A static portfolio site, built as plain HTML/CSS (no build step, no dependencies) so it can be hosted directly on GitHub Pages.

## Structure

```
index.html                          → homepage (bio + case study index)
work/
  rubrik-saas-zero-to-one.html      → Case 01
  rubrik-admin-diary-study.html     → Case 02
  nhi-research.html                 → Case 03
  jabel-redesign.html               → Case 04
assets/
  css/style.css                     → the entire design system (colors, type, components)
  images/                           → all case study images, organized by project
```

## Previewing locally

No build step needed. Either:
- Open `index.html` directly in a browser, or
- Run a local server from this folder so relative paths behave exactly like they will on GitHub Pages:
  ```
  python3 -m http.server 8000
  ```
  then visit `http://localhost:8000`.

## Deploying to GitHub Pages (project subpage)

This site is built to live at a **project subpage** — `https://<your-username>.github.io/<repo-name>/` — using relative paths throughout, so it works regardless of the repo name you choose.

1. Create a new repository on GitHub (e.g. `portfolio`).
2. Push the contents of this folder to the repository's default branch (`main`):
   ```
   git init
   git add .
   git commit -m "Initial portfolio site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/<repo-name>.git
   git push -u origin main
   ```
3. In the repo on GitHub: **Settings → Pages → Build and deployment → Source → Deploy from a branch**, then select `main` and `/ (root)`.
4. Save. GitHub will give you a live URL within a minute or two, at `https://<your-username>.github.io/<repo-name>/`.

If you'd rather host this at the **root** of your GitHub Pages account (`https://<your-username>.github.io/`), name the repository exactly `<your-username>.github.io` — everything else works the same, since all links are relative.

## Editing content

- **Text:** edit directly in the relevant `.html` file — there's no templating, so each page is self-contained.
- **Images:** stored as `.webp` (optimized for web). To swap one out, replace the file in `assets/images/<project>/` and keep the filename, or update the `src` in the matching `<img>` tag.
- **Colors / fonts / spacing:** all defined as CSS variables at the top of `assets/css/style.css` under `:root` — change a value there and it updates everywhere.
- **Adding a new case study:** copy an existing file in `work/`, update its content, then add a new row to the case list in `index.html` and update the "previous/next" links in the two adjacent case study pages.

## Notes

- Fonts (Fraunces, Source Serif 4, IBM Plex Mono) load from Google Fonts via `<link>` tags — no local font files to manage.
- The site has no JavaScript dependencies and no analytics. If you want visitor analytics, you'd add a snippet (e.g. Plausible, GoatCounter) to the `<head>` of each page.
