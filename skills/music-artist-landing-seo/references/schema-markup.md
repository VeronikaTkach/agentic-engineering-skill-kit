# Structured Data for Music Artist Sites

Use JSON-LD. Validate with Google's Rich Results Test when targeting Google rich results, and with the Schema Markup Validator for broader Schema.org correctness.

Only mark up content that is visible to users on the same page. Structured data should clarify the page, not introduce hidden claims.

## Primary Entity

Use one of:

- `MusicGroup` for artist project/band identity. Schema.org notes that a music group can be a solo musician;
- `Person` for individual artist identity;
- `Organization` for label;
- combine `Person` and `MusicGroup` only when there is a real distinction.

Recommended default for a DJ/artist website:

- Use `MusicGroup` as the public artist project entity when the site is marketed under the artist alias/stage name.
- Use `Person` when the public site intentionally represents the individual person and real name.
- Connect profiles with `sameAs`, and keep those URLs consistent with visible social/streaming links.

## Artist Schema Example

```json
{
  "@context": "https://schema.org",
  "@type": "MusicGroup",
  "@id": "https://example.com/#artist",
  "name": "Artist Name",
  "alternateName": ["Artist Alias"],
  "url": "https://example.com/",
  "image": "https://example.com/og/artist.jpg",
  "genre": ["Techno", "Melodic Techno", "Electronic Music"],
  "sameAs": [
    "https://www.instagram.com/example/",
    "https://www.youtube.com/@example",
    "https://soundcloud.com/example",
    "https://open.spotify.com/artist/example"
  ]
}
```

If using `Person`, keep `jobTitle` such as `DJ and music producer`. If using `MusicGroup`, prefer artist/music properties such as `genre`, `album`, `track`, `sameAs`, and `url`.

## Website Schema

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "@id": "https://example.com/#website",
  "url": "https://example.com/",
  "name": "Artist Name",
  "publisher": {
    "@id": "https://example.com/#artist"
  }
}
```

## Music Release

Use `MusicAlbum` or `MusicRecording` when release data is available.

Google may not show a dedicated rich result for every music schema type, but this markup can still strengthen entity clarity when it accurately reflects visible release data.

```json
{
  "@context": "https://schema.org",
  "@type": "MusicRecording",
  "name": "Track Title",
  "byArtist": {
    "@id": "https://example.com/#artist"
  },
  "datePublished": "2026-01-01",
  "url": "https://example.com/music/track-title/",
  "image": "https://example.com/media/track-cover.jpg",
  "sameAs": [
    "https://open.spotify.com/track/example",
    "https://music.apple.com/example"
  ]
}
```

## Tour Event

Use `MusicEvent` for individual events. For Google event eligibility, include required fields and test with Rich Results Test.

```json
{
  "@context": "https://schema.org",
  "@type": "MusicEvent",
  "name": "Artist Name at Venue Name",
  "startDate": "2026-09-15T22:00:00+03:00",
  "eventStatus": "https://schema.org/EventScheduled",
  "eventAttendanceMode": "https://schema.org/OfflineEventAttendanceMode",
  "performer": {
    "@id": "https://example.com/#artist"
  },
  "location": {
    "@type": "Place",
    "name": "Venue Name",
    "address": {
      "@type": "PostalAddress",
      "addressLocality": "City",
      "addressCountry": "Country"
    }
  },
  "offers": {
    "@type": "Offer",
    "url": "https://tickets.example.com/",
    "price": "35.00",
    "priceCurrency": "USD",
    "availability": "https://schema.org/InStock",
    "validFrom": "2026-07-01T10:00:00+03:00"
  }
}
```

If price is unknown, do not invent it. Use the ticket URL and availability only when accurate.

## Video

Use `VideoObject` for hosted or embedded music videos/live sets.

Required useful fields:

- `name`
- `description`
- `thumbnailUrl`
- `uploadDate`
- `embedUrl` or `contentUrl`

Recommended fields:

- `duration`
- `description`
- `publisher`
- `interactionStatistic` when reliable

Do not use `VideoObject` for a decorative, silent homepage background loop unless the page visibly presents it as a real video item with title, description, and thumbnail.

For video SEO, create a dedicated page for each important clip or live set. Third-party YouTube/Vimeo embeds can still be indexed, but the page should provide unique metadata and supporting text.

## Breadcrumbs

Use `BreadcrumbList` for deeper pages like releases, videos, press items, and tour events.

## Django + Astro Implementation Notes

- Store schema-relevant fields in Django models and serializers: artist profile, releases, tour events, videos, press, contacts, social links.
- Render JSON-LD in Astro page templates from the same data shown in the UI.
- Generate stable `@id` values such as `https://example.com/#artist`, `https://example.com/#website`, and `https://example.com/tour/event-slug/#event`.
- Keep schema, title/meta, OG tags, and visible page data synchronized during CMS preview and publish.
