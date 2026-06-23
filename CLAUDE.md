# BaggageIQ-hub — Marketing Site Reference

Living index of the marketing site at `baggageiq.app`. Update when structure changes. For per-file truth, always read the file.

## What it is
Static marketing site for the BaggageIQ browser extension. Vanilla HTML + CSS, no framework, no build step. Hosted on **GitHub Pages** with **Cloudflare** in front (DNS, AI bot policy, edge cache). The extension itself lives in the sibling repo at `/Users/ashishbansal/Documents/Projects/BaggageIQ`.

- Repo: `AspaceB/BaggageIQ-hub` (sibling to the extension repo).
- Domain: `baggageiq.app` (via `CNAME` file at root).
- Deploy: push to `main` → GitHub Pages auto-builds and serves; Cloudflare caches at edge.
- No build, no transpile, no JS bundler. Browsers load raw HTML/CSS directly.

## Top-level layout
```
index.html             Landing page (hero, sites, demo, features, install, FAQ, feedback, FAQ schema)
about.html             AboutPage schema, Organization sameAs to listings + socials
methodology.html       Sourcing/verification/correction process for the airline + card DBs
glossary.html          DefinedTermSet schema with 25 airline-pricing terms
privacy.html           Privacy policy (own embedded CSS — predates index.css extraction)
terms.html             Terms of service (own embedded CSS — predates index.css extraction)
admin.html             Admin tool for fee corrections review (noindex, robots-disallowed)
404.html               Branded "diverted, gate not found" page; GitHub Pages serves on missing URLs

index.css              Shared chrome (nav, footer, hero, body, FAQ) — extracted from index.html
                       Used by: index, about, methodology, glossary, 404. NOT used by privacy/terms (embedded).
                       Top of file declares the self-hosted @font-face rules (see fonts/).

fonts/                 Self-hosted woff2 (latin subset) — Space Grotesk / Inter / JetBrains Mono,
                       weights 400/500/600/700 (mono: 400/500/700). 11 files, ~230KB total.
                       Replaced the Bunny Fonts CDN on 2026-06-23 (kills a render-blocking
                       cross-origin request; also a privacy win — no third-party font CDN).
                       @font-face lives in index.css + blog/blog.css + the inline <style> of
                       privacy.html & terms.html (those four are the only stylesheets). All use
                       absolute /fonts/ paths + font-display:swap. index.html preloads the two
                       above-the-fold faces (space-grotesk-700, inter-400).

blog/
  index.html           Blog landing — article-grid cards, ItemList JSON-LD, intro
  blog.css             Shared blog stylesheet (nav, hero, article-container, post-meta, intro, cta)
  airlines-free-checked-bags-2026.html
  budget-airline-baggage-fees-compared.html
  how-to-avoid-surprise-baggage-fees.html         (HowTo schema, 8 steps)
  why-cheapest-flight-isnt-cheapest.html
  personal-item-size-limits-by-airline.html       (added 2026-05-09)
  credit-cards-that-waive-baggage-fees.html       (added 2026-05-09)
  feed.xml             RSS 2.0 feed of all posts (regenerated when posts added)

robots.txt             Cloudflare-managed AI bot block was removed 2026-05-09; only Disallows /data/ + /admin.html
sitemap.xml            13 URLs — pages + blog index + posts. Authority pages priority 0.5; posts 0.7; home 1.0.
security.txt           Root copy + /.well-known/security.txt for legacy scanners (RFC 9116)
.well-known/security.txt
llms.txt               Curated AI-crawler index following AnswerAI convention (Core / Blog / Reference / Quick facts)
llms-full.txt          ~50KB concatenated full content of every page for direct LLM ingestion
b45975767ce30e222f252fc5d1a11255.txt   IndexNow key file (push protocol for Bing/Yandex/Seznam/Naver)
og-image.png           1200×630 OG card; lossless-optimized to 100KB (was 272KB) on 2026-05-09
favicon.svg            Vector favicon (also 16/48 PNG variants + apple-touch-icon)
CNAME                  Holds "baggageiq.app" — GitHub Pages custom domain

.notes/growth-playbook.md   Internal growth/awareness playbook — launch channels, HN/PH/newsletter/HARO/video/Reddit tactics, ready-to-ship Show HN draft and pitch templates. NOT served (Jekyll excludes dot-prefixed dirs). Update as channels are tried.
```

