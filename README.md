# Burbach
Burbach Companies

## Projects

- [**Blasting Kidney Stones**](blasting-kidney-stones/) — an Asteroids-style
  browser game. Open `blasting-kidney-stones/index.html` to play.

## Hosting

`.github/workflows/pages.yml` publishes this repo to GitHub Pages on every push
to `main`, serving the landing page at the site root and the game beneath it.

The workflow needs Pages pointed at it once, by hand: **Settings → Pages →
Build and deployment → Source → GitHub Actions**. Until that is set the workflow
run fails at the deploy step. After that, pushes to `main` publish on their own:

- `/` — landing page
- `/blasting-kidney-stones/` — the game
