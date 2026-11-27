# Rider Saathi Pro V8.2 — BugFix Edition

Mobile-first PWA based on the V8 Ultimate Rider Assistant. The Neon Rider Cockpit visual style and existing calculator, platform rates, orders, expenses, reports, assistant, timers, GPS, local backup/restore and analytics are retained.

## V8.2 fixes
- Midnight rollover: the "today" lists (orders, incentives, expenses, other costs, trips) now reset automatically when the date changes, even if the app stays open overnight. Monthly history is kept.
- CSV report now has a Date column (plus Time), so monthly rows can be read by day. CSV cells are also protected against spreadsheet formula injection.
- GPS: points with accuracy worse than 40 m are skipped, tiny stationary jitter is ignored, and the screen is kept awake while GPS is running (needs HTTPS and a browser that supports Screen Wake Lock).
- Code cleanup: 11 duplicate function definitions removed (the version that was actually running is kept, so behaviour is unchanged).
- Version labels, manifest and service-worker cache updated to V8.2.

## V8.1 fixes
- PIN change requires the current PIN. New PIN hashes use PBKDF2-HMAC-SHA256 (150,000 iterations, random salt). Existing V8 SHA-256 PINs are supported and upgraded after successful unlock.
- Firebase Auto Sync uses ETag conditional writes (`X-Firebase-ETag` + `if-match`) and retries concurrent-write conflicts up to four attempts.
- Deleted order/expense IDs are retained as tombstones and merged, reducing record resurrection after syncing multiple devices.
- Edited orders get `updatedAt` metadata.
- GPS validates coordinates and reports errors, clearing the watch after a failure so it can be restarted.
- Monthly incentive history is retained, migrated from V8 daily records where possible, and included in reports/analytics.
- Monthly history load limit matches the persistence limit.

## Run / host
1. Extract the ZIP.
2. For local testing, serve the folder using a local web server; for production use HTTPS hosting.
3. GitHub Pages can host the extracted project files. Upload the contents of the project folder (not only the ZIP) to the repository.
4. Open the hosted `index.html` URL. Install as a PWA from Chrome only after verifying the hosted build.

## Firebase setup and safety
1. Create a Firebase Realtime Database and copy its HTTPS database URL.
2. Use a unique rider-specific path, for example `riders/your-rider-id`.
3. Configure authenticated Firebase access / database rules for that rider. Add a valid Firebase ID token only if your deployment obtains and refreshes it securely.
4. Never enable public read/write rules. Never publish tokens or credentials in a public GitHub repository.
5. Auto Sync reads the selected node with an ETag, merges records and tombstones, then writes conditionally with `if-match`. If another device changes the node first, Firebase returns a conflict and the app retries. This is safer than the previous unconditional GET/PUT flow, but it is not a substitute for a server-side transaction model for high-concurrency multi-user systems.
6. The token field, if used, is stored in browser localStorage. Avoid saving tokens on shared devices.

## PIN limitations
The PIN is a local app lock. It does not encrypt the stored orders/rates in localStorage and does not authenticate the rider to Firebase. Use Android's device lock and proper Firebase Authentication / database rules as well.

## Backups
- Use the app's **Backup घ्या** button regularly and store the JSON file somewhere separate from the phone.
- Automatic local snapshots are best-effort and retain up to five snapshots in the same browser storage. They are not a replacement for an exported backup.
- The Assistant tab has a separate chat export for the in-app assistant messages.
- A separate project-chat backup summary is included in the supplied backup files; ChatGPT does not automatically export the entire conversation after each reply.

## Verification status
See `CHANGELOG.md` and `QA_REPORT.md`. Static syntax, manifest and HTML structure checks were performed. Real Android, GPS field, Firebase and multi-device tests remain pending.
