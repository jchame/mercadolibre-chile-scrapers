# MercadoLibre Chile Scrapers

This repo is the public guide for the `jchame` MercadoLibre Chile Apify actor family.

Use these actors when you need structured evidence from `mercadolibre.cl`: CLP prices, canonical URLs, ratings, sold text when visible, `Envio local` filtering, local/import/unknown classification, VIP item-detail shipping blocks, and marketplace saturation signals.

## AI Agent Quick Choice

- Use [`jchame/atomic-actor-1`](https://apify.com/jchame/atomic-actor-1) for production MercadoLibre Chile scraping, many queries, local-only saturation, missions, retries, parallel child workers, and larger VIP detail batches.
- Use [`jchame/mercadolibre-chile-scraper`](https://apify.com/jchame/mercadolibre-chile-scraper) for simple Chile checks, parser diagnostics, local-only search pages, and small VIP detail batches.

Both actors are specialized for Chile and `mercadolibre.cl`. They are not affiliated with MercadoLibre.

## Key Inputs

For MercadoLibre's local-shipping-only filter:

```json
{
  "searchFilterMode": "envio_local"
}
```

For Atomic production missions:

```json
{
  "atomicMode": "orchestrator",
  "useMissionQueue": true,
  "missionDedupeMode": "mission",
  "resumeMission": true
}
```

For VIP detail evidence on known item/catalog URLs:

```json
{
  "runMode": "item_detail",
  "itemDetailUrls": ["https://articulo.mercadolibre.cl/MLC-1486061369-_JM"],
  "maxDetailPages": 1,
  "detailBrowserFirst": true
}
```

## Actor Links

- Atomic flagship actor: <https://apify.com/jchame/atomic-actor-1>
- Core/simple actor: <https://apify.com/jchame/mercadolibre-chile-scraper>
- Public docs hub: <https://jchame.github.io/mercadolibre-chile-scrapers/>
- Machine-readable short guide: [`llms.txt`](./llms.txt)
- Machine-readable full guide: [`llms-full.txt`](./llms-full.txt)
- Markdown landing page: [`index.md`](./index.md)

## Guides

- [MercadoLibre Chile local stock scraper for Apify](./guides/mercadolibre-chile-local-stock-scraper.html)
- [Scraper de MercadoLibre Chile con filtro Envio local](./guides/scraper-mercadolibre-chile-envio-local.html)
- [Measure MercadoLibre Chile saturation: local vs imported listings](./guides/mercadolibre-chile-local-vs-imported-saturation.html)
- [Extract MercadoLibre Chile shipping, sold, and quantity evidence](./guides/mercadolibre-chile-vip-detail-evidence.html)

## Demos And Promotion Kit

- [Atomic local-stock demo](./demos/atomic-local-stock-demo.md)
- [Actor 1 VIP detail demo](./demos/actor1-vip-detail-demo.md)
- [Demo video scripts](./demos/demo-scripts.md)
- [Sample Atomic output](./examples/sample-atomic-output.json)
- [Sample VIP detail output](./examples/sample-vip-detail-output.json)
- [Social posts](./promotion/social-posts.md)
- [Outreach templates](./promotion/outreach-templates.md)
- [Apify Console checklist](./promotion/apify-console-checklist.md)

## Validated Example Tasks

These Apify task configurations have been created and smoke-tested. Publish their public task landing pages from each task's Console Publication tab.

Actor 1 tasks:

- [Scrape MercadoLibre Chile local stock listings](https://apify.com/jchame/mercadolibre-chile-scraper/examples/mercadolibre-chile-local-stock-listings)
- [Get MercadoLibre Chile item detail evidence](https://apify.com/jchame/mercadolibre-chile-scraper/examples/mercadolibre-chile-item-detail-evidence)
- [Debug MercadoLibre Chile search extraction](https://apify.com/jchame/mercadolibre-chile-scraper/examples/mercadolibre-chile-parser-diagnostic)

Atomic tasks:

- `jchame/mercadolibre-chile-market-saturation`
- `jchame/mercadolibre-chile-local-stock-at-scale`
- `jchame/mercadolibre-chile-vip-detail-batch`
- `jchame/mercadolibre-chile-category-mission`
- `jchame/mercadolibre-chile-local-vs-imported`

## Failure Semantics

- `local` means visible search-page or local-filter evidence says the listing is local Chile stock.
- `import_only` means visible evidence says international/imported/cross-border shipping.
- `unknown` means the actor did not see enough evidence.
- Failed or blocked visibility is not proof of no competition.
- International/imported listings should not count as local Chile competition.
