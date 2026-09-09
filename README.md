# OTOS Continuity — Cambridgeshire Public Health

Private briefing site for **Scott Davidson**, Public Health, Drugs & Alcohol, Cambridgeshire County
Council. Static. No build step, no dependencies, no framework — every page is self-contained.

**⛔ Not public. `noindex` on every page, `robots.txt` disallows all crawlers, `vercel.json` sends
`X-Robots-Tag` on every response. Never link to it from anywhere public.** (TL-0208.)

---

## Deploy

1. Create a **new, private** GitHub repository — `otos-cccph`.
2. Upload the **contents of this folder** to the repository root — `index.html` must sit at the top
   level, not inside a folder.
3. Vercel: **Add New → Project → import the repository.**
   - Framework preset: **Other**
   - Build command: **leave empty**
   - Output directory: **leave empty** (root)
4. Vercel → Project → Settings → Domains → add **`cccph.otos.network`**, then point the `cccph`
   record at Vercel in DNS.
5. ⚠️ **Check Vercel → Settings → Deployment Protection.** TL-0238 found `hub.otos.network` publicly
   reachable because protection was set to *all except custom domains* — the `.vercel.app` URL was
   locked and the real domain was wide open. Whatever is chosen, verify it on the custom domain, not
   on the preview URL.

---

## The pages

| File | |
|---|---|
| `index.html` | **The case.** Dean's page of 25 Aug 2026, insert-only, 52 marked changes. Carries the calculator |
| `services.html` | **The six services** — six people who stepped outside the process |
| `01-cgl-crs.html` | CGL & CRS — the service the Council commissions |
| `02-cpft-adhd.html` | CPFT Adult ADHD Team |
| `03-alcohol-liaison.html` | Alcohol Liaison — the bedside at Addenbrooke's |
| `04-rce-wellbeing.html` | RCE Wellbeing Hub |
| `05-mind-workwell.html` | Mind / WorkWell East |
| `06-lamp.html` | Dr Claire Gillvray — LAMP |
| `robots.txt` | Disallows all crawlers |
| `vercel.json` | `X-Robots-Tag: noindex` plus three security headers on every response |

Each page is ~500KB because CSS, JavaScript, images and the calculator are inlined as `data:` URIs.
That is deliberate: any single file can be opened, emailed or moved on its own and still renders.

---

## ⛔ Do not edit these files by hand

They are generated. The source and the three build commands are in
`04 — WORKING/SCOTT SITE BUILD/` in the Playground. Editing a built page loses the guards — the
anchor check, the banned-claim list, the style-nesting check and the internal-link check — every one
of which has caught a real error.

---

## What is on these pages

Dean's own words throughout, quarried from his partner briefs and his approved copy. **No service
named on this site has been approached, has agreed anything, or has endorsed anything** (TL-0519).
Every figure carries a named published source. The 18 claims removed during the build, and the ruling
that forced each one, are listed at the foot of `sixpages/content.py` in the build folder.
