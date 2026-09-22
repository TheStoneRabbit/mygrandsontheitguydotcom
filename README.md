# My Grandson The IT Guy — Website

Marketing site for **My Grandson The IT Guy** (mygrandsontheitguy.com), the
consumer subscription line of Stone Rabbit Technologies LLC. Helps older and
non-technical people in lower Fairfield County manage email, passwords, and
their online accounts.

Strategy, pricing derivation, and the legal/custody model live in the business
repo: `docs/MY_GRANDSON_THE_IT_GUY.md`.

## ⚠️ Do not point DNS at this yet

This site is **a draft**. Several things in §6 of the strategy doc must be done
before it goes live — see the pre-launch checklist below. A live page selling a
service that isn't legally set up is a real problem, not a cosmetic one.

## Stack

Static — no build step, no dependencies. Same approach as the Stone Rabbit site.

```
index.html        # all page content
css/styles.css    # design system + responsive layout
js/main.js        # mobile menu, scroll reveals, footer year
CNAME             # mygrandsontheitguy.com
```

## Design

Deliberately different from stonerabbittechnologies.com. That site sells
engineering to businesses; this one sells reassurance to people in their
seventies and to their adult children.

- **Palette:** calm teal `#2b6b66` on warm cream `#fdfaf6`, warm amber `#a85615`
  for accents. No red — it reads as alarm to this audience.
- **Type:** Lora (serif headings, warm and human) + Inter (body). **19px base**,
  noticeably larger than a standard marketing site. This is the single most
  important accessibility decision on the page — don't shrink it.
- **Contrast:** body text ~7.5:1, headings ~14:1. Comfortably past WCAG AA.
- **Tap targets:** buttons are ≥56px tall.
- **Phone number is the primary call to action** everywhere. This audience
  calls; they don't fill in forms. Every plan's button dials rather than submits.
- Fully responsive, `prefers-reduced-motion` respected, works without JS.

## Page order, and why

Problems → what I help with → scam check → plans → **my promise** → for family →
steps → about → contact.

The **promise** section (the custody rules, stated publicly) is load-bearing,
not decoration. It is the strongest trust asset the business has and it
pre-empts the first objection any adult child will raise. Don't move it below
the fold or soften it.

## Pre-launch checklist

- [ ] Create the mailboxes: `hello@mygrandsontheitguy.com` and
      `check@mygrandsontheitguy.com` (both are referenced on the page)
- [ ] Write `privacy.html` and `terms.html` — the footer links to both
- [ ] Replace the `ML` monogram with a real photograph. For this audience a
      face materially outperforms a monogram
- [ ] Add a favicon and an Open Graph image to `assets/`
- [ ] Trade name registered with the Stamford town clerk
- [ ] E&O + general liability bound, in-home visits disclosed
- [x] Yale outside-activity policy cleared (2026-09-22)
- [ ] Subscription agreement drafted and attorney-reviewed
- [ ] Replace the example monthly summary with a real (anonymised) one
- [ ] Add testimonials once the founding cohort exists — this section is
      missing on purpose rather than filled with invented quotes

## Run locally

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Deploy

GitHub Pages: push, enable Pages on the branch root, then point the domain at
it. `CNAME` is already set. Netlify/Vercel/Cloudflare Pages also work with no
build command and `.` as the publish directory.

## Keeping prices honest

Prices on this page are derived from the pricing engine in the business repo,
not typed from memory:

```bash
python3 .claude/skills/quote/pricing.py --mgtig
```

If a price changes there, it changes here and in
`docs/MY_GRANDSON_THE_IT_GUY.md` in the same pass. The three must never drift.
