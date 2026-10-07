# sazalabs.com

The company website of SaZaLabs: a static site with no build step, no
JavaScript, no cookies and no external resources. GitHub Pages serves it
from the root of the `main` branch.

## Pages

| Path | File | Language | Content |
|---|---|---|---|
| `/` | `index.html` | English | Company, IntelliBrief, services, about, contact |
| `/de/` | `de/index.html` | German | The same content in German |
| `/impressum.html` | `impressum.html` | German | Legal notice (§ 5 DDG) |
| `/datenschutz.html` | `datenschutz.html` | German, English summary | Privacy policy of the website |

Shared files: `style.css` (light and dark theme via `prefers-color-scheme`,
responsive), `favicon.svg` (also the logo in the header), `CNAME` (the
custom domain for GitHub Pages) and `.nojekyll` (serve the files as they
are, without Jekyll processing).

The English and German home pages carry the same content. When one
changes, change the other in the same commit.

## Hosting and DNS

- **Hosting:** GitHub Pages, repository `sazarghani/sazalabs-website`,
  branch `main`, folder `/`. HTTPS is enforced; GitHub issues and renews the
  certificate.
- **Domain:** `sazalabs.com`, bought through Microsoft 365. Its DNS is
  managed in the Microsoft 365 admin center under
  Settings → Domains → sazalabs.com → DNS records.

Records for the website:

| Type | Name | Value |
|---|---|---|
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |
| CNAME | `www` | `sazarghani.github.io` |
| TXT | `_github-pages-challenge-sazarghani` | value from GitHub → Settings → Pages → Verified domains |

The TXT record verifies the domain for the GitHub account, so that no other
account can publish a Pages site under it.

The same zone holds the Microsoft 365 mail records (MX, SPF, autodiscover,
DKIM, DMARC). Do not remove them when changing website records.

## Changing the site

Edit the HTML, preview locally, commit and push; Pages republishes within a
minute or two.

```bash
python3 -m http.server 8000      # then open http://127.0.0.1:8000/
git commit -am "website: <what changed>"
git push
```

Keep the site free of cookies, analytics and third-party resources
(fonts, scripts, embedded media). The privacy policy says it has none; adding
one means updating `datenschutz.html` in the same change, and possibly a
consent banner.

## Legal content to keep current

- **Impressum:** update the VAT identification number (USt-IdNr.) once the
  tax office assigns it (currently "Beantragt"); update the address if the
  business address changes.
- **Datenschutz:** the date at the end ("Stand"); the hosting and e-mail
  providers if they change.
- **IntelliBrief privacy policy:** the app stores require a privacy policy
  URL. Publish it here (for example `/intellibrief/privacy.html`) before the
  store submission, and replace section 6 of `datenschutz.html` with a link
  to it.

The legal texts are a careful starting point, not legal advice. Have them
checked when the app launches or the business grows.
