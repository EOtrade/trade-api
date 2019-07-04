- [General API information](#org310f231)
- [Public API endpoints](#org415af95)
  - [Currencies](#org4e2600b)
  - [Symbols](#org2c486a3)
  - [Recent trade list](#orgab2805d)
  - [Fetch single deal](#org4e4cdca)
  - [Order book](#org4353dba)



<a id="org310f231"></a>

# General API information

-   The base endpoint is: [https://b.eo.trade](https://b.eo.trade).
-   All endpoints return either JSON object or array.
-   All time and timestamp related fields are in milliseconds.
-   For `GET` endpoints parameters must be sent as `query string`.


<a id="org415af95"></a>

# Public API endpoints


<a id="org4e2600b"></a>

## Currencies

Get all available currencies information.

```restclient
GET /api/trading/currencies/
```

Response:

```js
[
  {
    "currency": "BTC",
    "name": "Bitcoin",
    "canDeposit": true,
    "canWithdraw": true,
    "minWithdrawal": "0.000056160909653938"
  },
  {
    "currency": "EO",
    "name": "EO Coin",
    "canDeposit": true,
    "canWithdraw": true,
    "minWithdrawal": "2"
  },
  {
    "currency": "ETH",
    "name": "Ethereum",
    "canDeposit": true,
    "canWithdraw": true,
    "minWithdrawal": "0.005"
  }
]
```


<a id="org2c486a3"></a>

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


<a id="orgab2805d"></a>

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


<a id="org4e4cdca"></a>

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


<a id="org4353dba"></a>

## Order book

Get order book for pair.

```restclient
GET /api/trading/depth/
```

Query parameters:

| Parameter         | Type    | Description                                                          |
|----------------- |------- |-------------------------------------------------------------------- |
| symbol `required` | string  | Pair symbol                                                          |
| limit             | integer | Valid limits: [1, 5, 10, 20, 50, 100, 500, 1000]. Default value: 100 |

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