## Schema graph (per page)
| Page | JSON-LD types |
|---|---|
| `/` | SoftwareApplication, Organization, WebSite, FAQPage |
| `/about.html` | AboutPage, BreadcrumbList |
| `/methodology.html` | WebPage, BreadcrumbList |
| `/glossary.html` | DefinedTermSet (25 terms with stable @id anchors), BreadcrumbList |
| `/privacy.html`, `/terms.html` | none (intentional — legal docs) |
| `/blog/` | Blog, BreadcrumbList, ItemList |
| `/blog/<post>.html` | BlogPosting (16 fields incl. mentions, wordCount, dateModified, mainEntityOfPage), BreadcrumbList |
| `/blog/how-to-avoid-surprise-baggage-fees.html` | + HowTo (8 steps) |

BlogPosting `mentions` arrays link to Wikidata + Wikipedia for airlines (Spirit Q1392680, Delta Q188920, etc.) and card issuers (Amex Q108585, Chase Q192314, Citi Q219508). Helps AI search engines ground claims to canonical entities.

## AI-readability stack (live)
- robots.txt: clean — all AI bots allowed (was Cloudflare-managed-blocked until 2026-05-09)
- Cloudflare AI Labyrinth: OFF (was ON until 2026-05-09)
- Cloudflare Block AI Bots: OFF
- /llms.txt + /llms-full.txt for AI tools that look for them
- /blog/feed.xml RSS 2.0 for feed-following AI agents
- IndexNow key file at root — Cloudflare's Crawler Hints feature can auto-ping Bing/Yandex on content changes (user must enable in Cloudflare dashboard)
- Per-post OG article tags + `<time datetime>` markers + `<article>` semantic wrappers

## Conventions & gotchas
- **No build step.** Edits to HTML/CSS deploy as-is when pushed to `main`. GitHub Pages takes ~30-90s to propagate; Cloudflare may cache HTML briefly.
- **CSS cache-busting.** When `/index.css` or `/blog/blog.css` changes, bump the `?v=N` query string in every HTML reference, otherwise users get stale CSS. Currently: `/index.css?v=3`, `/blog/blog.css?v=6`.
- **`privacy.html` and `terms.html` have embedded CSS.** They predate the `index.css` extraction. Don't refactor them without explicit ask — they work and refactoring risks breaking layout for legal pages.
- **Footer parity.** All 14 HTML pages share the same footer link list (Home / Blog / Install / About / Methodology / Glossary / Privacy / Terms). When adding a top-level page, update every footer.
- **Sticky nav.** `.nav` is `position: sticky; top: 0; z-index: 50;` plus `html { scroll-padding-top: 72px; }` so anchor links don't slide under the header.
- **No CSS framework, no JS frameworks.** Vanilla everywhere. The extension feedback form on `/` posts to `formsubmit.co/support@baggageiq.app` — no JS handler.
- **Privacy posture.** No cookies, no localStorage, no analytics scripts. Cloudflare Web Analytics is enabled at the edge (no client JS, GDPR-compliant). Documented in `/privacy.html`.
- **Stale-claim risk.** Numbers (109 airlines, 62 cards, 6 sites, version 3.0.1) appear in many places — landing copy, JSON-LD, FAQ, blog posts. When updating one, grep for the old number and update everywhere. The supported-sites list is a frequent stale spot — `Booking.com` and `Expedia` were added when the lineup trimmed 11→6.
- **Admin page.** `/admin.html` is noindex'd, robots-disallowed, and has its own auth flow. Linked nowhere from the public site. Don't surface it.

## Deploy
- Push to `main` → GitHub Pages auto-deploys → Cloudflare edge cache → live at `baggageiq.app`.
- For HTML changes: typically live within 1-2 minutes.
- For CSS changes: also bump `?v=N` cache-buster in HTML to skip Cloudflare's CSS cache.
- The IndexNow key file enables Cloudflare's Crawler Hints to ping Bing/Yandex on content change — currently requires user to enable in Cloudflare dashboard (Caching → Configuration → Crawler Hints).

## Quick debug
```bash
# Check robots.txt is clean (no Cloudflare AI block)
curl -sS https://baggageiq.app/robots.txt

# Verify a page is live + new
curl -sS -I https://baggageiq.app/blog/personal-item-size-limits-by-airline.html

# Verify CSS cache-bust took effect
curl -sS https://baggageiq.app/blog/ | grep blog.css

# Validate sitemap
xmllint --noout sitemap.xml && echo OK

# Validate RSS
xmllint --noout blog/feed.xml && echo OK
```

---
Last refreshed: 2026-05-09. Major changes since site went live: Pro tier removed (extension); site lineup trimmed 11→6; Edge Add-ons listing went live; AI bot gating fully removed from Cloudflare; 3 authority pages added (about/methodology/glossary); 2 new blog posts added; /llms.txt + /llms-full.txt + /feed.xml + IndexNow key shipped; sitemap grew 8→13 URLs; CSS extracted from `index.html` to `/index.css`. Re-verify any specific claim before acting on it — code is the source of truth.
