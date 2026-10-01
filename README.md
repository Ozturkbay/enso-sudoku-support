# Enso Sudoku — Privacy & Support site

Public support and privacy website for the **Enso Sudoku** mobile game
(iOS and Android). It provides the Privacy Policy URL and Support URL
required by the Apple App Store and Google Play Console, in English and
Turkish.

- **Developer:** Fatih Öztürkbay
- **Support email:** [ensosudoku.support@gmail.com](mailto:ensosudoku.support@gmail.com)
- **Repository:** [Ozturkbay/enso-sudoku-support](https://github.com/Ozturkbay/enso-sudoku-support)

It is a plain static site: HTML and one CSS file. No framework, no build
step, no JavaScript, no external fonts, scripts or stylesheets.

## URLs

Hosted with GitHub Pages from the `main` branch, repository root:

| Page | URL |
| --- | --- |
| Home | https://ozturkbay.github.io/enso-sudoku-support/ |
| Privacy Policy (EN) | https://ozturkbay.github.io/enso-sudoku-support/privacy/ |
| Gizlilik Politikası (TR) | https://ozturkbay.github.io/enso-sudoku-support/privacy/tr/ |
| Support (EN) | https://ozturkbay.github.io/enso-sudoku-support/support/ |
| Destek (TR) | https://ozturkbay.github.io/enso-sudoku-support/support/tr/ |

Use the **Privacy Policy (EN)** URL for App Store Connect, the Play Console
and the AdMob consent (UMP) message. Use the **Support (EN)** URL for App
Store Connect's Support URL field.

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

To preview under the same `/enso-sudoku-support/` path GitHub Pages uses,
serve the parent directory instead and open
http://localhost:8000/enso-sudoku-support/.

## Publishing (GitHub Pages)

Pages deploys automatically from `main` / `(root)` on every push. The
setting lives at **Settings → Pages → Build and deployment → Deploy from a
branch → `main` → `/ (root)`**. No custom domain and no `CNAME` file are
used.

## Updating "Last updated"

The privacy policies show their date near the top:

- `privacy/index.html` — `Last updated: October 1, 2026`
- `privacy/tr/index.html` — `Son güncelleme: 1 Ekim 2026`

When the policy changes, edit both lines together and keep the English and
Turkish texts aligned section by section. Turkish month names: Ocak, Şubat,
Mart, Nisan, Mayıs, Haziran, Temmuz, Ağustos, Eylül, Ekim, Kasım, Aralık.

The policy describes what the app actually does (ads via Google AdMob,
consent via Google UMP, the Remove Ads purchase, optional Game Center /
Google Play Games integration, local reminders, local storage that may be
included in device backups). If the app adds or removes an SDK, a
permission, an account system, analytics or a server — or once platform
game services, the production consent messages or the store age ratings are
finalized — review both privacy pages before releasing that version.

## App icon

`assets/images/enso-icon.png` is a copy of the approved store icon
`assets/brand/enso_icon_googleplay_512.png` from the Enso Sudoku app
repository (512×512). `favicon.png` (64×64) and `apple-touch-icon.png`
(180×180) were resized with macOS `sips` from
`assets/brand/enso_icon_store_master_1024.png` in the same repository. The
source files were not modified, and nothing is hotlinked.

## Privacy of this website

This website contains no first-party analytics or tracking code: its own
code sets no cookies, uses no analytics, tracking scripts or marketing
pixels, loads no third-party fonts, scripts or stylesheets, and contains no
JavaScript. It is hosted on GitHub Pages; see the
[GitHub Privacy Statement](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement)
for how GitHub handles data.
