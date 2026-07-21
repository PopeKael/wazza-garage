# Garage Alchemy — Conversation Record

**Date created:** 2026-07-21  
**Project:** Garage Alchemy / Pope Kael TV  
**Local workspace:** `D:\Downloads\Websites\garage`  
**GitHub repository:** <https://github.com/PopeKael/wazza-garage>  
**Local preview:** <http://localhost:8085/>

> This is a readable record of the collaboration. Ambient browser metadata and raw internal tool payloads are omitted; the resulting actions and outcomes are recorded below.

---

## 1. Initial handover reference

### User

Referenced:

`W:/site/garage/GARAGE-ALCHEMY-HANDOVER.md`

No specific action was included in the first message.

### Assistant

Asked what should be done with the handover file.

---

## 2. Replicating the UNC/mapped source locally

### User

Explained that the handover reference was continuing an earlier workflow. The source project was currently on a UNC path, and the desired process was:

1. Replicate the project into the local workspace.
2. Create a GitHub repository backup.
3. Proceed later to publishing.

### Assistant

Confirmed that the UNC-hosted site would be treated as the source of truth and that the project would be copied into the local workspace while preserving the existing local state.

### Actions and results

- Source inspected at `W:\site\garage`.
- Local destination inspected at `D:\Downloads\Websites\garage`.
- The local destination was empty.
- Source contents included:
  - `.agents`
  - `.codex`
  - `assets`
  - `images`
  - `compose.yaml`
  - `GARAGE-ALCHEMY-HANDOVER.md`
  - `index.html`
  - `style.css`
- The project was copied locally.
- Source `.git` metadata was excluded so a clean Git repository could be created locally.
- `.agents` and `.codex` were preserved.
- SHA-256 verification confirmed that all copied project files matched the source.

### Assistant

Reported that the project had been replicated at:

`D:\Downloads\Websites\garage`

The local copy was ready for GitHub setup.

---

## 3. Choosing the GitHub repository

### User

Asked whether a GitHub repository link could be pasted into the conversation.

### Assistant

Confirmed that the repository link could be pasted, or that the GitHub owner, repository name, and visibility could be supplied if the repository did not yet exist.

### User

Provided:

<https://github.com/PopeKael/wazza-garage>

### Assistant

Used the GitHub publishing workflow to inspect the local project and remote repository before committing and pushing.

### Actions and results

- Confirmed that `PopeKael/wazza-garage` existed.
- Confirmed that it was initially private and empty.
- Confirmed write access through the connected GitHub account.
- GitHub CLI was not installed locally, so the connected GitHub capability and normal Git commands were used instead.
- Initialised a local Git repository on branch `main`.
- Created the first commit:

  `aec9e46 Back up Garage Alchemy website`

- Added the GitHub remote:

  `https://github.com/PopeKael/wazza-garage.git`

- Pushed `main` to GitHub.
- Verified that the remote branch pointed to commit `aec9e46`.
- Verified that the local working tree was clean.

### Assistant

Reported that the full project had been backed up successfully to the private GitHub repository.

---

## 4. Discussion of private versus public visibility

### User

Explained a strong preference for open source and sharing ideas, while recognising that passwords, security details, identity information, and similar material should remain private.

Mentioned the existing Adiariadne project and the two web projects, and raised the idea of a journaling process to track project decisions and experiments for future videos.

### Assistant

Explained the distinction between:

- Repository visibility: who can see the repository.
- Licensing: what others are legally allowed to do with the contents.

The recommendation was that these practical Garage Alchemy projects were suitable candidates for public repositories, subject to a quick audit.

Suggested public material:

- Website source code
- Public images and assets
- AI experiments and lessons
- Build notes and design decisions
- Sanitised video research

Suggested private material:

- Passwords and API keys
- Domain and server administration details
- Personal or sensitive journal material
- Raw Knowledge Vault data
- Private deployment configuration

The current Garage Alchemy repository was checked and had no `LICENSE` file at that point. The assistant explained that public visibility alone does not provide the normal open-source permissions.

