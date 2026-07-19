# 07 — The Retailer Platform MVP: What Small Retailers Pay For

[03 — MVP](03-mvp.md) defined the loop (issue → claim → redeem) and the
no-funds-held money flow. This doc goes a level deeper: **which features a cafe,
coffee shop, or restaurant owner actually cares about enough to pay for**, and
what the platform MVP is, screen by screen. The UI itself is specified in
[08 — UI design](08-ui-design.md) with a clickable mock at
[`mock/dashboard.html`](../mock/dashboard.html).

## The one rule of selling to small hospitality

**Cafes don't buy software. They buy revenue they can see.**

A cafe owner already gives Uber Eats and DoorDash **20–30%** of every delivery
order and pays **~1.5–2%** on every card tap — because those costs are attached
to visible money coming in. The same owner will not pay $49/month for a
"platform". So every paid feature must be framed as *a small cut of new money*,
and every free feature exists to make the paid moments happen.

## Features ranked by willingness to pay

### 1. Sell gift cards with zero effort — the #1 pay driver

- A **shareable purchase link** and a **counter QR**: anyone can buy a card for
  themselves or as a gift from the cafe's Instagram bio, Google listing, or the
  sticker next to the till.
- The pitch line: *"Your Instagram followers become prepaid revenue tonight."*
- Why they pay: the money lands **upfront** — gift cards are working capital for
  a business that lives week to week. A % fee on a sale they'd never have made
  feels like Square, not like SaaS.
- This is where Spendy charges (per [04 — Business model](04-business-model.md)):
  a small % on online card sales, nothing else.

### 2. The repeat-visit engine — the #2 pay driver (and the retention proof)

- Every issued card sits in the holder's Spendy app with **live balance and
  smart reminders** — Spendy does the chasing, so the retailer doesn't.
- The dashboard shows the owner the numbers that make it real: **redemption rate
  vs the ~19% national loss rate**, and **average spend above card balance** at
  redemption (the $50-voucher-becomes-$100-basket effect from
  [01 — Opportunity](01-opportunity.md)).
- Why they pay: this is the retention argument made visible. A card that comes
  back is a customer who comes back.

### 3. Store credit instead of cash refunds — the goodwill wedge (always free)

- Two taps to issue **refund-as-credit** to a customer's phone; no scribbled
  note, no argument at the counter.
- Keeps the revenue in the till (~68% of store-credit holders return vs ~45–50%
  for cash refunds).
- **Always free** — it's the moment that makes an owner love the product and the
  wedge that puts Spendy in a new consumer's pocket. Never monetise it.

### 4. Know your customers — the future paid tier

- Who holds unspent value, top customers by lifetime spend, **peak redemption
  hours**, uplift per card.
- Small retailers currently have *nothing* — no CRM, no data. Even basic
  insight feels like magic.
- v1.x, and the anchor of a later Pro tier (with promo pushes and loyalty
  stamps). Not an MVP pay driver — sell revenue first, insight second.

### 5. Zero-hardware redemption — the adoption enabler (not a pay driver)

- Staff redeem by **scanning the customer's QR** or typing a **6-character
  code** on any phone or the counter iPad. Partial redemption, live balance.
- No POS change, no terminal, no training beyond one sentence. This doesn't
  earn money; it removes every excuse not to sign up.

### Fast-follows that deepen the paid tier

Loyalty stamp cards (the daily-visit hook for coffee), opt-in promo pushes to
card holders, POS integrations (Square, Lightspeed), Apple/Google Wallet passes.
All v1.x+ per [02 — Features](02-features.md).

## The MVP platform, screen by screen

Six screens. Everything else is a later tab.

| # | Screen | What it does |
|---|--------|--------------|
| 1 | **Dashboard** | Stat tiles (outstanding balance, cards sold, redemption rate, avg extra spend), gift-card sales chart, peak redemption hours, recent-cards ledger. The screen that proves the value. Mocked in [`mock/dashboard.html`](../mock/dashboard.html). |
| 2 | **Issue** | One form, two modes: gift card (amount → recipient phone/email → pay at till) and store credit (amount → recipient → done). Under 15 seconds during service. |
| 3 | **Redeem** | Full-screen staff mode: camera QR scan or 6-char code entry → shows balance → enter amount → confirm. Built for a phone held in one hand. |
| 4 | **Cards** | The full ledger: every card, holder, balance, expiry, status; filter and CSV export. |
| 5 | **Share kit** | The counter QR as a printable A6/A4 PDF, the purchase link, an Instagram-story-sized tile. Marketing assets, zero design skill needed. |
| 6 | **Settings** | Business profile, card branding (logo + colour), payout details, staff PINs. |

## What the MVP build involves

Consistent with the no-funds-held decision in [03 — MVP](03-mvp.md):

- **Retailer web app** — the six screens above; mobile-friendly (owners live on
  their phones), desktop-capable (bookkeeping day).
- **Card ledger service** — the source of truth for card objects: issue, claim,
  partial redemption, expiry. Store credit and gift cards are the same object
  with a different `origin`.
- **Claim links** — SMS/email links that resolve into the Spendy consumer app,
  with a mobile-web fallback showing the balance and prompting install (the
  acquisition moment).
- **Payments (online sales only)** — direct-to-retailer settlement (e.g. Stripe
  Connect direct charges); Spendy never holds the funds. Till sales use the
  retailer's own EFTPOS and involve no Spendy payment path at all.
- **No POS integration, no native retailer app, no wallet passes** in MVP.

## Pricing recap

Per [04 — Business model](04-business-model.md): **free to join, no monthly fee,
a small % on online card sales** (benchmark assumption 3–6%, to validate),
store credit always free. The Pro tier (insights, promos, loyalty) is the
post-pilot monetisation layer — priced only after the pilot shows which numbers
owners stare at.
