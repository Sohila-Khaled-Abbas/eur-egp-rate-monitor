# Data dictionary

## Normalized API record

| Field | Type | Description |
|---|---|---|
| `currencyPair` | string | Asset identifier; this workflow requires `EUR-EGP`. |
| `unit` | string | Provider's quoted unit, expected to represent EGP per EUR. |
| `youSellEurRate` | number | Bank buying rate from the customer's perspective: customer sells EUR. |
| `youSellEurBank` | string | Provider label for the bank associated with `youSellEurRate`. |
| `youBuyEurRate` | number | Bank selling rate from the customer's perspective: customer buys EUR. |
| `youBuyEurBank` | string | Provider label for the bank associated with `youBuyEurRate`. |
| `officialBuyBenchmark` | number / null | Provider's official buy benchmark, when present. |
| `officialSellBenchmark` | number / null | Provider's official sell benchmark, when present. |
| `globalRate` | number / null | Provider's global reference rate, when present. |
| `asOf` | string | Provider's effective observation date. |
| `observedAt` | string | Provider's observation timestamp. |
| `freshness` | string | Provider freshness state. |
| `isStale` | boolean | Whether the provider marks the data stale. |
| `confidence` | string | Provider confidence level, when present. |
| `providers` | number | Number of contributing providers, when present. |
| `source` | string | Constant source label: `Daleelak`. |
| `sourceUrl` | string | Public source reference included in notifications. |

## Comparison record

| Field | Type | Description |
|---|---|---|
| `previousSellRate` | number | Prior saved `youSellEurRate`. |
| `previousBuyRate` | number | Prior saved `youBuyEurRate`. |
| `sellDifference` | number | Current minus previous customer-sells-EUR rate, rounded to 2 decimals. |
| `buyDifference` | number | Current minus previous customer-buys-EUR rate, rounded to 2 decimals. |
| `sellChanged` | boolean | Whether `sellDifference` is non-zero. |
| `buyChanged` | boolean | Whether `buyDifference` is non-zero. |
| `rateChanged` | boolean | Whether either directional rate changed. |
| `shouldNotify` | boolean | `rateChanged` and feed is marked fresh and not stale. |
| `decisionReason` | string | Human-readable routing reason. |

## Persisted baseline

`EUR_EGP_Rate_State` is a deliberately small current-state table. It is not a rate-history fact table; successful change notifications overwrite the single `EUR-EGP` baseline row.
