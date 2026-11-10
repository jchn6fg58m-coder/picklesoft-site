# PickleSoft website

The studio website for PickleSoft, published at **https://picklesoft.co.uk**. It is a small static site: plain HTML and one stylesheet, with no build step, framework, analytics, cookies or third-party scripts.

| Address | File |
| --- | --- |
| `/` | `index.html`: home (hero, then tabs: `/#apps` (default), `/#websites`, `/#tools`) |
| `/support/` | `support/index.html`: studio support, linking to each app's |
| `/privacy/` | `privacy/index.html`: the website's own policy, linking to each app's |
| `/terms/` | `terms/index.html`: the website's own terms, linking to each app's |
| `/horologist/privacy/`, `/terms/`, `/support/` | `horologist/…/index.html` |
| `/bigger-than-you/privacy/`, `/support/` | `bigger-than-you/…/index.html` (its terms are Apple's standard licence) |
| `/fc-score/privacy/`, `/support/` | `fc-score/…/index.html` (its terms are Apple's standard licence) |
| `/licensing/`, `/sponsorship/` | licensing the FC Score and Net Spend data; sponsoring the apps |
| any missing page | `404.html` |

AVDB's policy, terms and support live on avdb.co.uk (`/privacy-policy`, `/terms-of-use`, `/contact`).

## Adding an app

Every app gets its own pages under its own folder, never the studio-wide ones: `/<app>/privacy/` and `/<app>/support/`, plus `/<app>/terms/` if it has terms beyond Apple's standard licence. Its App Store Connect URLs point at those. Then add one line for it to each list on `/privacy/`, `/terms/` and `/support/`. The app's own pages keep the studio header, but their footer links point at the app's own pages.

Shared pieces: `styles.css`, `fonts/` (self-hosted Young Serif, Figtree and DM Mono, all under the SIL Open Font Licence), `images/`, the icons in the root, and `site.webmanifest`.

The header and footer are repeated in each HTML file, so a change to either needs making in every HTML file.

## Preview locally

```sh
cd ~/Developer/PickleSoft-site
python3 -m http.server 8000
```

Then open http://localhost:8000. Use a local server rather than opening the files directly: the links start with `/`, so they need a server to work.

## How it's published

GitHub Pages serves the `main` branch from the repository root. The `CNAME` file holds the custom domain, `picklesoft.co.uk`, and `.nojekyll` tells Pages to serve the files exactly as they are. Pushing to `main` updates the live site, usually within a minute or two.

## Placeholders

Slots still waiting for images or wording are dashed brass boxes starting "Placeholder:". Find them with `grep -n 'class="ph' index.html`. Swap a screenshot placeholder `<span>` for an `<img>`; the Websites gallery has room for 6–10, so copy a `<figure>` to add more.
