# Coro — site

Static one-page site for Coro, built from the `Coro Site v2` design. No build step,
no dependencies — a single `index.html` with inline CSS and vanilla JS.

## Run locally

Open `index.html` in a browser, or serve the folder:

```bash
python -m http.server 8000
```

## Deploy to GitHub Pages

1. Push this folder to a GitHub repo.
2. Repo → **Settings** → **Pages**.
3. **Source**: *Deploy from a branch*. **Branch**: `main`, folder `/ (root)`. Save.
4. The site appears at `https://<user>.github.io/<repo>/` within a minute or two.

For a user/org site, name the repo `<user>.github.io` and it serves from the root domain.

## Feedback form

The "Your turn" form is client-side only. By default nothing is transmitted — submitting
just swaps in the thank-you panel. To actually receive responses, set `FEEDBACK_ENDPOINT`
near the bottom of `index.html` to a form endpoint that accepts a JSON `POST`
(Formspree, Basin, a Google Apps Script webhook, etc.):

```js
var FEEDBACK_ENDPOINT = 'https://formspree.io/f/xxxxxxx';
```

Posted body:

```json
{ "gut": "…", "liked": ["…"], "note": "…", "submittedAt": "ISO-8601" }
```

GitHub Pages is static hosting, so it cannot receive the POST itself — the endpoint has
to be a third-party service.
