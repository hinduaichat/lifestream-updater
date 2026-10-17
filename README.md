# LifeStream Content Updater

This public repository contains **only** the scheduled automation that keeps
the LifeStream website's data fresh. No application code, no data, no secrets.

- **Every 2 days** (06:00 UTC) plus a manual run button, the workflow
  `.github/workflows/update-content.yml` checks out the website repository,
  runs the ingest pipeline (`npm run update` — new movies, TV, anime and
  episode playlists), and commits any new `data/*.json` files back.
- The website repo's Vercel integration auto-deploys on every push, so new
  content appears without any manual work.

## Credentials

The GitHub personal access token and the website repo slug are **GitHub
Actions secrets only** (`GH_PAT`, `WEBSITE_REPO`) — set in
*Settings → Secrets and variables → Actions*. They are never echoed into
logs and never stored in any file in this repository.
