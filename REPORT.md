# Report: PickleSoft website, brief W1 (13 October 2026)

## Where things stand

- **Repository:** https://github.com/jchn6fg58m-coder/picklesoft-site (public), branch `main`, committed as Rufus Constant with your GitHub noreply address, as in the Horologist repository. The Horologist repository was only read, to copy that address, and was not changed.
- **GitHub Pages:** turned on, serving `main` from the root, with the custom domain `picklesoft.co.uk` (from the `CNAME` file).
- **Live addresses (once your DNS is updated):**
  - https://picklesoft.co.uk/
  - https://picklesoft.co.uk/support/  ← for App Store Connect "Support URL"
  - https://picklesoft.co.uk/privacy/  ← for App Store Connect "Privacy Policy URL"
  - https://picklesoft.co.uk/terms/
- **Builds are working.** The two "Page build failed" records are from the first two pushes, made while Pages was still being switched on. Every build since has succeeded. `.nojekyll` has been in the repository from the first commit, so Jekyll is skipped and only one build runs per push. I left the source on "Deploy from a branch". Asking GitHub's servers for picklesoft.co.uk directly already returns the new pages.
- **Not live yet.** The domain still points at GoDaddy's parking page (`3.33.130.190` and `15.197.148.33`). The site will appear when you make the DNS changes below.

## What was built

- Four pages (`/`, `/support/`, `/privacy/`, `/terms/`) and a `404.html`. Each is a complete HTML document sharing `styles.css`, with the same header and footer, and the header links now go to the pages. The palette, fonts, layout, wording and images are the draft's. The only changes you'd notice in the code: the text pages start with an `h1`, so their sub-headings are `h2`s, styled to look exactly as before.
- Fonts are self-hosted WOFF2 files in `fonts/`, with the draft's fallback stacks. No request goes to Google.
- Icons from `pickle-head.webp`: `favicon-32.png`, `apple-touch-icon.png` (180 px) and `icon-512.png`, plus a small `site.webmanifest`.
- Sharing tags (title, description, image) on every page. The image, `images/og-image.jpg`, is a 1200 × 630 crop of the pickle on its own plum background.
- The copy button is kept on the support page, along with its fallback.
- No analytics, cookies or third-party scripts.

## Checks

- **Widths:** every page at 375 px (iPhone SE) and 1280 px. No sideways scrolling.
- **Errors:** no console errors and no failed requests. All internal links return 200. A missing address returns the 404 page.
- **Copy button:** shows "Copied" and copies the address when the clipboard is allowed. Otherwise it falls back to "Selected: press Copy".
- **Image sizes, all under 200 KB:**
  - `pickle.webp`: 135 KB
  - `icon-512.png`: 131 KB
  - `og-image.jpg`: 83 KB
  - `apple-touch-icon.png`: 55 KB
  - `bench.webp`: 26 KB
  - `pickle-head.webp`: 22 KB
  - `favicon-32.png`: 2 KB
- **Lighthouse 12, run locally:**

| Page | Performance | Accessibility | Best practices | SEO |
| --- | --- | --- | --- | --- |
| Home (mobile / desktop) | 97 / 100 | 100 / 100 | 100 / 100 | 100 / 100 |
| Support | 100 / 100 | 100 / 100 | 100 / 100 | 100 / 100 |
| Privacy | 100 / 100 | 100 / 100 | 100 / 100 | 100 / 100 |
| Terms | 100 / 100 | 100 / 100 | 100 / 100 | 100 / 100 |
| 404 | 100 / 100 | 100 / 100 | 100 / 100 | 63 / 63 |

The 404 page's SEO score is low on purpose: it is marked "noindex" so search engines don't list it.

## What you need to do

### 1. DNS at GoDaddy (picklesoft.co.uk)

These are GitHub's current addresses, from GitHub's documentation: [Managing a custom domain for your GitHub Pages site](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site/managing-a-custom-domain-for-your-github-pages-site).

| Type | Name | Value | TTL |
| --- | --- | --- | --- |
| A | @ | 185.199.108.153 | 1 hour |
| A | @ | 185.199.109.153 | 1 hour |
| A | @ | 185.199.110.153 | 1 hour |
| A | @ | 185.199.111.153 | 1 hour |
| CNAME | www | jchn6fg58m-coder.github.io | 1 hour |

Clicks:

