# Burbach
Burbach Companies

## Projects

- [**Bait Station**](bait-station/) — a Donkey Kong-style climber played as a
  house mouse in a house that has just been treated. Open
  `bait-station/index.html` to play.
- [**Blasting Kidney Stones**](blasting-kidney-stones/) — an Asteroids-style
  browser game. Open `blasting-kidney-stones/index.html` to play.

## Hosting

`.github/workflows/pages.yml` publishes this repo to GitHub Pages on every push
to `main`, serving the landing page at the site root and the games beneath it.

The workflow needs Pages pointed at it once, by hand: **Settings → Pages →
Build and deployment → Source → GitHub Actions**. Until that is set the workflow
run fails at the deploy step. After that, pushes to `main` publish on their own:

- `/` — landing page
- `/bait-station/` — Bait Station
- `/blasting-kidney-stones/` — Blasting Kidney Stones
