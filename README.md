# test-cross-branch-image-links

1. Try to render `assets/inbox-01.png` from `develop` branch.

2. If successful, _rotate_ the content at that path on `develop` and confirm whether or not the link updates, and/or how long it takes.

3. Create a `<picture>` with a `<source>` - the `srcset` property should point to an asset from `develop` that we have proven works on its own. At the bottom, include an `<img>` fallback whose `src` is the `black-pixel-ish.png`.



---


1. Create an `<img src="...." alt="A">` linking to a broken link on develop.

2. Note what happens if `src` is broken.

---

# TEST AREA

Try Markdown-style images and HTML image stynax.

## Probe 01: Markdown + raw.githubusercontent.com + develop-only asset

This probe is rendered from `main`, but the image source explicitly targets `develop`.

![Probe 01: Markdown raw develop asset](https://raw.githubusercontent.com/hesreallyhim/test-cross-branch-image-links/develop/assets/inbox-02.png)
