# Zen River Publishing

The Zen River Publishing hub — a single-page reader landing hub for the *Hours Back* series by Maya Bennett.

- `index.html` — the whole site (styles + scripts inline, no build step, no dependencies)
- Books link out to Amazon (`amazon.com/dp/<ASIN>`) — the ebooks are KDP Select exclusive, so they are never sold directly here
- Email capture: signup band framed as **free-book alerts** ("The Sunday Reset"). Currently wired to
  [FormSubmit](https://formsubmit.co) AJAX → `james.robinson12128@gmail.com` (**activated 2026-10-06**) as the
  working interim. The form block is wrapped in `EMAIL-FORM-START` / `EMAIL-FORM-END` comment markers —
  swapping in the Brevo embed later is a delete-and-paste (see `BUILD-NOTES.md`).
- Book #1's "Free Oct 5–9" promo badge **auto-expires** via the `PROMO_END_UTC` script (end of Oct 9 Pacific);
  the card reverts to the normal $3.99 price/button with no manual edit. Promo blocks also wrapped in
  `FREE-PROMO-START` / `FREE-PROMO-END` comments for manual removal.
- `BUILD-NOTES.md` — what changed in Phase 1, Jim's 4 Brevo steps, post-Oct-9 notes, pre-push approvals.

Published with GitHub Pages from the `main` branch. Jim pushes via his usual git flow (never push for him).
