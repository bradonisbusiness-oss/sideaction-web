# SideAction Waitlist QA Runbook

Purpose: verify that `sideactionapp.com` actually captures waitlist signups end to end before pushing harder on traffic.

## Why this matters

The page can look right and still fail on the only thing that matters right now: getting real emails into Mailchimp.

Do this once after any meaningful waitlist form change.

## Pass criteria

A test is only a pass if **all 5** happen:

1. A signup is submitted on the live site.
2. The page shows the inline success state.
3. The email appears in the correct Mailchimp audience.
4. `MMERGE6` source value is populated so we know which form captured it.
5. `MMERGE7` fit value is populated so we know which message variant the visitor saw.

If any one of those fails, treat signup capture as not verified.

## Recommended test emails

Use tagged emails so each form can be tested cleanly.

Examples:
- `yourname+sa-hero@example.com`
- `yourname+sa-mid@example.com`
- `yourname+sa-bottom@example.com`

## Live test order

### Test 1: hero inline form

URL:
- `https://sideactionapp.com/`

Steps:
1. Open the live site in a private/incognito window.
2. Submit the hero inline waitlist form with a tagged email.
3. Wait for the inline success message.
4. Check Mailchimp for the new contact.
5. Confirm these fields:
   - Email = submitted test email
   - `MMERGE6` source contains `hero-inline`
   - `MMERGE7` fit contains the active fit, likely `sports-bets`

Expected result:
- Contact exists in Mailchimp within a minute.
- Source and fit fields are not blank.

### Test 2: mid-page detailed form

Steps:
1. Reload fresh.
2. Submit the `#hero-waitlist` form with a new tagged email.
3. Confirm success state and Mailchimp capture.
4. Confirm `MMERGE6` contains `hero-detail`.

### Test 3: bottom CTA form

Steps:
1. Reload fresh.
2. Submit the `#waitlist` form with a new tagged email.
3. Confirm success state and Mailchimp capture.
4. Confirm `MMERGE6` contains `cta-bottom`.

## Fit-specific test

Purpose: make sure fit routing updates the hidden fields correctly.

Use one of these URLs:
- `https://sideactionapp.com/?fit=prop-bets`
- `https://sideactionapp.com/?fit=side-deals`

Steps:
1. Open one fit-specific URL in a private window.
2. Submit the hero inline form.
3. Confirm Mailchimp shows `MMERGE7` matching that fit.
4. Confirm the page copy and CTA changed to match the fit.

## What to screenshot if something breaks

Capture these 4 things:
1. The submitted form and visible success or error state
2. Browser console errors
3. Network request result if visible
4. The Mailchimp contact record or missing-contact proof

## Fail patterns to watch for

- Inline success appears but no Mailchimp contact is created
- Contact is created but `MMERGE6` source is blank
- Contact is created but `MMERGE7` fit is blank or wrong
- One form works and another does not
- Success on desktop but failure on mobile
- Fit-specific URL updates copy but not hidden fields

## If the test passes

Then do these next:
1. Turn on Mailchimp new-subscriber notifications
2. Start measuring which source values convert best
3. Push harder on X / Instagram / Reddit traffic

## If the test fails

Fix in this order:
1. Live capture itself
2. Hidden source / fit attribution
3. Success / error UI clarity
4. Traffic push

Do not push significant traffic before step 1 is verified on the live site.
