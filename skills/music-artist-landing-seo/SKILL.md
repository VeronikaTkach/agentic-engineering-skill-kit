---
name: music-artist-landing-seo
description: SEO strategy, audits, content architecture, metadata, schema markup, launch checklists, and optimization workflows for music artist websites, DJ/producer landing pages, release pages, tour pages, press pages, label pages, and booking-focused artist sites. Use when an AI agent needs to plan, review, write, or improve SEO for an artist website or music landing page, including mobile-first media-heavy pages with videos, social links, streaming links, tour dates, press coverage, and artist biographies.
---

# Music Artist Landing SEO

## Overview

Use this skill to produce source-grounded SEO strategy for music artist landing pages and small artist websites. Prioritize search intent, artist entity clarity, technical indexability, performance, structured data, social previews, and conversion paths for streaming, tickets, press, and booking.

Primary source families for this skill:

- Google Search Central for crawling, indexing, images, videos, structured data, JavaScript SEO, and page experience.
- Schema.org for entity vocabulary such as `MusicGroup`, `MusicEvent`, `MusicRecording`, and `VideoObject`.
- Open Graph protocol for social graph metadata.
- Official Astro docs for image optimization, rendering, islands, and media constraints.
- Official Django docs for sitemaps, admin-managed content, static/media handling, and model fields.

When the user asks for "latest", "current", compliance, or exact platform behavior, browse and cite primary docs before giving final recommendations.

## Core Workflow

1. Identify the site type:
   - artist homepage
   - full artist website
   - release landing page
   - tour page
   - press / EPK page
   - label page
   - booking page

2. Define the primary SEO goal:
   - own branded search results
   - rank for artist + genre / city / label queries
   - support release discovery
   - sell tickets
   - generate bookings
   - strengthen press / knowledge graph signals

3. Map pages to intent:
   - Home: entity, brand, latest priority, navigation hub
   - Music: discography, releases, streaming links
   - Tour: upcoming dates, tickets, cities, venues
   - Videos: music videos, live sets, interviews
   - Press: authority, quotes, publications, EPK
   - Info: biography, contacts, management, booking
   - Label: label entity, catalog, releases, submissions if relevant

4. Audit the page using the fast checklist in `references/audit-checklist.md`.

5. For metadata and copy, use `references/content-keywords.md`.

6. For structured data, use `references/schema-markup.md`.

7. For video, image, Core Web Vitals, crawlability, and launch QA, use `references/technical-seo.md`.

8. When recommendations could conflict, apply the conflict rules below.

## Conflict Rules

- If design wants video/canvas-only hero but SEO needs crawlable content, keep the visual hero and add concise server-rendered artist/entity text.
- If a video is decorative background, optimize for performance and accessibility; do not mark it as a primary `VideoObject`.
- If a video is the main content, create a dedicated watch page and add video metadata/schema.
- If Astro can optimize an image, use `Image`/`Picture`; if the image is remote from Django/CDN, configure authorized domains or accept that it may be passed through.
- If Django is the CMS and Astro is the frontend, ensure SEO fields are modeled in Django but rendered in final Astro HTML.
- If structured data is accurate but not visible to users, do not add it; Google's structured data guidance expects page markup to describe page content visible to users.
- If a page should not rank, use intentional `noindex`/robots handling from the initial HTML or HTTP layer; do not rely on client-side JS to remove `noindex`.

## Output Formats

Choose the output shape based on the user request:

- SEO audit: findings first, ordered by severity, with exact page/section references.
- SEO plan: page map, target queries, metadata, schema, technical checklist.
- Metadata pack: title, meta description, OG title, OG description, canonical, image notes.
- Launch checklist: critical / recommended / post-launch.
- Content brief: H1/H2 structure, copy blocks, internal links, media requirements.
- Implementation notes: framework-specific guidance for Astro, Next.js, Django, or static HTML.

## Artist SEO Principles

- Treat the artist as an entity, not just a brand phrase.
- Make the exact artist name easy to parse in title, H1, schema, alt text, social profiles, and footer.
- Use genre, role, location, label, notable releases, radio shows, festivals, and press as entity support.
- Keep hero pages visually strong, but never hide all crawlable text behind video/canvas.
- Prefer short, indexable text blocks over decorative copy.
- Every major page needs one clear search purpose.
- Use real media and canonical social / streaming links.
- Preserve performance: a beautiful hero video that blocks LCP is an SEO problem.
- Do not overstuff keywords like "DJ", "techno", "music producer"; place them naturally.

## Minimum Page Requirements

Every public page should have:

- one unique `<title>`;
- one unique meta description;
- one canonical URL;
- one clear H1;
- crawlable body text;
- Open Graph and Twitter Card metadata;
- optimized preview image;
- descriptive media alt text where relevant;
- internal links to related pages;
- structured data where applicable.

For `Django + Astro`, "public page" means the final rendered page, not merely fields stored in Django. Verify the built/served HTML contains the intended metadata, links, JSON-LD, and crawlable text.

## Red Flags

Flag these immediately:

- homepage only says "coming soon" without artist entity text;
- video hero has no poster or blocks LCP;
- no crawlable artist biography;
- social links use icons without accessible names;
- releases have only platform buttons, no titles/dates;
- tour dates are images instead of text;
- YouTube/Vimeo embeds load heavily before interaction;
- missing canonical URLs;
- duplicate title/meta across pages;
- no Organization/Person/MusicGroup schema;
- booking form has no visible contact fallback;
- press logos/images lack publication names in text.
