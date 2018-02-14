FORMAT: 1A
HOST: http://demo.bitkami.com/

# Bitkami

Bitkami API allow you to easily access the exchange functions

## List Accounts [/api/user/listAccounts]

### List Accounts [GET]

+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

+ Response 200 (application/json)

    + Body

            {
                "success":true,
                "error":null,
                "result":
                    [
                        {
                          "name":"default",
                          "created":"2018-02-07T17:19:13.622Z",
                          "type":"trading"
                        },
                        {
                          "name":"kamix278",
                          "created":"2018-02-07T17:19:21.013Z",
                          "type":"trading"
                        }
                    ]
            }



## Create Account [/api/user/createAccount]

### Create Account [POST]

Create an additional trading account, default account is created on signup, checkout /api/user/getUserRango to verify if you are elegible for an additional trading account.

+ Request (application/json)


    + Headers

            Authorization:  Bearer {{API_TOKEN}}

    + Body

            {
                "type": "trading",
                "name": "accountName"
            }

+ Response 200 (application/json)

    + Body

            {
                "success": true,
                "error":null
            }

## Get Balance [/api/user/getBalance]

### Get Balance [GET]
+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

+ Response 200 (application/json)

    + Body

            {
                "success":true,
                "error":null,
                "result":{
                    "default":{
                        "name":"default",
                        "created":"2018-02-07T17:19:13.622Z",
                        "type":"trading",
                        "balance":{
                            "USDT":{
                                "available":"72798001.99023744",
                                "freeze":"26000"
                            },
                            "BTC":{
                                "available":"10933.393894",
                                "freeze":"100.5099"
                            }
                        }
                    }
                }
            }

## Current User Rango [/api/user/getUserRango]

### Current User Rango [GET]
+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

+ Response 200 (application/json)

    + Body

            {
                "success":true,
                "error":null,
                "result":{
                   "openedOrderLimit":20,
                   "tradingAccounts":2,
                   "copyAccounts":3,
                   "makerFee":0.19,
                   "takerFee":0.19,
                   "required_bkm":100000,
                   "name":"pro"
                }
            }

## Get Deposit Address [/api/user/getDepositAddress]

### Get Deposit Address [POST]
+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

+ Response 200 (application/json)

    + Body

            {
                "success":true,
                "error":null,
                "result":{
                    "asset":"{{ASSET}}",
                    "address":"{{ADDRESS}}"
                }
            }

## Set Witdrawal Address [/api/user/setWithdrawalAddress]

### Set Withdrawal Address [POST]
+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

    + Body

            {
                "asset":"{{ASSET}}",
                "address":"{{ADDRESS}}"
            }

+ Response 200 (application/json)

    + Body

            {
                "success":true,
                "error":null,
                "message": "Address registered",
                "result":null
            }

## Withdrawal Request [/api/user/requestWithdrawal]

### Withdrawal Request [POST]
+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

    + Body

            {
                "amount":      1
                "asset":       "BTC"
                "fromAccount": "default"
                "internal":    true
                "target":      "matteo@bitkami.com"
                "toAccount":   "default"
            }

+ Response 200 (application/json)

    + Body

            {
                "success":true,
                "error":null,
                "message":"Transfer request succesfully registered",
                "result":null
            }


## Get Instruments [/api/data/instruments]

### instruments [GET]

+ Response 200 (application/json)

    + Body

            {
                "success":true,
                "error":null,
                result:[
                    "BTC/USDT",
                    "ETH/BTC",
                    "ETH/USDT"
                ]
            }


## Get Candles [/api/data/candles]

### candles [POST]

+ Request (application/json)

    + Body

            {
                "market": "BTCUSDT"
            }

+ Response 200 (application/json)

    + Body

            {
                "success":true,
               "error":null,
               "result":[
                  [
                     1518444000,
                     "20000",
                     "20000",
                     "20000",
                     "20000",
                     "0",
                     "0",
                     "BTCUSDT"
                  ],
                  [
                     1518447600,
                     "20000",
                     "20000",
                     "20000",
                     "20000",
                     "0",
                     "0",
                     "BTCUSDT"
                  ],
                  [
                     1518451200,
                     "20000",
                     "20000",
                     "20000",
                     "20000",
                     "0",
                     "0",
                     "BTCUSDT"
                  ],
                  [
                     1518454800,
                     "20000",
                     "20000",
                     "20000",
                     "20000",
                     "0",
                     "0",
                     "BTCUSDT"
                  ],
                  [
                     1518458400,
                     "20000",
                     "20000",
                     "20000",
                     "20000",
                     "0",
                     "0",
                     "BTCUSDT"
                  ]
               ]
            }


