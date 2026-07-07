# Actor 1 VIP Detail Demo

Goal: show how Actor 1 extracts detail-page evidence for known MercadoLibre Chile item URLs.

## Actor

`jchame/mercadolibre-chile-scraper`

## Input

```json
{
  "runMode": "item_detail",
  "itemDetailUrls": [
    "https://articulo.mercadolibre.cl/MLC-1486061369-_JM",
    "https://articulo.mercadolibre.cl/MLC-1595944459-_JM"
  ],
  "maxDetailPages": 2,
  "detailBrowserFirst": true,
  "proxyConfiguration": {
    "useApifyProxy": true,
    "apifyProxyGroups": ["RESIDENTIAL"],
    "apifyProxyCountry": "CL"
  }
}
```

## What to show

1. Open Actor 1 on Apify.
2. Paste the VIP detail input.
3. Run the actor.
4. Open the dataset.
5. Highlight `shipping_block_text_visible`, `sold_text_visible`, `available_quantity_text_visible`, `catalog_product_id`, and `fetched_item_ids`.

## Talk track

Actor 1 is the simple diagnostic scraper. VIP detail mode is intentionally capped and only follows URLs the caller already knows. It captures the missing shipping, sold, quantity, and catalog evidence that a pure search page cannot always expose.

