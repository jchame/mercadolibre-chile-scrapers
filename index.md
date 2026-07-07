# MercadoLibre Chile Scrapers For Apify

Specialized Apify actors for scraping `mercadolibre.cl` with Chile marketplace evidence.

## Which Actor Should I Use?

Use [`jchame/atomic-actor-1`](https://apify.com/jchame/atomic-actor-1) for production saturation jobs, many queries, local-only scraping, category missions, retries, mission dedupe, residential/custom proxy support, and larger VIP detail batches.

Use [`jchame/mercadolibre-chile-scraper`](https://apify.com/jchame/mercadolibre-chile-scraper) for simple checks, diagnostics, local-only pages, and small item-detail evidence batches.

## What They Extract

- CLP prices and canonical MercadoLibre Chile item URLs.
- Ratings and rough sold text when visible.
- Local/import/unknown evidence from search cards.
- MercadoLibre's `Envio local` filtered search pages.
- Query-level local-filter counts where MercadoLibre exposes them.
- VIP item-detail evidence: shipping block text, sold text, available quantity signals, catalog product IDs, and seller-offer count text when visible.

## Local Stock Rule

Only local Chile stock should count as local competition. International/imported MercadoLibre listings weigh zero for local competition. Unknown or failed visibility must remain unknown rather than being treated as no competition.

## Copy-Paste Inputs

Local-only search:

```json
{
  "searchQueries": ["cama perro"],
  "searchFilterMode": "envio_local",
  "maxItems": 60,
  "maxItemsPerQuery": 60,
  "maxPagesPerQuery": 1,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"],
    "apifyProxyCountry": "CL"
  }
}
```

Atomic production mission:

```json
{
  "atomicMode": "orchestrator",
  "searchQueries": ["monitor de bebe", "propane gauge"],
  "searchFilterMode": "envio_local",
  "maxItems": 120,
  "maxItemsPerQuery": 60,
  "maxPagesPerQuery": 1,
  "useMissionQueue": true,
  "missionDedupeMode": "mission",
  "resumeMission": true,
  "maxConcurrentChildRuns": 4,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"],
    "apifyProxyCountry": "CL"
  }
}
```

## Public Actor Pages

- <https://apify.com/jchame/atomic-actor-1>
- <https://apify.com/jchame/mercadolibre-chile-scraper>

## Validated Example Tasks

Created and smoke-tested task names:

- `jchame/mercadolibre-chile-local-stock-listings`
- `jchame/mercadolibre-chile-item-detail-evidence`
- `jchame/mercadolibre-chile-parser-diagnostic`
- `jchame/mercadolibre-chile-market-saturation`
- `jchame/mercadolibre-chile-local-stock-at-scale`
- `jchame/mercadolibre-chile-vip-detail-batch`
- `jchame/mercadolibre-chile-category-mission`
- `jchame/mercadolibre-chile-local-vs-imported`

Apify task landing pages are published from each task's Console Publication tab after a successful smoke run.
