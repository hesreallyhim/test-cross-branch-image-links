# test-cross-branch-image-links

1. Try to render `assets/inbox-01.png` from `develop` branch.

2. If successful, _rotate_ the content at that path on `develop` and confirm whether or not the link updates, and/or how long it takes.

3. Create a `<picture>` with a `<source>` - the `srcset` property should point to an asset from `develop` that we have proven works on its own. At the bottom, include an `<img>` fallback whose `src` is the `black-pixel-ish.png`.



---


1. Create an `<img src="...." alt="A">

2. Note what happens if `src` is broken.
