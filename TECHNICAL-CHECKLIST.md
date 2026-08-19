# Technical SEO Checklist — southbucksdriveways.co.uk

Generated 2026-07-09 on branch claude/driveway-seo-research-dy1wxm.
Every item below was verified by script against the committed HTML — regenerate after structural changes.

## Per-page audit

| Page | Canonical self-ref (https) | Title ≤60 | Desc ≤155 | OG+Twitter | One H1 | Heading order | Form labels | Images | Perf (inline CSS, defer JS, preconnect) | Skip link |
|---|---|---|---|---|---|---|---|---|---|---|
| about.html | ✅ | ✅ (40) | ✅ (143) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| block-paving.html | ✅ | ✅ (57) | ✅ (149) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| contact.html | ✅ | ✅ (56) | ✅ (130) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| driveway-repairs.html | ✅ | ✅ (55) | ✅ (130) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| driveways-amersham.html | ✅ | ✅ (46) | ✅ (130) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| driveways-beaconsfield.html | ✅ | ✅ (56) | ✅ (142) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| driveways-chalfont-st-peter.html | ✅ | ✅ (53) | ✅ (144) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| driveways-gerrards-cross.html | ✅ | ✅ (53) | ✅ (137) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| gravel-driveways.html | ✅ | ✅ (53) | ✅ (143) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| guides/driveway-planning-permission.html | ✅ | ✅ (52) | ✅ (155) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| guides/driveways-conservation-areas-chilterns.html | ✅ | ✅ (57) | ✅ (149) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| guides/index.html | ✅ | ✅ (41) | ✅ (128) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| guides/resin-driveway-cost-guide.html | ✅ | ✅ (54) | ✅ (141) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| guides/resin-vs-block-paving-vs-gravel.html | ✅ | ✅ (57) | ✅ (141) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| guides/suds-driveway-drainage.html | ✅ | ✅ (55) | ✅ (138) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| index.html | ✅ | ✅ (59) | ✅ (151) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |
| resin-driveways.html | ✅ | ✅ (51) | ✅ (154) | ✅ | ✅ | ✅ | ✅ | no imgs | ✅ | ✅ |

## Site-wide items

- **Sitemap**: sitemap.xml lists all 17 pages with correct https://southbucksdriveways.co.uk URLs — ✅ complete, no missing/extra entries
- **robots.txt**: references sitemap ✅; explicitly allows GPTBot, ClaudeBot, PerplexityBot, Google-Extended ✅ (plus OAI-SearchBot, CCBot, Applebot-Extended, meta-externalagent and general allow-all)
- **Titles/descriptions**: all unique across the site ✅
- **Images**: the site currently ships zero raster images; the audit column confirms none are missing lazy/width/height. POLICY: any image added later MUST carry `loading="lazy"` (below the fold), explicit `width`/`height`, and descriptive `alt`.
- **og:image / twitter:image**: deliberately absent (no brand imagery yet); TODO comments sit in every page head.
- **Critical CSS**: ~7.6 KB inlined per page (tokens, reset, typography, header/nav, hero, buttons, breakpoints, reduced-motion); full stylesheet preloaded and applied via `media="print"` swap with `<noscript>` fallback.
- **JS**: single 0.6 KB script, `defer`red; no third-party JS. Fonts: preconnect to fonts.googleapis.com and fonts.gstatic.com (crossorigin) on every page.

## Colour contrast (WCAG AA, computed from design tokens)

| Usage | Colours | Ratio | Result |
|---|---|---|---|
| body text (ink on flint) | #26302B on #F5F2EC | 12.20:1 | PASS |
| body text on chalk sections | #26302B on #EDEAE2 | 11.34:1 | PASS |
| muted text on flint | #606661 on #F5F2EC | 5.26:1 | PASS |
| muted text on chalk | #606661 on #EDEAE2 | 4.89:1 | PASS |
| hero/nav text (flint on woodland) | #F5F2EC on #2F4A38 | 8.71:1 | PASS |
| hero lede (85% flint on woodland) | #d7d9d1 on #2F4A38 | 6.83:1 | PASS |
| brand small / guide-meta (78% on woodland) | #c9cdc4 on #2F4A38 | 6.03:1 | PASS |
| CTA button (flint on bronze-deep) | #F5F2EC on #7E5527 | 5.84:1 | PASS |
| price/table figures (bronze-deep on flint) | #7E5527 on #F5F2EC | 5.84:1 | PASS |
| price/table figures (bronze-deep on chalk) | #7E5527 on #EDEAE2 | 5.43:1 | PASS |
| footer meta (75% flint on woodland-deep) | #c1c4bc on #24392B | 7.01:1 | PASS |
| footer text (flint on woodland-deep) | #F5F2EC on #24392B | 11.09:1 | PASS |

Note: raw bronze (#A8763E) is used only for non-text decoration (aggregate band, bullets, borders, focus ring uses bronze-deep); all text-on-surface pairs use AA-passing combinations above.

## Outstanding TODOs before launch

- ~~Replace phone placeholder~~ DONE: live number 01494 328592 in page bodies, footers, LocalBusiness schema and llms.txt.
- Replace NAP address placeholders in footers and LocalBusiness schema (marked TODO-*).
- Add real project imagery to /images/ (then add og:image/twitter:image and populate galleries).
- Add review schema only once genuine public reviews exist (see TODO comment in index.html).
- Wire the contact form to a form handler (currently action="#").
