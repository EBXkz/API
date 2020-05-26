# 接口

## 接口列表

| 接口类型 | 请求方法 | 描述 |
| --- | --- | --- |
| 资产 | [POST /api_market/getBalance](#%E8%8E%B7%E5%8F%96%E4%BD%99%E9%A2%9D) | 获取余额 |
| 交易品种信息 | [GET /api_market/getTokenPrecision](#%E6%89%80%E6%9C%89%E5%B8%81%E7%A7%8D%E7%B2%BE%E5%BA%A6) | 所有币种精度 |
| 市场行情 | [GET /api_market/apiKline](#K%E7%BA%BF) | K线 |
| 市场行情 | [GET /api_market/getTradeLists](#%E6%89%80%E6%9C%89symbol24%E5%B0%8F%E6%97%B6%E8%A1%8C%E6%83%85) | 所有symbol24小时行情(请求需携带api_key) |
| 市场行情 | [GET /api_market/getLatestTradeByPair](#%E5%8D%95%E4%B8%AAsymbol%E6%9C%80%E6%96%B0%E6%88%90%E4%BA%A4%E8%AE%B0%E5%BD%95) | 单个symbol最新成交记录 |
| 市场行情 | [GET /api_market/getDataOfTradesLatest](#%E6%89%B9%E9%87%8F%E8%8E%B7%E5%8F%96%E5%8D%95%E4%B8%AAsymbol%E6%9C%80%E8%BF%91%E6%88%90%E4%BA%A4%E8%AE%B0%E5%BD%95) | 批量获取单个symbol最近成交记录 |
| 市场行情 | [GET /api_market/market/depth](#%E5%8D%95%E4%B8%AAsymbol%E5%B8%82%E5%9C%BA%E6%B7%B1%E5%BA%A6%E8%A1%8C%E6%83%85) | 单个symbol市场深度行情 |
| 市场行情 | [GET /api_market/buyAndSellOnePrice](#%E5%8D%95%E4%B8%AAsymbol%E4%B9%B0%E4%B8%80%E5%8D%96%E4%B8%80) | 单个symbol买一卖一 |
| 市场行情 | [GET /api_market/getLatestPrice](#%E5%8D%95%E4%B8%AAsymbol%E7%89%8C%E4%BB%B7%E4%BF%A1%E6%81%AF) | 单个symbol牌价信息 |
| 用户订单信息 | [POST /api_market/placeOrder](#%E4%B8%8B%E5%8D%95) | 下单 |
| 用户订单信息 | [POST /api_market/batchPlaceOrder](#%E6%89%B9%E9%87%8F%E4%B8%8B%E5%8D%95) | 批量下单 |
| 用户订单信息 | [POST /api_market/getOrdersByOrderNo](#%E6%A0%B9%E6%8D%AE%E5%8D%95%E5%8F%B7%E6%89%B9%E9%87%8F%E6%9F%A5%E8%AF%A2%E8%AE%A2%E5%8D%95) | 根据单号批量查询订单 |
| 用户订单信息 | [POST /api_market/cancelOrder](#%E5%8F%96%E6%B6%88%E8%AE%A2%E5%8D%95) | 取消订单 |
| 用户订单信息 | [POST /api_market/batchCancelOrder](#%E6%A0%B9%E6%8D%AE%E5%8D%95%E5%8F%B7%E6%89%B9%E9%87%8F%E5%8F%96%E6%B6%88%E8%AE%A2%E5%8D%95) | 根据单号批量取消订单 |
| 用户订单信息 | [POST /api_market/getOrderByOrderNo](#%E8%8E%B7%E5%8F%96%E6%9F%90%E4%B8%80%E8%AE%A2%E5%8D%95) | 获取某一订单 |
| 用户订单信息 | [POST /api_market/getOrders](#%E8%8E%B7%E5%8F%96%E7%94%A8%E6%88%B7%E8%AE%A2%E5%8D%95%E5%88%97%E8%A1%A8) | 获取用户订单列表 |
| 用户订单信息 | [POST /api_market/getOrders](#%E8%8E%B7%E5%8F%96%E7%94%A8%E6%88%B7%E6%9C%AA%E6%88%90%E4%BA%A4%E8%AE%A2%E5%8D%95%E5%88%97%E8%A1%A8) | 获取用户未成交订单列表 |
| 用户订单信息 | [POST /api_market/getTrades](#%E8%8E%B7%E5%8F%96%E7%94%A8%E6%88%B7%E6%88%90%E4%BA%A4%E5%8D%95%E5%88%97%E8%A1%A8) | 获取用户成交单列表 |
| 用户订单信息 | [POST /api_market/getTrades](#%E7%94%A8%E6%88%B7%E5%8D%95%E4%B8%AAsymbol%E6%89%B9%E9%87%8F%E6%88%90%E4%BA%A4%E8%AE%B0%E5%BD%95) | 用户单个symbol批量成交记录 |
| 充提币 | [POST /api_market/searchDepositlList](#%E8%8E%B7%E5%8F%96%E5%85%85%E5%B8%81%E8%AE%B0%E5%BD%95) | 获取充币记录 |
| 充提币 | [POST /api_market/searchWithdrawlList](#%E8%8E%B7%E5%8F%96%E6%8F%90%E5%B8%81%E8%AE%B0%E5%BD%95) | 获取提币记录 |

## 获取余额

### POST /api_market/getBalance

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~10000 |
| tokens | 是 | array | 币种数组 |  | ["BTC","ETH"...] |

**响应参数**

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
                "token_as": "BTC",
                "usable": "0",
                "locked": "0",
                "total": "0"
            },
            {
                "user_id": 1,
                "org_id": 12,
                "token": "ETH",
                "token_as": "ETH",
                "usable": "0",
                "locked": "0",
                "total": "0"
            }
        ]
    }
}

```

**data说明：**

```
        "data": [
            {
                "user_id": 用户id,
                "org_id": 机构id,
                "token": 币名,
                "token_as": 币种别名（展示名称）,
                "usable": 可用资产,
                "locked": 锁定资产,
                "total": 总资产
            }
        ]

```

## 所有币种精度

### GET /api_market/getTokenPrecision

**请求参数**

**响应参数**

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

**data说明：**

```
    {
        "calc_precision": 计算精度,
        "phy_precision":  提币数量精度,
        "biz_precision":  委托数量精度
    }

```

## K线

### GET /api_market/apiKline

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| time_type | 是 | string | K线类型 |  | 1、5、10、15、30、60、240、1440、10080、43200 |
| market | 是 | string | 市场 |  |  |
| token | 是 | string | 币名 |  |  |
| limit | 是 | string | 数量 |  |  |

**响应参数**

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

**data说明**

```
    "data": [
        {
            "amount": 交易量,
            "c_price": 收盘价,
            "o_price": 开盘价,
            "min_price": 最低价,
            "max_price": 最高价,
            "volume": 成交额,
            "timestamp": 时间点
        }
    ]

```

## 所有symbol24小时行情

### GET /api_market/getTradeLists

**请求参数** 此接口需携带api_key

**响应参数**

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

**data说明**

```
{
    "code":0,
    "msg":"success",
    "data"{
        "main":{
            "USDT":[ 交易区
                {
                    "id": id,
                    "vol": 交易额,
                    "market": 市场,
                    "market_as": 市场展示名称,
                    "token": 币种,
                    "token_as": 币种展示名称,
                    "amount": 交易量,
                    "max_price": 最高价,
                    "min_price": 最低价,
                    "open_price": 开盘价,
                    "is_up": 是否涨跌 1涨 -1跌,
                    "prev_price": 上次价格,
                    "p_precision": 价格精度,
                    "n_precision": 数量精度,
                    "currency": { 发币参考，
                        "CNY":人民币，
                        "KRW":韩元
                    },
                    "latest_price": 最新价格,
                    "percent_change": 涨跌幅
                }
            ],
            "ETH":[
            ]
        },
        "hot":[],交易量最大的四个交易对
        "by_percent":[],涨跌幅最大的四个交易对
        "by_time":[],最新上线的交易对
    }
}

```

## 单个symbol最新成交记录

### GET /api_market/getLatestTradeByPair

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| market | 是 | string | 市场 |  |  |
| token | 是 | string | 币名 |  |  |

**响应参数**

```
[
    {
        "created_at": "2018-08-31 11:26:10",
        "price": "1",
        "amount": "0",
        "volume": "0",
        "dominance": "2"
    },
    {
        "created_at": "2018-08-31 10:26:14",
        "price": "1",
        "amount": "1",
        "volume": "1",
        "dominance": "1"
    }
]

```

**data说明**

```
[
    {
        "created_at": 创建时间,
        "price": 价格,
        "amount": 交易币数额,
        "volume": 市场币数额,
        "dominance":主动成交方 1买方 2卖方
    }
]

```

## 批量获取单个symbol最近成交记录

### GET /api_market/getDataOfTradesLatest

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~100 |
| market | 是 | string | 市场 |  |  |
| token | 是 | string | 币名 |  |  |

**响应参数**

```
{
    "code": 0,
    "msg": "successful",
    "data": [
        {
            "id": 1,
            "created_at": "2018-08-31 10:26:14",
            "price": "1",
            "amount": "1",
            "dominance": "1"
        },
        {
            "id": 2,
            "created_at": "2018-08-31 10:26:14",
            "price": "1",
            "amount": "1",
            "dominance": "1"
        }
    ]
}

```

**data说明**

```
    "data": [
      {
        "id": 成交id,
        "price": 成交价,
        "amount": 成交量,
        "dominance": 主动成交方向,
        "created_at": 成交时间
      }
   ]

```

## 单个symbol市场深度行情

### GET /api_market/market/depth

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| market | 是 | string | 市场 |  |  |
| token | 是 | string | 币名 |  |  |

**响应参数**

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

**data说明**

```
{
        "bids": [
            [
                "2.8",   //价格
                "6.32"   //数量
            ],
            [
                "2.77",  //价格
                "6.72"   //数量
            ]
        ],
        "asks": [
            [
                "5.6",   //价格
                "2.3"    //数量
            ]
        ]
}

```

## 单个symbol买一卖一

### GET /api_market/buyAndSellOnePrice

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| market | 是 | string | 市场 |  |  |
| token | 是 | string | 币名 |  |  |

**响应参数**

```
{
    "buy": "0.02657781",
    "sell": "1.1998887"
}

```

**data说明**

```
{
    "buy": "0.02657781", //买的高价
    "sell": "1.1998887"  //卖的最低价
}

```

## 单个symbol牌价信息

### GET /api_market/getLatestPrice

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| market | 是 | string | 市场 |  |  |
| token | 是 | string | 币名 |  |  |

**响应参数**

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

**data说明**

```
{
	"code": 0,
	"msg": "success",
	"data": {
		"buy": { //买
			"orders": [{ //订单列表
				"price": //价格
				"exchange": { // 兑换为法币
					"CNY" //人民币
					"KRW" //韩元
				},
				"fiat" //法币币种
				"percent_change": //涨跌幅
				"amount": //委托量
				"matching_amount": //未成交数量
				"matched_amount":  //已成交数量
			}],
			"best_price": //买入的最高价
			"max_amount": //委托的最大量
		},
		"sell": { //卖
			"orders": [], //订单列表
			"best_price": //卖出的最低价
			"max_amount": //委托的最大量
		}
	}
}

```

## 下单

### POST /api_market/placeOrder

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| market_type | 是 | string | 市场类型 |  | 1 |
| market | 是 | string | 市场 |  |  |
| token | 是 | string | 币名 |  |  |
| type | 是 | string | 买/卖 |  | 1:买 2:卖 |
| price | 是 | string | 价格 |  |  |
| amount | 是 | string | 数量 |  |  |

**响应参数**

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

**data说明**

```
    "data": {
        "id": 订单id,
        "status": 状态 0已取消 1已创建 2撮合中 3已完成,
        "order_no": 订单单号,
        "type": 类型 1买 2卖,
        "market_type": 市场类型 现阶段值为1,
        "account_id_from": 付款账号id',
        "account_id_to": 收款账号id',
        "org_id": 机构id,
        "user_id": 用户id,
        "market": 市场,
        "token": 币名,
        "price": 价格,
        "amount": 交易币数额,
        "volume": 市场币数额,
        "matched_amount": 已撮合交易币数额,
        "matched_volume": 已撮合市场币数额,
        "avg_price":已撮合部分平均单价,
        "created_at": 创建时间,
        "updated_at": 更新时间
    }

```

## 批量下单

### POST /api_market/batchPlaceOrder

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| data | 是 | array | 订单数组 |  |  |

**响应参数**

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

```

**data说明**

```
    "data": {
        "id": 订单id,
        "status": 状态 0已取消 1已创建 2撮合中 3已完成,
        "order_no": 订单单号,
        "type": 类型 1买 2卖,
        "market_type": 市场类型 现阶段值为1,
        "account_id_from": 付款账号id',
        "account_id_to": 收款账号id',
        "org_id": 机构id,
        "user_id": 用户id,
        "market": 市场,
        "token": 币名,
        "price": 价格,
        "amount": 交易币数额,
        "volume": 市场币数额,
        "matched_amount": 已撮合交易币数额,
        "matched_volume": 已撮合市场币数额,
        "avg_price":已撮合部分平均单价,
        "created_at": 创建时间,
        "updated_at": 更新时间
    }

```

## 根据单号批量查询订单

### POST /api_market/getOrdersByOrderNo

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| arr_order_no | 是 | array |  |  |  |

**响应参数**

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

**data说明**

```
    "data": {
        "id": 订单id,
        "status": 状态 0已取消 1已创建 2撮合中 3已完成,
        "order_no": 订单单号,
        "type": 类型 1买 2卖,
        "market_type": 市场类型 现阶段值为1,
        "account_id_from": 付款账号id',
        "account_id_to": 收款账号id',
        "org_id": 机构id,
        "user_id": 用户id,
        "market": 市场,
        "market_as": 市场别名（展示名称）,
        "token": 币名,
        "token_as": 币种别名（展示名称）,
        "price": 价格,
        "amount": 交易币数额,
        "volume": 市场币数额,
        "matched_amount": 已撮合交易币数额,
        "matched_volume": 已撮合市场币数额,
        "unmatched_amount":未撮合交易币数额,
        "avg_price":已撮合部分平均单价,
        "created_at": 创建时间,
        "updated_at": 更新时间
    }

```

## 取消订单

### POST /api_market/cancelOrder

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| order_nos | 是 | json | 订单单号 |  | "["2018091315164516313901209422","2018091315164516313901209422"]" |

**响应参数**

```
{
    "code": 0,
    "msg": "successful",
    "data": null
}

```

## 根据单号批量取消订单

### POST /api_market/batchCancelOrder

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| order_nos | 是 | json | 订单单号json |  | "["2018091315164516313901209422","2018091315164516313901209422"]" |

**响应参数**

```
{
    "code": 0,
    "msg": "successful"
}

```

## 获取某一订单

### POST /api_market/getOrderByOrderNo

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| order_no | 是 | string | 订单单号 |  |  |

**响应参数**

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

**data说明**

```
    "data": {
        "id": 订单id,
        "status": 状态 0已取消 1已创建 2撮合中 3已完成,
        "order_no": 订单单号,
        "type": 类型 1买 2卖,
        "market_type": 市场类型 现阶段值为1,
        "account_id_from": 付款账号id',
        "account_id_to": 收款账号id',
        "org_id": 机构id,
        "user_id": 用户id,
        "market": 市场,
        "market_as": 市场别名（展示名称）,
        "token": 币名,
        "token_as": 币种别名（展示名称）,
        "price": 价格,
        "amount": 交易币数额,
        "volume": 市场币数额,
        "matched_amount": 已撮合交易币数额,
        "matched_volume": 已撮合市场币数额,
        "unmatched_amount":未撮合交易币数额,
        "avg_price":已撮合部分平均单价,
        "created_at": 创建时间,
        "updated_at": 更新时间
    }

```

## 获取用户订单列表

### POST /api_market/getOrders

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~100 |
| type | 否 | string | 类型 |  | 1买 2卖 |
| market | 否 | string | 市场 |  |  |
| token | 否 | string | 币名 |  |  |
| status | 否 | array | 状态,格式：[0,1,2,3] |  | 0取消 1已创建 2撮合中 3已完成 |
| begin_time | 否 | string | 开始时间， 例2018-08-20 00:00:00； 必须与end_time结合使用 |  |  |
| end_time | 否 | string | 结束时间， 例2018-08-21 23:59:59；必须与start_time结合使用 |  |  |

**响应参数**

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

**data说明**

```
    "data": {
        "id": 订单id,
        "status": 状态 0已取消 1已创建 2撮合中 3已完成,
        "order_no": 订单单号,
        "type": 类型 1买 2卖,
        "market_type": 市场类型 现阶段值为1,
        "account_id_from": 付款账号id',
        "account_id_to": 收款账号id',
        "org_id": 机构id,
        "user_id": 用户id,
        "market": 市场,
        "market_as": 市场别名（展示名称）,
        "token": 币名,
        "token_as": 币种别名（展示名称）,
        "price": 价格,
        "amount": 交易币数额,
        "volume": 市场币数额,
        "matched_amount": 已撮合交易币数额,
        "matched_volume": 已撮合市场币数额,
        "unmatched_amount":未撮合交易币数额,
        "avg_price":已撮合部分平均单价,
        "created_at": 创建时间,
        "updated_at": 更新时间
    }

```

## 获取用户未成交订单列表

### POST /api_market/getOrders

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~100 |
| status | 否 | array | 状态(1未撮合 2撮合中) |  | [1,2] |

**响应参数**

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

**data说明**

```
    "data": {
        "id": 订单id,
        "status": 状态 0已取消 1已创建 2撮合中 3已完成,
        "order_no": 订单单号,
        "type": 类型 1买 2卖,
        "market_type": 市场类型 现阶段值为1,
        "account_id_from": 付款账号id',
        "account_id_to": 收款账号id',
        "org_id": 机构id,
        "user_id": 用户id,
        "market": 市场,
        "market_as": 市场别名（展示名称）,
        "token": 币名,
        "token_as": 币种别名（展示名称）,
        "price": 价格,
        "amount": 交易币数额,
        "volume": 市场币数额,
        "matched_amount": 已撮合交易币数额,
        "matched_volume": 已撮合市场币数额,
        "unmatched_amount":未撮合交易币数额,
        "avg_price":已撮合部分平均单价,
        "created_at": 创建时间,
        "updated_at": 更新时间
    }

```

## 获取用户成交单列表

### POST /api_market/getTrades

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~100 |
| type | 否 | string | 类型 |  | 1买 2卖 |
| market | 否 | string | 市场 |  |  |
| token | 否 | string | 币名 |  |  |
| begin_time | 否 | string | 开始时间， 例2018-08-20 17:59:33； 必须与end_time结合使用 |  |  |
| end_time | 否 | string | 结束时间， 例2018-08-31 17:59:33； 必须与start_time结合使用 |  |  |

**响应参数**

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

**data说明**

```
        "data": {
            "id": 1,
            "trade_no": 成交单号,
            "buy_order_id": 买入的订单id,
            "buy_order_no": 买入的订单单号,
            "sell_order_id": 卖出的订单id,
            "sell_order_no": 卖出的订单单号,
            "dominance": 主动成交方,
            "buyer_user_id": 买入的用户id,
            "seller_user_id": 卖出的用户id,
            "org_id": 机构id,
            "trade_strategy": 交易类型 1限价交易,
            "market": 市场,
            "market_as": 市场别名（展示名称）,
            "token": 币名,
            "token_as": 币种别名（展示名称）,
            "price": 价格,
            "amount": 交易币数额,
            "volume": 市场币数额,
            "created_at": 创建时间,
            "updated_at": 更新时间
        }

```

## 用户单个symbol批量成交记录

### POST /api_market/getTrades

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~100 |
| market | 否 | string | 市场 |  |  |
| token | 否 | string | 币名 |  |  |

**响应参数**

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

**data说明**

```
        "data": {
            "id": 1,
            "trade_no": 成交单号,
            "buy_order_id": 买入的订单id,
            "buy_order_no": 买入的订单单号,
            "sell_order_id": 卖出的订单id,
            "sell_order_no": 卖出的订单单号,
            "dominance": 主动成交方,
            "buyer_user_id": 买入的用户id,
            "seller_user_id": 卖出的用户id,
            "org_id": 机构id,
            "trade_strategy": 交易类型 1限价交易,
            "market": 市场,
            "market": 市场别名（展示名称）,
            "token": 币名,
            "token_as": 币种名称（展示名称）,
            "price": 价格,
            "amount": 交易币数额,
            "volume": 市场币数额,
            "created_at": 创建时间,
            "updated_at": 更新时间
        }

```

## 获取充币记录

### POST /api_market/searchDepositList

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~100 |
| token | 是 | string | 币名，可为空 |  |  |
| begin_time | 是 | string | 开始时间， 例2018-08-20 17:59:33，可为空；必须与end_time结合使用 |  |  |
| end_time | 是 | string | 结束时间， 例2018-08-31 17:59:33，可为空；必须与start_time结合使用 |  |  |

**响应参数**

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

**data说明：**

```
        "data": {
            "id": 充币单id,
            "user_id": 用户,
            "org_id": 机构id,
            "account_id": 账号id,
            "token": 币名,
            "token_as": 币种别名（显示名称）,
            "amount": 数量,
            "blockchain_tx_id": txid,
            "deposit_no": 充币单号,
            "address": 充币地址,
            "confirm_count": 确认数,
            "status": 状态 1已创建 5已完成,
            "created_at": 创建时间,
            "updated_at": 更新时间
        }

```

## 获取提币记录

### POST /api_market/searchWithdrawalList

**请求参数**

| 参数名称 | 是否必须 | 数据类型 | 描述 | 默认值 | 取值范围 |
| --- | --- | --- | --- | --- | --- |
| page | 是 | string | 页码 |  | 1~10000 |
| size | 是 | string | 每页显示数量 |  | 1~100 |
| token | 是 | string | 币名，可为空 |  |  |
| begin_time | 是 | string | 开始时间， 例2018-08-20 17:59:33，可为空；必须与end_time结合使用 |  |  |
| end_time | 是 | string | 结束时间， 例2018-08-31 17:59:33，可为空；必须与start_time结合使用 |  |  |

**响应参数**

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

**data说明：**

```
        "data": {
            "id": 提币单id,
            "user_id": 用户,
            "org_id": 机构id,
            "account_id": 账号id,
            "fee_account_id": 手续费账号id,
            "token": 币名,
            "token_as": 币种别名（展示名称）,
            "fee_token": 网络费币名,
            "protocol": 协议,
            "amount": 实际到账数量,
            "apply_amount": 申请数量,
            "blockchain_tx_id": txid,
            "network_fee": 网络费,
            "withdrawal_no": 提币单号,
            "address_to": 收款地址,
            "address_from": 付款地址,
            "fee_address": 手续费地址,
            "reason": 审核原因,
            "confirm_count": 确认数,
            "status": 状态 0未审核 1已审核 2钱包已拉取 3已产生矿工费 4已产生第一块 5已完成 6审核未通过 7取消,
            "created_at": 创建时间,
            "updated_at": 更新时间
        }

```
