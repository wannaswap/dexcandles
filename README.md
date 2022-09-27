# DEX Candles Subgraph

This subgraph tracks all the DEX trades with 5m/15m/1h/4h/1d/1w candles.

## Example

Query 1h candles (3600 seconds) for first week of 2021: `2020-01-01` (1609459200) - `2020-01-07` (1609977600):

```graphql
{
    candles(where: {period: 3600, time_in: [1609459200, 1609977600]}) {
        id
        time
        open
        close
        low
        high
        token0TotalAmount
        token1TotalAmount
    }
}
```

## Schema

```graphql
type Candle @entity {
    id: ID! # time + period + srcToken + dstToken
    time: Int!
    period: Int!
    token0TotalAmount: BigInt!
    token1TotalAmount: BigInt!
    open: BigDecimal!
    close: BigDecimal!
    low: BigDecimal!
    high: BigDecimal!
}
```
