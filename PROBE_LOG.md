# Probe Log

This file records each cross-branch README image probe run from `main` against assets on `develop`.

## Probe 01

- Change made: Added a Markdown image on `main` that points to a `develop`-only asset via `raw.githubusercontent.com`.
- What this tests: Whether GitHub README rendering on `main` will resolve and display an image hosted on another branch when the URL is absolute and explicitly names `develop`.
- Syntax under test: `![alt](https://raw.githubusercontent.com/hesreallyhim/test-cross-branch-image-links/develop/assets/inbox-02.png)`
- Expected result: The image resolves because the URL is absolute and targets an existing file on `develop`.
- Outcome: Pending GitHub render verification after push.
