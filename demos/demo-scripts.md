# Demo Video Scripts

## Video 1: Atomic Local Stock Saturation

Length: 60-90 seconds.

Script:

> If you validate products on MercadoLibre Chile, normal search results can be misleading. Imported listings often show up next to local stock, but only local Chile stock should count as local competition.
>
> This is Atomic Actor 1 on Apify. I paste two queries, set `searchFilterMode` to `envio_local`, and keep the run bounded to one page per query.
>
> Atomic launches worker shards, uses Chile residential proxy settings, dedupes mission work, and returns one row per listing.
>
> In the dataset I can read `price_clp`, `item_id`, canonical URL, rating, local-stock status, and the actual evidence text. Here the rows are marked local because MercadoLibre's local-shipping filter was used, and fast delivery text is preserved when visible.
>
> This is built for saturation checks, pricing samples, and product validation pipelines where imported listings should not count as Chile local competition.

## Video 2: VIP Detail Evidence

Length: 60-90 seconds.

Script:

> Search pages are fast, but sometimes a pipeline needs detail evidence for a known MercadoLibre Chile listing.
>
> Actor 1 has a capped VIP detail mode. I pass a small list of item URLs, enable browser-first detail loading, and keep `maxDetailPages` low.
>
> The output captures the fetched item ID, catalog product ID, visible sold text, available quantity signal, and shipping block text for the Chile delivery context.
>
> This is useful for shipping verification, demand evidence, and catalog-overstatement correction. Failed visibility stays explicit; it is not treated as no competition.

