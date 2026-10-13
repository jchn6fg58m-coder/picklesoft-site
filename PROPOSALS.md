# Proposals

Ideas noticed while building the site. None of these have been made: the brief asks for the draft's design and wording to be kept exactly. Each needs the owner's say-so.

## Wording that the move to separate pages has made inaccurate

1. **The partners strip says "Get in touch using the address below."** On the draft's single page, the support email came straight after it. On the new home page nothing with an address follows. Suggested fix: "Get in touch at support@picklesoft.co.uk." or "Get in touch through our support page." with a link.

## Privacy policy accuracy (worth fixing before Apple review)

2. **"If you tap a partner's link, it may pass through our website, which counts the tap..."** The site is now purely static on GitHub Pages and has no way to count anything. Either remove the counting claim, or decide how taps would be counted (which would itself need describing).
3. **GitHub logs visitors' IP addresses.** GitHub's documentation says: "When a GitHub Pages site is visited, the visitor's IP address is logged and stored for security purposes." The policy covers the game rather than the website, so it isn't wrong as written, but the home page's "No tracking" chip and the policy's spirit would be better served by one honest line, for example: "Our website is hosted by GitHub, which keeps visitors' IP addresses in its security logs. We don't use cookies or analytics, and we don't see those logs."

## Small polish

4. **The page has the browser's default 8 px margin around it** (the draft never reset it), so the header's bottom line and the footer line stop 8 px short of the window edge. Adding `body{margin:0}` would let them run edge to edge. Left as-is to match the approved draft.
5. **Show which page you're on.** The header links carry `aria-current="page"` for screen readers but look the same. A style such as `nav a[aria-current]{color:var(--cotton)}` would show it visually.
6. **A sharper 512 px icon.** `pickle-head.webp` is only 256 px, so the 512 px app icon is an enlargement and slightly soft. A 512 px or larger export of the head would fix it.
7. **A `sitemap.xml` and `robots.txt`**, once the domain is live, to help search engines find the support and privacy pages.
