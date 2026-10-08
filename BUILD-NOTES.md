# Reader Hub Phase 1 — Build Notes (2026-10-08)

Built per the CEO's greenlight (~10:40 AM EDT). Source of truth for numbers: the decision brief at
`~/workspace/goals/autonomous-ebook-publishing-company/hidden_files/storefront-decision-brief-2026-10-06.md`.

## What changed in `index.html`

1. **Email capture reframed as a reader magnet.** The signup band now leads with a
   "FREE-BOOK ALERTS" kicker and the promise "Never miss a free book — first dibs on every
   free-book window," plus the existing Sunday Reset newsletter. Hero button changed from
   "Get the newsletter" to "Get free-book alerts." Same `#newsletter` anchor — no links break.
2. **Brevo-ready embed slot.** Everything between `<!-- EMAIL-FORM-START -->` and
   `<!-- EMAIL-FORM-END -->` (form + FormSubmit script) is one self-contained block. Swapping
   in Brevo later = delete that block, paste Brevo's embed code. The section `id="newsletter"`
   stays put. Full instructions are in an HTML comment right above the block.
3. **FormSubmit wired as the WORKING interim.** Same AJAX endpoint as before
   (`formsubmit.co/ajax/james.robinson12128@gmail.com`, activated 2026-10-06). Submissions land
   in Jim's inbox with the subject "New Zen River Publishing subscriber" — no reader is lost
   while Brevo is pending. The submit handler was moved inline next to the form so the Brevo
   swap is a clean delete-and-paste.
4. **Free badge auto-expires.** Book #1's "Free Oct 5–9" badge, free price line, and
   "Download free on Amazon" button automatically revert to the normal `$3.99 Kindle` /
   "Buy on Amazon" card at end of Oct 9 Pacific (script constant `PROMO_END_UTC`,
   bottom of page). Nothing for Jim to do after Oct 9 — but the promo blocks are also wrapped
   in `FREE-PROMO-START` / `FREE-PROMO-END` comments if he ever wants to remove them by hand.
5. **KDP Select compliance.** The hub links OUT to Amazon for all four ebooks. It does not
   sell, give away, or host any enrolled ebook content. (Deliberately NOT offering a "free
   chapter" download: sharing >10% of a Select-enrolled book off Amazon violates the terms.
   The lead magnet is free-book *alerts*, which is the proven funnel anyway.)

## The 4 Brevo steps for Jim (free plan — no card)

1. Go to brevo.com and create a **free** account.
2. Create a contact list named **"Zen River Readers"**.
3. Create a **signup form** attached to that list (Contacts → Forms → Create) and copy the
   **embed code** it gives you.
4. Hand the embed code to Eva — she deletes the block between `EMAIL-FORM-START` and
   `EMAIL-FORM-END` in `index.html` and pastes Brevo's code in. Two-minute change, then push.

Brevo free = unlimited contacts, 300 emails/day, automation included, no credit card
(per the verified 2026-10-06 comparison — beats Mailchimp free and MailerLite free).

## After Oct 9 — nothing required

The badge and free pricing retire themselves via the `PROMO_END_UTC` script. Optional manual
cleanup: delete the `FREE-PROMO-*` comment blocks in the Book #1 card.

## Before pushing live — Jim's approval needed on

- **The signup promise:** "first dibs on every free-book window" commits him to actually
  sending those alerts (Sunday Reset editions + free-run notices). Fine as long as he means it.
- **Copy review:** skim the new signup band once — kicker, headline, and paragraph.
- **Then his usual git flow:** `git add -A && git commit -m "Reader hub phase 1: free-book alerts capture + Brevo slot" && git push`
  (from `~/workspace/zen-river-publishing/`, repo `agileJavaJim/zen-river-publishing`).
  Eva does NOT push — Jim's habit, his hands.
