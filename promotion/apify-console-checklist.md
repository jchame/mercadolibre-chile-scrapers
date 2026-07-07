# Apify Console Checklist

These steps require Apify Console access and should not be automated blindly.

## Actor Store Pages

- Confirm `jchame/mercadolibre-chile-scraper` is public.
- Confirm `jchame/atomic-actor-1` is public.
- Confirm source files are hidden on both Actor detail pages.
- Upload icons:
  - Actor 1: `assets/store-icon-local-stock.svg` from the Actor 1 repo.
  - Atomic: `assets/store-icon-atomic.svg` from the Atomic repo.
- Confirm categories: `ECOMMERCE`, `DEVELOPER_TOOLS`.

## Publish Task Landing Pages

Publish these tasks only after confirming the latest run has useful output:

Actor 1:

- `mercadolibre-chile-local-stock-listings`
- `mercadolibre-chile-item-detail-evidence`
- `mercadolibre-chile-parser-diagnostic`

Atomic:

- `mercadolibre-chile-market-saturation`
- `mercadolibre-chile-local-stock-at-scale`
- `mercadolibre-chile-vip-detail-batch`
- `mercadolibre-chile-category-mission`
- `mercadolibre-chile-local-vs-imported`

For each task:

1. Open the task in Apify Console.
2. Check the latest run succeeded.
3. Check the dataset has useful rows.
4. Open the Publication tab.
5. Publish the task page.
6. Hide confusing advanced inputs from the public preview when Console allows it.
7. Confirm the public task URL loads logged out.

## Atomic Monetization Gate

Do not enable Atomic paid traffic until this is verified from a non-owner Apify account:

1. Run a small Atomic task from the non-owner account.
2. Confirm child worker costs are charged to the caller or recoverable.
3. Compare parent `usageTotalUsd` plus `OUTPUT.estimated_child_run_cost_usd`.
4. If safe, enable pay-per-event:
   - `apify-actor-start`: `$0`
   - `apify-default-dataset-item`: `$0.0030`
   - primary event: default dataset item
   - platform usage cost pass-through enabled
   - minimum max-cost setting: `$0.25`
5. If child costs bill the owner unrecoverably, keep Atomic public but not monetized until custom cost-recovery events are implemented.

