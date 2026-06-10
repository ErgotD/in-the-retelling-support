# In the Retelling — support site

Public-facing static site for the In the Retelling iPhone app (previously called Once Said until 2026-05-31). Hosts the landing page, support FAQ, Privacy Notice, and Terms of Use. Served via GitHub Pages.

## What is hosted

- `index.html` — landing page, brief description, links to the other pages.
- `support.html` — six-FAQ support page with a `mailto:` contact line.
- `privacy.html` — Privacy Notice. Must stay in sync with the app's bundled `assets/legal/privacy.md`.
- `terms.html` — Terms of Use. Must stay in sync with the app's bundled `assets/legal/terms.md`.
- `styles.css` — single stylesheet using the app's brand tokens. Light and dark mode via `prefers-color-scheme`.
- No JavaScript, no third-party requests, no fonts loaded from a CDN, no analytics.

## Support contact

The contact email for support, privacy questions, and quote corrections is `enquiries@consideredideas.com`. This is the address referenced from the in-app Settings screen, the bundled legal documents, and the `mailto:` links throughout this site.

## URLs

The site serves at the custom domain `intheretelling.com` (mapped 2026-06-10):

- Landing: `https://intheretelling.com`
- Support: `https://intheretelling.com/support.html`
- Privacy: `https://intheretelling.com/privacy.html`
- Terms: `https://intheretelling.com/terms.html`

`https://intheretelling.co.uk` and the old `https://ergotd.github.io/in-the-retelling-support/...` URLs both 301-redirect to the custom domain, so links published before the mapping keep working.

The Support URL and the Privacy URL above are what the App Store Connect listing references. The Marketing URL field uses the landing URL.

## Enabling GitHub Pages

1. Make this repo public (Settings → General → Danger Zone → Change repository visibility). GitHub Pages on a free GitHub account requires a public repo.
2. In the repo on GitHub: Settings → Pages.
3. Source: "Deploy from a branch".
4. Branch: `main`, Folder: `/ (root)`.
5. Save.
6. Wait one to two minutes for the first publish. GitHub will show the live URL once published.

## Updating the legal text

The Privacy Notice and Terms of Use are duplicated between the app repo's bundled markdown and this site's HTML. When either set is updated, the other must follow.

The `[insert date]` placeholders in `privacy.html` and `terms.html` should be stamped with the same date that lands in the bundled markdown when the legal text is finalised.

There is no automated sync between the app repo and this site repo. A future option is a small build step that converts the markdown to HTML on every push, but for v1 the manual cross-check is enough.

## Custom domain (done, 2026-06-10)

The custom domain `intheretelling.com` is mapped to this repo via Settings → Pages → Custom domain, with the registrar carrying GitHub's `A` records on the apex and a `CNAME` for `www`. `intheretelling.co.uk` forwards to the `.com` at registrar level. GitHub 301-redirects the old `ergotd.github.io/in-the-retelling-support/...` URLs to the custom domain automatically, which keeps the support links inside already-shipped app builds working.

## Brand and design

The visual style mirrors the in-app brand:

- Warm paper background, deep ink primary text, warm grey secondary text, soft warm grey hairlines, persimmon accent on link underlines.
- Serif body type (system fallbacks: Newsreader, Source Serif Pro, Charter, Iowan Old Style, Georgia).
- Sans-serif navigation (system fallbacks: SF Pro via `-apple-system`, then Inter, then platform defaults).
- Light and dark colour schemes via `prefers-color-scheme`, both honoured by mobile browsers.

No JavaScript is used. The site is intentionally static, simple, and small.
