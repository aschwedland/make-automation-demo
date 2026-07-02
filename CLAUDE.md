# AI Lead Follow-Up Automation — Claude Code Build Context

Build the **"AI Lead Follow-Up Automation"** case study page — a polished static portfolio page showcasing a Make.com + Claude AI automation. No framework, no build step. Single `index.html` using Tailwind CSS via CDN.

**Design reference:** The `design/README.md` in this repo has the claude_design MCP prompt. Run `/design-login` first, then use the MCP to pull the design. Two frames: full desktop scroll (all 6 sections) and mobile (375px) — use them as source of truth for all layout, section structure, colors, and the automation flow diagram.

---

## File Structure

```
make-automation-demo/
  index.html
  package.json
  railway.toml
  README.md
```

---

## Requirements

**`index.html`** — fully self-contained, no external files except Tailwind CDN:
- Load Tailwind from: `https://cdn.tailwindcss.com`
- All 6 sections from the design file:
  1. **Hero** — headline, subtext, two stat chips
  2. **The Problem** — short section, gray-600 paragraph
  3. **The Solution** — 4-step horizontal flow diagram with SVG chevron arrows
  4. **Demo Video** — Loom embed placeholder
  5. **What Gets Automated** — 3 cards (Instant Response, Personalized by AI, Always Logged)
  6. **CTA** — blue-600 bg, "Let's Talk" button
- Smooth scroll from any nav anchor links
- The automation flow diagram in Section 3:
  - Desktop: horizontal 4-step layout with SVG chevron arrows between steps (inline SVG, gray-300 color)
  - Mobile (`md:` breakpoint): stack steps vertically with down-pointing SVG arrows
- Section 4 — Video embed placeholder:
```html
<!-- REPLACE THE src BELOW WITH YOUR LOOM EMBED URL -->
<!-- Format: https://www.loom.com/embed/YOUR_VIDEO_ID -->
<div class="relative w-full" style="padding-bottom: 56.25%;">
  <iframe 
    src="REPLACE_WITH_LOOM_EMBED_URL"
    class="absolute inset-0 w-full h-full rounded-xl"
    frameborder="0"
    allowfullscreen
  ></iframe>
</div>
```
- CTA "Let's Talk" button: `href="mailto:aschwedland@pixel-master.com"` — include a comment: `<!-- TODO: Update this link to schwedland.dev/#contact once the portfolio site is live -->`
- Fully responsive (375px mobile through 1440px desktop)
- No JavaScript needed — pure HTML + Tailwind utility classes

**`package.json`** (needed only for Railway serve):
```json
{
  "name": "make-automation-demo",
  "version": "1.0.0",
  "scripts": {
    "start": "npx serve@latest . -l $PORT"
  }
}
```

**`railway.toml`:**
```toml
[build]
builder = "nixpacks"

[deploy]
startCommand = "npx serve@latest . -l $PORT"
```

**`README.md`:**
- What this page is and why it exists (portfolio case study for a Make.com automation demo)
- How to update the Loom embed URL (with exact instructions — find the `REPLACE_WITH_LOOM_EMBED_URL` placeholder)
- How to update the contact link after portfolio site is live
- How to deploy to Railway (single service, no env vars needed)

---

## Railway Deployment (already configured)

Railway project: "Make Automation Demo"
- Service `make-demo-page`: root directory = `/` (repo root)
- No env vars needed

After building:
1. Push code to GitHub (`git push`)
2. Railway auto-deploys — no env vars to set
3. After recording the Loom walkthrough: replace `REPLACE_WITH_LOOM_EMBED_URL` in `index.html`, commit and push
