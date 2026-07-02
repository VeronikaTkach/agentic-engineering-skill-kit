# Primary Sources

Use these sources when a task needs verification, citations, or up-to-date technical guidance.

## Google Search Central

- SEO Starter Guide: https://developers.google.com/search/docs/fundamentals/seo-starter-guide
- Structured data intro: https://developers.google.com/search/docs/appearance/structured-data/intro-structured-data
- Image SEO: https://developers.google.com/search/docs/appearance/google-images
- Video SEO: https://developers.google.com/search/docs/appearance/video
- Video structured data: https://developers.google.com/search/docs/appearance/structured-data/video
- Event structured data: https://developers.google.com/search/docs/appearance/structured-data/event
- Organization structured data: https://developers.google.com/search/docs/appearance/structured-data/organization
- JavaScript SEO basics: https://developers.google.com/search/docs/crawling-indexing/javascript/javascript-seo-basics
- Canonicalization: https://developers.google.com/search/docs/crawling-indexing/consolidate-duplicate-urls
- Sitemaps: https://developers.google.com/search/docs/crawling-indexing/sitemaps/overview

## Schema.org

- MusicGroup: https://schema.org/MusicGroup
- MusicEvent: https://schema.org/MusicEvent
- MusicRecording: https://schema.org/MusicRecording
- MusicAlbum: https://schema.org/MusicAlbum
- VideoObject: https://schema.org/VideoObject
- Person: https://schema.org/Person
- Organization: https://schema.org/Organization
- WebSite: https://schema.org/WebSite
- BreadcrumbList: https://schema.org/BreadcrumbList

## Social Metadata

- Open Graph protocol: https://ogp.me/

## Astro

- Images: https://docs.astro.build/en/guides/images/
- View transitions: https://docs.astro.build/en/guides/view-transitions/
- On-demand rendering: https://docs.astro.build/en/guides/on-demand-rendering/
- Sitemap integration: https://docs.astro.build/en/guides/integrations-guide/sitemap/

## Django

- Sitemap framework: https://docs.djangoproject.com/en/stable/ref/contrib/sitemaps/
- Admin site: https://docs.djangoproject.com/en/stable/ref/contrib/admin/
- Static files: https://docs.djangoproject.com/en/stable/howto/static-files/
- FileField/ImageField: https://docs.djangoproject.com/en/stable/ref/models/fields/#filefield

## Verified Technical Conclusions

- Google can discover images in standard HTML `<img src>` and picture descendants; CSS background images are not equivalent for image indexing.
- Google recommends descriptive, contextual alt text and warns against keyword stuffing.
- Google can find videos embedded with common HTML elements (`video`, `embed`, `iframe`, `object`), but video SEO eligibility is stronger when the video has an indexed watch page and metadata.
- Open Graph's required page object properties are `og:title`, `og:type`, `og:image`, and `og:url`.
- Astro provides image optimization via `Image` and `Picture`, but has no native video processing/streaming support; use a hosted video service or prepared/CDN-hosted files.
- Django includes a high-level sitemap framework that can generate `/sitemap.xml` from Python `Sitemap` classes.