## Get Market History [/api/data/history]

### history [POST]

+ Request (application/json)

    + Body

            {
                "market": "BTCUSDT"
            }

+ Response 200 (application/json)

    + Body

            {
                "success":true,
               "error":null,
               "result":[
                  {
                     "type":"sell",
                     "price":"20000",
                     "id":304791,
                     "time":1518106180.040278,
                     "amount":"11.4901"
                  },
                  {
                     "type":"buy",
                     "price":"14877.07",
                     "id":304790,
                     "time":1517927612.071244,
                     "amount":"0.0465"
                  },
                  {
                     "type":"buy",
                     "price":"14177.91",
                     "id":304789,
                     "time":1517927612.071048,
                     "amount":"0.2015"
                  },
                  {
                     "type":"buy",
                     "price":"14132.59",
                     "id":304788,
                     "time":1517927612.070849,
                     "amount":"0.1107"
                  },
                  {
                     "type":"buy",
                     "price":"14118.32",
                     "id":304787,
                     "time":1517927612.07065,
                     "amount":"0.0231"
                  },
                  {
                     "type":"buy",
                     "price":"13797.32",
                     "id":304786,
                     "time":1517927612.070455,
                     "amount":"0.2609"
                  },
                  {
                     "type":"buy",
                     "price":"13776.57",
                     "id":304785,
                     "time":1517927612.070247,
                     "amount":"0.2068"
                  },
                  {
                     "type":"buy",
                     "price":"13633.38",
                     "id":304784,
                     "time":1517927612.070041,
                     "amount":"0.1571"
                  }
               ]
            }


## Get Order Book [/api/data/orderbook]

### orderbook [POST]

+ Request (application/json)

    + Body

            {
                "market": "BTCUSDT",
                "side": 1
            }

+ Response 200 (application/json)

    + Body

            {
                "success":true,
               "error":null,
               "result":{
                  "offset":0,
                  "orders":[
                     {
                        "id":721067,
                        "mtime":1518124953.596943,
                        "source":"",
                        "market":"BTCUSDT",
                        "type":1,
                        "side":2,
                        "user":1,
                        "ctime":1518124953.596943,
                        "price":"8000",
                        "left":"1",
                        "amount":"1",
                        "taker_fee":"0.002",
                        "maker_fee":"0.001",
                        "deal_stock":"0",
                        "deal_fee":"0",
                        "deal_money":"0"
                     },
                     {
                        "id":721062,
                        "mtime":1517868186.183723,
                        "source":"",
                        "market":"BTCUSDT",
                        "type":1,
                        "side":2,
                        "user":11,
                        "ctime":1517868186.183717,
                        "price":"5090",
                        "left":"2703.9761",
                        "amount":"3000",
                        "taker_fee":"0.19",
                        "maker_fee":"0.19",
                        "deal_stock":"296.0239",
                        "deal_fee":"56.244541",
                        "deal_money":"296023.9"
                     },
                     {
                        "id":721063,
                        "mtime":1517927595.682893,
                        "source":"",
                        "market":"BTCUSDT",
                        "type":1,
                        "side":2,
                        "user":10,
                        "ctime":1517927595.682893,
                        "price":"2000",
                        "left":"13",
                        "amount":"13",
                        "taker_fee":"0.19",
                        "maker_fee":"0.19",
                        "deal_stock":"0",
                        "deal_fee":"0",
                        "deal_money":"0"
                     }
                  ],
                  "limit":50,
                  "total":3
               }
            }


## Get Market Status [/api/data/marketStatus]

### marketStatus [POST]

+ Request (application/json)

    + Body

            {
                "market": "BTCUSDT"
            }

+ Response 200 (application/json)

    + Body

            {
                "success":true,
               "error":null,
               "result":{
                  "period":86400,
                  "last":"20000",
                  "low":"0",
                  "open":"0",
                  "close":"0",
                  "high":"0",
                  "volume":"0"
               },
            }




## Get Pending Orders [/api/exchange/pendingOrders]

### pendingOrders [POST]

+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

    + Body

            {
                "market": "BTCUSDT",
                "selectedAccount": "default"
            }

