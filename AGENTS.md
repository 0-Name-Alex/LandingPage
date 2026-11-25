# LandingPage (`dhayananth.me`) — AI Agent Guide

Personal engineering hub and project link index served via **GitHub Pages + Cloudflare DNS** at [`dhayananth.me`](https://dhayananth.me) (`0-Name-Alex/LandingPage`).

## 1. Key Files & Schema
- [`links.json`](links.json): Single source of truth for all project cards rendered on the page. Schema:
  ```json
  {
    "links": [
      {
        "id": "unique-slug",
        "title": "Project Display Name",
        "url": "https://github.com/0-Name-Alex/<repo>",
        "category": "Connect & Profiles | Energy & AI Research | Software & Hardware Projects",
        "description": "Concise stack & capability summary"
      }
    ]
  }
  ```
- [`index.html`](index.html): Self-contained vanilla JS / HTML / CSS UI that fetches `links.json` (with grep search, category filters, and built-in GitHub API token editor `sudo`). Configured for `MANUAL = { owner: "0-Name-Alex", repo: "LandingPage", branch: "main" }`.
- [`CNAME`](CNAME): Keeps custom domain `dhayananth.me` active on GitHub Pages—never delete or overwrite.

## 2. Deployment & Validation Rules
- Validate JSON syntax before pushing:
  ```powershell
  python -c "import json; json.load(open('links.json', encoding='utf-8'))"
  ```
- Verify every new `url` in `links.json` returns HTTP 200 (public repository or live GitHub Pages/Vercel URL).
- Push directly to `main` (`0-Name-Alex <0-Name-Alex@users.noreply.github.com>`); GitHub Pages redeploys automatically within ~1 minute.
