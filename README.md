# Garage Alchemy

Garage Alchemy is a practical workshop for testing useful ideas, everyday AI, automation, local hardware, and human–AI collaboration.

> Take AI into the garage and see if it actually works.

## Live site

https://garage.dia.net.au/

## What is here

- `index.html` — the current static site
- `style.css` — site styling and responsive layout
- `assets/` — public branding and social preview assets
- `images/` — workshop and project imagery used by the site
- `compose.yaml` — a small Apache container for local preview
- `GARAGE-ALCHEMY-HANDOVER.md` — detailed project handover and maintenance notes
- `PROJECT-JOURNAL.md` — decisions, experiments, and lessons worth carrying into future episodes

## Run locally

With Docker Desktop running:

```powershell
docker compose up -d
```

Then open http://localhost:8085/.

To stop the preview:

```powershell
docker compose down
```

## Project status

This is an active, deliberately practical project. The site is maintained incrementally as the Garage Alchemy workflow develops.

## Licence and asset note

The website source code is released under the MIT License; see [`LICENSE`](LICENSE).

The written content, brand identity, and visual assets may have separate copyright or usage terms. Do not assume that an image or third-party asset is reusable merely because it appears in this repository. Where an asset has a separate licence or attribution requirement, that information should be recorded alongside the asset.

## Contributing

Useful experiments, corrections, and improvements are welcome. Please explain what was tested, what happened, and any limitations discovered.
