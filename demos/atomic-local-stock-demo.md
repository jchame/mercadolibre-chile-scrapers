# Atomic Local Stock Demo

Goal: show a developer or coding agent how to run Atomic for MercadoLibre Chile local-stock saturation.

## Actor

`jchame/atomic-actor-1`

## Input

```json
{
  "atomicMode": "orchestrator",
  "searchQueries": ["cama perro", "cortina bano"],
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

## What to show

1. Open the Atomic actor page on Apify.
2. Paste the input.
3. Run the actor.
4. Open the dataset.
5. Highlight `item_id`, `title`, `price_clp`, `local_stock_status`, `local_stock_evidence_text`, `search_filter_mode`, and `permalink_canonical`.
6. Open the `OUTPUT` key-value record and show child-run cost and shard health.

## Talk track

Atomic is the production MercadoLibre Chile scraper. It uses bounded child workers, mission dedupe, retries, and residential/custom proxy support. The key input is `searchFilterMode: "envio_local"`, which requests MercadoLibre's local-shipping filtered search page so imported listings do not dominate the sample.

