# XO Playbook v1.2.0 — Friday Night Ready

This folder is a drop-in static-site release. The existing CNAME, Firebase project configuration, icons, and data paths are preserved.

## What changed

- Added a no-account varsity coach demo.
- Reorganized playbook tools into Practice, Game Day, Share, Manage, and Danger Zone groups.
- Added native team sharing, direct-link copying, view-code copying, password reset, and install support.
- Added a service worker for the app shell and corrected the connection indicator.
- Retired client-side legacy password login and removed password display from the admin UI.
- Prevented automatic claiming of unowned playbooks.
- Fixed formation deletion so child plays and uploaded images are cleaned up.
- Added save-on-back behavior in the play and formation editors.
- Fixed Run/Pass metadata when duplicating drawn plays.
- Fixed quiz ambiguity by scoring play IDs and showing formation names.
- Parallelized several repeated database reads and lazy-rendered play previews.
- Improved contrast, browser zoom, focus states, form labels, screen-reader visibility, and icon-button labels.

## Before replacing the live files

1. Keep a copy of the currently deployed release.
2. Upload the contents of this folder together, including `sw.js` and `manifest.json`.
3. Confirm `sw.js` is served from the same directory as `index.html`.
4. Test one coach login, one player view code, one play save, the coach demo, and Share Playbook.
5. Open What's New and confirm the app reports v1.2.0.

## Firebase security follow-up

The supplied archive did not include Firestore or Storage rules, so those rules were not changed here. Before broad school adoption:

- Migrate any remaining legacy coaches to Firebase Authentication, then delete all legacy `password` fields from Firestore.
- Ensure users cannot write their own role or grant themselves Pro/Admin access.
- Ensure only owners/admins can create, edit, assign, or delete playbooks.
- Validate and rate-limit public viewer and leaderboard writes; consider Firebase App Check.
- Decide how team view codes should be revoked and rotated when a season ends.

No deployment or Firebase data migration is performed by this ZIP.
