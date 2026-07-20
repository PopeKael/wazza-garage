# Garage Alchemy — Project Handover

Updated: 20 July 2026

## Immediate objective

Move this static website from the UNC workspace into a normal local project folder, then establish a clean Git repository with a GitHub remote and a simple backup routine.

The live site is:

- https://garage.dia.net.au/

The current UNC source is:

- `\\KStore\\web\\site\\garage`

## Current site

Garage Alchemy is a cinematic, long-scroll static website for a practical digital workshop. It presents useful ideas, real-world experiments, media, people, systems, and places without presenting Warren as a corporate consultant or résumé subject.

The site is served by an Apache container behind an existing reverse proxy. There is no npm project, build step, framework, or application runtime.

The container configuration is in `compose.yaml`:

- Docker image: `httpd:2.4`
- Container name: `garage`
- Local container port: `8085`
- Site files mounted read-only into Apache’s document root

## Main files

- `index.html` — complete page markup, metadata, navigation, video data, and the small click-to-load YouTube script
- `style.css` — all layout, typography, responsive behaviour, overlays, card components, focus states, reveal effects, and reduced-motion rules
- `compose.yaml` — Apache container definition
- `assets/garage-alchemy-og.png` — social/link preview image
- `assets/garage-favicon.svg` — Garage Alchemy browser tab icon
- `assets/garage-alchemy-hero.png` — existing hero asset, retained and not deleted
- `images/` — original visual asset library; source files have not been renamed, moved, cropped, or deleted

## Page structure

The current page contains these sections and anchors:

1. Hero — Garage Alchemy
2. `#manifesto` — The right tools and the right people
3. `#workbench` — Projects and experiments
4. `#open-workshop` — Channels, community, and collaboration
5. `#field-notes` — Places & Things / featured video archive
6. `#closing` — Around the Workshop / A few doors worth opening

The navigation links to the major sections. The design is intentionally editorial and cinematic rather than corporate.

## Content currently represented

### Hero

The landing message is centred and currently uses this direction:

> Ideas are only useful when you take them into the garage.

Supporting ideas include technology, media, people, practical curiosity, and the line:

> A place to share your ideas.

### Workbench cards

The reusable project-card system currently contains temporary, honest entries for:

- Practical AI and local computing
- Knowledge Vault and information systems
- Websites, automation, and infrastructure
- Photography and media enhancement
- Prototypes and experiments

These do not claim invented achievements, clients, statistics, credentials, or outcomes.

### Open Workshop cards

The reusable media-card system currently provides room for:

- Chanya & Wazza — Life in Thailand
- Garage Alchemy — Pope Kael
- Community meetups
- Videos and small projects for friends and local people

### Places & Things video archive

There are nine featured YouTube entries, grouped as:

- Life in Thailand
- Bangkok After Dark
- Garage Alchemy / Pope Kael

Each entry has a real public title, description, category label, thumbnail, accessible link/button, and play control. The page does not load nine YouTube iframes on startup. A privacy-enhanced `youtube-nocookie.com` iframe is created only after the visitor activates a video.

On wide desktop, the entries alternate consistently:

- thumbnail left, text right
- thumbnail right, text left
- thumbnail left, text right

This continues through all three groups. On intermediate widths the entries stack to avoid narrow vertical columns. On mobile they use a single-column layout with controlled 16:9 thumbnails.

## Visual assets

The `images/` directory contains the original generated workshop backgrounds and related visual material. Existing source images must be preserved. The current page maps these backgrounds to the major sections with dark overlays and responsive background positioning.

The social preview image is:

- `assets/garage-alchemy-og.png`
- 1672 × 941 PNG
- Used by the Open Graph and Twitter metadata

The favicon is:

- `assets/garage-favicon.svg`
- Compact dark/orange Garage Alchemy mark designed for browser tabs

## Accessibility and responsive behaviour

The page currently includes:

- semantic sections, headings, articles, navigation, and links
- logical heading order
- accessible labels for video and destination controls
- visible keyboard focus states
- responsive desktop, intermediate-width, tablet, and narrow-mobile rules
- mobile-safe background cropping
- no autoplay video
- lazy-loaded video thumbnails
- click-to-load embedded media
- scroll-reveal effects only when JavaScript is available
- reduced-motion support
- no external framework or heavy animation library

## HTTPS diagnosis

The page itself was checked for mixed-content references. The served HTTPS HTML and CSS contained no plain `http://` resource URLs, and the CSS, favicon, and OG image loaded successfully over HTTPS.

A certificate-name error was previously observed. After a new certificate was created, the public HTTPS endpoint now returns HTTP 200 and certificate validation succeeds.

One reverse-proxy issue remains: `http://garage.dia.net.au/` still returns the page directly with HTTP 200 instead of redirecting to HTTPS. Configure the proxy to return a permanent redirect from HTTP to HTTPS. This is a proxy configuration task, not an `index.html` or `style.css` task.

Recommended order:

1. Confirm the certificate includes `garage.dia.net.au` in its SANs.
2. Confirm the reverse proxy selects that certificate for this hostname.
3. Configure HTTP → HTTPS as a `301` redirect.
4. Confirm both IPv4 and IPv6 routes use the same correct certificate.
5. Add HSTS only after HTTPS is consistently working.

## Repository state

The folder contains a `.git` directory, but it is empty or otherwise not recognised as a usable Git repository. There is no confirmed branch, commit history, or GitHub remote in the current UNC copy.

Treat the current UNC folder as the working source, not as a reliable backup.

## Recommended local migration

Use a normal local path such as:

```powershell
New-Item -ItemType Directory -Force -Path 'C:\Users\Warren\Projects\garage-alchemy'
robocopy '\\KStore\web\site\garage' 'C:\Users\Warren\Projects\garage-alchemy' /E /COPY:DAT /R:2 /W:2 /XD .git
```

Review the copied files before creating Git history. Do not copy the empty `.git` directory.

Then initialise the new repository:

```powershell
Set-Location 'C:\Users\Warren\Projects\garage-alchemy'
git init -b main
git add index.html style.css compose.yaml assets images
git commit -m "Initial Garage Alchemy static site"
```

Create an empty private GitHub repository named something like `garage-alchemy`, then connect and push it:

```powershell
git remote add origin https://github.com/YOUR-ACCOUNT/garage-alchemy.git
git push -u origin main
```

Do not commit certificates, private keys, passwords, tokens, local secrets, or unrelated personal files. The current site files do not require secrets.

## Suggested backup hierarchy

Keep three distinct layers:

1. Live site — the Apache-served copy behind the reverse proxy.
2. Local working repository — the copy edited in Codex or an editor.
3. GitHub remote — version history and off-machine backup.

After each meaningful change:

```powershell
git status
git diff --check
git add index.html style.css assets images compose.yaml
git commit -m "Describe the change"
git push
```

The live UNC copy should be updated deliberately from the reviewed local copy, not treated as the source of truth forever.

## Future maintenance notes

- Keep the site static unless a real requirement justifies adding a framework or build system.
- Edit `index.html` and `style.css` for normal page work.
- Preserve the `images/` source library.
- Preserve the click-to-load YouTube behaviour.
- Use real metadata when adding videos; do not invent titles, descriptions, achievements, or outcomes.
- Recheck wide desktop, intermediate resize states, and narrow mobile after layout changes.
- Recheck HTTPS, redirects, favicon, OG image, anchor navigation, and image requests after deployment.

## Next practical step

Copy the project to a local folder excluding `.git`, initialise a fresh Git repository there, make the first commit, and push it to a new private GitHub repository. Keep this handover file in the repository as the project’s operating note.

