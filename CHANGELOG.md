# Rider Saathi Pro — Changelog

## V8.2.0 — BugFix Edition

### Fixed / improved
- Automatic midnight rollover of daily lists (orders, incentives, expenses, other costs, trips); checked every 15 s, on returning to the app and before adding an order/expense/incentive. Monthly history is unaffected.
- CSV export includes a Date column and neutralises formula-like text.
- GPS ignores readings worse than 40 m accuracy and stationary jitter; Screen Wake Lock keeps the screen on while tracking.
- Removed 11 duplicate function definitions (no behaviour change).
- Version labels, manifest and service-worker cache bumped to V8.2.

### Verification performed
- JavaScript, service-worker and manifest syntax checks: passed.
- Simulated test (stubbed browser): an order added after midnight lands under the new date, today's list resets, monthly history keeps both days, CSV shows the Date column.
- Not tested: real Android phone, GPS outdoors, Firebase sync, wake lock on device.

## V8.1.0 — BugFix Edition

### Fixed / improved
- PIN change now requires verification of the current PIN before allowing a replacement.
- New PINs use PBKDF2-HMAC-SHA256 with a random salt and 150,000 iterations. Existing V8 SHA-256 PIN records remain compatible and are upgraded after a successful unlock.
- Firebase Auto Sync now requests an RTDB ETag and uses conditional `if-match` writes, retrying up to four times after a concurrent-write conflict (HTTP 412).
- Order and expense deletions now create tombstones. Tombstones are merged across devices and suppress deleted records from reappearing during subsequent syncs.
- Edited orders now receive an `updatedAt` timestamp for more reliable record merging.
- GPS watch now validates coordinates and reports permission, unavailable-position, and timeout errors; the watch is cleared after an error so the rider can retry.
- Monthly incentive history is retained and included in CSV/Excel/PDF exports and monthly analytics. Existing V8 daily incentive data is migrated into the monthly history when possible.
- Monthly order history load cap now matches the 3,000-record persistence cap.
- Cloud Push now uses the guarded merge sync path rather than an unconditional overwrite.
- Updated app metadata, icon label, manifest and service-worker cache version to V8.1.

### Preserved
- Neon Rider Cockpit design, five bottom tabs, platform selector, calculator, expenses, reports, assistant, voice input, timers, GPS, manual backup/restore, PIN lock, auto local snapshots and analytics.

## Verification performed
- JavaScript syntax check (`node --check`): passed.
- Manifest JSON parse: passed.
- HTML static audit: 94 unique IDs; no duplicate IDs.
- Inline handler scan: no unresolved function references found (one false-positive parser match for Promise `.catch`).
- Source/asset inspection: performed.
- ZIP integrity check: to be performed on final archive.

## Not tested / remaining limitations
- No real Android phone or Android Chrome end-to-end test was possible in this build environment.
- Firebase ETag conditional requests, authentication, database rules, CORS, network interruption and multi-device race scenarios still require testing with the user's own Firebase project.
- Firebase credentials are not bundled. Never use public read/write database rules.
- The PIN remains a local UI access barrier; it does not encrypt all localStorage data and is not Firebase Authentication.
- GPS distance needs a real outdoor ride test; phone GPS quality and power-management settings vary.
- Speech recognition availability depends on browser/device and microphone permission.
- Earnings remain estimates based on rider-entered rates and data; there are no official platform APIs.
- A full visual regression test on multiple Android screen sizes was not performed. CSS overrides inherited from earlier versions remain and may need a dedicated cleanup pass.
