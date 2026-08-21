# imobabics.com

Personal website of Imo Babics. Growth & Brand, European fintech. CGO & CMO at Relai, ex-Bitpanda.

Hand-written static HTML. No framework, no build step, no dependencies. Hosted on GitHub Pages.

## Stack

- Single-file pages: all CSS lives in one `<style>` block per page, behaviour in inline `<script>`
- Fonts: Jost (display, labels) and Instrument Sans (body) via Google Fonts
- Analytics: Umami (self-hosted, cookieless)
- No cookies, no consent banner needed

## Structure

```
index.html              Homepage
writing/                Essays (5 articles, same identity system)
photo-hero.webp         Hero cutout with orange print-shadow (baked into asset)
photo.png               Square B/W portrait (OG image only, not referenced by <img>)
photo-avatar.webp       256px byline avatar for articles
photo2.jpg              Stage banner, 1800x900, B/W via CSS filter
icon-192.png            Manifest icons + apple-touch-icon.png
icon-512.png
manifest.json
llms.txt                GEO source file for AI crawlers
.well-known/security.txt
.nojekyll               Required: stops Jekyll from dropping the .well-known folder
```

## Identity system ("Homage / Nike-first")

Documented here so future edits stay on-brand. The identity layer sits at the
end of each page's `<style>` block, clearly commented.

**Tokens**
- Paper `#F7F7F5` · Ink `#0E0E0E` · Black sections `#0A0A0A` · Touch orange `#D96D00`

**Type**
- Headlines: Jost 900, uppercase, tight leading (poster register)
- Labels/eyebrows/nav/buttons: Jost 500, tracked uppercase
- Body: Instrument Sans
- No italics anywhere

**Colour rules (one orange, two jobs)**
1. Static marks, exactly three kinds: the hero full stop, the print-shadow
   silhouette behind the portrait, the index numbers (01-04 beliefs, 01-03 services)
2. Orange marks what moves: arrow links at rest, all hovers, text selection,
   focus rings. If it is orange, you can touch it or it matters. Nothing else
   gets the colour.

**Photography**
- All photos monochrome (grayscale, contrast 1.06)
- Hero and LinkedIn banner: cutout on a solid orange offset silhouette
  (misregistered-print shadow, offset down-left)
- No employer logos or slogans on the personal hero

**Copy rules**
- No em dashes or en dashes anywhere. Plain hyphens or restructured sentences.
- Visible copy is first person. Schema/FAQ JSON stays third person (AI engines
  quote it as biography). Keep visible FAQ answers and schema answers factually
  in sync when editing either.

## SEO / GEO

- Person + ProfilePage schema with sameAs, knowsAbout, hasOfferCatalog.
  Deliberately no Organization schema: this is a person, not a company.
  Deliberately no Event schema until there are real upcoming talks.
- llms.txt mirrors the site positioning. Update it whenever the bio or
  positioning changes on index.html.
- Meta description stays under 155 characters.
- Every `<img>` carries width/height. Keep sampled images under ~200 KB
  (webp for new assets).

## Deployment

Push to main. GitHub Pages serves the root.

GitHub Pages cannot set response headers (HSTS, CSP, cache-control). For the
full security-header set, route DNS through Cloudflare (free) and add a
Response Header Transform rule; the header values live in this repo's history
under `headers-config.md` notes.

Post-deploy sanity check: homepage hero renders (webp), one article byline
avatar loads, `/manifest.json` and `/.well-known/security.txt` resolve.
