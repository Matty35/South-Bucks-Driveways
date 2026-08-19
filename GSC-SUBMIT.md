# Search Engine Submission Plan — southbucksdriveways.co.uk

Pre-launch verification status (9 July 2026):

- ✅ All 17 canonicals, all 17 sitemap `<loc>` entries and all 17 `og:url` tags use `https://southbucksdriveways.co.uk` — zero netlify.app, staging or localhost references anywhere in the repo.
- ✅ robots.txt (650B), llms.txt (3.9KB) and sitemap.xml (1.5KB) all serve correctly from the site root.
- ⚠️ **Live DNS could not be verified from the build environment** (`southbucksdriveways.co.uk` did not resolve — likely propagation or resolver scope). Run step 0 below from your own machine before submitting anything.

## 0. Confirm the live domain first (2 minutes)

```
curl -sI https://southbucksdriveways.co.uk/robots.txt      # expect HTTP/2 200
curl -sI https://southbucksdriveways.co.uk/llms.txt        # expect HTTP/2 200
curl -sI https://southbucksdriveways.co.uk/sitemap.xml     # expect HTTP/2 200
curl -sI http://southbucksdriveways.co.uk/                 # expect 301 -> https
curl -sI https://www.southbucksdriveways.co.uk/            # expect 301 -> apex (or vice versa — pick ONE canonical host)
```

If www and apex both serve 200 without a redirect, set a 301 in the host config before submitting — the canonicals point at the apex, so the apex must be the surviving host.

## 1. Google Search Console

1. Add a **Domain property** for `southbucksdriveways.co.uk` (covers http/https/www/apex in one property). Verification is by DNS TXT record at your registrar — this is the GSC-verification item from the deploy checklist.
2. **Sitemaps → Add a new sitemap** → enter `sitemap.xml` → Submit. Expect "Success" with 17 discovered URLs within a day or two.
3. Check **Settings → robots.txt report** after 48h to confirm Google fetched it cleanly.

### Priority indexing requests (URL Inspection → Request Indexing)

GSC rate-limits inspection requests (~10/day) — do these six on day one, in this order:

| Priority | URL | Why first |
|---|---|---|
| 1 | `https://southbucksdriveways.co.uk/` | Entity home; everything hangs off it |
| 2 | `https://southbucksdriveways.co.uk/resin-driveways.html` | Flagship service |
| 3 | `https://southbucksdriveways.co.uk/guides/resin-driveway-cost-guide.html` | Primary money page — the cost query had zero local competition |
| 4 | `https://southbucksdriveways.co.uk/block-paving.html` | Core service |
| 5 | `https://southbucksdriveways.co.uk/gravel-driveways.html` | Core service |
| 6 | `https://southbucksdriveways.co.uk/driveway-repairs.html` | Core service |

Day two, request the wedge and comparison guides (`driveways-conservation-areas-chilterns.html`, `resin-vs-block-paving-vs-gravel.html`, `driveway-planning-permission.html`) — the AI-citation targets. Location pages can wait for natural crawl via the footer links.

## 2. Bing Webmaster Tools

1. Sign in at bing.com/webmasters → **Add site**. Fastest route: **Import from Google Search Console** (one click, reuses the GSC verification). Otherwise verify with the same DNS TXT method.
2. Submit `https://southbucksdriveways.co.uk/sitemap.xml` under Sitemaps.
3. Use **URL Submission** for the same six priority URLs (Bing allows a larger daily quota).
4. Bing powers Copilot/DuckDuckGo answers — worth the ten minutes given the site's AI-citation strategy (llms.txt, direct-answer format).

## 3. UK citations & directories (10 targets, in priority order)

Use the canonical NAP exactly as it appears in the site footer and llms.txt — same name ("South Bucks Resin & Driveways"), same service description, same phone format on every listing. Inconsistent citations dilute local rankings. The phone number (01494 328592) is live; do not create listings until the real address also replaces its placeholder.

| # | Directory | Why it matters for this trade |
|---|---|---|
| 1 | **Google Business Profile** | The local-pack ranking factor; competitor research showed review visibility is the weakest signal across every rival — this is where to win it |
| 2 | **Bing Places for Business** | Free, quick, feeds Bing/Copilot local results; import from GBP |
| 3 | **Checkatrade** | Held top-10 slots in 3 of the 4 target SERPs ("48 driveway services in Gerrards Cross" etc.) — occupy the directory that outranks competitors |
| 4 | **TrustATrader** | Ranked #1 for "driveways Gerrards Cross Buckinghamshire" and top-5 for Chalfont St Giles block paving in the research |
| 5 | **Yell.com** | Legacy citation with high domain trust; several competitors' only third-party presence |
| 6 | **Which? Trusted Traders** | Premium trust badge that suits the "Chilterns premium" positioning; Ashley Paving is the only local rival using it |
| 7 | **MyBuilder** | High-intent quote requests; its cost guides rank for the money queries this site targets |
| 8 | **FreeIndex** | Free UK citation with strong indexation; easy NAP win |
| 9 | **Houzz UK** | Matches the substantial-period-home customer; portfolio format ready for project photos when they exist |
| 10 | **Yelp UK / Cylex** | Secondary citations that aggregate into local-pack trust (Cylex already aggregates rival reviews) |

Trade-body extras once accreditations exist: **Marshalls Register** and **Brett Approved Installer** listings — the research found these almost absent among local competitors and they double as manufacturer-backed guarantee signals.

## 4. After submission (week one)

- GSC Coverage: confirm 17 valid pages, zero excluded-by-noindex (there is no noindex anywhere).
- Rich results: check the FAQ and Breadcrumb enhancements register in GSC (FAQPage on 15 pages, BreadcrumbList on 17).
- Set up GSC email alerts; check the robots report shows GPTBot/ClaudeBot/PerplexityBot/Google-Extended allowed as intended.
- When the first genuine reviews land on Google/Checkatrade: add review schema per the TODO comment in index.html — not before.
