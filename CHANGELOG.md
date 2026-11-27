# Rider Saathi Pro — Changelog

## V8.4.0 — Professional theme
- New visual theme: slate surfaces, a single amber accent for actions and the net-pay figure, flat cards with thin borders.
- Bottom tabs use line icons instead of emoji; active tab marked with an amber indicator.
- Platform selector shows a small brand-colour dot; emoji removed from headings and labels (translations updated to match).
- Header simplified; theme colours in manifest and browser bar updated.
- No change to data, calculations or Backup format.

## V8.3.0 — Simple Edition
- Removed all Cloud / Firebase features (Push, Pull, Auto Sync, token fields). Data stays on the phone; use Backup घ्या / Backup Restore निवडा.
- Added a Backup / Restore card to Settings (same buttons as the Orders tab).
- Backup file format unchanged, so older V8.x backups still restore.
- Removed the code that only existed for cloud merging.

## V8.2.0
- Automatic midnight rollover of daily lists; monthly history kept.
- CSV report has a Date column and is protected against formula injection.
- GPS ignores weak/stationary readings and keeps the screen awake while tracking.
- Removed 11 duplicate function definitions.

## V8.1.0
- PIN change requires the current PIN; PBKDF2 hashing for new PINs.
- Deletion tombstones, `updatedAt` on edits, GPS error handling.
- Monthly incentive history retained; monthly load cap matches persistence cap.

## Verification
- JavaScript, service-worker and manifest syntax checks passed; no undefined element IDs or handlers.
- Simulated test (stubbed browser): old-app data restored (24 orders, 6 expenses, 2 incentives), orders after midnight land under the new date, CSV shows the Date column.
- Not tested: real Android phone, GPS outdoors, wake lock on device.
