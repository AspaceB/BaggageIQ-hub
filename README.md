# BaggageIQ Hub — marketing site

This repository serves [`baggageiq.app`](https://baggageiq.app) via GitHub
Pages. It contains the public marketing site, blog, and admin pages.

## What's in this repo

- `index.html` — landing page
- `pricing.html` — Pro pricing
- `privacy.html` / `terms.html` — legal
- `admin.html` — internal admin dashboard
- `blog/` — content marketing
- `sitemap.xml`, `robots.txt`, `og-image.png`, `CNAME`

## What used to be here

Until April 2026 this repo also held nightly snapshots of the BaggageIQ
backend database in `data/airlineBaggageDB.json` and
`data/cardBenefitsDB.json`. As part of the Phase 4.7 public-data lockdown,
those files were:

1. Migrated to a private repo (`AspaceB/BaggageIQ-backup`) which only
   authenticated users with repo access can read.
2. Removed from this repository's working tree.
3. Removed from this repository's entire git history via `git filter-repo`,
   followed by a force-push.

If you're looking for the BaggageIQ database, you have two legitimate
options:

- **End-user access:** install the [BaggageIQ browser extension](https://baggageiq.app).
  The extension fetches data through authenticated API endpoints with
  per-install rate limits.
- **Internal recovery:** the private `BaggageIQ-backup` repo is the
  weekly disaster-recovery snapshot. Access is restricted to project
  maintainers.

## Source of truth

Neither this repo nor the backup repo is the source of truth. The system
of record is the Supabase project behind `api.baggageiq.app`, and the
extension is the only client that reads from it directly.
