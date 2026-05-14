# BaggageIQ — Growth & Awareness Playbook

Internal reference. Not served by GitHub Pages (`.notes/` is excluded by Jekyll's dot-prefix rule). Update as channels are tried and results come in.

Last updated: 2026-05-14

---

## Constraints baked in

- Free product (no Pro tier, no affiliate, no tracking). CAC > LTV for paid ads → don't run any.
- Solo, side-project time budget. Optimize for high-leverage one-shot or compounding moves.
- Already on Chrome / Edge / Brave / Firefox / Safari (macOS, approved 2026-05-13).
- Already launched on Product Hunt with an older version → cannot relaunch the same product on PH.
- New Google Search Console property (as of 2026-05-13): 2/13 pages indexed. Authority-building backlinks > paid promotion.

## What to skip (low ROI for this product/stage)

- Paid ads (Google / Meta / TikTok ads). CAC math doesn't work for a free extension.
- Mass-blast PR services.
- Building a Twitter/X following from zero.
- Weekly email newsletter — nothing to send weekly.
- Influencer outreach with payment.
- Buying HN/Reddit upvotes (vote-ring detection is aggressive; gets the account banned permanently).

---

## Priority order — what to do, in what sequence

### This week
1. **Short-form video** — TikTok / Reels / YT Shorts demoing bait-fare → real cost overlay.
2. **HARO / Connectively signup** — daily journalist requests, free, biggest single backlink lever.
3. **Travel newsletter outreach (Tier 1)** — View From The Wing + Going.
4. **Product Hunt "Ship"** post on existing product page for Safari + free-everything news (low effort, low ceiling).

### Next 2-4 weeks
5. **HN karma building** — 3-5 substantive comments per week, no self-promo. Goal: ~25-50 karma to unlock Show HN.
6. **Reddit r/SideProject** — single launch post, no karma gate.
7. **Travel newsletter outreach (Tier 2)** — TPG + One Mile at a Time.
8. **Chrome/Edge/Firefox/Safari store listing optimization** — title keywords, screenshots, demo video.

### Month 2+
9. **Show HN attempt** once karma threshold is met.
10. **Reddit r/travel, r/awardtravel, r/Flights, r/churning, r/flightdeals** — only after 2 weeks of helpful commenting in each. Self-promo without lurk gets banned.
11. **Quora answers** to evergreen "hidden airline fees" / "real flight cost" questions.
12. **Travel YouTuber cold outreach** — offer free use, no expectation of coverage.

---

## Channel: Hacker News (Show HN)

### Status
- **Blocked for now.** New account, doesn't meet karma threshold. Estimated 25-50 karma unlock, exact threshold mod-dependent.
- Karma must be built organically. No way to game it without permanent ban.

### Karma-building tactics
1. Find 3-5 recent threads per week on topics with genuine personal expertise: Manifest V3 migration pain, browser extension distribution, side-project monetization, scraping fragile DOM-driven sites, airline/travel pricing dynamics.
2. Drop substantive comments with concrete first-hand detail. Not generic agreement, not opinions — specifics ("when I built BaggageIQ's parser for Skyscanner, the DOM structure changed three times in six months and broke X").
3. **Never mention or link to baggageiq.app** in any karma-building comment. Self-promo from a new account flags the entire account.
4. Avoid replying to obvious flame-bait threads. Calm technical contributions get upvoted; arguments do not.

### Show HN draft (ready to ship once karma is unlocked)

**Title** (78/80 chars, "Show HN:" prefix mandatory):
```
Show HN: BaggageIQ – Browser extension that adds baggage fees to flight search
```

**URL field:**
```
https://baggageiq.app
```

**First comment** (post within 2-3 minutes of submitting):
```
Hi HN — I built this because "$49 to Vegas" kept turning into $215 at
checkout and no booking site shows the real total upfront. They all sort
by the bait fare on purpose.

What it does: reads the flight cards already rendered on Google Flights /
Skyscanner / Kayak / MakeMyTrip / Booking.com / Expedia, looks up the
airline's actual bag and seat-selection fees for the fare tier shown,
subtracts any credit-card baggage benefit you've added to your wallet,
and stamps the real total onto every card. No checkout simulation, no
API call per flight.

How it works under the hood: bundled DB of 109 airlines (per-fare-tier,
per-route allowances) and 62 travel credit cards ships inside the
extension, AES-256-GCM at rest, decrypted in the service worker. Zero
network round-trip per search — everything's local. Only network call is
a lazy hydrate when it sees an IATA code that isn't in the bundled
snapshot, cached 7 days. Manifest V3. Chrome / Edge / Brave / Firefox.
Safari on macOS got approved this week.

Things I deliberately didn't build:
- No affiliate links. If you book the flight, I don't get paid. That was
  the whole point.
- No Pro tier — full feature set is free.
- No tracking of which flights you search. Opt-in extension-health
  metrics only (version, crash counts).
- No scraping of booking sites' own fee fields. They're inconsistent and
  sometimes personalized. The airline's own published fee page is the
  only source.

Honest limits: doesn't work on mobile (extension API gaps on Safari iOS
and Chrome Android), only 6 booking sites (trimmed from 11 — I couldn't
keep parsers working through enough redesigns), and a chunk of airlines
have "medium confidence" rows because not every carrier publishes a clean
fee schedule. Methodology and sourcing here:
https://baggageiq.app/methodology.html

Side project, no team. Happy to answer anything about the
parser-vs-redesigns arms race, the fee research pipeline, or why I
refuse to do affiliate.
```

### Launch-day tactics
- Post **Tuesday or Wednesday, 8–10am PT**. Avoid Monday (announcement clutter) and Friday (weekend dropoff).
- **Don't ask anyone to upvote.** Vote-ring detection is aggressive; dead-ranks the post invisibly. Just submit and let it ride.
- **Reply to every comment within 30 min for the first 4 hours.** Engagement velocity is the biggest ranking factor. After hour 4 the post is either on the front page or dead.
- Comments needing fast replies — anything skeptical: "how is this different from Honey", "what's your business model", "isn't this Google's job", "why no mobile". The "Things I deliberately didn't build" section in the first comment preempts most.
- **Don't link to baggageiq.app in comment replies.** People are already on the post. Linking out reads as marketing.
- Expected outcome if front-paged: 5k-20k visitors over 24h. Cloudflare caching handles it; no infra prep needed.

---

## Channel: Product Hunt

### Status
- Previous launch already consumed the launch-day slot for the existing product page.
- PH consolidates relaunches rather than allowing a second front-page run.

### Plays still available

**1. PH "Ship" update on existing product page** (low effort, do this week)
- Post an update for: Safari (macOS) approval + Pro tier removed (now fully free) + 109 airlines / 62 cards milestones.
- Notifies existing followers, appears in Ship feed, doesn't drive launch-day spike.
- ~15 min effort.

**2. Speculative relaunch as "BaggageIQ for Safari"** (lottery ticket)
- Submit Safari version as a new product on PH.
- Moderators sometimes allow platform-expansion relaunches, sometimes consolidate into existing page.
- ~50/50 odds. Worst case: gets merged into existing page (same outcome as Ship).
- ~5 min effort to attempt.
- **In progress as of 2026-05-14.**

### Shoutouts strategy (PH submission form has a Shoutouts tab)
- Purpose: notify 3-5 PH-listed products' teams, build relationships, occasional reciprocation on launch day.
- Rules of thumb: mix travel-adjacent + Mac/browser (since this is the Safari launch) + maker stack. Avoid direct competitors (shoutout frames you as adjacent, not distinct).
- **Slots used for BaggageIQ for Safari (2026-05-14):** Going, Skiplagged, Flighty, Raycast.
  - Going + Skiplagged: travel/consumer-advocate audience overlap. Going is also a Tier-1 newsletter pitch target — shoutout warms it up.
  - Flighty: beloved Mac/iOS travel app, halo effect with Safari audience.
  - Raycast: Mac power-user crowd that installs niche extensions.
- **Avoided:** Hopper (closest price-prediction competitor; shoutout would conflate positioning), Honey-style coupon extensions (different value prop).

---

## Channel: Travel newsletters

### Priority order

**Tier 1 — high fit + reachable. Hit first.**
1. **View From The Wing** (Gary Leff, solo, gary@viewfromthewing.com — verify current address) — consumer-advocate angle aligns perfectly with bait-fare framing.
2. **Going (formerly Scott's Cheap Flights)** — 2M+ subscribers, formal editorial team. Complements their deal alerts.

**Tier 2 — bigger reach, harder.**
3. **The Points Guy** — approach a specific author who covers tools/extensions, not the generic inbox.
4. **One Mile at a Time** (Ben Schlappig) — bigger team than VFTW, slower response.

**Tier 3 — try if Tier 1/2 lands.**
5. **Thrifty Traveler** — similar to Going, smaller.
6. **Travel Pirates** — deal-aggregation, less editorial. Skip unless spare cycles.

### General principles (every outlet)
- **Don't ask for "coverage."** Ask for a specific action: mention in next bait-fare piece, inclusion in "best tools" roundup, quote opportunity, share with paid tier as free companion tool.
- **Lead with their audience's pain, not the product.** First two sentences about *their* readers.
- **Reference a real recent post from them.** 2 minutes to find one. The opening line is the only signal it isn't a mass-blast.
- **Keep under 150 words.** Editors get hundreds of pitches per week.
- **Send Tue–Thu, 9–11am ET.**
- **Follow up once after 8 days.** Then drop it. Three pitches = harassment.
- **Verify current email addresses** via masthead / About / Contact / LinkedIn — editor emails rot fast.
- **Don't send attachments.** Inline links only. Attachments trigger spam filters + signal "PR template."
- **Reply within 2 hours when an editor responds.** Velocity matters more than polish.

### Template: View From The Wing (Gary Leff)

```
Subject: Real-cost overlay tool for the Spirit/Frontier bait-fare problem

Hi Gary,

Long-time reader — your piece on [reference a specific recent post he's
written about hidden fees, fare-tier bait, basic economy traps, or
similar] is part of why I built this.

BaggageIQ is a browser extension that does what you've been calling for
in those posts: it stamps the real total cost (base + bags + seat fees
− credit-card benefits) onto every flight in Google Flights /
Skyscanner / Kayak / etc. Free, no affiliate, no Pro tier, no tracking
of which flights anyone searches.

Spirit MCO→LAS shows $49 on Skyscanner's results page — BaggageIQ
overlays the $215 real cost a basic-economy traveler will actually pay
once they add a personal item bag at gate-check. Numbers come from
airlines' own published fee pages (109 airlines, sourcing documented at
baggageiq.app/methodology).

No expectation of coverage — would just value your honest take. If it
holds up, a mention next time you write about bait-fare ranking on
booking sites would mean a lot.

Ashish
```

### Template: Going (editorial team)

```
Subject: Free tool that complements Going's flight deals — would your
Premium members find this useful?

Hi [editor name — find from masthead],

Going's members are great at finding the $49 fare. The bait-fare
problem most of them still hit is at checkout, when bags + seat fees
turn that $49 into $200+. I built a free browser extension that fixes
this — overlays the real total cost (incl. bag/seat fees, minus any
credit-card baggage benefits) onto Google Flights, Skyscanner, Kayak,
MakeMyTrip, Booking.com, and Expedia.

It complements rather than competes with Going's flight alerts — your
team identifies which fares are worth chasing, BaggageIQ helps members
confirm the deal is still a deal once bags are added.

Free, no affiliate, no Pro tier. 109 airlines, 62 travel credit cards,
methodology at baggageiq.app/methodology.

Would you consider mentioning it to Going Premium / Elite members as a
free companion tool? Happy to draft something or send installs in
whatever format works for your editorial flow.

Ashish
```

### Template: The Points Guy (specific writer, not generic inbox)

Find the writer first: search TPG for "browser extensions," "travel tools," "Chrome extensions for travelers," or "credit card baggage benefits." Pitch the author of that specific piece.

```
Subject: BaggageIQ — extension that subtracts your card's baggage
benefit from real flight cost in real time

Hi [author],

Saw your [reference specific piece] — wanted to flag a tool that fits
the same angle. BaggageIQ is a free browser extension that overlays
the real total cost of each flight (base + bags + seats − card baggage
benefit) on flight search results. 62 travel cards mapped — when a TPG
reader holds a United Explorer card, BaggageIQ subtracts that free bag
from United flights in real time so they can actually see when the
card is paying off and when it isn't.

This is the part most card-benefit articles can't show: the practical
value at the booking moment, per-flight, per-card. Free, no affiliate
on bookings, no Pro tier.

If you ever do a "best browser extensions for travelers" or "tools
that maximize card benefits" piece, would value being considered.
Happy to send a 90-second demo video showing the card-benefit
subtraction overlay in action.

Ashish
```

### Template: One Mile at a Time (Ben Schlappig)

Same structure as the VFTW template. Swap "Gary" → "Ben" or specific writer. Reference a recent OMAAT post on bait fares, basic economy, or card benefits.

### Press kit (build before pitching)

A `/press` page on baggageiq.app, not in sitemap, lightly linked from About. Should contain:
- Logo (`og-image.png` works) + favicon
- One-liner + 50-word + 150-word descriptions
- 3 concrete data examples (Spirit, Ryanair, basic-economy Delta — real numbers)
- Founder bio (Ashish Bansal, side project, India-based)
- Screenshot pack (3-5 PNGs of overlay in action)
- Link to 30-second demo video (unlisted YouTube)
- Contact: support@baggageiq.app

Editors who say yes often need this before they can publish — having it ready cuts response time from days to minutes.

---

## Channel: Short-form video (TikTok / Reels / YT Shorts)

### Why this channel
- Highest viral ceiling for the bait-fare hook. The "$49 → $215" overlay is genuinely surprising and 100% visual.
- TikTok algorithm rewards niche-but-relatable financial pain (airline pricing dishonesty is universally hated).
- Cheap: phone + screen recorder + 30 min per video.
- Reusable: same 30-second clip uploads to TikTok, IG Reels, YT Shorts. One asset, three platforms.

### Format (per video)
- 15-30 seconds
- Hook in first 2 seconds: on-screen text "This $49 flight actually costs $215."
- Show Skyscanner / Google Flights screen → BaggageIQ overlay stamps real cost → cut to checkout confirming the math
- End with: "Free browser extension. Link in bio." (or "Search BaggageIQ")
- No voice-over needed; on-screen text + screen recording is enough

### Cadence
- Post 1 video / week minimum, 3 / week if it's working.
- Don't repost dead videos; iterate on the hook.
- After 4-5 videos you'll know which hook angle has legs.

---

## Channel: HARO / Connectively

### What it is
Daily emails to journalists writing stories who need expert quotes. Reply with a quote → sometimes get cited with a byline + backlink from major outlets (CNBC, NYT, Conde Nast Traveler, USA Today, etc.).

### Why high ROI
- Free.
- One backlink from a high-DR domain is worth more for Google indexing speed than 100 blog posts of internal SEO work.
- Travel/personal-finance journalists write about hidden fees constantly.

### Setup
1. Sign up at connectively.us (formerly helpareporter.com / HARO — Cision sunset HARO and migrated it to Connectively).
2. Subscribe to: Travel, Lifestyle & Fitness, Business & Finance newsletters.
3. Draft a reusable 3-paragraph "expert bio": who you are, what BaggageIQ does, contact info. Used as the closer in every response.

### Response template
```
Hi [journalist],

Re: [their query topic] — here's a quote you can use:

"[2-3 sentences with a concrete, quotable insight about the topic.
Numbers if possible. Avoid jargon.]"

— Ashish Bansal, founder of BaggageIQ (https://baggageiq.app), a free
browser extension that overlays real flight cost (base + bag + seat
fees, minus credit-card benefits) onto Google Flights, Skyscanner,
Kayak, Booking.com, Expedia, and MakeMyTrip. The extension covers 109
airlines and 62 travel credit cards.

Happy to expand on any of this, send screenshots, or do a quick
interview if helpful.

[contact details]
```

### Cadence
- Open Connectively email daily, skim for travel/airlines/credit-card stories.
- Respond to ~3 queries per week. Each response takes ~10 min.
- Expect ~10-20% citation rate. Each citation = high-DR backlink.

---

## Channel: Reddit

### Status
- **Self-promo without history = instant ban + post deletion** on every relevant subreddit.
- Must lurk + comment helpfully for ~2 weeks before posting.

### Subreddit fit (in order of audience match)
1. r/SideProject — no lurk requirement; can post a launch announcement today.
2. r/awardtravel — points/miles + airline pricing nerds. Perfect audience.
3. r/Flights — flight-search obsessives.
4. r/travel — broad travel, large audience.
5. r/churning — credit card / points obsessed.
6. r/flightdeals — deal-hunters.

### Approach (for #2-6)
1. Pick one subreddit. Read top posts of the past month. Sort comments by "controversial" to see what gets pushback.
2. Comment substantively on 5-10 posts over 2 weeks. Reference specific airlines, fees, fare tiers. Build a comment history visible in your profile.
3. Then post: "I built a free Chrome extension that adds baggage fees to flight search [proof screenshot]". No marketing language. Title in first-person.
4. Reply to every comment in the first 2 hours.
5. Don't crosspost the same content to multiple subreddits same week; Reddit suppresses.

### What to avoid
- "Hey guys, just launched my product..." — instant downvote.
- Marketing-speak titles.
- Posting from a fresh account (Reddit shadow-bans new accounts that post links).

---

## Channel: Browser store optimization

### Why underrated
Most extension installs come from in-store search ("baggage fee", "flight comparison", "real price"), not from baggageiq.app. Store listings are SEO-able properties in their own right.

### Per store
**Chrome Web Store**
- Title: include 2-3 high-volume search terms ("real flight cost", "baggage fees", "flight comparison").
- Screenshots: 5 high-res shots showing overlay in action. Caption each with a use case.
- Short description (132 char limit): lead with the value, not the brand.
- Detailed description: structure with paragraphs + emoji-free bullet lists.
- Promo video: 30-second demo (same as the TikTok one — reusable).
- Updates ship version bumps frequently — Chrome treats active extensions as higher quality.

**Microsoft Edge Add-ons** — same drill, smaller audience.

**Firefox Add-ons (AMO)** — Mozilla rewards detailed descriptions + screenshots more than Chrome does.

**Mac App Store** — different beast. Apple's app review judges screenshots harshly. Use the App Store Connect "What's New" field for every Safari update.

### Worth ~3 hours per store, one-time.

---

## Channel: Quora

### Why
- Evergreen traffic for years (top Quora answers rank on Google indefinitely).
- Free, written once.

### Approach
- Find questions with 100+ existing answers and high view count: "Why is the cheapest flight not the cheapest", "What hidden fees do airlines charge", "How do I find the real cost of a flight", "Which credit card waives baggage fees".
- Write 300-500 word answers with a concrete example. Mention BaggageIQ in the *body*, not the closing — Quora flags promotional closers.
- 1 answer per week. After 10-15 answers, expect 50-200 BaggageIQ installs/month from this channel alone.

---

## Other low-effort directories (set + forget)

- **BetaList** — submit at betalist.com. Free, low-effort, modest traffic + backlink.
- **Launching Next** — same idea.
- **Beta Page** — same.
- **AlternativeTo** — list BaggageIQ as an alternative to Hopper / Google Flights / Skyscanner.
- **Indie Hackers Products** — submit at indiehackers.com/products. Small audience, high signal.

~30 min total for all submissions.

---

## Decision log

### 2026-05-14
- Chose to attempt the speculative "BaggageIQ for Safari" relaunch on Product Hunt (option #2 above), not just a Ship update. Worst case is moderator consolidation back into the existing page — same outcome as Ship, so the downside is bounded.
- Filled PH Shoutouts with: Going, Skiplagged, Flighty, Raycast. Rationale logged in the Product Hunt section above.
- **Pending observation:** whether moderators allow this as a standalone launch or merge it into the existing BaggageIQ page. Outcome determines whether the speculative-relaunch tactic stays in the playbook for future platform expansions (e.g., a future Safari-iOS or Android port).

### 2026-05-13
- Submitted 13 sitemap URLs to IndexNow API (`api.indexnow.org`). HTTP 202 → 200 on retry confirms key validated. Bing + Yandex + Seznam + Naver now have URLs queued.
- Manually requested indexing for all 11 not-indexed URLs in Google Search Console.
- Safari (macOS) extension approved on Mac App Store. Site updated to include install link.
- Confirmed: cannot relaunch on Product Hunt (existing product page already used). Pivoted strategy to compounding-distribution channels.
- Confirmed: cannot Show HN yet (new account, karma threshold not met). Karma-building plan in progress.

### Pending decisions
- Whether to build `/press` page now or wait for first newsletter editor to ask for one.
- Whether to spin up TikTok/Reels account under personal name or BaggageIQ brand.

---

## Quick-reference: emails / accounts to create

- [ ] Connectively (HARO replacement) signup → connectively.us
- [ ] Verify current emails for: VFTW (Gary Leff), Going editorial, TPG writers, OMAAT writers
- [ ] TikTok account: @baggageiq (or under personal name — TBD)
- [ ] YouTube unlisted upload of 30-second demo video (for press pitches + extension store)
- [ ] `/press` page on baggageiq.app — only if a newsletter editor asks first

## Quick-reference: things already done

- IndexNow submission across 4 engines (Bing/Yandex/Seznam/Naver)
- GSC "Request Indexing" for 11 URLs (1 day quota burned)
- Safari macOS extension listed on Mac App Store + linked from site
- Sitemap lastmod bumped to 2026-05-13
- llms.txt + llms-full.txt + about page updated for Safari + Mac App Store
- Mac App Store URL added to Organization schema `sameAs` (helps search engines link the site to the Apple listing)
