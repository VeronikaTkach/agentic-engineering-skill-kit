# Google SEO for Astro Implementations

This file covers technical SEO only: crawlability, rendered HTML, metadata, links, status codes, sitemap, canonical, and image discoverability.

## Rendered HTML

- Put primary content in the initial/prerendered HTML whenever practical.
- Use Astro's static output for indexable content by default.
- Avoid app-shell pages where meaningful text arrives only after client-side fetch.
- If using SSR, verify production HTML, not only local dev output.
- Do not depend on JavaScript to fix canonical URLs, noindex, title, or core metadata after load.

## Links

- Use real `<a href="/path/">` links for navigation and important internal links.
- Avoid navigation implemented only with buttons, click handlers, or custom elements without hrefs.
- Do not block CSS/JS resources required for Google to see the page as users do.

## Metadata

Every indexable page should render:

- unique `<title>`;
- unique meta description;
- canonical URL;
- `robots` only when needed;
- Open Graph/Twitter preview tags when social sharing matters;
- structured data only when relevant and visible.

## Status Codes

- Static mode: ensure generated 404 page and host configuration behave correctly.
- Server mode: return meaningful status codes from dynamic routes and endpoints.
- Missing pages/entities should return 404 or 410.
- Redirects should use 301/308 for permanent moves and 302/307 for temporary moves.
- Avoid soft 404s, especially in client-routed experiences.

## Sitemap

- Configure `site` in `astro.config.*`.
- Use `@astrojs/sitemap` for statically generated routes.
- For SSR-only dynamic routes, generate sitemap entries from the data source or another backend process because the integration cannot infer arbitrary request-time URLs.
- Exclude noindex, draft, private, duplicate, or parameter-only URLs.

## Canonical URLs

- Generate canonicals from one URL helper.
- Keep trailing slash behavior consistent with Astro config and hosting.
- Match sitemap URLs, canonical tags, redirects, and internal links.

## Images

- Use `<Image />`, `<Picture />`, or standard `<img>` output that includes a real `src`.
- When using `<picture>`, include an `<img src>` fallback.
- Use descriptive filenames and alt text for content images.
- Set dimensions or use Astro image components to prevent layout shifts.

## QA

- Test production pages with Search Console URL Inspection when available.
- Crawl the built site with JavaScript disabled and enabled.
- Check rendered source for titles, canonicals, body content, links, and JSON-LD.
- Validate sitemap and robots behavior after deploy.
