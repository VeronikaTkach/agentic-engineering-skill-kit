# Technical SEO for Media-Heavy Artist Landings

## Hero Video

Recommended limits:

- mobile: 6-8 seconds, 720px wide, 24fps, 800-1500 kbps, target 0.7-1.5 MB;
- desktop: 8-12 seconds, 1440-1920px wide, 24fps, 2500-4500 kbps, target 3-6 MB;
- no audio track;
- include `poster`;
- use `muted`, `playsinline`, `loop`, `autoplay` only when appropriate;
- provide static fallback for `prefers-reduced-motion`.

Avoid making the background video the only meaningful content.

## Images

- Use AVIF/WebP where possible.
- Preserve dimensions to avoid CLS.
- Use descriptive alt for content images.
- Use empty alt for purely decorative images.
- Keep OG image separate and platform-safe.
- Avoid uploading 4000px images directly into grids without generated sizes.
- Use standard `<img>` or `<picture>` markup for images that should be discoverable by Google Images.
- Do not rely on CSS background images for release covers, artist portraits, press thumbnails, or other indexable image content.
- Avoid keyword stuffing in alt text; describe the image in context.

## Iframes and Embeds

- Lazy-load YouTube/Vimeo embeds.
- Use a clickable poster that loads iframe after interaction.
- Avoid loading many third-party players on first paint.
- Use privacy-enhanced YouTube embed when possible.
- Give important videos their own detail/watch page with unique text, thumbnail, upload date, and embed/content URL.

## Crawlability

- Important text should be server-rendered or available in initial HTML.
- Avoid canvas-only or image-only identity.
- Ensure robots.txt and sitemap.xml exist.
- Include XML sitemap URLs for core pages.
- Submit sitemap in Google Search Console.
- Important internal links should be real `<a href>` elements.
- Use meaningful HTTP status codes: 200 for valid pages, 301/302 for redirects, 404/410 for removed or missing content.
- Avoid soft 404s where a missing page displays an error message but returns status 200.
- Do not hide primary page content behind client-only state that is unavailable in the initial HTML.

## Core Web Vitals

- LCP: optimize hero poster/image; defer video.
- CLS: reserve dimensions for images, embeds, and cards.
- INP: avoid heavy animation and third-party scripts during initial load.

## Astro Notes

- Use `astro:assets` for image optimization.
- Use Astro `<Image />` or `<Picture />` for local and authorized remote images when optimization is needed.
- Remember that images in `public/` are served as-is and are not processed by Astro's image pipeline.
- Configure remote image domains/patterns before expecting Astro to optimize CMS-hosted remote media.
- Astro does not provide native video optimization comparable to its image pipeline; use prepared video files, external video hosting, or a media/CDN workflow.
- Keep React islands only where interactive.
- Lazy-load video modals and embeds.
- Generate static pages for stable content; use SSR/API where live updates matter.
- For Django CMS content, prefer build-time/static generation for mostly stable pages and SSR or webhooks/rebuilds only where editorial freshness requires it.

## Next.js Notes

- Use `next/image` with configured remote domains.
- Be explicit with caching and ISR.
- Avoid converting a simple artist site into unnecessary client-side app logic.
- Next.js image tooling is mature, but video still usually requires external hosting/transcoding/CDN decisions; do not assume `next/image` solves video delivery.

## Django Notes

- Generate image sizes on upload or via storage/CDN.
- Expose absolute media URLs for frontend metadata.
- Store SEO fields per page: title, description, OG image, canonical override, noindex flag.
- Store structured fields for releases, tour events, videos, and press items.
- Use Django's sitemap framework when Django owns public URL generation, or expose sitemap data to Astro if Astro owns public routes.
- Keep slug, canonical URL, publish status, noindex, and last modified dates explicit in CMS models.
- Ensure media uploads produce predictable dimensions and derivatives for mobile grids, OG images, and thumbnails.
- If Astro renders the public site, Django admin preview must match the final Astro-rendered metadata and schema output.

## Production QA

- Crawl the deployed site with JavaScript disabled and enabled.
- Test key pages with Google Rich Results Test, Schema Markup Validator, PageSpeed Insights/Lighthouse, and Search Console URL Inspection.
- Verify `robots.txt`, `sitemap.xml`, canonical tags, noindex flags, OG tags, and HTTP status codes on production, not only local/staging.
