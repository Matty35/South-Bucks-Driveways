# Design QA — southbucksdriveways.co.uk

Reviewed 9 July 2026. All 17 pages audited in headless Chromium at **360px, 768px and 1280px**
(external font requests deliberately blocked during audit to simulate worst-case network).
Every issue below was found by script, fixed, and re-verified by re-running the same audit to zero findings.

## Findings & fixes

### 1. Horizontal overflow
- **Found:** none, at any width on any page. Tables were already wrapped in `.table-wrap { overflow-x: auto }`.
- **Fix:** none needed; scroll-hint improvement logged under item 7.

### 2. Tap targets under 44px
- **Found:** none. Nav links, buttons, form controls, FAQ summaries and footer nav links all measure ≥44px
  (enforced by the `--tap-target` token). In-paragraph text links rely on the WCAG 2.5.8 inline exception.
- **Fix:** none needed.

### 3. Text under 16px on mobile
- **Found (360px):** systematic — everything on the `--text-sm` token rendered at 14px (trust strip, nav
  toggle, table cells/captions, table notes, form labels, guide datelines, footer meta, brand tagline,
  compare-card notes), and `.data` measurements rendered at 15.2px.
- **Fix:** `--text-sm` is now `1rem` in the mobile-first base and steps down to `0.875rem` only at ≥768px;
  `.data` is `1em` on mobile, `0.95em` from 768px. Re-audit at 360px found zero text nodes under 16px on
  representative pages (home, service, cost guide, contact, location).

### 4. Hero exceeding one mobile viewport
- **Found (360×740):** homepage hero measured 803px — the CTA row fell below the fold. All other pages fit.
- **Fix:** hero `padding-block` reduced to `--space-5/--space-6` on mobile (restored to `--space-7` at
  ≥768px) and base `--text-3xl` reduced 2.25rem → 2rem (2.25rem restored at ≥480px, larger steps unchanged).
  Homepage hero now fits within 740px with both CTAs and the trust strip start visible; screenshot-verified.

### 5. Accordion misbehaviour
- **Found:** default `<summary>` disclosure triangle rendered alongside the design system's +/− indicator
  (double marker).
- **Fix:** `list-style: none` + `::-webkit-details-marker { display: none }` on `.faq summary`.
  Open/close toggling verified programmatically (opens on click, closes on second click, indicator flips).

### 6. Sticky call button overlap
- **N/A:** the site has no sticky/floating call button. Tap-to-call lives in hero and closing CTA rows.
  If one is added later, test against FAQ summaries and the footer at 360px.

### 7. Table overflow scroll hint
- **Found:** tables scrolled correctly but gave no visual cue that more columns existed off-screen.
- **Fix:** CSS-only scroll shadows on `.table-wrap` (the `background-attachment: local/scroll` technique):
  a soft edge shadow appears only while content remains off-screen in that direction and disappears at the
  scroll extents. Cover gradients match the section background via `--table-bg` (flint on plain sections,
  chalk on alternate sections). No JS involved.

### 8. Font flash
- **Found:** the Google Fonts stylesheet was render-blocking; on a slow font CDN the whole first paint
  stalled (observed directly during audit when font requests hung).
- **Fix:** the fonts stylesheet now loads asynchronously (preload + `media="print"` swap + `<noscript>`
  fallback), keeping `display=swap`. Text paints immediately in metric-similar fallbacks (Georgia for
  Fraunces, system-ui for Inter) and upgrades when the webfonts arrive. Verified rendering with font
  requests blocked entirely.

## Consistency pass

- **Spacing rhythm:** identical by construction — every page uses `.section { padding-block: --space-7 }`
  (`--space-8` at ≥1100px), the same `.container` gutter, and the same hero paddings. No page-level
  overrides exist (verified: zero inline styles, zero page-specific CSS).
- **Signature element (aggregate band):** implemented exclusively as `h1::after`, so it appears under the
  single H1 of each page and can appear nowhere else. Verified one H1 per page and no other selector
  carries the band's background pattern.
- **Accent colour discipline:** bronze now appears only in: the aggregate band (signature), primary CTA
  buttons, FAQ +/− indicators and focus rings (interaction states), and key data (`.price`, table
  `.figure` cells, process-step numerals, trust-marker dots). Removed from: checklist bullets (→ woodland),
  card hover borders (→ woodland), and active-nav indicators (→ flint on the woodland header).
- **Placeholder text:** visible `[Registered address line …]` blocks removed from all 17 footers (replaced
  with an HTML comment TODO; the LocalBusiness schema keeps machine-readable TODO markers). Contact-page
  "details will appear here" copy replaced with the real contact routes. Remaining known-placeholder
  values tracked in TECHNICAL-CHECKLIST.md: the schema address fields (phone is now the live number,
  01494 328592) — the address needs real data, not different copy.
- **Internal links:** full crawl of every `href` on all 17 pages — zero 404s (all targets resolve,
  including the `/guides/` directory index).

## Re-verification

Final state: all 17 pages × 3 widths re-audited — no overflow, no sub-44px structural tap targets,
no sub-16px mobile text, hero within one 360×740 viewport on every page, accordions single-markered and
toggling, table scroll hints active, fonts non-blocking. Inline critical CSS was regenerated from the
updated stylesheet so head styles and `/css/styles.css` cannot disagree.