For the journaling process, the assistant suggested a public `PROJECT-JOURNAL.md` or `docs/journal/` alongside the technical Git history.

---

## 5. Preparing the project for public release

### User

Asked to make the changes and present the project professionally, with a humorous reference to the Pet Shop Boys lyric about brains and looks.

### Assistant

Confirmed the plan to establish a professional public-release baseline:

- Audit the project.
- Add licensing and project documentation.
- Add a journal structure.
- Exclude Windows-generated clutter.
- Push the changes.
- Change the GitHub repository visibility to public.

### Files added or changed

#### `README.md`

Added:

- Project description and motto.
- Live site link.
- Repository structure.
- Local Docker preview instructions.
- Project status.
- Licence and asset-rights notes.
- Contributing guidance.

#### `LICENSE`

Added the MIT License for the website source code, with copyright attributed to Warren Gerdes / Garage Alchemy, 2026.

#### `.gitignore`

Added exclusions for:

- `Thumbs.db`
- `Desktop.ini`
- `.DS_Store`
- Local environment files and secrets.
- Logs and build output.

#### `PROJECT-JOURNAL.md`

Added:

- A public-facing project journal purpose statement.
- A warning not to place credentials, private information, unpublished material, or raw Knowledge Vault data in the public repository.
- A first entry recording the local migration, verification, GitHub backup, and public-release preparation.
- A reusable journal-entry template.

#### Windows metadata cleanup

The tracked `images/Thumbs.db` file was removed from Git tracking. The local source copy was left untouched, and the new `.gitignore` prevents future tracking.

### Commit and push

Created and pushed:

`ad3d812 Prepare project for public release`

---

## 6. Making the repository public

### User

Reported that they were logged into GitHub.

### Assistant

Returned to the GitHub repository settings and changed the visibility from private to public.

GitHub displayed the confirmation effects, including that the code would be visible to everyone, the repository could be forked, and activity and Actions history would be public.

### Verification

The GitHub repository metadata was rechecked and confirmed:

- Repository: `PopeKael/wazza-garage`
- Visibility: `public`
- Default branch: `main`
- Repository remained unarchived.

### Assistant

Reported that the repository was now public and that the professional baseline was in place.

---

## 7. Opening the local copy in the browser panel

### User

Asked for the local copy to be opened in the right-hand browser panel, using a known port number in the same manner as a previous Linktree project.

### Assistant

Inspected the existing `compose.yaml` and confirmed that the project was configured to run through Apache on port `8085`.

### Actions and results

- Started the local container with:

  ```powershell
  docker compose up -d
  ```

- Docker pulled and started the `httpd:2.4` image.
- Container name: `garage`.
- Port mapping:

  `0.0.0.0:8085 -> 80/tcp`

- Verified the local site returned HTTP 200.
- Verified the response contained the Garage Alchemy page content.
- Opened the local copy in the in-app browser at:

  <http://localhost:8085/>

- Confirmed the browser title:

  `Garage Alchemy — Useful ideas, taken into the garage`

### Useful commands

Start the preview:

```powershell
docker compose up -d
```

Stop the preview:

```powershell
docker compose down
```

---

## 8. Closing the work session

### User

Confirmed that the project was up to speed, documented, and ready to close out.

### Assistant

Confirmed that the project was documented, backed up publicly on GitHub, licensed, and available locally at `http://localhost:8085/`.

---

## Current project state

- Local project: `D:\Downloads\Websites\garage`
- Local preview: <http://localhost:8085/>
- Docker service: `garage`
- Git branch: `main`
- GitHub repository: <https://github.com/PopeKael/wazza-garage>
- GitHub visibility: public
- Initial backup commit: `aec9e46`
- Public-release commit: `ad3d812`
- Documentation files:
  - `README.md`
  - `LICENSE`
  - `PROJECT-JOURNAL.md`
  - `GARAGE-ALCHEMY-HANDOVER.md`
- Repository cleanup file: `.gitignore`

