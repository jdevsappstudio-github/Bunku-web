# Bunku-web

GitHub Pages site for Bunku. Hosted at `https://bunku.jdevsappstudio.com/` (custom domain via the
`CNAME` file — was previously `jdevsappstudio-github.github.io/bunku/`, kept live there as a
redirect target, not deleted).

## Structure

```
/
├── index.html                            ← Landing page
├── privacy-policy.html                   ← Privacy policy (linked from Play Console)
├── tools/
│   └── attendance-calculator/index.html  ← Free SEO tool: safe-bunk / attendance % calculator
├── blog/
│   ├── index.html                        ← Blog listing
│   └── <slug>/index.html                 ← One folder per post (4 so far)
├── assets/
│   ├── css/                              ← main.css (shared everywhere) + home/tools/blog.css
│   └── fonts/                            ← real Manrope + DM Sans woff2 files (not inlined)
├── sitemap.xml
├── robots.txt
└── CNAME                                 ← bunku.jdevsappstudio.com
```

No `app-ads.txt` — Bunku doesn't run ads (no ad SDK in the app; monetization is the one-time
₹50 Pro unlock only). No `terms-of-service.html` either — Bunku has never published one; don't
add one without checking that's actually intended.

## How pages are built (not Jekyll — no Ruby available locally)

The plan was real Jekyll (GitHub Pages runs it natively, zero config), but there's no Ruby/Jekyll
toolchain on this machine to preview a build before pushing. Instead, `index.html`, every
`tools/**/index.html`, and every `blog/**/index.html` are generated from a small Node script —
**the generator lives outside this repo** (scratchpad, not committed here) and only its *output*
(plain static HTML) is committed, same pattern as the image/font asset pipeline already used for
the landing page. If you want to regenerate or add a page:

1. The generator source: `render.js` (shared `<head>`/nav/footer template), `build-home.js`,
   `build-tool.js`, `build-blog.js` + `posts-data.js` (post content lives here as a JS array —
   add a new post by adding an entry, not by hand-writing HTML).
2. To add a blog post: add an entry to `posts-data.js`, rerun `node build-blog.js` — it
   regenerates every post page *and* the index, so cross-links/related-posts stay in sync.
3. Preview locally by serving this directory (`npx serve .`) rather than opening the HTML files
   directly — pages reference `/assets/...` with root-absolute paths, which don't resolve over
   `file://`.
4. **Revisit real Jekyll later** if the blog grows enough to want `jekyll-seo-tag` /
   `jekyll-sitemap` — would need Ruby installed to preview locally first.

## Live URLs

| Page | URL |
|---|---|
| Landing page | `https://bunku.jdevsappstudio.com/` |
| Attendance calculator (SEO tool) | `https://bunku.jdevsappstudio.com/tools/attendance-calculator/` |
| Blog | `https://bunku.jdevsappstudio.com/blog/` |
| Privacy policy | `https://bunku.jdevsappstudio.com/privacy-policy.html` |

## How to update

```bash
git add .
git commit -m "update: <what you changed>"
git push
```

GitHub Pages rebuilds automatically — changes go live within a few minutes.

## Notes

- Play Store link uses the real package ID (`com.jdevsappstudio.bunku`).
- Landing page copy (headlines, Pro price/features) was written against the real screenshots and
  the live paywall — not the old marketing copy, which had drifted (mini-games/JSON-backup claims
  no longer match the real Pro paywall). If Pro's price or feature list changes, update both here
  and check the live paywall stayed the source of truth.
- **SEO content strategy (2026-08-08):** the tool + 4 posts target real, validated search demand
  (checked via live search — "attendance calculator," "bunk calculator," "75% attendance" all have
  active competitors, mostly thin ad-stuffed sites with no real product behind them). One flagship
  calculator page rather than several near-duplicate tool pages, to avoid a duplicate-content
  penalty. Every post/tool has exactly one contextual CTA to the Play Store, not a banner.
  **Phase 2 idea, not built — discussed and explicitly held off (2026-08-08):**
  university-specific attendance-rule pages (VTU, Anna University, Mumbai University, etc.). Real
  opportunity — long-tail, university-named searches have far less competition and much higher
  intent than the general posts here, since someone searching their exact university is very
  likely to click through. Deliberately not started: each page needs to be *actually correct* for
  that specific university (real minimum %, real condonation policy, real consequences), not the
  generic UGC/AICTE baseline the general posts use — that's real per-university research, not
  something to template out. If picking this up: shortlist universities first (ideally by whatever
  signal exists on Bunku's actual user base, otherwise by size), research each one's real policy,
  then draft.
