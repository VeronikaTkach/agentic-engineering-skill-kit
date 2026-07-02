# Content and Keyword Strategy

## Query Clusters

Prioritize natural, user-facing language. Use keyword research to cover search intent, but do not turn titles, headings, alt text, or schema into keyword lists.

### Branded

- `{artist name}`
- `{artist name} DJ`
- `{artist name} producer`
- `{artist name} music`
- `{artist name} tour`
- `{artist name} booking`
- `{artist name} press`
- `{artist name} label`

### Genre / Positioning

- `{artist name} techno`
- `{artist name} melodic techno`
- `{artist name} electronic music`
- `{artist name} electronic artist`
- `{artist name} DJ set`
- `{artist name} live set`
- `{artist name} mixes`
- `{artist name} releases`

### Release

- `{track title} {artist name}`
- `{artist name} {release title}`
- `{release title} Spotify`
- `{release title} music video`

### Tour / Booking

- `{artist name} tour dates`
- `{artist name} tickets`
- `{artist name} live`
- `book {artist name}`
- `{artist name} booking contact`
- `{artist name} press kit`
- `{artist name} EPK`

### Entity / Disambiguation

- `{artist name} official`
- `{artist name} official website`
- `{artist name} Instagram`
- `{artist name} SoundCloud`
- `{artist name} Spotify`
- `{artist name} YouTube`
- `{artist name} Discogs`

## Page Copy Guidelines

### Home

Include:

- artist name;
- role: DJ, producer, musician, label founder if true;
- core genre;
- current priority: latest release, tour, label, video;
- links to music, tour, booking, socials.

Avoid:

- vague lines like "welcome to the official website" as the only crawlable copy;
- image-only text;
- keyword stuffing.

Technical note:

- If the first screen is mostly video and logo, place the crawlable entity copy below the fold or in an accessible Info/EPK section rendered in HTML.
- Match the page copy, schema, title, OG tags, and visible social links so Google and social platforms receive the same entity signals.

### Info / Bio

Use two bio lengths:

- short bio: 50-80 words for homepage/press intro;
- long bio: 250-500 words for Info/EPK.

Include:

- origin/location if useful;
- genre and sound;
- notable releases/tours/festivals;
- label/radio show;
- press proof;
- booking/management contact.

Avoid unverifiable claims like "the best", "world-famous", or inflated festival/press proof unless the claim is supported by visible evidence.

### Music

For each item:

- title;
- type: single, EP, album, mix, radio show;
- date/year;
- 1-2 sentence description if strategically useful;
- platform links;
- cover alt text: `{artist name} - {release title} cover artwork`.

Avoid writing the same generic description for every release. Unique 1-2 sentence context is better than repeated filler.

### Tour

Use text fields:

- date;
- city;
- country;
- venue/event;
- ticket URL;
- status: upcoming/sold out/past.

Use ISO dates in data/CMS fields and human-readable dates in the UI. Keep cancelled, postponed, sold out, and past statuses explicit.

### Press

For each item:

- publication name;
- article title;
- date;
- excerpt or quote;
- external link;
- image alt text containing publication/title when relevant.

Use short excerpts or summaries unless republishing rights are confirmed.

## Metadata Patterns

Homepage title:

```text
{Artist Name} | DJ & Music Producer
```

Music title:

```text
Music | {Artist Name}
```

Tour title:

```text
Tour Dates | {Artist Name}
```

Booking title:

```text
Booking | {Artist Name}
```

Meta description pattern:

```text
Official website of {Artist Name}, {role/genre phrase}. Listen to music, watch videos, view tour dates, read press, and find booking contacts.
```

## CMS Fields to Preserve SEO Consistency

For each editable page or content item, store:

- SEO title;
- meta description;
- canonical URL override;
- OG title;
- OG description;
- OG image;
- noindex flag;
- schema-relevant fields such as date, venue, location, platform links, thumbnail, upload date, and source URL.

In a Django + Astro stack, Django can own these fields, but Astro must render them into the final HTML for every public URL.
