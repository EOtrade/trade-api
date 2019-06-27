- [General API information](#org8951cc4)
- [Public API endpoints](#org4f3dbbd)
  - [Symbols](#org2d8db21)
  - [Recent trade list](#orge3dadd6)
  - [Fetch single deal](#org909219c)
  - [Order book](#orgd530e56)



<a id="org8951cc4"></a>

# General API information

-   The base endpoint is: [https://b.eo.trade](https://b.eo.trade).
-   All endpoints return either JSON object or array.
-   All time and timestamp related fields are in milliseconds.
-   For `GET` endpoints parameters must be sent as `query string`.


<a id="org4f3dbbd"></a>

# Public API endpoints


<a id="org2d8db21"></a>

## Symbols

Get all available pairs information.

```restclient
GET /api/trading/symbols/
```

Response:

```js
[
  {
    "symbol": "XRPETH",
    "isActive": true,
    "baseAsset": "XRP",
    "baseAssetPrecision": "1",
    "baseAssetMinAmount": "50",
    "quoteAsset": "ETH",
    "quoteAssetPrecision": "0.01",
    "quoteAssetMinAmount": "0.1",
    "pricePresicion": "0.00000001"
  },
  {
    "symbol": "EOETH",
    "isActive": true,
    "baseAsset": "EO",
    "baseAssetPrecision": "1",
    "baseAssetMinAmount": "1",
    "quoteAsset": "ETH",
    "quoteAssetPrecision": "0.00000001",
    "quoteAssetMinAmount": "0.00000001",
    "pricePresicion": "0.00000001"
  },
]
```


<a id="orge3dadd6"></a>

## Recent trade list

Get list of latest deals.

```restclient
GET /api/trading/deals/
```

Query parameters:

| Parameter         | Type    | Description                                             |
|----------------- |------- |------------------------------------------------------- |
| symbol `required` | string  | Pair symbol                                             |
| limit             | integer | Maximum deals which will be fetched. Default value: 500 |

Response:

```js
[
  {
    "id": 3234614,
    "price": "0.01",
    "qty": "63789.9323",
    "time": 1559908006
  },
  {
    "id": 3234613,
    "price": "0.2345",
    "qty": "758.5687",
    "time": 1559908006
  },
  {
    "id": 3234612,
    "price": "0.0034",
    "qty": "267.6805",
    "time": 1559908006
  }
]
```


<a id="org909219c"></a>

## Fetch single deal

Get single deal by `id`.

```restclient
GET /api/trading/deals/:id/
```

Path parameters:

| Parameter     | Type    | Description |
|------------- |------- |----------- |
| id `required` | integer | Deal ID     |

Response:

```js
{
  "id": 3223614,
  "price": "33.5978",
  "qty": "2.99366",
  "time": 1559685290
}
```


<a id="orgd530e56"></a>

## Order book

Get order book for pair.

```restclient
GET /api/trading/depth/
```

Query parameters:

| Parameter         | Type    | Description                                                       |
|----------------- |------- |----------------------------------------------------------------- |
| symbol `required` | string  | Pair symbol                                                       |
| limit             | integer | Valid limits: [5, 10, 20, 50, 100, 500, 1000]. Default value: 100 |

Response:

```js
{
  "bids": [
    [
      "0.0016397",
      "54"
    ],
    [
      "0.00164062",
      "53"
    ],
    [
      "0.00164127",
      "59"
    ],
    [
      "0.00164224",
      "59"
    ],
    [
      "0.00164259",
      "91"
    ]
  ],
  "asks": [
    [
      "0.00139559",
      "54"
    ],
    [
      "0.00139541",
      "53"
    ],
    [
      "0.0013943",
      "51"
    ],
    [
      "0.00139428",
      "66"
    ],
    [
      "0.00139391",
      "57"
    ]
  ]
}
```
