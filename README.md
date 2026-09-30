# Monthly Expense Tracker — with cross-device sync

**The file:** `expense-tracker.html` — one self-contained page. No account, no sign-in form, no server of mine in the middle.

Set up for you: **£6,500 income**, **£2,750 fixed-bills budget**, **12 rolling months from Oct 2026**, **£ GBP**.

Two ways to use it:

| | Works | Needs |
|---|---|---|
| **Offline mode** | Everything except sync. Data lives in the browser that opened the file | Nothing |
| **Cloud sync** | Same numbers on phone, PC, anywhere — auto-saved | A free GitHub account + a token (3 min setup) |

---

## A. Get the web link (do this once, on your PC)

You'll need a GitHub account (you already have `venjercode`).

1. Create a repo, e.g. **`expenses`**. Public or private both work for the *code* — no money figures ever go in the repo.
2. Upload `expense-tracker.html` to it (drag-and-drop on the repo page → "Commit changes").
3. Repo → **Settings → Pages** → Source: **Deploy from a branch** → Branch: **main**, folder **/ (root)** → Save.
4. Two minutes later your link is live:
   `https://venjercode.github.io/expenses/expense-tracker.html`
   *(If you keep the repo private, Pages needs a paid plan — a public repo is fine here, since only the app lives in it. The data goes to a secret gist instead.)*

Open that link on the phone and **Add to Home Screen** — it behaves like an app.

> Prefer Bitbucket? It can host the file, but Bitbucket killed app passwords in June 2026 and its snippet API needs email + API-token basic auth from the browser, so the auto-save half is GitHub-only. Say the word if you want it wired up anyway.

---

## B. Turn on sync (same 3 minutes)

**On the PC (first device):**

1. Get a token — open this link (it pre-ticks everything for you), press **Generate token**, copy it:
   `https://github.com/settings/tokens/new?scopes=gist&description=Monthly%20Expense%20Tracker&default_expires_at=90`
   *(Fine-grained alternative: `https://github.com/settings/personal-access-tokens/new?name=Monthly%20Expense%20Tracker&expires_in=366&gists=write` — needs **Gists: read and write**.)*
   The app itself has a **“Get a token ↗”** button that opens the same page.
2. Open your tracker → **☁ Sync across your devices** → paste the token → **Connect**.
   The app creates a **secret gist** for you and pushes this device's numbers into it.
3. Copy the **Gist ID** shown in the panel.

**On the phone (every other device):**

4. Open the same web link → paste the **same token** → paste the **Gist ID** → **Connect**.
   It pulls your numbers down automatically, then keeps both sides in step.

What happens from then on: every edit saves locally first (so a bad connection can never lose it), then pushes to your gist about a second later. Each open page also checks the cloud every 45 seconds and whenever you switch back to it — so a charge logged on the phone appears on the PC on its own.

---

## C. Rules the app follows so nothing gets lost

- **Both devices changed since the last sync?** The app refuses to guess. You get a **“Pick a version”** warning with both copies listed, their fingerprint, and a button each. Whichever copy you *don't* pick is parked and downloadable — nothing is deleted quietly.
- **New empty device?** It adopts the cloud copy silently, no questions.
- **Push this device up** overwrites the cloud with this device (cloud copy parked first).
- **Load cloud copy** replaces this device (this device's copy parked first).
- **Disconnect** stops all cloud traffic on that device. Local data and the gist both stay.

**Never send your token to anyone** — not to me, not in a chat, not in a screenshot. Paste it straight into the app's box on your own device. If it ever leaks, revoke it at `https://github.com/settings/tokens` (one click) and make a new one; nothing else breaks.

**Your token:** stored only in that one browser, never inside the gist, never in an exported file. It can only touch gists. Revoke it any time in GitHub — worst case, sync stops.

**Still do this:** **Export backup** at the end of each month and keep the file. Sync protects you from device loss; the backup protects you from everything else.

---

## D. Everyday use

| What you want | Where |
|---|---|
| Log a charge in seconds | **Add a charge** box, or the **＋ Add charge** button (bottom-right on phone) |
| One month's numbers | **Month summary** → pick the month |
| Compare months | **All 12 months at a glance** — the whole year on one page |
| Fix a mis-filed charge | Tap any cell → each charge has its own dropdown → re-file it |
| Repeat a bill across months | **↻ Fill forward** (all rows) or ↻ on a single row |
| Add a category to the dropdown | **My categories** → **+ Add category** (Fixed / Variable / Savings) |
| Move the 12-month window | **‹ ›** or **This month** in the header |
| Excel / Sheets | **Export CSV** |

Totals: **Spent** = Fixed + Variable · **Saved** = Savings rows · **Left over** = income − spent − saved. Fixed bills are watched against your **£2,750** line — that row and the bar turn red the moment you cross it.