1. Sign in at godaddy.com and click your name, then **My Products**.
2. Next to picklesoft.co.uk, click **DNS** (or **Manage DNS**).
3. **Delete the existing A record for `@`** (GoDaddy's "Parked" record, pointing to 3.33.130.190 or 15.197.148.33). If GoDaddy won't let you delete it, edit it to the first IP address in the table.
4. Click **Add New Record** and add the four A records above, one at a time (Type **A**, Name **@**, Value the IP address).
5. Find the existing **CNAME** record named **www** (it usually points to `@`). Click the pencil icon and change its value to `jchn6fg58m-coder.github.io`. If there's no such record, add it.
6. If **Forwarding** is set up on this page for the domain, remove it.
7. Click **Save**.

Optional extras from the same GitHub page:
- Four **AAAA** records for `@`: `2606:50c0:8000::153`, `2606:50c0:8001::153`, `2606:50c0:8002::153` and `2606:50c0:8003::153`.
- **Verify the domain** to stop anyone else using it with GitHub Pages: GitHub → your picture → **Settings** → **Pages** → **Add a domain**. GitHub then gives you a TXT record to add at GoDaddy.

### 2. Turn on HTTPS, once DNS has spread (a few hours, sometimes up to a day)

1. Go to https://github.com/jchn6fg58m-coder/picklesoft-site/settings/pages.
2. Wait until the Custom domain box shows a green "DNS check successful".
3. Tick **Enforce HTTPS**. If it's greyed out, GitHub is still issuing the certificate. Try again in an hour.
4. Check that both https://picklesoft.co.uk and https://www.picklesoft.co.uk load. The second should redirect to the first.

### 3. Email forwarding for support@picklesoft.co.uk

The online information about GoDaddy is mixed. GoDaddy used to include free forwarding with domains, but it has since retired the "Workspace Email" credits that came with domains. Its separate "Email Forwarding" product may now be paid. I couldn't confirm this from GoDaddy's help pages (they blocked automated reading), so check your own account first:

1. GoDaddy → **My Products**. Scroll to **Additional Products** (or **Email**).
2. If you see **Email Forwarding** with a **Redeem** or **Set up** button and no charge: choose picklesoft.co.uk, type `support` before the @, enter your own inbox as the destination, and save. That's done.
3. If it asks for payment, **stop**. Don't buy it. Use the free alternative below instead.

**Free alternative: ImprovMX** (forwarding only, with a free plan for one domain; I haven't signed you up). Sign up at improvmx.com with your own email address and add `picklesoft.co.uk`. Create the alias `support` → your inbox. Then in GoDaddy's DNS page, add these records ([ImprovMX's GoDaddy guide](https://improvmx.com/guides/godaddy/)) and delete any other MX records:

| Type | Name | Priority | Value |
| --- | --- | --- | --- |
| MX | @ | 10 | mx1.improvmx.com |
| MX | @ | 20 | mx2.improvmx.com |
| TXT | @ | | v=spf1 include:spf.improvmx.com ~all |

Then send a test email to support@picklesoft.co.uk from a different account. Replies will come from your personal address unless you set up sending as well, which is a later job.

## Still to do and decisions for you

- **`[full name]` is still a placeholder** in the footer of every page and in the privacy policy's "Who we are". The brief didn't supply it. Your Git commits use "Rufus Constant", but I didn't assume that's the legal name to publish.
- **Wording changes (owner's decisions, 13 October 2026):**
  1. The partners strip now reads "Get in touch through our Support page.", with a link to the Support page.
  2. The privacy policy's "Partner links" section no longer mentions counting taps. It now says "Partner links go straight to the partner's own website, which has its own privacy policy."
  3. A new "Our website" section says the site is hosted by GitHub Pages, which keeps visitors' IP addresses in its security logs for a short time, with a link to GitHub's privacy statement.
  The "No tracking" chip is unchanged, because it refers to the game.
- **Worth confirming: "for a short time".** GitHub's Pages documentation says IP addresses are "logged and stored for security purposes" but gives no retention period. If GitHub's privacy statement doesn't support "a short time", consider dropping those words.
- **The 512 px icon is an enlargement** of the 256 px `pickle-head.webp`, so it's slightly soft. A larger export would sharpen it.
- Once the domain is live, re-run Lighthouse on the real addresses, and put the support and privacy addresses into App Store Connect.
