# Rider Saathi Pro V8.4 — Pro Theme

Mobile-first PWA for delivery riders: earnings calculator, orders, expenses, reports, assistant, timers, GPS, PIN lock and analytics. **All data is stored only on the phone.** There is no cloud / Firebase sync in this version.

## Backup / Restore (how to keep data safe)
- **Backup घ्या** → saves a `.json` file. Available in the Orders tab (bottom of page) and in Settings → Backup / Restore.
- **Backup Restore निवडा** → pick a saved `.json` file to bring the data back. Restoring replaces the data currently in the app.
- Take a backup about once a week and keep the file somewhere other than the phone (WhatsApp to yourself, Google Drive).
- Automatic local snapshots (last five) are kept in the same browser storage; they are not a replacement for an exported backup.

## Host on GitHub Pages
Upload the **files** (not the ZIP itself) to the repository root: `index.html`, `sw.js`, `manifest.webmanifest`, `icon.svg` (plus README/CHANGELOG). Open the hosted URL over HTTPS. Data is tied to that address and browser, so always use the same address.

## Notes
- The PIN is a local app lock; it does not encrypt data stored on the phone.
- Earnings are estimates from the rates you enter; there are no official platform APIs.
- GPS keeps the screen awake while tracking (needs HTTPS and a supporting browser) and ignores weak readings (>40 m) and standing-still jitter.
- Daily lists reset automatically at midnight; monthly history is kept.
- Real-phone testing of GPS and the wake lock is still pending.
