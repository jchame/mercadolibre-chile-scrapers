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

## Guides

- [MercadoLibre Chile local stock scraper for Apify](./guides/mercadolibre-chile-local-stock-scraper.html)
- [Scraper de MercadoLibre Chile con filtro Envio local](./guides/scraper-mercadolibre-chile-envio-local.html)
- [Measure MercadoLibre Chile saturation: local vs imported listings](./guides/mercadolibre-chile-local-vs-imported-saturation.html)
- [Extract MercadoLibre Chile shipping, sold, and quantity evidence](./guides/mercadolibre-chile-vip-detail-evidence.html)

## Demo And Promotion Assets

- [Atomic local-stock demo](./demos/atomic-local-stock-demo.md)
- [Actor 1 VIP detail demo](./demos/actor1-vip-detail-demo.md)
- [Demo video scripts](./demos/demo-scripts.md)
- [Sample Atomic output](./examples/sample-atomic-output.json)
- [Sample VIP detail output](./examples/sample-vip-detail-output.json)
- [Social posts](./promotion/social-posts.md)
- [Outreach templates](./promotion/outreach-templates.md)
- [Apify Console checklist](./promotion/apify-console-checklist.md)

## Validated Example Tasks

Created, smoke-tested, and published task landing pages:

- [Scrape MercadoLibre Chile local stock listings](https://apify.com/jchame/mercadolibre-chile-scraper/examples/mercadolibre-chile-local-stock-listings)
- [Get MercadoLibre Chile item detail evidence](https://apify.com/jchame/mercadolibre-chile-scraper/examples/mercadolibre-chile-item-detail-evidence)
- [Debug MercadoLibre Chile search extraction](https://apify.com/jchame/mercadolibre-chile-scraper/examples/mercadolibre-chile-parser-diagnostic)
- [Check MercadoLibre Chile market saturation](https://apify.com/jchame/atomic-actor-1/examples/mercadolibre-chile-market-saturation)
- [Scrape MercadoLibre Chile local stock at scale](https://apify.com/jchame/atomic-actor-1/examples/mercadolibre-chile-local-stock-at-scale)
- [Extract MercadoLibre Chile VIP detail evidence](https://apify.com/jchame/atomic-actor-1/examples/mercadolibre-chile-vip-detail-batch)
- [Run a deduped MercadoLibre Chile category mission](https://apify.com/jchame/atomic-actor-1/examples/mercadolibre-chile-category-mission)
- [Compare local vs imported MercadoLibre Chile listings](https://apify.com/jchame/atomic-actor-1/examples/mercadolibre-chile-local-vs-imported)
