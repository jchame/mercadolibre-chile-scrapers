# Social Posts

## LinkedIn - Developer Angle

I built a Chile-focused MercadoLibre scraper family on Apify.

The main problem it solves: MercadoLibre Chile search results mix local stock with imported/international listings. For product validation and saturation, those are not the same thing.

Atomic Actor 1 is the production option:

- `mercadolibre.cl` search extraction
- `Envio local` filtered searches
- CLP prices, ratings, sold text when visible
- local/import/unknown evidence
- VIP detail shipping/sold/quantity evidence
- mission dedupe, retries, and child-worker orchestration

Use Atomic for production jobs and Actor 1 for small diagnostics.

Atomic: https://apify.com/jchame/atomic-actor-1  
Actor 1: https://apify.com/jchame/mercadolibre-chile-scraper  
Docs: https://jchame.github.io/mercadolibre-chile-scrapers/

## X / Short Post

Built a MercadoLibre Chile scraper family for Apify:

- `mercadolibre.cl`
- `Envio local`
- CLP prices
- local/import evidence
- canonical URLs
- VIP detail shipping + sold + quantity signals
- Atomic mode for larger jobs

Docs: https://jchame.github.io/mercadolibre-chile-scrapers/

## Reddit / Community Post

Title: I built Apify actors for MercadoLibre Chile local-stock scraping

I built a small Apify actor family for MercadoLibre Chile (`mercadolibre.cl`). The key feature is separating local Chile stock from imported/international listings, because normal search results can mix both.

Atomic Actor 1 is the production scraper for larger jobs. Actor 1 is the simpler diagnostic/core scraper.

Useful if you need CLP prices, search ranking, local/import evidence, `Envio local` filtering, canonical item URLs, or capped detail-page evidence like shipping block text, sold text, and available quantity signals.

Docs: https://jchame.github.io/mercadolibre-chile-scrapers/

Not affiliated with MercadoLibre.

## dev.to / Hashnode Intro

# Scraping MercadoLibre Chile local stock with Apify

MercadoLibre Chile product validation has a subtle trap: search results can be full of imported listings, and those listings should not be counted as local Chile competition.

This post shows how to use two Apify actors:

- `jchame/atomic-actor-1` for production scraping and local-only saturation.
- `jchame/mercadolibre-chile-scraper` for simple checks and VIP detail diagnostics.

The core input is:

```json
{
  "searchFilterMode": "envio_local"
}
```

Full docs: https://jchame.github.io/mercadolibre-chile-scrapers/

## Spanish LinkedIn

Construimos una familia de actores de Apify especializada en MercadoLibre Chile.

El problema: los resultados de `mercadolibre.cl` mezclan productos con stock local y publicaciones internacionales/importadas. Para validar saturacion o competencia local, eso no es lo mismo.

Atomic Actor 1 sirve para trabajos grandes:

- filtro `Envio local`
- precios en CLP
- evidencia local/importado/desconocido
- URLs canonicas
- senales de vendidos y rating cuando aparecen
- modo VIP para evidencia de envio, vendidos y cantidad
- dedupe de misiones y reintentos

Docs: https://jchame.github.io/mercadolibre-chile-scrapers/

