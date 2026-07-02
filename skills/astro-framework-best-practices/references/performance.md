# Astro Performance and Core Web Vitals

## Targets

Use Google's Core Web Vitals thresholds as practical targets:

- LCP: 2.5s or less.
- INP: 200ms or less.
- CLS: 0.1 or less.

Assess at the 75th percentile, segmented by mobile and desktop, when field data is available.

## LCP

- Make the LCP element obvious: hero image, heading block, or main content image.
- Avoid making a large video, carousel, or client-rendered island the LCP bottleneck.
- Preload only the actual critical LCP asset.
- Use `fetchpriority="high"` carefully for the primary LCP image.
- Avoid lazy-loading above-the-fold LCP images.
- Keep render-blocking CSS small and deliberate.

## INP

- Hydrate fewer components.
- Use `client:visible` and `client:idle` for non-critical islands.
- Split heavy UI libraries from the initial route.
- Avoid long main-thread tasks from animation, analytics, embeds, syntax highlighting, and large client state.
- Prefer CSS transitions over JavaScript animation loops for simple UI.

## CLS

- Reserve dimensions for images, embeds, iframes, ads, and dynamic UI.
- Use Astro image components to emit dimensions where possible.
- Avoid injecting banners, cookie notices, or late content above existing content without reserved space.
- Use font loading strategies that reduce layout shift.

## JavaScript Budget

- Treat every framework island as a cost.
- Prefer Astro components for layout and static content.
- Audit bundle size after adding integrations or UI libraries.
- Avoid global client scripts for behavior that can live in one island.
- Use Partytown or delayed loading for heavy third-party scripts only after measuring benefit and risk.

## CSS

- Prefer component-scoped styles or a clear global design system.
- Avoid shipping unused framework CSS.
- Keep critical layout stable before fonts and client code load.
- Avoid excessive animation on layout-affecting properties.

## Measurement

- Use Lighthouse/PageSpeed Insights for lab checks.
- Use field data when available: CrUX, Search Console Core Web Vitals, or RUM via `web-vitals`.
- Compare before/after changes on the same route and device class.
- Treat Lighthouse TBT as a lab proxy for INP, not a replacement for field INP.
