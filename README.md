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
- Machine-readable short guide: [`llms.txt`](./llms.txt)
- Machine-readable full guide: [`llms-full.txt`](./llms-full.txt)
- Markdown landing page: [`index.md`](./index.md)

## Validated Example Tasks

These Apify task configurations have been created and smoke-tested. Publish their public task landing pages from each task's Console Publication tab.

Actor 1 tasks:

- `jchame/mercadolibre-chile-local-stock-listings`
- `jchame/mercadolibre-chile-item-detail-evidence`
- `jchame/mercadolibre-chile-parser-diagnostic`

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
