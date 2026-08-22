# Vidhya Industries Billing — Simple Edition

No server, no database, no npm, no git, no Vercel. Everything lives in
this browser via `localStorage`. Same architecture as your Update Cars
billing app.

## How to run it

**Option A — just open it.** Double-click `index.html`. That's it — it
works immediately, no setup.

**Option B — install as an app on your phone (recommended for daily use).**
This needs to be served over `http://` or `https://`, not opened directly
as a file, for the "Install app" / "Add to Home Screen" feature to work.
Easiest ways to get that:
- Upload all 6 files to any free static host (GitHub Pages, Netlify, or
  even a folder in Google Drive shared as a website via a service like
  Vercel's drag-and-drop deploy — no build step needed, just upload as-is)
- Or run a tiny local server on your own machine when testing:
  `npx serve .` (from inside this folder), then open the URL it gives you

Once it's served over http(s):
- **Android (Chrome):** open the URL, tap the menu → "Install app"
- **iPhone (Safari):** open the URL, tap Share → "Add to Home Screen"

## First login

- Name: **Admin**
- PIN: **1234**

Go to **Users** and change this (or add a real named user and delete
Admin) before relying on this for real billing.

## Your data lives on THIS device only

This is the most important thing to understand about this version:
there's no server, so there's no automatic multi-device sync. If you use
this on your phone and your laptop, they will have **two separate,
independent sets of data** unless you manually export from one and import
into the other.

For one person (or one shared device) doing all the billing, this is
exactly the right amount of complexity — nothing to configure, nothing to
pay for, nothing that can go down. If you ever need multiple staff on
different devices to see the same live invoices in real time, that's the
point where the fuller version (the Next.js + database one built earlier
in this conversation) becomes worth its extra setup — not before.

## Backing up your data (do this regularly)

Three ways, in **Settings**:

1. **Download Backup** — saves a `.json` file to your Downloads folder.
   Keep a few of these somewhere safe.
2. **Restore from File** — loads a previously downloaded backup, replacing
   everything currently in the app. Useful for moving to a new
   phone/laptop, or recovering after clearing browser data.
3. **Cloud Backup** — one-time setup using `cloud-backup-script.gs.txt`
   (a Google Apps Script that saves timestamped backups to your own Google
   Drive automatically). Setup instructions are the first comment block
   inside that file — about 5 minutes, no coding needed, just copy-paste
   and click Deploy.

## What was verified before this was handed to you

- The GST engine (CGST+SGST for same-state, IGST for inter-state) was
  tested against known amounts and confirmed correct
- Sequential invoice numbering, partial payments, overpayment rejection,
  and payment-status transitions (unpaid → partial → paid) were all
  exercised end-to-end
- Currency formatting and amount-in-words (for the "Rupees ... Only" line
  on invoices) were checked against known values
- The print/PDF preview was confirmed to render the right invoice number,
  customer, and totals

One thing this build process could NOT verify directly: exactly how the
install prompt and standalone app window look on a real phone (my
environment has no way to run a real mobile browser). The manifest and
icons follow the same structure as your working Update Cars app, so it
should behave the same way — worth a quick check on your own phone before
relying on it.
