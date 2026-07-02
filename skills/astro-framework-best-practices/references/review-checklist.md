# Astro Technical Review Checklist

## Architecture

- Rendering mode is justified per route.
- Static pages are prerendered unless request-time behavior is required.
- Dynamic routes use `getStaticPaths()` when content is known at build time.
- SSR routes return correct status codes and redirects.
- Server islands are used only when they simplify dynamic fragments without slowing the page shell.

## Components

- Static UI is implemented with `.astro` components.
- Framework components are used only for interactive UI.
- Hydration directives match the interaction priority.
- Browser-only code is not imported into server/static paths accidentally.
- Props passed to islands are minimal and serializable.

## Data

- Data fetching is centralized and typed.
- Required data failures fail clearly during build or return proper SSR errors.
- Optional data has controlled fallback states.
- URL, slug, canonical, and date helpers are consistent.

## SEO/Crawlability

- Important content is present in generated HTML.
- Navigation and internal links use `<a href>`.
- Titles, descriptions, canonicals, robots, and structured data render in the page HTML.
- `site` is configured when sitemap or absolute URLs are needed.
- Sitemap excludes drafts/noindex/private routes.
- Missing dynamic content returns 404/410.

## Performance

- LCP asset is optimized and not lazy-loaded.
- Images have dimensions/aspect ratios.
- Below-fold islands and embeds are deferred.
- Third-party scripts are delayed or isolated.
- Bundle size is checked after adding integrations.
- View transitions do not break scripts, analytics, focus, reduced motion, or scroll.

## Accessibility

- Semantic HTML is preserved.
- Interactive islands are keyboard accessible.
- Motion respects `prefers-reduced-motion`.
- Images have appropriate alt text.
- Route transitions preserve focus and announce navigation where relevant.

## Verification

- Run build.
- Run typecheck or Astro check if available.
- Run tests if configured.
- Inspect production-like HTML output.
- Run Lighthouse/PageSpeed for affected pages.
- Test desktop and mobile viewport behavior.
