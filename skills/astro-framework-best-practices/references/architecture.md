# Astro Architecture and Rendering

## Rendering Mode Selection

Prefer the least dynamic model that satisfies the feature.

| Requirement | Recommended Astro model |
|---|---|
| Static marketing/content/docs pages | prerendered static routes |
| Dynamic route content known at build time | `getStaticPaths()` |
| CMS content updated on publish | prerender with webhook rebuild, or SSR if freshness requires request-time data |
| Auth, cookies, per-user personalization | SSR/on-demand route |
| One slow/personalized fragment in mostly static page | server island |
| Form submission or small server action | endpoint or Astro Actions where appropriate |
| Full app-like state across pages | consider framework islands or a different app framework if most pages become client apps |

## Project Structure

Recommended baseline:

```text
src/
  components/
  layouts/
  pages/
  content/
  lib/
  styles/
  assets/
public/
astro.config.mjs
```

Use:

- `src/pages` for route ownership;
- `src/layouts` for document shell and metadata composition;
- `src/components` for reusable UI;
- `src/lib` for data fetching, transforms, URL helpers, and schema helpers;
- `src/assets` for images that should be processed;
- `public` for fixed files that should be served without processing.

## Islands Rules

- Build static UI as `.astro` components first.
- Add React/Vue/Svelte/Solid only for interactive components.
- Hydrate only the component that needs browser state.
- Prefer narrow props over passing large data blobs into hydrated islands.
- Avoid importing heavy browser-only libraries into shared static components.

Hydration directive guidance:

- `client:load`: only for immediately interactive, above-the-fold UI.
- `client:idle`: non-critical UI after the browser becomes idle.
- `client:visible`: below-the-fold or expensive UI that can wait for viewport entry.
- `client:media`: UI needed only for a viewport/media condition.
- `client:only`: browser-only components that cannot render on the server; use sparingly.

## Data Fetching

- Fetch build-time data in page frontmatter or content loaders for static pages.
- Centralize CMS/API clients in `src/lib`.
- Normalize data at the boundary, not throughout templates.
- Fail builds intentionally for required content; degrade gracefully only for optional blocks.
- Cache request-time data deliberately in SSR/server routes.

## Routing

- Keep URLs stable and descriptive.
- Use dynamic routes for repeated content types.
- Use `getStaticPaths()` for prerendered dynamic pages.
- Generate canonical URL helpers from a single base `site` config.
- In server mode, make missing dynamic entities return 404/410, not a rendered empty page with 200.

## View Transitions

- Use view transitions as progressive enhancement.
- Test script re-execution after client-side navigation.
- Reinitialize third-party widgets and analytics on Astro lifecycle events.
- Verify focus, scroll restoration, and `prefers-reduced-motion`.
- Disable transitions on flows where native browser navigation semantics matter more than animation.
