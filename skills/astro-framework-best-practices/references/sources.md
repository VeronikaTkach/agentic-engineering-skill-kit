# Primary Sources

Use these sources when verification or citations are required.

## Astro

- Docs home: https://docs.astro.build/en/getting-started/
- Islands architecture: https://docs.astro.build/en/concepts/islands/
- Project structure: https://docs.astro.build/en/basics/project-structure/
- Configuration reference: https://docs.astro.build/en/reference/configuration-reference/
- Routing: https://docs.astro.build/en/guides/routing/
- Endpoints: https://docs.astro.build/en/guides/endpoints/
- Middleware: https://docs.astro.build/en/guides/middleware/
- Data fetching: https://docs.astro.build/en/guides/data-fetching/
- Content collections: https://docs.astro.build/en/guides/content-collections/
- Images: https://docs.astro.build/en/guides/images/
- Frontend frameworks: https://docs.astro.build/en/guides/framework-components/
- Client directives: https://docs.astro.build/en/reference/directives-reference/#client-directives
- On-demand rendering: https://docs.astro.build/en/guides/on-demand-rendering/
- Server islands: https://docs.astro.build/en/guides/server-islands/
- Route caching: https://docs.astro.build/en/guides/route-caching/
- View transitions: https://docs.astro.build/en/guides/view-transitions/
- Prefetch: https://docs.astro.build/en/guides/prefetch/
- Sitemap integration: https://docs.astro.build/en/guides/integrations-guide/sitemap/
- Testing: https://docs.astro.build/en/guides/testing/
- Deploy: https://docs.astro.build/en/guides/deploy/

## Google Search Central

- SEO Starter Guide: https://developers.google.com/search/docs/fundamentals/seo-starter-guide
- JavaScript SEO basics: https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics
- Crawlable links: https://developers.google.com/search/docs/crawling-indexing/links-crawlable
- Image SEO: https://developers.google.com/search/docs/appearance/google-images
- Sitemaps: https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview
- Canonicalization: https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls
- Meta tags Google supports: https://developers.google.com/search/docs/crawling-indexing/special-tags

## web.dev

- Web Vitals: https://web.dev/articles/vitals
- Largest Contentful Paint: https://web.dev/articles/lcp
- Interaction to Next Paint: https://web.dev/articles/inp
- Cumulative Layout Shift: https://web.dev/articles/cls
- Optimize LCP: https://web.dev/articles/optimize-lcp
- Optimize INP: https://web.dev/articles/optimize-inp
- Optimize CLS: https://web.dev/articles/optimize-cls

## Verified Technical Baselines

- Astro prerenders pages, routes, and API endpoints by default unless SSR/on-demand rendering is enabled.
- Astro islands keep most UI as static HTML and hydrate only explicitly marked interactive components.
- Astro image components optimize local `src/` images and authorized remote images; `public/` images are served as-is.
- `@astrojs/sitemap` generates a sitemap from statically generated routes and requires a configured deployed `site` URL.
- Google can process JavaScript, but server-side or prerendered HTML is still better for users, crawlers, and non-JS bots.
- Google discovers links from `href` attributes and recommends meaningful HTTP status codes.
- Core Web Vitals good thresholds are LCP <= 2.5s, INP <= 200ms, CLS <= 0.1 at the 75th percentile by device class.
