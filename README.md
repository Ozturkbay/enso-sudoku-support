# Enso Sudoku — Privacy & Support site

Public support and privacy website for the **Enso Sudoku** mobile game
(iOS and Android). It provides the Privacy Policy URL and Support URL
required by the Apple App Store and Google Play Console, in English and
Turkish.

It is a plain static site: HTML and one CSS file. No framework, no build
step, no JavaScript, no external fonts, scripts or stylesheets.

## URLs

Hosted with GitHub Pages from `Ozturkbay/enso-sudoku-support`:

| Page | URL |
| --- | --- |
| Home | https://ozturkbay.github.io/enso-sudoku-support/ |
| Privacy Policy (EN) | https://ozturkbay.github.io/enso-sudoku-support/privacy/ |
| Gizlilik Politikası (TR) | https://ozturkbay.github.io/enso-sudoku-support/privacy/tr/ |
| Support (EN) | https://ozturkbay.github.io/enso-sudoku-support/support/ |
| Destek (TR) | https://ozturkbay.github.io/enso-sudoku-support/support/tr/ |

Use the **Privacy Policy** URL for App Store Connect, the Play Console and
the AdMob consent (UMP) message. Use the **Support** URL for App Store
Connect's Support URL field.

## Structure

```
index.html              Landing page (EN, with TR links)
privacy/index.html      Privacy Policy (EN)
privacy/tr/index.html   Gizlilik Politikası (TR)
support/index.html      Support (EN)
support/tr/index.html   Destek (TR)
assets/css/styles.css   The only stylesheet
assets/images/          App icon, favicon, apple-touch-icon
.nojekyll               Serve files as-is (no Jekyll processing)
```

All internal links are relative, so the site works under the
`/enso-sudoku-support/` project path. The only absolute URLs are the
`<link rel="canonical">` and `hreflang` tags in each page's `<head>`, which
point at the GitHub Pages addresses above. If the site ever moves (for
example, to a custom domain), update those tags too:

```sh
grep -rl "https://ozturkbay.github.io/enso-sudoku-support/" --include='*.html' .
```

## Local preview

From the repository root:

```sh
python3 -m http.server 8000
```

Then open http://localhost:8000/. (Opening the files directly with
`file://` won't resolve the directory-style links such as `privacy/`.)

## Publishing (GitHub Pages)

1. Push `main` to `https://github.com/Ozturkbay/enso-sudoku-support`.
2. In the repository on GitHub: **Settings → Pages → Build and deployment**,
   set **Source** to *Deploy from a branch*, **Branch** to `main`, folder
   `/ (root)`, and save.
3. After the first deployment finishes, the URLs above are live.

No custom domain and no `CNAME` file are used.

## Replacing the support email placeholder

The public support email has not been chosen yet. Every place that needs it
uses this exact token:

```
SUPPORT_EMAIL_PLACEHOLDER
```

It appears in visible text and in `mailto:` links on every page. Once the
address exists, replace it everywhere at once (macOS / BSD `sed`):

```sh
grep -rl "SUPPORT_EMAIL_PLACEHOLDER" --include='*.html' . \
  | xargs sed -i '' 's/SUPPORT_EMAIL_PLACEHOLDER/support@example.com/g'
```

On Linux (GNU `sed`), use `sed -i` instead of `sed -i ''`. Replace
`support@example.com` with the real address, then confirm nothing is left:

```sh
grep -rn "SUPPORT_EMAIL_PLACEHOLDER" . --exclude=README.md
```

(This README mentions the token on purpose; the command above excludes it.)

## Updating "Last updated"

The privacy policies show their date near the top:

- `privacy/index.html` — `Last updated: October 1, 2026`
- `privacy/tr/index.html` — `Son güncelleme: 1 Ekim 2026`

When the policy changes, edit both lines together and keep the English and
Turkish texts aligned. Turkish month names: Ocak, Şubat, Mart, Nisan,
Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık.

The policy describes what the app actually does (ads via Google AdMob,
consent via Google UMP, the Remove Ads purchase, Game Center / Google Play
Games, local reminders, local-only storage). If the app adds or removes an
SDK, a permission, an account system, analytics or a server, update both
privacy pages before releasing that version.

## App icon

`assets/images/enso-icon.png` is a copy of the approved store icon
`assets/brand/enso_icon_googleplay_512.png` from the Enso Sudoku app
repository (512×512). `favicon.png` (64×64) and `apple-touch-icon.png`
(180×180) were resized with macOS `sips` from
`assets/brand/enso_icon_store_master_1024.png` in the same repository. The
source files were not modified, and nothing is hotlinked.

## Privacy of this website

This website sets no cookies, has no analytics, no tracking scripts, no
third-party fonts, scripts or stylesheets, and contains no JavaScript.
GitHub Pages, as the host, may process technical data such as IP addresses
to serve and secure the site (see the GitHub Privacy Statement).
