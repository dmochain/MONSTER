# 介绍

DMO项目的API文档

# 支持的API列表

### 地址

- <a href="#add1">检查地址格式(checkAddress)</a>
- <a href="#add2">生成地址(createAddress)</a>
- <a href="#add3">获取地址余额(getBalance)</a>

### 区块

- <a href="#bl1">获取最新区块高度(getLatestBlockNum)</a>
- <a href="#bl2">根据区块高度获取信息(getBlock)</a>
- <a href="#bl3">获取最近产生的区块(getBlocks)</a>

### 交易

- <a href="#tra1">发起转账(sendTransaction)</a>
- <a href="#tra2">根据hash获取交易信息(getTransactionByHash)</a>
- <a href="#tra3">获取所有最新的交易(getTransactions)</a>
- <a href="#tra4">根据地址获取最新的交易(getTransactionsByAddress)</a>
- <a href="#tra5">获取矿工手续费(getFee)</a>


***

### <a name="add1">检查地址格式(checkAddress)</a>
###### 请求地址
```
/checkAddress
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|address|  string	|是	     |地址	   |   -	 |

###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  array	|是	     |返回数据	   |   -	 |


###### 返回JSON示例
````
{
    "code": 400,
    "msg": "地址有误",
    "data": []
}
````

###### 备注说明
````
无
````


***

### <a name="add2">生成地址(createAddress)</a>
###### 请求地址
```
/createAddress
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|num|  number	|是	     |数量	   |   -	 |
|password|  string	|是	     |密码	   |   -	 |


###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  array	|是	     |返回数据(地址数组)	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "创建成功",
    "data": [
        "1xeb475b87b227d027a53dcd29eb5346bf2sh6lxi3"
    ]
}
````

###### 备注说明
````
无
````

***

### <a name="add3">获取地址余额(getBalance)</a>
###### 请求地址
```
/getBalance
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|address|  string	|是	     |地址	   |   -	 |


###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  string	|是	     |返回数据	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "获取成功",
    "data": "5208.98290000"
}
````

###### 备注说明
````
无
````


***
### <a name="bl1">获取最新区块高度(getLatestBlockNum)</a>
###### 请求地址
```
/getLatestBlockNum
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |

###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  string	|是	     |返回数据	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "获取成功",
    "data": 176
}
````

###### 备注说明
````
无
````


***
### <a name="bl2">根据区块高度获取信息(getBlock)</a>
###### 请求地址
```
/getBlock
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|block_num|  number	|是	     |区块高度	   |   -	 |

###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  array	|是	     |返回数据	   |   -	 |
|block|  number	|是	     |区块高度	   |   -	 |
|miner_address|  string	|是	     |矿工地址	   |   -	 |
|transaction_num|  number	|是	     |交易数量	   |   -	 |
|miner_reward|  number	|是	     |矿工费	   |   -	 |
|created_at|  string	|是	     |产生的时间	   |   -	 |
|transactions|  array	|是	     |交易信息	   |   -	 |
|amount     |  number	|是	     |转账数量	   |   -	 |
|fee        |  number	|是	     |该笔交易矿工费	   |   -	 |
|value      |  number	|是	     |实际到账数量	   |   -	 |
|hash       |  string	|是	     |hash	   |   -	 |
|from       |  string	|是	     |交易发送方	   |   -	 |
|to         |  string	|是	     |交易接收方	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "获取成功",
    "data": {
        "block": 120,
        "miner_address": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje",
        "transaction_num": 9,
        "miner_reward": "0.00180000",
        "created_at": "2020-08-21 17:45:48",
        "transactions": [
            {
                "amount": "2.00000000",
                "fee": "0.00020000",
                "value": "1.99980000",
                "hash": "1xad49d5ccd550d2cd78c544a8cd95c129bvljmznew1op4xyyrs0q3qlrnaidk5xo",
                "from": "1x74ecf924135a85715d78ec05882cf282dnrfytms",
                "to": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje"
            },
            {
                "amount": "2.00000000",
                "fee": "0.00020000",
                "value": "1.99980000",
                "hash": "1x8e244e607b2c59ed10138d1b65371fc0ucjaigx7nrkvwzeb5ld2vfku8r9spald",
                "from": "1x74ecf924135a85715d78ec05882cf282dnrfytms",
                "to": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje"
            }
        ]
    }
}
````

###### 备注说明
````
无
````
***

### <a name="bl3">获取最近产生的区块(getBlocks)</a>
###### 请求地址
```
/api/customer-flow
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|page|  number	|否	     |页码	   |   1	 |
|limit|  number	|否	     |条数	   |   10	 |

###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  array	|是	     |返回数据	   |   -	 |
|block|  string	|是	     |区块高度	   |   -	 |
|miner_address|  string	|是	     |矿工地址	   |   -	 |
|transaction_num|  string	|是	     |交易笔数	   |   -	 |
|count|  number	|是	     |总条数	   |   -	 |
|last_page|  number	|是	     |总页数	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "获取成功",
    "data": [
        {
            "block": 176,
            "miner_address": "1x409cfa3c73873fecf42614caa5f2361flkdbyr9t",
            "transaction_num": 1
        },
        {
            "block": 175,
            "miner_address": "1x409cfa3c73873fecf42614caa5f2361flkdbyr9t",
            "transaction_num": 1
        }
    ],
    "count": 176,
    "last_page": 18
}
````

###### 备注说明
````
无
````
***


