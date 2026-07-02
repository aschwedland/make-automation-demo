# AI Lead Follow-Up Automation — Case Study Page

A polished, single-page portfolio case study that showcases a **Make.com + Claude AI**
automation: every contact form submission triggers a personalized, AI-written follow-up
email and logs the lead to a spreadsheet — in about 30 seconds, with zero manual work.

The page is a fully self-contained static site (`index.html`) styled with Tailwind CSS via
CDN. There is no framework and no build step — open the file in a browser and it just works.

## What's on the page

Six sections, matching the design source of truth:

1. **Hero** — headline, subtext, and two stat chips
2. **The Problem** — why manual follow-up fails
3. **The Automation** — a 4-step flow diagram (form → Make → Claude → Gmail + Sheets)
4. **Demo Video** — a Loom embed placeholder (see below to wire up your recording)
5. **What This Replaces** — three benefit cards (Instant Response, Personalized by AI, Always Logged)
6. **CTA** — a "Let's Talk" contact button

The layout is responsive from 375px mobile through 1440px desktop. On mobile the automation
flow stacks vertically with down-pointing arrows; on desktop it runs horizontally with
chevron arrows between steps.

## Local preview

No tooling required — just open the file:

```bash
# macOS
open index.html
# Windows
start index.html
```

Or serve it locally the same way Railway does:

```bash
npx serve@latest .
```

## Updating the Loom embed URL

After recording the walkthrough, wire up the video:

1. Open `index.html`.
2. Find the placeholder `REPLACE_WITH_LOOM_EMBED_URL` (in **Section 4 — Demo Video**).
   It sits just below these guide comments:
   ```html
   <!-- REPLACE THE src BELOW WITH YOUR LOOM EMBED URL -->
   <!-- Format: https://www.loom.com/embed/YOUR_VIDEO_ID -->
   ```
3. Replace `REPLACE_WITH_LOOM_EMBED_URL` with your Loom **embed** URL, which looks like:
   `https://www.loom.com/embed/YOUR_VIDEO_ID`
   (In Loom, use **Share → Embed** and copy the URL from the `src` of the `<iframe>` — not
   the regular share link.)
4. Save, commit, and push. Railway redeploys automatically.

## Updating the contact link

The CTA button currently opens an email to `aschwedland@pixel-master.com`.

Once the portfolio site is live, update it to point at the contact section. In `index.html`,
find the CTA button in **Section 6** (marked with a `TODO` comment) and change:

```html
<a href="mailto:aschwedland@pixel-master.com" ...>Let's Talk</a>
```

to:

```html
<a href="https://schwedland.dev/#contact" ...>Let's Talk</a>
```

## Deploying to Railway

The repo is already configured for Railway (`railway.toml` + `package.json`).

- **Single service** — root directory is the repo root (`/`).
- **No environment variables** required.
- Railway serves the static files with `npx serve` on the injected `$PORT`.

To deploy:

1. Push to GitHub:
   ```bash
   git push
   ```
2. Railway auto-deploys the `make-demo-page` service — nothing else to configure.
3. After recording the Loom walkthrough, replace `REPLACE_WITH_LOOM_EMBED_URL` in
   `index.html` (see above), then commit and push to trigger a redeploy.
