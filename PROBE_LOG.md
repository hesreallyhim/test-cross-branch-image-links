# Probe Log

This file records the local test suite for GitHub README image rendering from `main` against assets on `develop`.

## Notes

- Important precondition: the target branch must exist on `origin`. Before `origin/develop` existed, direct raw URLs to `develop` returned `404`.
- Current status: suite prepared locally; outcomes remain pending until you approve a push and manual verification on GitHub after rate limiting cools down.

## Probe Matrix

### Probe 00

- Category: baseline control
- Change made: Added a Markdown image that uses a relative path to an asset present on `main`.
- What this tests: Whether normal README image rendering is healthy before interpreting cross-branch results.
- Syntax under test: `![alt](assets/inbox-01.png)`
- Expected result: Should render on `main`.
- Observed outcome: Pending manual GitHub verification.

### Probe 01

- Category: primary null case
- Change made: Added a Markdown image on `main` that points to a `develop`-only asset via `raw.githubusercontent.com`.
- What this tests: Whether GitHub README rendering on `main` will resolve and display an image hosted on another branch when the URL is absolute and explicitly names `develop`.
- Syntax under test: `![alt](https://raw.githubusercontent.com/hesreallyhim/test-cross-branch-image-links/develop/assets/inbox-02.png)`
- Expected result: Should render if cross-branch raw URLs are accepted.
- Observed outcome: Pending manual GitHub verification.

### Probe 02

- Category: syntax variation
- Change made: Added an HTML `<img>` on `main` whose `src` targets a `develop`-only asset via `raw.githubusercontent.com`.
- What this tests: Whether GitHub treats raw HTML image tags differently from Markdown image syntax for cross-branch absolute URLs.
- Syntax under test: `<img src="https://raw.githubusercontent.com/hesreallyhim/test-cross-branch-image-links/develop/assets/inbox-03.png" ...>`
- Expected result: Should render if GitHub preserves the tag and allows the URL.
- Observed outcome: Pending manual GitHub verification.

### Probe 03

- Category: picture/source variation
- Change made: Added a `<picture>` block with a `<source srcset>` pointing to `develop` and a nested `<img>` fallback on `main`.
- What this tests: Whether GitHub README rendering preserves `<picture>` and whether the browser uses the cross-branch `srcset` or falls back to the nested image.
- Syntax under test: `<picture><source srcset="https://raw.githubusercontent.com/.../develop/..."><img src="assets/black-pixel-ish.png"></picture>`
- Expected result: Prefer the `develop` source if preserved; otherwise fall back or degrade.
- Observed outcome: Pending manual GitHub verification.

### Probe 04

- Category: negative control
- Change made: Added an HTML `<img>` whose `src` points to a non-existent file on `develop`.
- What this tests: The visible failure mode for a broken absolute cross-branch URL.
- Syntax under test: `<img src="https://raw.githubusercontent.com/hesreallyhim/test-cross-branch-image-links/develop/assets/does-not-exist.png" ...>`
- Expected result: Should fail visibly.
- Observed outcome: Pending manual GitHub verification.

### Probe 05

- Category: negative control
- Change made: Added a Markdown image with a relative path to `assets/inbox-02.png`, which exists only on `develop`.
- What this tests: Whether a relative path can cross a branch boundary.
- Syntax under test: `![alt](assets/inbox-02.png)`
- Expected result: Should fail, because the relative path resolves against `main`.
- Observed outcome: Pending manual GitHub verification.

### Probe 06

- Category: secondary URL variation
- Change made: Added an HTML `<img>` whose `src` uses a GitHub blob URL with `?raw=1` for a `develop`-only asset.
- What this tests: Whether blob-style raw links behave differently from `raw.githubusercontent.com` inside a README.
- Syntax under test: `<img src="https://github.com/hesreallyhim/test-cross-branch-image-links/blob/develop/assets/inbox-03.png?raw=1" ...>`
- Expected result: May render, but is secondary to the preferred raw-host syntax.
- Observed outcome: Pending manual GitHub verification.
