# 08 — UI Design System (Retailer Platform)

The retailer dashboard must look like **Spendy** — the warm, rounded,
cream-and-coral identity of the consumer app — while borrowing the *structure*
of the best small-business dashboards. A clickable mock of the dashboard screen
lives at [`mock/dashboard.html`](../mock/dashboard.html).

## Design direction

Two references set the bar (chosen by the founders):

- **Growlytics-style analytics dashboard** → we take its *structure*: left
  sidebar nav, a row of stat tiles, one big chart beside a compact secondary
  visual (their heatmap), and a data table with inline bars. Calm, dense,
  legible.
- **SugarCRM "Customer Journeys"** → we take its *warmth*: a softly tinted
  canvas instead of flat white, very rounded cards that feel physical, pill
  buttons, and **one dark emphasis element** per screen (their black "Request
  Processing" pill) that anchors the eye.

Rendered not in their cold gray/blue but in **Spendy's own palette** — warm
cream canvas, peach tints, coral accent, ink text — pulled directly from the
consumer app so both sides of the product are unmistakably one brand.

## Brand tokens (source of truth: `smart-spend-buddy/src/styles.css`)

| Token | Value | Hex (computed) | Use |
|-------|-------|-----|-----|
| `--cream` | `oklch(0.975 0.022 80)` | `#fff6e7` | app canvas |
| `--cream-deep` | `oklch(0.945 0.04 70)` | `#ffe9d1` | tinted fills, meter tracks |
| `--peach` | `oklch(0.86 0.09 55)` | `#ffc298` | accents, tints, de-emphasis marks |
| `--coral` | `oklch(0.72 0.17 38)` | `#fb784f` | primary actions, brand moments |
| `--coral-deep` | `oklch(0.64 0.20 32)` | `#ec4d33` | chart lines/marks, hover states |
| `--ink` | `oklch(0.18 0.02 50)` | `#190f0a` | text, the dark emphasis card |
| muted text | `oklch(0.45 0.02 60)` | `#5e534a` | secondary text (7.5:1 on white) |
| `--border` | `oklch(0.9 0.025 70)` | `#e9dccd` | hairlines, card borders |
| `--radius` | `1.25rem` | — | cards 20px, buttons/pills full-round |
| shadows | `shadow-soft` / `shadow-card` | — | warm-tinted, inset top highlight — copy values verbatim |
| canvas wash | two radial gradients (peach top-left, coral bottom-right) | — | copy `styles.css` body background verbatim |

**Type:** Inter (UI, data, numbers) · Instrument Serif (page headings only —
personality, never data) · lowercase **spendy** wordmark in Nunito 800,
`-0.02em`, coral `#ee7a5f`. **Logo:** two tilted rounded rects (`#f7c9a8` at
−14°, `#f0a988` at +6°) + wordmark, reproduced as inline SVG.
**Icons:** lucide, 2px stroke, `1em` sizing — never emoji.

**A contrast rule discovered while validating:** brand coral `#fb784f` is only
**2.66:1** on white — fine for buttons and fills, **too light for chart lines
and small marks**. Data marks use **coral-deep `#ec4d33` (3.70:1)**; coral is
the wash/fill hue. The heatmap uses a monotone warm ramp
`#feeee6 → #ffd3bc → #fbaf8f → #f28058 → #da4624` (one hue family, lightness
strictly decreasing).

## Anti-slop rules (what makes it not look AI-generated)

1. **One accent.** Coral only. No purple-blue gradients, no rainbow charts, no
   second accent "for variety".
2. **No emoji as icons.** Lucide strokes everywhere. Emoji appear only inside
   user content (never chrome).
3. **No glow.** Shadows are the two warm brand shadows; nothing luminous, no
   neon borders, no glassmorphism blur.
4. **Serif is for headings, sans is for data.** Instrument Serif gives the page
   its voice; every number is Inter (semibold for values, `tabular-nums` only
   inside table columns).
5. **8px spacing grid, one radius family.** 20/24px cards, full-round pills —
   no mixed corner radii per card.
6. **Real data or no data.** Mocks use plausible AUD figures, real Sydney
   suburb/cafe names, believable dates. Never "Lorem", never "$1,234,567",
   never five metrics all trending up 12%.
7. **One dark emphasis moment per screen** — the ink card (à la SugarCRM's
   black pill). If everything shouts, nothing does.
8. **Warm neutrals.** Grays are gray-browns from the brand ramp (`#5e534a`,
   `#e9dccd`) — never `#888`, never cold slate.
9. **Charts follow the dataviz method**: 2px lines, ~10% area washes, ≥8px
   end-markers with 2px surface rings, hairline solid gridlines, selective
   direct labels (endpoint only), no legend for a single series, sequential =
   one hue light→dark, tooltips on hover, status always icon + label (never
   colour alone).

## Screen specs (the six MVP screens)

### 1. Dashboard (mocked)
Sidebar (240px, white, warm border) → logo + "for business" tag; nav: Overview
(Dashboard) / Actions (Issue a card, Redeem, Share kit) / Manage (Cards,
Customers `v1.x`, Settings); help + account at bottom. Main: serif page title +
retailer identity; coral "Issue gift card" CTA top-right. Row of 4 stat tiles
(outstanding balance + sparkline, cards sold this month, redemption rate vs
~19% national loss, avg spend above balance). Chart row: gift-card sales area
chart (8 weeks) beside peak-redemption-hours heatmap. Bottom: recent-cards
table (code, holder, type, balance meter, expiry, status pill) beside the **ink
Counter-QR card** (the dark emphasis moment) with print + copy-link actions.

### 2. Issue
One card, two segmented modes (Gift card / Store credit). Amount presets
($25/$50/$100 + custom), recipient phone/email, optional note, big coral
confirm. Success state shows the claim link + "sent" confirmation. Total time
target: under 15 seconds.

### 3. Redeem
Full-screen staff mode, ink background (it's the one screen used mid-service):
camera viewport for QR, 6-char code fallback, then balance → amount keypad →
confirm → new balance. Giant touch targets; works one-handed on a phone.

### 4. Cards
The ledger as a full-page table: search, status/type filters in one row above,
CSV export. Same row anatomy as the dashboard table.

### 5. Share kit
Grid of ready assets: counter QR (A6/A4 print), purchase link with copy button,
Instagram-story tile. Each card shows a live preview in the retailer's own card
branding.

### 6. Settings
Business profile, card branding (logo upload + colour → live card preview),
payout details, staff PINs. Card preview uses the same card component the
consumer app renders — the brand bridge, literally.

## The mock

[`mock/dashboard.html`](../mock/dashboard.html) — a single self-contained HTML
file (inline SVG icons and charts, no JS libraries, Google-Fonts link with
system fallbacks). Open it in any browser. It is the visual contract for
screen 1 and the component kit (tiles, table, pills, buttons, chart styles) for
the other five.