+ Response 200 (application/json)

    + Body

            {
               "success":true,
               "error":null,
               "result":{
                  "records":[
                     {
                        "id":721066,
                        "mtime":1518106665.659952,
                        "source":"",
                        "market":"BTCUSDT",
                        "type":1,
                        "side":1,
                        "user":10,
                        "ctime":1518106665.659952,
                        "price":"11000",
                        "left":"12",
                        "amount":"12",
                        "taker_fee":"0.19",
                        "maker_fee":"0.19",
                        "deal_stock":"0",
                        "deal_fee":"0",
                        "deal_money":"0"
                     },
                     {
                        "id":721065,
                        "mtime":1518106180.040278,
                        "source":"",
                        "market":"BTCUSDT",
                        "type":1,
                        "side":1,
                        "user":10,
                        "ctime":1518106180.040269,
                        "price":"12000",
                        "left":"88.5099",
                        "amount":"100",
                        "taker_fee":"0.19",
                        "maker_fee":"0.19",
                        "deal_stock":"11.4901",
                        "deal_fee":"43662.38",
                        "deal_money":"229802"
                     },
                     {
                        "id":721063,
                        "mtime":1517927595.682893,
                        "source":"",
                        "market":"BTCUSDT",
                        "type":1,
                        "side":2,
                        "user":10,
                        "ctime":1517927595.682893,
                        "price":"2000",
                        "left":"13",
                        "amount":"13",
                        "taker_fee":"0.19",
                        "maker_fee":"0.19",
                        "deal_stock":"0",
                        "deal_fee":"0",
                        "deal_money":"0"
                     }
                  ],
                  "limit":50,
                  "offset":0,
                  "total":3
               }
            }


## Get User Transaction History [/api/exchange/transactionHistory]

### transactionHistory [POST]

+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

    + Body

            {
                "market": "BTCUSDT",
                "selectedAccount": "default"
            }

+ Response 200 (application/json)

    + Body

            {
               "success":true,
               "error":null,
               "result":{
                  "offset":0,
                  "limit":50,
                  "records":[
                     {
                        "side":2,
                        "time":1518106180.040278,
                        "user":10,
                        "id":304791,
                        "price":"20000",
                        "amount":"11.4901",
                        "role":1,
                        "deal":"229802",
                        "deal_order_id":721065,
                        "fee":"2.183119"
                     },
                     {
                        "side":1,
                        "time":1518106180.040278,
                        "user":10,
                        "id":304791,
                        "price":"20000",
                        "amount":"11.4901",
                        "role":2,
                        "deal":"229802",
                        "deal_order_id":721064,
                        "fee":"43662.38"
                     }
                  ]
               }
            }

## Order [/api/exchange/order]

### Order [POST]

+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

    + Body

            {
                "market": "BTCUSDT",
                "selectedAccount": "default",
                "amount": 13,
                "price": 8000,
                "side": 1
            }

+ Response 200 (application/json)

    + Body

            {
               "success":true,
               "error":null,
               "result":{
                  "id":721068,
                  "mtime":1518534960.649597,
                  "source":"",
                  "market":"BTCUSDT",
                  "type":1,
                  "side":1,
                  "user":10,
                  "ctime":1518534960.649587,
                  "price":"8000",
                  "left":"12",
                  "amount":"13",
                  "taker_fee":"0.19",
                  "maker_fee":"0.19",
                  "deal_stock":"1",
                  "deal_fee":"1520",
                  "deal_money":"8000"
               }
            }

## Close Order [/api/exchange/closeOrder]

### closeOrder [POST]

+ Request (application/json)

    + Headers

            Authorization:  Bearer {{API_TOKEN}}

    + Body

            {
                "market": "BTCUSDT",
                "selectedAccount": "default",
                "orderID": 721065
            }

+ Response 200 (application/json)

    + Body

            {
               "success":true,
               "error":null,
               "result":{
                  "id":721065,
                  "mtime":1518106180.040278,
                  "source":"",
                  "market":"BTCUSDT",
                  "type":1,
                  "side":1,
                  "user":10,
                  "ctime":1518106180.040269,
                  "price":"12000",
                  "left":"88.5099",
                  "amount":"100",
                  "taker_fee":"0.19",
                  "maker_fee":"0.19",
                  "deal_stock":"11.4901",
                  "deal_fee":"43662.38",
                  "deal_money":"229802"
               }
            }

