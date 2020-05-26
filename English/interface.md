# Interface

## interface list

| Interface type | request method | description |
| --- | --- | --- |
| asset | [POST /api_market/getBalance](#get-balance) | get balance |
| trading pairs | [POST /api_market/getTokenPrecision](#token-precision) | token precision |
| market condition | [GET /api_market/apiKline](#K-line) | K-Line |
| market condition | [GET /api_market/getTradeLists](#get-24hr-price-for-all-symbles) | 24hr conditions for all symbols |
| Market condition | [GET /api_market/getLatestTradeByPair](#single-symbol-latest-trading-record) | latest trade record of single symbol |
| Market condition | [POST /api_market/getDataOfTradesLatest](#get-latest-data-of-trades-of-single-symbol) | get latest data of trades of single symbol |
| Market condition | [POST /api_market/market/depth](#market-deep-analysis-of-single-symbol) | deep(Order book) |
| Market condition | [POST /api_market/buyAndSellOnePrice](#buy-one-and-sell-one) | deep |
| Market condition | [GET /api_market/getLatestPrice](#token-price-information-of-single-sympol) | token price information of single sympol |
| User order information | [POST /api_market/placeOrder](#place-order) | place order |
| User order information | [POST /api_market/batchPlaceOrder](#place-batch-orders) | place batch orders |
| User order information | [POST /api_market/getOrdersByOrderNo](#track-orders-by-order-number) | track orders by order number |
| User order information | [POST /api_market/cancelOrder](#cancel-order) | cancel order |
| User order information | [POST /api_market/batchCancelOrder](#cancel-batch-orders-by-order-numbers) | cancel batch orders by order numbers |
| User order information | [POST /api_market/getOrderByOrderNo](#get-order-by-order-number) | get order by order number |
| User order information | [POST /api_market/getOrders](#get-list-of-order) | get list of user orders |
| User order information | [POST /api_market/getOrders](#get-the-list-of-unsettled-order) | get list of uncompleted oders |
| User order information | [POST /api_market/getTrades](#get-list-of-completed-orders) | get list of completed orders |
| User order information | [POST /api_market/getTrades](#user-single-symbol-trading-record) | get list of trades of single symbol |
| Deposit and withdraw | [POST /api_market/searchDepositlList](#search-deposit-list) | search deposit list |
| Deposit and withdraw | [POST /api_market/searchWithdrawlList](#search-withdraw-list) | search withdraw list |

## get balance

### POST /api_market/getBalance

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page number |  | 1~10000 |
| size | yes | string | orders on each page |  | 1~10000 |
| token | yes | array | token list |  | ['BTC','ETH','CKUSD'...] |
| **respond parameter** |  |  |  |  |  |

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "count": 3,
        "data": [
            {
                "user_id": 1,
                "org_id": 12,
                "token": "BTC",
                "usable": "0",
                "locked": "0",
                "total": "0"
            },
            {
                "user_id": 1,
                "org_id": 12,
                "token": "ETH",
                "usable": "0",
                "locked": "0",
                "total": "0"
            }
        ]
    }
}

```

**data introduction：**

```
        "data": [
            {
                "user_id": user id,
                "org_id": organization id,
                "token": token name,
                "usable": usable asset,
                "locked": locked asset,
                "total": total asset
            }
        ]

```

## token precision

### POST /api_market/getTokenPrecision

**request parameter**

**respond parameter**

```
{
    "code": 0,
    "msg": "Operational success",
    "data": {
        "BTC": {
            "calc_precision": 4,
            "biz_precision": 8,
            "phy_precision": 8
        },
        "ETH": {
            "calc_precision": 4,
            "biz_precision": 8,
            "phy_precision": 8
        },
        "EOS": {
            "calc_precision": 4,
            "biz_precision": 8,
            "phy_precision": 8
        },
        "USDT": {
            "calc_precision": 4,
            "biz_precision": 8,
            "phy_precision": 8
        },
        "QTUM": {
            "calc_precision": 4,
            "biz_precision": 8,
            "phy_precision": 8
        }
    }
}

```

**data introduction：**

```
    {
        "calc_precision": calculation precision,
        "phy_precision": physical precision,
        "biz_precision": biz precision
    }

```

## K line

### GET /api_market/apiKline

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| time_type | yes | string | K line type |  | 1、5、10、15、30、60、240、1440、10080、43200 |
| market | yes | string | market |  |  |
| token | yes | string | token name |  |  |
| limit | yes | string | limit amount |  |  |
| **respond parameter** |  |  |  |  |  |

```
{
    "code": 0,
    "msg": "success",
    "data": [
        {
            "amount": "1",
            "c_price": "100",
            "o_price": "100",
            "min_price": "100",
            "max_price": "100",
            "volume": "0",
            "timestamp": 1535618520000
        },
        {
            "amount": "1",
            "c_price": "100",
            "o_price": "100",
            "min_price": "100",
            "max_price": "100",
            "volume": "0",
            "timestamp": 1535618580000
        }
    ]
}

```

**data introduction**

```
    "data": [
        {
            "amount": trading amount,
            "c_price": closing price,
            "o_price": opening price,
            "min_price": lowest price,
            "max_price": highest price,
            "volume": trading volume,
            "timestamp": timestamp
        }
    ]

```

## get 24hr price for all symbles

### GET /api_market/getTradeLists

**request parameter**

**respond parameter**

```
{
    "code": 0,
    "msg": "success",
    "data": {
        "main": {
            "USDT": [
                {
                    "id": 10,
                    "vol": "27337458.015767",
                    "market": "USDT",
                    "market_as": "USDT",
                    "token": "BTC",
                    "token_as": "BTC",
                    "sort": 0,
                    "opening_time": null,
                    "amount": "3826.3038",
                    "max_price": "8002.4452",
                    "min_price": "5075.06",
                    "open_price": "6799",
                    "is_up": "-1",
                    "prev_price": "6634.66",
                    "p_precision": "4",
                    "n_precision": "4",
                    "currency": {
                        "CNY": "45768.321",
                        "KRW": "7447036.4739"
                    },
                    "latest_price": "6633.09",
                    "percent_change": "-0.1348463208"
                },
                {
                    "id": 11,
                    "vol": "607.3851",
                    "market": "USDT",
                    "market_as": "USDT",
                    "token": "ETH",
                    "token_as": "ETH",
                    "sort": 0,
                    "opening_time": null,
                    "amount": "2.23",
                    "max_price": "272.37",
                    "min_price": "272.37",
                    "open_price": "272.37",
                    "is_up": "1",
                    "prev_price": "228.84",
                    "p_precision": "4",
                    "n_precision": "4",
                    "currency": {
                        "CNY": "1876.6293",
                        "KRW": "305349.349473"
                    },
                    "latest_price": "272.37",
                    "percent_change": "0.1902202412"
                }
            ],
            "ETH": [
                {
                    "id": 14,
                    "vol": "0",
                    "market": "ETH",
                    "market_as": "ETH",
                    "token": "QTUM",
                    "token_as": "QTUM",
                    "sort": 0,
                    "opening_time": null,
                    "amount": "0",
                    "max_price": "0.0212",
                    "min_price": "0.0212",
                    "open_price": "0.0212",
                    "is_up": "-1",
                    "prev_price": "0.0222",
                    "p_precision": "8",
                    "n_precision": "4",
                    "currency": {
                        "CNY": "16.512424185",
                        "KRW": "2658.6213073839"
                    },
                    "latest_price": "0.0212",
                    "percent_change": "0"
                }
            ]
        },
        "hot": [
            {
                "id": 14,
                "vol": "0",
                "market": "ETH",
                "market_as": "ETH",
                "token": "QTUM",
                "token_as": "QTUM",
                "sort": 0,
                "opening_time": null,
                "amount": "0",
                "max_price": "0.0212",
                "min_price": "0.0212",
                "open_price": "0.0212",
                "is_up": "-1",
                "prev_price": "0.0222",
                "p_precision": "8",
                "n_precision": "4",
                "currency": {
                        "CNY": "16.512424185",
                    "KRW": "2658.6213073839"
                },
                "latest_price": "0.0212",
                "percent_change": "0"
            },
            {
                "id": 10,
                "vol": "27337458.015767",
                "market": "USDT",
                "market_as": "USDT",
                "token": "BTC",
                "token_as": "BTC",
                "sort": 0,
                "opening_time": null,
                "amount": "3826.3038",
                "max_price": "8002.4452",
                "min_price": "5075.06",
                "open_price": "6799",
                "is_up": "-1",
                "prev_price": "6634.66",
                "p_precision": "4",
                "n_precision": "4",
                "currency": {
                        "CNY": "45768.321",
                    "KRW": "7447036.4739"
                },
                "latest_price": "6633.09",
                "percent_change": "-0.1348463208"
            }
        ],
        "by_percent":[
            {
                "id": 11,
                "vol": "607.3851",
                "market": "USDT",
                "market_as": "USDT",
                "token": "ETH",
                "token_as": "ETH",
                "sort": 0,
                "opening_time": null,
                "amount": "2.23",
                "max_price": "272.37",
                "min_price": "272.37",
                "open_price": "272.37",
                "is_up": "1",
                "prev_price": "228.84",
                "p_precision": "4",
                "n_precision": "4",
                "currency": {
                    "CNY": "1876.6293",
                    "KRW": "305349.349473"
                },
                "latest_price": "272.37",
                "percent_change": "0.1902202412"
            },
            {
                "id": 32,
                "vol": "0.5769332",
                "market": "ETH",
                "market_as": "ETH",
                "token": "ONT",
                "token_as": "ONT",
                "sort": 0,
                "opening_time": null,
                "amount": "4",
                "max_price": "0.1442333",
                "min_price": "0.1442333",
                "open_price": "0.1442333",
                "is_up": "1",
                "prev_price": "0.1442",
                "p_precision": "8",
                "n_precision": "4",
                "currency": {
                    "CNY": "112.3415769435",
                    "KRW": "18087.8171987879"
                },
                "latest_price": "0.1442333",
                "percent_change": "0.0002309292"
            }
        ],
        "by_time": [
            {
                "id": 14,
                "vol": "0",
                "market": "ETH",
                "market_as": "ETH",
                "token": "QTUM",
                "token_as": "QTUM",
                "sort": 0,
                "opening_time": null,
                "amount": "0",
                "max_price": "0.0212",
                "min_price": "0.0212",
                "open_price": "0.0212",
                "is_up": "-1",
                "prev_price": "0.0222",
                "p_precision": "8",
                "n_precision": "4",
                "currency": {
                        "CNY": "16.512424185",
                    "KRW": "2658.6213073839"
                },
                "latest_price": "0.0212",
                "percent_change": "0"
            },
            {
                "id": 10,
                "vol": "27337458.015767",
                "market": "USDT",
                "market_as": "USDT",
                "token": "BTC",
                "token_as": "BTC",
                "sort": 0,
                "opening_time": null,
                "amount": "3826.3038",
                "max_price": "8002.4452",
                "min_price": "5075.06",
                "open_price": "6799",
                "is_up": "-1",
                "prev_price": "6634.66",
                "p_precision": "4",
                "n_precision": "4",
                "currency": {
                    "CNY": "45768.321",
                    "KRW": "7447036.4739"
                },
                "latest_price": "6633.09",
                "percent_change": "-0.1348463208"
            }
        ]
    }
}

```

**data introduction**

```
{
    "code":0,
    "msg":"success",
    "data"{
        "main":{
            "USDT":[ market
                {
                    "id": id,
                    "vol": trading volume,
                    "market": market,
                    "market_as": market display name,
                    "token": token type,
                    "token_as": token type display name,
                    "sort": the sorting,
                    "opening_time": the opening time,
                    "amount": trading amount,
                    "max_price": highest price,
                    "min_price": lowest price,
                    "open_price": opening price,
                    "is_up": is up or down 1up -1down,
                    "prev_price": latest price,
                    "p_precision": price precision,
                    "n_precision": number precision,
                    "currency": { Issue reference，
                        "CNY":Chinese Yuan，
                        "KRW":Korean Won
                    },
                    "latest_price": latest price,
                    "percent_change": percent change                 }
            ],
            "ETH":[
            ]
        },
        "hot":[],largest four trading pairs according to amount
        "by_percent":[],largest for trading pairs according to percent change        
        "by_time":[],latest listing trading pair
    }
}

```

## single symbol latest trading record

### GET /api_market/getLatestTradeByPair

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| market | Yes | string | Market name;For example:USDT |  |  |
| token | Yes | string | Token name;For example:ETH |  |  |

**respond parameter(Default 100)**

```
[
    {
        "created_at": "2018-08-31 11:26:10",
        "price":"1",
        "amount":"0",
        "volume":"0",
        "dominance":2,
        "trade_no":"2018080108323947697492867430",
        "sorting":1564648359.14661
    },
    {
        "created_at": "2018-08-31 10:26:14",
        "price":"1",
        "amount":"1",
        "volume":"1",
        "dominance":1,
        "trade_no":"2018080108320782283292865987",
        "sorting":1564648327.585736
    }
]

```

**data introduction**

```
[
    {
        "created_at": creation time ,
        "price":price,
        "amount":trading amount,
        "volume":trading volume,
        "dominance":dominance 1:buyer 2:seller，
        "trade_no":order no,
        "sorting":sort field
    }
]

```

##  get latest data of trades of single symbol

### POST /api_market/getDataOfTradesLatest

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page number |  | 1~10000 |
| size | yes | string | orders on each page |  | 1~100 |
| market | yes | string | market |  |  |
| token | yes | string | token name |  |  |
| **respond parameter** |  |  |  |  |  |

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "data": [
            {
                "id": 1,
                "created_at": "2018-08-31 10:26:14",
                "price": "1",
                "amount": "1",
                "dominance": 1
            },
            {
                "id": 2,
                "created_at": "2018-08-31 10:26:14",
                "price": "1",
                "amount": "1",
                "dominance": 1
            }
        ]
    }
}

```

**data introduction**

```
    "data": [
      {
        "id": completed id,
        "price": price,
        "amount": amount of token,
        "dominance": dominance,
        "created_at": creation time
      }
    ]

```

## market deep analysis of single symbol

### GET /api_market/market/depth

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| market | yes | string | market name;For example:USDT |  |  |
| token | yes | string | token name;For example:ETH |  |  |

**respond parameter**

```
{
	"code": 0,
	"msg": "success",
	"data": {
		"bids": [
			["6595.25", "20"],
			["6595.24", "2.73"],
			["6595.14", "3.25"],
			["6594.61", "3.34"],
		],
		"asks": [
			["7713.62", "0.23"],
			["7712.74", "10.98"],
			["7712.52", "1.81"],
			["7712.45", "0.66"],
		]
	}
}

```

**data introduction**

```
{
        "bids": [
            [
                "2.8",   //price
                "6.32"   //amount
            ],
            [
                "2.77",  //price
                "6.72"   //amount
            ]
        ],
        "asks": [
            [
                "5.6",   //price
                "2.3"    //amount
            ]
        ]
}

```

## buy one and sell one

### GET /api_market/buyAndSellOnePrice

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| market | yes | string | market |  |  |
| token | yes | string | token name |  |  |
| **respond parameter** |  |  |  |  |  |

```
{
    "buy": "0.02657781",
    "sell": "1.1998887"
}

```

**data introduction**

```
{
    "buy": "0.02657781", //The highest price of buy
    "sell": "1.1998887"  //The lowest price of sell
}

```

## token price information of single sympol

### GET /api_market/getLatestPrice

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| market | yes | string | market |  |  |
| token | yes | string | token name |  |  |
| **respond parameter** |  |  |  |  |  |

```
{
	"code": 0,
	"msg": "success",
	"data": {
		"buy": {
			"orders": [{
				"price": "270.99",
				"exchange": {
					"CNY": "6.9",
					"KRW": "1122.71"
				},
				"fiat": "CNY",
				"percent_change": "",
				"amount": "2",
				"matching_amount": "2",
				"matched_amount": "0"
			}, {
				"price": "99",
				"exchange": {
					"CNY": "6.9",
					"KRW": "1122.71"
				},
				"fiat": "CNY",
				"percent_change": "",
				"amount": "1",
				"matching_amount": "1",
				"matched_amount": "0"
			}],
			"best_price": "270.99",
			"max_amount": "2"
		},
		"sell": {
			"orders": [],
			"best_price": "0",
			"max_amount": "0"
		}
	}
}

```

**data introduction**

```
{
	"code": 0,
	"msg": "success",
	"data": {
		"buy": { //buy
			"orders": [{ // order list
				"price": //price 
				"exchange": { // exchange to fiat currency
					"CNY" // Chinese Yuan
					"KRW" //Korean Won
				},
				"fiat" //
				"percent_change": //percent change
				"amount": //trade amount				                           "matching_amount": //matching amount
				"matched_amount":  //matched amount
			}],
			"best_price": //best bid price
			"max_amount": //max bid amount
		},
		"sell": { //sell
			"orders": [], //order list
			"best_price": //lowest ask price
			"max_amount": //maximum ask amount
		}
	}
}

```

## place order

### POST /api_market/placeOrder

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| market_type | yes | string | market type |  | 1 |
| market | yes | string | market |  |  |
| token | yes | string | token name |  |  |
| type | yes | string | buy/sell(1:buy 2:sell) |  | 1 or 2 |
| price | yes | string | price |  |  |
| amount | yes | string | amount |  |  |

**respond parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "id": 1,
        "status": 1,
        "order_no": "2018090313134038386500017289",
        "type": "1",
        "market_type": "1",
        "account_id": 6,
        "org_id": 12,
        "user_id": 1,
        "market": "BTC",
        "token": "ETH",
        "price": "0.05",
        "amount": "1",
        "volume": "0.05",
        "matched_amount": "0",
        "matched_volume": "0",
        "avg_price":"0",
        "created_at": "2018-09-03 13:13:40",
        "updated_at": "2018-09-03 13:13:40"
    }
}

```

**data introduction**

```
    "data": {
        "id":  order ID
        "status":  status 0 canceled 1 created 2 matching 3 completed
        "order_no": order number,
        "type": type 1buy 2sell,
        "market_type": market type  value for now is 1,
        "account_id_from": payment account id',
        "account_id_to": recipient account id',
        "org_id": organization id,
        "user_id":  user ID,
        "market": marke,
        "token": token name,
        "price": price,
        "amount": amount of token,
        "volume": trading volume of token,
        "matched_amount": matched amount of token,
        "matched_volume": matched trading volume of token,
        "avg_price":average price of the matched part of token,
        "created_at":  creation time,
        "updated_at":  update time,
    }

```

## place batch orders

### POST /api_market/batchPlaceOrder

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| data | yes | array | array of orders |  |  |

**respond parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "count": 10,
        "data": [
            {
                "id": 1,
                "status": 1,
                "type": 1,
                "market_type": 1,
                "order_no": "2018090313134038386500017289",
                "account_id": 6,
                "user_id": 1,
                "org_id": 12,
                "market": "BTC",
                "token": "ETH",
                "price": "0.05",
                "amount": "1",
                "volume": "0.05",
                "matched_amount": "0",
                "matched_volume": "0",
                "avg_price":"0",
                "created_at": "2018-09-03 13:13:40",
                "updated_at": "2018-09-03 13:13:40"
            },
            {
                "id": 2,
                "status": 1,
                "type": 1,
                "market_type": 1,
                "order_no": "2018090313134038386500017299",
                "account_id": 6,
                "user_id": 1,
                "org_id": 12,
                "market": "BTC",
                "token": "ETH",
                "price": "0.05",
                "amount": "1",
                "volume": "0.05",
                "matched_amount": "0",
                "matched_volume": "0",
                "avg_price":"0",
                "created_at": "2018-09-03 13:13:42",
                "updated_at": "2018-09-03 13:13:42"
            }
        ]
    }
}

```

**data introduction**

```
    "data": {
        "id": 订单id,
        "status": status 0canceled 1created 2matching 3completed,
        "order_no": order number,
        "type": type 1buy 2sell,
        "market_type": market type  value for now is 1,
        "account_id_from": payment account id’,
        "account_id_to": recipient account id’,
        "org_id": organization id,
        "user_id": user id,
        "market": market,
        "token": token name,
        "price": price,
        "amount": amount of token,
        "volume": trading volume of token,
        "matched_amount": matched amount of token,
        "matched_volume": matched trading volume of token,
        "avg_price": average price of the matched part of token,
        "created_at": creation time,
        "updated_at": update time
    }

```

## track orders by order number

### POST /api_market/getOrdersByOrderNo

**request parameter**

| parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| arr_order_no | yes | array |  |  |  |

**response parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": [
        {
            "id": 1,
            "status": 1,
            "type": 1,
            "market_type": 1,
            "order_no": "2018090313134038386500017289",
            "account_id": 6,
            "user_id": 1,
            "org_id": 12,
            "market": "BTC",
            "market_as": "BTC",
            "token": "ETH",
            "token_as": "ETH",
            "price": "0.05",
            "amount": "1",
            "volume": "0.05",
            "matched_amount": "0",
            "matched_volume": "0",
            "avg_price":"0",
            "created_at": "2018-09-03 13:13:40",
            "updated_at": "2018-09-03 13:13:40",
            "unmatched_amount": "1"
        },
        {
            "id": 2,
            "status": 1,
            "type": 1,
            "market_type": 1,
            "order_no": "2018090313134038386500017299",
            "account_id": 6,
            "user_id": 1,
            "org_id": 12,
            "market": "BTC",
            "market_as": "BTC",
            "token": "ETH",
            "token_as": "ETH",
            "price": "0.05",
            "amount": "1",
            "volume": "0.05",
            "matched_amount": "0",
            "matched_volume": "0",
            "avg_price":"0",
            "created_at": "2018-09-03 13:13:42",
            "updated_at": "2018-09-03 13:13:42",
            "unmatched_amount": "1"
        }
    ]

```

**data introduction**

```
    "data": {
        "id": order id,
        "status": status 0 canceled 1created 2 matching 3 completed,
        "order_no": order number,
        "type": type 1buy 2sell,
        "market_type": market type  value for now is 1,
        "account_id_from": payment account id',
        "account_id_to": recipient account id',
        "org_id": organization id,
        "user_id": user id,
        "market": market ,
        "market_as": market alias（name displayed）,
        "token": token name,
        "token_as": token alias（name displayed）,
        "price": price,
        "amount": amount of token,
        "volume": volume of token,
        "matched_amount": matched amount of token,
        "matched_volume": matched trading volume of token,
        "unmatched_amount":unmatched amount of token,
        "avg_price":average price of matched part of token,
        "created_at": creation time,
        "updated_at": update time
    }

```

## cancel order

### POST /api_market/cancelOrder

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| order_nos | yes | json string | order number |  | "["2018091315164516313901209422"]" |

**response parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": null
}

```

## cancel orders by order number

### POST /api_market/batchCancelOrder

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| order_nos | yes | json string | group of order number |  | "["2018091315164516313901209422","2018091315164516313901209422"]" |

**response parameter**

```
{
    "code": 0,
    "msg": "successful"
}

```

##  get order by order number

### POST /api_market/getOrderByOrderNo

**response parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| order_no | yes | string | order number |  |  |

**response parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "id": 1,
        "status": 1,
        "order_no": "2018090313134038386500017289",
        "type": "1",
        "market_type": "1",
        "account_id": 6,
        "org_id": 12,
        "user_id": 1,
        "market": "BTC",
        "market_as": "BTC",
        "token": "ETH",
        "token_as": "ETH",
        "price": "0.05",
        "amount": "1",
        "volume": "0.05",
        "matched_amount": "0",
        "matched_volume": "0",
        "avg_price":"0",
        "created_at": "2018-09-03 13:13:40",
        "updated_at": "2018-09-03 13:13:40"
        "unmatched_amount":"0"
    }
}

```

**data introduction**

```
    "data": {
        "id": order id,
        "status": status 0canceled 1created 2matching 3completed,
        "order_no": order number,
        "type": type 1buy 2sell,
        "market_type": market type  value for now is 1,
        "account_id_from": payment id',
        "account_id_to": recipient id',
        "org_id": organization id,
        "user_id": user id,
        "market": market,
        "market_as": market alias（name displayed）,
        "token": token name,
        "token_as": token alias（name displayed）,
        "price": price,
        "amount": amount of token,
        "volume": trading volume of token,
        "matched_amount": matched amount of token,
        "matched_volume": matched amount of token,
        "unmatched_amount":unmatched amount of token,
        "avg_price":average price of matched part of token,
        "created_at": creation time,
        "updated_at": update time
    }

```

##  get list of order

### POST /api_market/getOrders

**request parameter**

| Parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page |  | 1~10000 |
| size | yes | string | orders on each page |  | 1~100 |
| type | no | string | type |  | 1buy 2sell |
| market | no | string | market |  |  |
| token | no | string | token name |  |  |
| status | no | array | status, format：[0,1,2,3] |  | 0canceled 1created 2matching 3completed |
| begin_time | no | string | start time， example 2018-08-20 00:00:00； must work with end_time |  |  |
| end_time | no | string | end time， example:2018-08-21 23:59:59；must work with start_time |  |  |

**response parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "count": 10,
        "data": [
            {
                "id": 1,
                "status": 1,
                "type": 1,
                "market_type": 1,
                "order_no": "2018090313134038386500017289",
                "account_id": 6,
                "user_id": 1,
                "org_id": 12,
                "market": "BTC",
                "market_as": "BTC",
                "token": "ETH",
                "token_as": "ETH",
                "price": "0.05",
                "amount": "1",
                "volume": "0.05",
                "matched_amount": "0",
                "matched_volume": "0",
                "avg_price":"0",
                "created_at": "2018-09-03 13:13:40",
                "updated_at": "2018-09-03 13:13:40",
                "unmatched_amount": "1"
            },
            {
                "id": 2,
                "status": 1,
                "type": 1,
                "market_type": 1,
                "order_no": "2018090313134038386500017299",
                "account_id": 6,
                "user_id": 1,
                "org_id": 12,
                "market": "BTC",
                "market_as": "BTC",
                "token": "ETH",
                "token_as": "ETH",
                "price": "0.05",
                "amount": "1",
                "volume": "0.05",
                "matched_amount": "0",
                "matched_volume": "0",
                "avg_price":"0",
                "created_at": "2018-09-03 13:13:42",
                "updated_at": "2018-09-03 13:13:42",
                "unmatched_amount": "1"
            }
        ]
    }
}

```

**data introduction**

```
    "data": {
        "id": order id,
        "status": status 0canceled 1created 2matching 3completed,
        "order_no": order number,
        "type": type 1buy 2sell,
        "market_type": market type  value for now is 1,
        "account_id_from": payment account id',
        "account_id_to": recipient account id',
        "org_id": organization id,
        "user_id": user id,
        "market": market,
        "market_as": market alias（name displayed）,
        "token": token name,
        "token_as": token alias （name displayed）,
        "price": price,
        "amount": amount of token,
        "volume": volume of token,
        "matched_amount": matched amount of token,
        "matched_volume": matched volume of token,
        "unmatched_amount":unmatched amount of token,
        "avg_price":average price of matched part of token,
        "created_at": creation time,
        "updated_at": update time
    }

```

##  get the list of unsettled order

### POST /api_market/getOrders

**request parameter**

| Parameter name | essential or not | data type | description | default | rang |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page |  | 1~10000 |
| size | yes | string | orders on each page |  | 1~100 |
| status | no | array | status(1unmatched 2matching) |  | [1,2] |

**response parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "count": 10,
        "data": [
            {
                "id": 1,
                "status": 1,
                "type": 1,
                "market_type": 1,
                "order_no": "2018090313134038386500017289",
                "account_id": 6,
                "user_id": 1,
                "org_id": 12,
                "market": "BTC",
                "market_as": "BTC",
                "token": "ETH",
                "token_as": "ETH",
                "price": "0.05",
                "amount": "1",
                "volume": "0.05",
                "matched_amount": "0",
                "matched_volume": "0",
                "avg_price":"0",
                "created_at": "2018-09-03 13:13:40",
                "updated_at": "2018-09-03 13:13:40",
                "unmatched_amount": "1"
            },
            {
                "id": 2,
                "status": 1,
                "type": 1,
                "market_type": 1,
                "order_no": "2018090313134038386500017299",
                "account_id": 6,
                "user_id": 1,
                "org_id": 12,
                "market": "BTC",
                "market_as": "BTC",
                "token": "ETH",
                "token_as": "ETH",
                "price": "0.05",
                "amount": "1",
                "volume": "0.05",
                "matched_amount": "0",
                "matched_volume": "0",
                "avg_price":"0",
                "created_at": "2018-09-03 13:13:42",
                "updated_at": "2018-09-03 13:13:42",
                "unmatched_amount": "1"
            }
        ]
    }
}

```

**data introduction**

```
    "data": {
        "id": order id,
        "status": status 0canceled 1created 2matching 3completed,
        "order_no": order number,
        "type": type 1buy 2sell,
        "market_type": market type  value for now is 1,
        "account_id_from": payment account id',
        "account_id_to": recipient account id',
        "org_id": organization id,
        "user_id": user id,
        "market": market,
        "market_as": market alias（name displayed）,
        "token": token name,
        "token_as": token alias（name displayed）,
        "price": price,
        "amount": amount of token,
        "volume": volume of token,
        "matched_amount": matched amount of token,
        "matched_volume": matched amount of token,
        "unmatched_amount":unmatched amount of token,
        "avg_price":average price of matched part of token,
        "created_at":  creation time,
        "updated_at": update time
    }

```

##  get list of completed orders

### POST /api_market/getTrades

**request parameter**

| parameter name | essential or not | data type | description | default | range |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page number |  | 1~10000 |
| size | yes | string | orders on each page |  | 1~100 |
| type | no | string | type |  | 1buy 2sell |
| market | no | string | market |  |  |
| token | no | string | token name |  |  |
| begin_time | no | string | start time， example:2018-08-20 17:59:33； must work with end_time |  |  |
| end_time | no | string | end time， example:2018-08-31 17:59:33； must work with start_time |  |  |

**respond parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "count": 10,
        "data": [
            {
                "id": 1,
                "trade_no": "2243534656575453445453343423",
                "buy_order_id": 1,
                "buy_order_no": "2243534656575453445453343465",
                "sell_order_id": 1,
                "sell_order_no": "12135647586799657463241324",
                "dominance": 1,
                "buyer_user_id": 1,
                "seller_user_id": 2,
                "org_id": 12,
                "trade_strategy": 1,
                "market": "BTC",
                "market_as": "BTC",
                "token": "ETH",
                "token_as": "ETH",
                "price": "10.00000000",
                "amount": "1.00000000",
                "volume": "1.00000000",
                "created_at": "1970-01-01 08:00:01",
                "updated_at": "2018-08-29 10:19:12"
            },
            {
                "id": 2,
                "trade_no": "2243534656575453445453345523",
                "buy_order_id": 1,
                "buy_order_no": "2243534656575453445453343472",
                "sell_order_id": 1,
                "sell_order_no": "12135647586799657463241367",
                "dominance": 1,
                "buyer_user_id": 1,
                "seller_user_id": 2,
                "org_id": 12,
                "trade_strategy": 1,
                "market": "BTC",
                "market_as": "BTC",
                "token": "ETH",
                "token_as": "ETH",
                "price": "10.00000000",
                "amount": "1.00000000",
                "volume": "1.00000000",
                "created_at": "1970-01-01 08:00:01",
                "updated_at": "2018-08-29 10:19:12"
            }
        ]
    }
}

```

**data introduction**

```
        "data": {
            "id": 1,
            "trade_no": order NO
            "buy_order_id": ID for buying orders
            "buy_order_no": buying order’s NO
            "sell_order_id": ID for selling orders
            "sell_order_no": Selling order’s NO
            "dominance": taker
            "buyer_user_id": buyer ID
            "seller_user_id": seller ID
            "org_id": organization ID
            "trade_strategy": trade strategy 1 limit order
            "market": market
            "market_as": alias for market（name displayed）,
            "token": token name,
            "token_as": alias for token（name displayed）,
            "price": price,
            "amount": amount of market token,
            "volume": amount of trading token,
            "created_at": creation time
            "updated_at": update time
        }

```

## user single symbol trading record

### POST /api_market/getTrades

**request parameter**

| Parameter name | required or optional | data type | discription | default value | value range |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page |  | 1~10000 |
| size | yes | string | orders displayed per page |  | 1~100 |
| market | no | string | market |  |  |
| token | no | string | token |  |  |

**feedback parameter**

```
{
    "code": 0,
    "msg": "successful",
    "data": {
        "count": 10,
        "data": [
            {
                "id": 1,
                "trade_no": "2243534656575453445453343423",
                "buy_order_id": 1,
                "buy_order_no": "2243534656575453445453343465",
                "sell_order_id": 1,
                "sell_order_no": "12135647586799657463241324",
                "dominance": 1,
                "buyer_user_id": 1,
                "seller_user_id": 2,
                "org_id": 12,
                "trade_strategy": 1,
                "market": "ETH",
                "market_as": "ETH",
                "token": "BTC",
                "token_as": "BTC",
                "price": "10.00000000",
                "amount": "1.00000000",
                "volume": "1.00000000",
                "created_at": "1970-01-01 08:00:01",
                "updated_at": "2018-08-29 10:19:12"
            },
            {
                "id": 2,
                "trade_no": "2243534656575453445453345523",
                "buy_order_id": 1,
                "buy_order_no": "2243534656575453445453343472",
                "sell_order_id": 1,
                "sell_order_no": "12135647586799657463241367",
                "dominance": 1,
                "buyer_user_id": 1,
                "seller_user_id": 2,
                "org_id": 12,
                "trade_strategy": 1,
                "market": "ETH",
                "market_as": "ETH",
                "token": "BTC",
                "token_as": "BTC",
                "price": "10.00000000",
                "amount": "1.00000000",
                "volume": "1.00000000",
                "created_at": "1970-01-01 08:00:01",
                "updated_at": "2018-08-29 10:19:12"
            }
        ]
    }
}

```

**data discription**

```
        "data": {
            "id": 1,
            "trade_no": order NO,
            "buy_order_id": buying order ID
            "buy_order_no": buyinh order NO,
            "sell_order_id": selling order ID
            "sell_order_no": selling order NO,
            "dominance": taker
            "buyer_user_id": buyer ID,
            "seller_user_id": seller ID,
            "org_id": organization id,
            "trade_strategy": trade strategy 1 limit order,
            "market": market,
            "market": alias for market（name displayed）,
            "token": token,
            "token_as": alias for token（name displayed）,
            "price": price,
            "amount": amount of market token,
            "volume": amount of trading token,
            "created_at": creation time,
            "updated_at": update time
        }

```

## search deposit list

### POST /api_market/searchDepositList

**request parameter**

| Parameter name | required or optional | data type | discription | default value | value range |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page |  | 1~10000 |
| size | yes | string | orders displayed per page |  | 1~100 |
| token | yes | string | token，nullable |  |  |
| begin_time | yes | string | start time， for example 2018-08-20 17:59:33，nullable；shall be used in combination with end time |  |  |
| end_time | yes | string | end time， for example 2018-08-31 17:59:33，nullable；shall be used in combination with start time |  |  |

**feedback parameter**

```
{
    "code": 0,
    "msg": "ok",
    "data": {
        "data": [
            {
                "id": 1,
                "user_id": 1,
                "org_id": 12,
                "account_id": 1,
                "token": "BTC",
                "token_as": "BTC",
                "amount": "1",
                "blockchain_tx_id": "ardtyuijuytredsasdfg",
                "deposit_no": "123456789765432133453",
                "address": "aSDFGUIYTREWAaertyrewasSDFGHJK",
                "confirm_count": 0,
                "status": 1,
                "created_at": "2018-09-03 17:23:20",
                "updated_at": "2018-09-03 17:24:24"
            },
            {
                "id": 2,
                "user_id": 1,
                "org_id": 12,
                "account_id": 1,
                "token": "BTC",
                "token_as": "BTC",
                "amount": "2",
                "blockchain_tx_id": "Awedtyuiuyfgdsa",
                "deposit_no": "345678985432132446577",
                "address": "asertyuiouytredasdrtyuiuytfdssasdfgh",
                "confirm_count": 12,
                "status": 5,
                "created_at": "2018-09-03 17:24:18",
                "updated_at": "2018-09-03 17:24:18"
            }
        ],
        "count": 2
    }

```

**data discription：**

```
        "data": {
            "id": deposit order ID,
            "user_id": user ID,
            "org_id": organization ID,
            "account_id": account ID,
            "token": token,
            "token_as": alias for token（name displayed）,
            "amount": amount,
            "blockchain_tx_id": txid,
            "deposit_no": deposit order NO,
            "address": deposit address,
            "confirm_count": confirmation amount,
            "status": status 1 created 5 completed,
            "created_at": creation time,
            "updated_at": update time
        }

```

## search withdrawal list

### POST /api_market/searchWithdrawalList

**request parameter**

| Parameter name | required or optional | data type | discription | default value | value range |
| --- | --- | --- | --- | --- | --- |
| page | yes | string | page |  | 1~10000 |
| size | yes | string | orders displayed per page |  | 1~100 |
| token | yes | string | token，nullable |  |  |
| begin_time | yes | string | start time， for example 2018-08-20 17:59:33，nullable；shall be used in combination with end time |  |  |
| end_time | yes | string | end time， for example 2018-08-31 17:59:33，nullable；shall be used in combination with start time |  |  |

**feedback parameter**

```
{
    "code": 0,
    "msg": "ok",
    "data": {
        "data": [
            {
                "id": 1,
                "user_id": 1,
                "org_id": 12,
                "account_id": 6,
                "fee_account_id": 3,
                "token": "BTC",
                "token_as": "BTC",
                "fee_token": "BTC",
                "protocol": 2,
                "amount": "",
                "apply_amount": "1",
                "blockchain_tx_id": null,
                "network_fee": "0.01",
                "withdrawal_no": "2018090317160306293300011976",
                "address_to": "1QT6UzFLZHtQKhWqUEXJgPWY1j5QevxfRk",
                "address_from": "ertyuiytrewrtyui987654ewsdftyu876t5rdsf1s",
                "fee_address": "ertyuiytrewrtyui987654ewsdftyu876t5rdsf1s",
                "reason": null,
                "confirm_count": 0,
                "status": 1,
                "created_at": "2018-09-03 17:16:03",
                "updated_at": "2018-09-03 17:16:03"
            }
        ],
        "count": 1
    }

```

**data discription：**

```
        "data": {
            "id": withdrawal order ID,
            "user_id": user ID,
            "org_id": organization ID,
            "account_id": account ID,
            "fee_account_id": transaction fee account ID,
            "token": token,
            "token_as": alias for token( name displayed)
            "fee_token": fee token name,
            "protocol": protocol,
            "amount": actual received amount,
            "apply_amount": applied amount,
            "blockchain_tx_id": txid,
            "network_fee": network fee,
            "withdrawal_no": withdrawal order NO,
            "address_to": address transfer to,
            "address_from": payment address,
            "fee_address": fee address,
            "reason": screening reason,
            "confirm_count": confirmation amount,
            "status": status0not audited 1audited 2wallet deployed 3mining fee generated 4first block generated 5completed 6auditing failed 7cancel,
            "created_at": creation time,
            "updated_at": update time
        }

```
