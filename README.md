# Move Masters — One-Page Website

A fast, single-page marketing site for **Move Masters**, a removals, cleaning and
refuse-removal business in Port Elizabeth (Gqeberha), Eastern Cape.

All enquiries route to WhatsApp — there is no contact form to maintain.

| | |
|---|---|
| **Pieter** | 069 519 9557 — removals, single item transport, refuse removal |
| **Anina** | 068 239 0875 — house cleaning, selling unwanted items |

## Files

```
index.html              The entire site (HTML + inline CSS + JSON-LD). No build step.
assets/img/*.svg        Logo and service icons, hand-drawn to match the flyer branding.
robots.txt              Allows all crawlers, points at the sitemap.
sitemap.xml             Single-URL sitemap.
```

There are no dependencies, no external requests and no JavaScript beyond a
one-line copyright year. The page is fully self-contained, which keeps Core Web
Vitals (a Google ranking factor) essentially perfect.

## Running it

Open `index.html` in a browser, or serve the folder:

```sh
python3 -m http.server 8000
```

## Deploying

Any static host works — Netlify, Cloudflare Pages, Vercel, GitHub Pages or
ordinary cPanel hosting. Upload the whole folder, keeping `assets/` alongside
`index.html`.

### Before going live — replace the placeholder domain

The site currently assumes `https://www.movemasters.co.za/`. If the real domain
differs, find-and-replace it in three files:

```sh
grep -rl 'www.movemasters.co.za' . | xargs sed -i 's|https://www.movemasters.co.za|https://YOUR-DOMAIN|g'
```

That updates the canonical tag, Open Graph tags, JSON-LD structured data,
`robots.txt` and `sitemap.xml`.

## Images

The proxy on the build machine blocked every stock-photo host, so the artwork is
hand-drawn SVG in the brand's navy/red palette rather than photography. Real
photos will convert better — swap them in like this:

1. Drop the photo into `assets/img/` (e.g. `team-loading-truck.jpg`).
2. Change the matching `<img src="...">` in `index.html`.
3. Keep the `alt` text descriptive and location-specific — alt text is read by
   Google Images and is a genuine local-SEO signal.

Best sources for free commercial-use photos: [Pexels](https://www.pexels.com),
[Unsplash](https://unsplash.com), [Pixabay](https://pixabay.com). Useful
searches: *moving truck*, *furniture removal*, *house cleaning*, *garden waste*.
Resize to roughly 1600px wide and save as WebP or JPEG under ~200KB so page
speed stays intact.

## Testimonials

**The three testimonials in the `#reviews` section are sample copy, not real
customers.** They are marked with an HTML comment in the source. Replace them
with genuine feedback before the site goes live.

They are deliberately *not* included in the structured data. Marking up invented
reviews as `Review` or `AggregateRating` schema violates Google's review snippet
policy and risks a manual action against the site — a real risk to the very
rankings this page is built for. Once there is real feedback, adding review
schema is safe and worth doing.

## What was done for search ranking

The page targets all five service categories against both city names —
"Port Elizabeth" and "Gqeberha" are used together throughout, since locals and
Google still use both.

- **Structured data** (`schema.org` JSON-LD): a `MovingCompany` / `LocalBusiness`
  node with geo coordinates, opening hours, both contact people, and an
  `OfferCatalog` listing all five services as separate `Service` entities with
  their own descriptions and `areaServed`. Plus a `WebSite` node and a `FAQPage`
  node so the FAQ is eligible for rich results.
- **Per-service sections** with keyword-led `<h3>`s and body copy covering the
  real search phrases: *furniture removals Port Elizabeth*, *single item
  transport Gqeberha*, *house cleaning service Port Elizabeth*, *garden refuse
  removal Gqeberha*, *sell unwanted furniture*.
- **Suburb coverage** — 34 Nelson Mandela Bay suburbs listed, which is what wins
  long-tail searches like "furniture removals Summerstrand".
- **Six FAQs** answering real questions, marked up for FAQ rich results.
- **Technical**: canonical URL, descriptive title and meta description, Open
  Graph and Twitter cards, `geo.region` / `geo.position` meta, semantic heading
  hierarchy, alt text on every image, `robots.txt`, `sitemap.xml`, and a
  mobile-first responsive layout.
- **Conversion**: WhatsApp deep links throughout, each pre-filled with a message
  naming the specific service, so enquiries arrive already qualified.

## The single most important next step

Structured data and copy get the site indexed. For a local service business,
what actually drives the map-pack rankings is a **Google Business Profile**.

1. Create one free at [business.google.com](https://business.google.com) for
   "Move Masters", Gqeberha, category *Mover* (add *House Cleaning Service* and
   *Garbage Collection Service* as secondary categories).
2. Verify the listing, add the service area, hours and photos of real jobs.
3. Ask every happy customer for a Google review. Nothing else moves local
   rankings as much.

Worth doing next: a Facebook Business Page (most removal enquiries in Gqeberha
start there), and free listings on Yellow Pages SA, Snupit, Brabys and Cylex.
Once those exist, add their URLs to the `sameAs` field in the JSON-LD.

## Online presence check

Searched for an existing Move Masters presence in Port Elizabeth / Gqeberha —
by business name plus city, and by both phone numbers. **Nothing found.** The
"Move Masters" results that do rank are unrelated companies in the USA and the
UK. This business appears to have no website, no Google Business Profile and no
indexed directory listings, which is why the Google Business Profile step above
matters more than anything else on this page.
