# Bunku-web

GitHub Pages site for Bunku. Hosted at `https://bunku.jdevsappstudio.com/` (custom domain via the
`CNAME` file — was previously `jdevsappstudio-github.github.io/bunku/`, kept live there as a
redirect target, not deleted).

## Structure

```
/
├── index.html             ← Landing page
├── privacy-policy.html    ← Privacy policy (linked from Play Console)
└── CNAME                  ← bunku.jdevsappstudio.com
```

No `app-ads.txt` — Bunku doesn't run ads (no ad SDK in the app; monetization is the one-time
₹50 Pro unlock only). No `terms-of-service.html` either — Bunku has never published one; don't
add one without checking that's actually intended.

## Live URLs

| Page | URL |
|---|---|
| Landing page | `https://bunku.jdevsappstudio.com/` |
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
- A `/blog/` directory is reserved for future SEO posts — GitHub Pages runs Jekyll natively with
  zero build config, so a `_posts/` collection can be dropped in later without migrating anything.
