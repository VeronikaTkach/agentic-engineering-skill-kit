---
name: astro-framework-best-practices
description: Technical development guidance, architecture reviews, implementation patterns, performance checks, SEO-safe rendering, and best-practice recommendations for Astro framework projects. Use when an AI agent needs to build, refactor, audit, or choose implementation details in Astro, including islands architecture, prerendering versus SSR, routing, data fetching, images, view transitions, integrations, deployment, Google crawlability, and Core Web Vitals. This skill is framework-specific and intentionally excludes domain-specific marketing, music artist, and brand-site strategy.
---

# Astro Framework Best Practices

## Scope

Use this skill for technical Astro work only: architecture, implementation, refactoring, audits, debugging, performance, rendering mode choices, SEO-safe HTML output, image handling, routing, integrations, testing, and deployment.

Do not add domain-specific content strategy unless the user explicitly asks. Keep recommendations grounded in Astro docs, Google Search Central, and web.dev performance guidance.

## Source Policy

When the user asks for current behavior, latest Astro features, compatibility, SEO correctness, or exact API details, browse and cite primary sources:

- Astro docs for framework APIs and integrations.
- Google Search Central for crawlability, indexing, links, metadata, and image SEO.
- web.dev for Core Web Vitals and browser performance practices.

Use `references/sources.md` as the source map.

## Core Workflow

1. Identify the project mode:
   - static/prerendered site;
   - hybrid site with selected SSR routes;
   - fully server-rendered app;
   - content-heavy site using collections or a CMS;
   - interactive UI with islands;
   - migration from another framework.

2. Inspect existing project conventions before changing code:
   - `astro.config.*`;
   - `package.json`;
   - `src/pages`;
   - `src/layouts`;
   - `src/components`;
   - `src/content` or CMS/data layer;
   - integrations and adapter.

3. Choose the least dynamic rendering model that satisfies the feature:
   - prerender static pages by default;
   - use hybrid SSR only for request-time personalization, auth, cookies, highly dynamic data, or server-only logic;
   - use server islands for slow or personalized fragments when the surrounding page can stay cacheable.

4. Keep the browser JavaScript budget deliberate:
   - prefer `.astro` components for static UI;
   - hydrate framework components only where interactivity is required;
   - choose `client:*` directives based on when interactivity is needed;
   - avoid turning the whole page into a client-side app unless the product truly requires it.

5. Apply the relevant reference file:
   - architecture/rendering: `references/architecture.md`;
   - SEO and crawlability: `references/google-seo.md`;
   - performance and Core Web Vitals: `references/performance.md`;
   - images and media: `references/images-media.md`;
   - implementation review checklist: `references/review-checklist.md`.

## Astro Defaults to Preserve

- Static HTML first.
- Islands for isolated interactivity.
- Route-level rendering decisions.
- TypeScript-friendly content/data modeling.
- Optimized images through `astro:assets` where possible.
- Real links, metadata, and content in HTML for search and non-JS clients.

## Decision Rules

- If content does not depend on the incoming request, prerender it.
- If only one component is dynamic, avoid SSR for the whole page when a server island or API-backed island is enough.
- If a component is visible but not immediately interactive, prefer delayed hydration such as `client:visible` or `client:idle`.
- If an image is local and content-bearing, import it from `src/` and render with `<Image />` or `<Picture />`.
- If an image is in `public/`, treat it as served as-is.
- If remote images must be optimized, configure authorized image sources.
- If using view transitions, test script reinitialization, focus behavior, reduced motion, and analytics/pageview behavior.
- If Google must index a page, do not rely on client-only rendering for primary content, canonical, title, or links.

## Red Flags

- React/Vue/Svelte app shell used where `.astro` templates would work.
- Important content exists only after client-side fetch.
- Navigation uses buttons/click handlers instead of crawlable `<a href>`.
- Dynamic routes lack stable canonical URLs and generated static paths where appropriate.
- All routes use SSR without a clear request-time need.
- Large images live in `public/` and are used directly in layouts/grids without sizing.
- Layout shifts from missing image, iframe, or ad/embed dimensions.
- View transitions are enabled but scripts or analytics do not re-run correctly.
- `site` is missing from `astro.config.*` while sitemap/canonical URLs are expected.
- Error pages return 200 instead of meaningful 404/410 statuses in server mode.

## Output Formats

- Implementation plan: rendering mode, file map, data flow, hydration choices, testing.
- Code review: findings first, with file/line references and severity.
- Architecture recommendation: options, tradeoffs, chosen path, risks.
- Performance audit: LCP/INP/CLS risks, JavaScript budget, image/media changes.
- SEO technical audit: crawlability, metadata, links, status codes, sitemap, canonical.
- Migration guidance: route mapping, component strategy, content/data migration, parity checks.
