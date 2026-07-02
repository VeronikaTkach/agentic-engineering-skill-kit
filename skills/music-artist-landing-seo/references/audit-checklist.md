# SEO Audit Checklist for Music Artist Landing Pages

## Critical

- Verify the artist name appears in title, H1, visible copy, schema, OG metadata, and footer/contact area.
- Confirm every important page is crawlable from the final HTML without requiring JavaScript-only rendering.
- Check that the homepage has at least 100-250 words of crawlable artist/entity text somewhere on the page or in an accessible info panel.
- Confirm canonical URLs are present and correct.
- Verify no important page is blocked by robots.txt, noindex, auth, or accidental staging settings.
- Verify missing content returns a meaningful 404/410 HTTP status, not a soft 404 page with a 200 status.
- Confirm internal navigation and important links use real `<a href="...">` links, not click handlers without hrefs.
- Check mobile LCP target: hero poster/image should load fast; video should not be the LCP bottleneck.
- Ensure social icons have accessible labels and links use canonical artist profiles.
- Confirm booking/contact information is visible even if the form fails.

## Metadata

- Homepage title should combine artist name + role/genre: `Artist Name | DJ / Producer`.
- Internal page titles should be specific: `Music | Artist Name`, `Tour Dates | Artist Name`.
- Meta descriptions should be human-readable, not keyword lists.
- OG image should be 1200x630 or a platform-safe equivalent.
- Open Graph should include at minimum `og:title`, `og:type`, `og:image`, and `og:url`; add `og:description` for share quality.
- Use consistent capitalization of the artist name everywhere.
- If the CMS stores SEO fields, verify the frontend renders them into the final page HTML, not only in admin previews.

## Content

- Home should establish who the artist is, genre, location/scene, current priority, and major links.
- Music page should list releases/mixes with titles, dates, covers, and streaming links.
- Tour page should list dates as text, not only embedded widgets/images.
- Videos page should include titles, categories, dates, and embed links.
- Important videos should have dedicated watch/detail pages with unique title, description, thumbnail, upload date, and embed/content URL.
- Press page should include publication names, dates, links, and excerpts/quotes.
- Info page should include bio, booking, press, management, socials.

## Internal Links

- Link Home to Music, Tour, Videos, Press, Info, Booking.
- Link Music items to streaming platforms and related videos.
- Link Tour dates to ticket pages.
- Link Press items to original publications.
- Link Info to booking/contact and official socials.
- Make sure canonical social/music profile URLs in `sameAs` match visible outbound links.

## Performance

- Use separate mobile and desktop hero media.
- Use a poster image for every background video.
- Treat decorative background video as a performance/brand asset, not as the primary SEO video.
- Lazy-load below-fold videos and iframes.
- Use optimized image formats and fixed dimensions.
- Put indexable content images in `<img>` or `<picture>` markup; do not rely on CSS background images for images that should be discoverable.
- Avoid autoplay audio.
- Respect `prefers-reduced-motion`.

## Structured Data QA

- Mark up only facts and entities that are visible on the page.
- Validate JSON-LD with Google's Rich Results Test when targeting Google rich results.
- Validate broader Schema.org correctness with the Schema Markup Validator.
- Use `MusicEvent` for tour dates with required event fields: name, start date, location, status, attendance mode, performer, and ticket offer when available.
- Use `VideoObject` only for real video pages or visible embedded/hosted videos, not for a decorative silent background loop.
- Use `MusicGroup` for an artist project identity; Schema.org allows it for a solo musician. Use `Person` when the site primarily represents the legal/individual person.

## Launch QA

- Generate and test `sitemap.xml`; include core pages and canonical detail pages.
- Submit sitemap in Google Search Console after launch.
- Inspect key URLs in Google Search Console after deployment.
- Check mobile rendering, noindex/canonical output, and HTTP status codes on production URLs.

## Local/Entity Signals

- Add sameAs links for Instagram, YouTube, SoundCloud, Spotify, Apple Music, Bandcamp, Beatport, Resident Advisor, Discogs, Songkick, Bandsintown, IMDb/press profiles if relevant.
- Include management/booking contacts where appropriate.
- Use consistent name, spelling, and stylization.
