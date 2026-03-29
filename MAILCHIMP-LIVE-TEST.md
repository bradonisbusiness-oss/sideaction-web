# SideAction live signup test

## Why this matters
Do not push real traffic until one live signup is proven to work on `sideactionapp.com`.

## Goal
Confirm all 3 things in one pass:
1. The form submits from the live site
2. The email lands in the right Mailchimp audience
3. The on-page success state shows after submit

## 3-minute test

### 1) Prep
- Open `https://sideactionapp.com/` in an incognito window
- Open Mailchimp audience view in another tab
- Use a fresh test email you control
  - Example: `bradon+sideactiontest1@yourdomain.com`

### 2) Submit on the live site
- Use the **first hero waitlist form**
- Enter the fresh email
- Click submit

## Pass criteria on the site
- Button changes to success state
- Success message appears
- No Mailchimp error message appears

## Pass criteria in Mailchimp
- The exact email shows up in the audience
- It appears as a new contact, not missing
- If merge fields are visible, confirm:
  - `MMERGE6` captured source info
  - `MMERGE7` captured fit/use-case info

## If it fails

### If the page shows an error
Check:
- wrong Mailchimp form action
- JS submit/JSONP issue
- browser console errors

### If the page says success but Mailchimp shows nothing
Check:
- wrong audience/list ID
- hidden iframe / JSONP mismatch
- duplicate-email false positive

### If Mailchimp gets the lead but page UX fails
Check:
- success message rendering
- submit button reset state
- timeout fallback showing too early

## After a pass
Do these immediately:
1. Turn on Mailchimp new-subscriber notifications
2. Save one screenshot of:
   - success state on site
   - matching contact in Mailchimp
3. Then start pushing harder on X / Instagram traffic assets

## Suggested test log
- Date:
- Test email used:
- Submitted from:
- Success state shown on site: Yes / No
- Contact appeared in Mailchimp: Yes / No
- MMERGE6 captured: Yes / No
- MMERGE7 captured: Yes / No
- Next action:

## Important
Run this on the live domain, not a local file or preview only.
