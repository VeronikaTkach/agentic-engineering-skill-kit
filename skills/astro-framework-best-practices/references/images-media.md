# Images and Media in Astro

## Image Placement

- Put processable local images in `src/assets` or another `src/` folder.
- Put unprocessed static files in `public`.
- Use `public` for favicons, manifest assets, robots.txt, static downloads, and files that require direct stable URLs.

## Astro Image Components

Use:

- `<Image />` for optimized single-image output.
- `<Picture />` for multiple formats/sizes and responsive art direction.
- Native `<img>` only when optimization is unnecessary or handled elsewhere.

Rules:

- Always provide meaningful `alt` for content images.
- Use empty `alt=""` for purely decorative images.
- Preserve or specify dimensions to prevent CLS.
- Configure authorized remote sources before expecting Astro to optimize remote images.
- Remember that `public/` images and unauthorized remote images are not optimized.

## Remote Images

- Treat CMS/CDN image URLs as remote images.
- Configure `image.domains` or `image.remotePatterns` as appropriate.
- Ensure the remote server returns cacheable, stable image URLs.
- For large CMS libraries, consider CDN-side transforms instead of generating too many variants at build time.

## Markdown and MDX

- Markdown image syntax can be optimized for local `src/` images and remote images.
- `public/` images referenced in Markdown are not optimized.
- Use MDX when authors need Astro image components or custom media components inside content.

## Video

Astro does not provide a native video optimization pipeline equivalent to `astro:assets` for images.

Use one of:

- prepared MP4/WebM files served from `public` or CDN;
- third-party video hosting;
- a media service such as Mux, Cloudinary, or ImageKit when transcoding/adaptive delivery is needed;
- a custom build/CDN pipeline outside Astro.

Implementation rules:

- Use `poster`.
- Use `preload="metadata"` or `preload="none"` unless the video is truly critical.
- Avoid autoplay audio.
- Use `muted` and `playsinline` for autoplaying inline video.
- Lazy-load below-fold iframes and heavy embeds.
- Reserve dimensions or aspect ratio for video containers.
