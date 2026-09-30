# Monthly Expense Tracker

A single-page expense tracker that keeps all 12 months of the year on one screen, with a
customisable category dropdown and a private cloud sync so the same numbers follow you
between your phone and your computer.

**Open the app:** [expense-tracker.html](expense-tracker.html)

## What it does

- Log a charge in seconds: pick a category, set the **date of expense**, type the amount, press Enter.
- Every month of the year on one page, so months sit side by side and compare at a glance.
- Tap any cell to see and edit the individual charges behind that month's total — each with its own **date**, amount, category and note.
- Categories are yours: add, rename, re-type (Fixed / Variable / Savings), reorder or delete.
- **Monthly amount**: one default, overridable for any single month (those months are tagged *own*).
- Fixed bills are just categories — no target to maintain. Log them and the monthly **Fixed total** row does the rest.
- Month summary tiles, a 12-month trend chart, and a fixed-bills line that turns red in any month where you go over.
- Savings are tracked separately from spending, so putting money aside never looks like an expense.
- Moving a charge's date into another month moves the charge with it; **Fill forward** repeats a bill on the same day each month.
- Export to CSV for Excel or Sheets (monthly grid, or every charge line by line with dates), and export/import a JSON backup.

## Sync between devices

The app can save to a **private GitHub gist** you own, so your figures are never stored
anywhere else. It needs a GitHub token with the `gist` scope, entered once per device —
the app walks you through it, with a pre-filled link that sets up the token for you.

Sync rules: every change saves locally first, then pushes to your gist a second later.
If two devices both changed, the app asks which copy to keep instead of guessing, and the
losing copy is parked rather than deleted.

## Getting a link

Put `expense-tracker.html` (and `index.html`) in a repository you own, then **Settings → Pages →
Deploy from a branch → main / root**. GitHub serves it at
`https://<username>.github.io/<repo>/`. Note that on a free plan the repository must be **public**
for Pages to publish — the repo holds only this app, never your figures.

## Running it

It is one self-contained HTML file — no build step, no dependencies, no server. Open
`expense-tracker.html` in any browser, or host it anywhere static and use that link.

Your data stays in your own browser and your own gist. Nothing is sent to the author of this page.
