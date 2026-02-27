2026-02-27

- Updated `index.html` so that QR codes now encode relative links to local pages:
  - `./pages/1.html` through `./pages/7.html`.
- Intended deployment: `index.html` at site root with `pages` subfolder containing the corresponding `1.html`, `2.html`, etc.

- Later updated behavior so each QR now encodes `./?page=N` instead of direct page links.
- Added logic in `window.onload` to:
  - Read `page` from the URL query.
  - If present, immediately redirect to `./pages/<page>.html` and skip the QR animation.
  - If absent, run the original QR rotation and confetti animation.

- Updated `qrLinks` again to use the final hosted domain:
  - `https://wheelqr.netlify.app/?page=1` through `?page=7`.
- This ensures QR scanners on phones open the correct hosted URL, which then redirects based on the `page` parameter.

- Added explicit `fileMap` in `index.html` to attach each QR (page id 1–7) to an exact file path:
  - `"1": "./pages/1.html"` through `"7": "./pages/7.html"`.
- Updated redirect logic to:
  - Read `page` from query, look it up in `fileMap`, and redirect to that exact file if found.
  - Fall back to the QR animation if no mapping exists.

- Simplified behavior so each QR now directly encodes its final page URL:
  - `https://wheelqr.netlify.app/pages/1.html` through `/pages/7.html`.
- Removed `fileMap` and query-parameter redirect logic; `index.html` now only shows rotating QR codes.