### <a name="tra1">发起转账(sendTransaction)</a>
###### 请求地址
```
/sendTransaction
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|from|  string	|是	     |发送方地址	   |   -	 |
|to|  string	|是	     |接收方地址	   |   -	 |
|amount|  string	|是	     |数量	   |   -	 |
|password|  string	|是	     |发送方的密码	   |   -	 |

###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  string	|是	     |hash	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "成功",
    "data": "1x14ee866d2fde73e207f63de07ba83f91m2gbwvitll4kbh5ydhumfqsrsve6tdc0"
}
````

###### 备注说明
````
无
````


***
### <a name="tra2">根据hash获取交易信息(getTransactionByHash)</a>
###### 请求地址
```
/getTransactionByHash
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|hash|  string	|是	     |hash	   |   -	 |

###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  array	|是	     |返回数据	   |   -	 |
|amount|  string	|是	     |转账发起时的数量	   |   -	 |
|fee|  string	|是	     |该笔的矿工费	   |   -	 |
|value|  string	|是	     |实际到账的数量	   |   -	 |
|hash|  string	|是	     |hash	   |   -	 |
|from|  string	|是	     |发起方地址	   |   -	 |
|to|  string	|是	     |接收方的地址	   |   -	 |
|block|  number	|是	     |区块高度	   |   -	 |
|status|  number	|是	     |状态0未打包1已打包	   |   -	 |
|confirm_num|  number	|是	     |区块确认高度	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "获取成功",
    "data": {
        "amount": "10.00000000",
        "fee": "0.00020000",
        "value": "9.99980000",
        "hash": "1x14ee866d2fde73e207f63de07ba83f91m2gbwvitll4kbh5ydhumfqsrsve6tdc0",
        "from": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje",
        "to": "1xcb6ae01f731c0d73378bc7bca70b258b2tdyjml6",
        "block": 176,
        "status": 1,
        "confirm_num": 0
    }
}
````

###### 备注说明
````
无
````


***
### <a name="tra3">获取所有最新的交易(getTransactions)</a>
###### 请求地址
```
/getTransactions
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|page|  number	|否	     |页码	   |   1	 |
|limit|  number	|否	     |条数	   |   10	 |


###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  array	|是	     |返回数据	   |   -	 |
|hash|  string	|是	     |hash	   |   -	 |
|from|  string	|是	     |交易发送方地址	   |   -	 |
|to|  string	|是	     |交易接收方地址	   |   -	 |
|amount|  string	|是	     |数量	   |   -	 |
|count|  number	|是	     |总条数	   |   -	 |
|last_page|  number	|是	     |总页数	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "获取成功",
    "data": [
        {
            "hash": "1x14ee866d2fde73e207f63de07ba83f91m2gbwvitll4kbh5ydhumfqsrsve6tdc0",
            "from": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje",
            "to": "1xcb6ae01f731c0d73378bc7bca70b258b2tdyjml6",
            "amount": "10.00000000"
        },
        {
            "hash": "1xeb18797a2440357f1e27d1e87b28d2c45tomvugbwiezaorhfu2yqwsptqlnvx3r",
            "from": "1xb064a196979fa73e52ea8ef051a87eb6eo4e1dxw",
            "to": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje",
            "amount": "1373.99660000"
        },
        {
            "hash": "1x623437fed17e08c8cd562bc62ec3e5c0kxkpeu0fgi56cavqxjhohqlv7m42sp8a",
            "from": "1x1ff9cd125013230e9bfaa348560d52b5ydnveqg4",
            "to": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje",
            "amount": "19.99980000"
        }
    ],
    "count": 930,
    "last_page": 93
}
````

###### 备注说明
````
无
````


***
### <a name="tra4">根据地址获取最新的交易(getTransactionsByAddress)</a>
###### 请求地址
```
/getTransactionsByAddress
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |
|page|  number	|否	     |页码	   |   1	 |
|limit|  number	|否	     |条数	   |   10	 |
|address|  string	|是	     |地址	   |   -	 |

###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  array	|是	     |返回数据	   |   -	 |
|hash|  string	|是	     |hash	   |   -	 |
|from|  string	|是	     |交易发送方地址	   |   -	 |
|to|  string	|是	     |交易接收方地址	   |   -	 |
|amount|  string	|是	     |数量	   |   -	 |
|count|  number	|是	     |总条数	   |   -	 |
|last_page|  number	|是	     |总页数	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "获取成功",
    "data": [
        {
            "hash": "1x61cd342c47cb12d16128797e382da6bfdcince1mj6quvtafrvji5qg729dsnolp",
            "from": "1x74ecf924135a85715d78ec05882cf282dnrfytms",
            "to": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje",
            "amount": "2.00000000"
        },
        {
            "hash": "1xf02956223c85a538b8558b800d6da8fciqnpy162hj0w7booxqjcfa5fak8r3pgg",
            "from": "1x74ecf924135a85715d78ec05882cf282dnrfytms",
            "to": "1x7e1bfd4b228d2638275ddefbed62f0b30gv1kqje",
            "amount": "2.00000000"
        }
    ],
    "count": 672,
    "last_page": 68
}
````

###### 备注说明
````
无
````


***
### <a name="tra5">获取矿工手续费(getFee)</a>
###### 请求地址
```
/getFee
```
###### 请求类型
```
POST
```
###### 请求参数
|参数名  |  类型	   |必填      |描述     |默认值|
|:---:  |   :---:  | :---:   | :---:   | :----: |


###### 响应数据
|参数名  |  类型	   |必填      |描述     |默认值|
|:---  |   :---:  | :---:   | :---:   | :----: |
|code|  number	|是	     |200为成功	   |   -	 |
|msg|  string	|是	     |错误信息	   |   -	 |
|data|  string	|是	     |最新的矿工费	   |   -	 |


###### 返回JSON示例
````
{
    "code": 200,
    "msg": "成功",
    "data": "0.0002"
}
````

###### 备注说明
````
无
````

***




