# ShowMANDB

```
https://api.showmoney.app/showMANDB
```



 ShowMANDB 数据结构

|	参数名称     |	类型	 |	描述   |
|----------------|-----------|---------------|
| metanetId           | string 	 | metanet ID |
| rootTxId        | string 	 | 所属顶点TxId |
| txId        | string 	 | 	交易id    |
| vouts        | []*MetaTxOut 	 | 	vouts   |
| parts          | []string 	 | metanet 的数据 |
| address   | string 	     | 	address |
| publicKey          | string 	 | publicKey |
| parentTxTd   | string 	     | 	父txId   |
| metaId        | string 	 | metaId tag |
| nodeName | string 	     | 	协议名称    |
| data      | interface 	 | 	数据      |
| encrypt      | string 	 | 	加密方式    |
| version      | string 	 | 	版本      |
| dataType      | string 	 | 	数据类型    |
| encoding      | string 	 | 	编码格式    |
| blockHeight      | int64 	 | 	所在块高    |
| timestamp         | int64 	 | 	时间戳     |
| isValid         | bool 	 | 	是否有效    |
| isNew         | bool 	 | 	是否最新    |
| fee         | uint64 	 | 该meta数据的费用 |



## 获取MetaID的Info

`/api/v1/query/getMetaIDInfo/<rootTxId>`

 请求参数


| 参数名称 | 类型   | 是否可空 | 长度限制 | 描述   |
| -------- | ------ | -------- | -------- | ------ |
| rootTxId | string | 否       |          | MetaID |

响应参数



| 参数名称     | 类型   | 是否可空 | 长度限制 | 描述            |
| ------------ | ------ | -------- | -------- | --------------- |
| metaIdTag    | string | 否       |          | metaId标识      |
| infoTxId     | string | 否       |          | info的TxId      |
| protocolTxId | string | 否       |          | protocol的TxId  |
| name         | string | 否       |          | 名称            |
| email        | string | 否       |          | Email           |
| phone        | string | 否       |          | 手机号          |
| avatar       | string | 否       |          | 头像，hexString |

```javascript
// 请求 

https://api.showmoney.app/showMANDB/api/v1/query/getMetaIDInfo/a717f2b8364ddab277216408230b1485d28ed3a0bd4b00ab7c7b2437fe58af2e
```

```javascript
// 响应数据：
 {
  "result": {
    "metaIdTag": "TestShowID",
    "infoTxId": "2e8ae6892b9b3873dcaa9d2f03a00325813cdc2c0e739856c1df622ed9c21090",
    "protocolTxId": "9e7f51a6af7d7c760ca003a4fd984987974d02a3b4cc8ba4042f8a16871654ba",
    "name": "Mark42",
    "email": "",
    "phone": "42494531037803de4a6378a98bf5f3164c830ff9a28c59684071146c54a7c56e052c795e4b492aa9647bd975b7988c0c046df3ce75cfe6fae6457f55b5992b62ea5dd74ff21a6f81f6787ff490dc6a683b9a34144599d13177372d5aa4c01ea967871dc3ca",
    "avatar": "..."
  },
  "code": 200,
  "msg": "success",
  "time": 1591329356028,
  "error": "null"
}
```

## 获取节点信息

获取某个节点信息

 `/api/v1/metanet/getNode/<txId>`

请求参数

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId          | string 	 | 	否           |	    			    |     txId           |

响应参数

***data***

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| nodeTxId          | int64 	 | 	否           |	    			    | 节点txId                        |
| nodeAddress       | string 	 | 	否      	 |	    			    | 节点地址		                    |
| nodePublicKey     | string 	 | 	否      	 |	    			    | 节点公钥			|
| parentTxId        | string 	 | 	否      	 |	    			    | 父节点txId			|
| parentAddress     | string 	 | 	否      	 |	    			    | 父节点地址			|
| parentPublicKey   | string 	 | 	否      	 |	    			    | 父节点公钥			|
| outputIndex       | int64 	 | 	否      	 |	    			    | 所在索引			|
| blockHeight       | int64 	 | 	否      	 |	    			    | 块高			        |
| rootTxId          | string 	 | 	否      	 |	    			    | 根节点txId			|
| rootAddress       | string 	 | 	否      	 |	    			    | 根节点地址			|
| rootPublicKey     | string 	 | 	否      	 |	    			    | 根节点公钥			|
| timestamp         | int64 	 | 	否      	 |	    			    | 时间戳			    |

请求响应实例

```javascript
api请求数据: 
    https://api.showmoney.app/showMANDB/api/v1/metanet/getNode/9f0fa21bfe7706fe51decd468069cd8610d7ceb1a1265f2e17559b75d95cc93c
    
响应数据：
{
  "result": {
    "nodeTxId": "9f0fa21bfe7706fe51decd468069cd8610d7ceb1a1265f2e17559b75d95cc93c",
    "nodeAddress": "1KrXEiKZtri9DnndD1MVDG5e1yXA5HNChn",
    "nodePublicKey": "NULL",
    "parentTxId": "c37ee0eef4a98a192c42f28d8c66d3b10bd07a4c84d6a50445c9c9674b1179ed",
    "parentAddress": "1GimPAbPAkmexbbdWqe9fQCQpgZdGNdjy7",
    "parentPublicKey": "",
    "outputIndex": 0,
    "blockHeight": 631827,
    "rootTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
    "rootAddress": "13DQH5o2WwH72ojKi2GRQAhUuEBUs4euhs",
    "rootPublicKey": "NULL",
    "timestamp": 1587633554062
  },
  "code": 200,
  "msg": "success",
  "time": 1590031471614,
  "error": "null"
}
```

## 获取MetaID节点parts信息

`/api/v1/metanet/getParts/<txId>`

	请求协议：HTTP GET
	
	功能简介：获取parts

请求参数

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId          | string 	 | 	否           |	    			    |     txId           |

响应参数

***data***

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId              | string 	 | 	否           |	    			    | 节点txId                        |
| outputIndex       | int64 	 | 	否      	 |	    			    | 所在索引			|
| blockHeight       | int64 	 | 	否      	 |	    			    | 块高			        |
| raw               | string 	 | 	否      	 |	    			    | 脚本			|
| parts             | []string 	 | 	否      	 |	    			    | 解析后的parts			|

请求响应实例	

```javascript
// api请求数据: 
   https://api.showmoney.app/showMANDB/api/v1/metanet/getParts/9f0fa21bfe7706fe51decd468069cd8610d7ceb1a1265f2e17559b75d95cc93c
    
// 响应数据：
{
  "result": {
    "txId": "9f0fa21bfe7706fe51decd468069cd8610d7ceb1a1265f2e17559b75d95cc93c",
    "blockHeight": 631827,
    "outputIndex": 0,
    "raw": "006a046d65746122314b725845694b5a74726939446e6e6444314d56444735653179584135484e43686e4063333765653065656634613938613139326334326632386438633636643362313062643037613463383464366135303434356339633936373462313137396564064d6574614944046e616d6505416c696365013004302e30390a746578742f706c61696e055554462d38",
    "parts": [
      "OP_0",
      "OP_RETURN",
      "meta",
      "1KrXEiKZtri9DnndD1MVDG5e1yXA5HNChn",
      "c37ee0eef4a98a192c42f28d8c66d3b10bd07a4c84d6a50445c9c9674b1179ed",
      "MetaID",
      "name",
      "Alice",
      "0",
      "0.09",
      "text/plain",
      "UTF-8"
    ]
  },
  "code": 200,
  "msg": "success",
  "time": 1588077699845,
  "error": "null"
}
```

-------------------------------------------------------------------------------------------------------------------------
-------------------------------------------------------------------------------------------------------------------------

## 获取根节点

 `/api/v1/metanet/getRoot/<txId>` 

	请求协议：HTTP GET
	
	功能简介：获取根节点

请求参数

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId          | string 	 | 	否           |	    			    |     txId           |

响应参数

***data***

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId              | string 	 | 	否           |	    			    | 节点txId                        |
| rootTxId          | string 	 | 	否      	 |	    			    | 根节点txId			|
| rootAddress       | string 	 | 	否      	 |	    			    | 根节点地址			|
| rootPublicKey     | string 	 | 	否      	 |	    			    | 根节点公钥			|

请求响应实例 	

```javascript
api请求数据: 
    https://api.showmoney.app/showMANDB/api/v1/metanet/getRoot/9f0fa21bfe7706fe51decd468069cd8610d7ceb1a1265f2e17559b75d95cc93c
    
响应数据：
 {
  "result": {
    "nodeTxId": "9f0fa21bfe7706fe51decd468069cd8610d7ceb1a1265f2e17559b75d95cc93c",
    "rootTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
    "rootAddress": "13DQH5o2WwH72ojKi2GRQAhUuEBUs4euhs",
    "rootPublicKey": "NULL"
  },
  "code": 200,
  "msg": "success",
  "time": 1588131611869,
  "error": "null"
}
```

## 获取子节点

 `/api/v1/metanet/getChildren/<txId>` 

请求参数

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId          | string 	 | 	否           |	    			    |     txId           |

响应参数

***data***

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| nodeTxId          | int64 	 | 	否           |	    			    | 节点txId              |
| nodeAddress       | string 	 | 	否      	 |	    			    | 节点地址		        |
| nodePublicKey     | string 	 | 	否      	 |	    			    | 节点公钥			    |
| parentTxId        | string 	 | 	否      	 |	    			    | 父节点txId			|
| parentAddress     | string 	 | 	否      	 |	    			    | 父节点地址			|
| parentPublicKey   | string 	 | 	否      	 |	    			    | 父节点公钥			|
| outputIndex       | int64 	 | 	否      	 |	    			    | 所在索引			    |
| blockHeight       | int64 	 | 	否      	 |	    			    | 块高			        |
| timestamp         | int64 	 | 	否      	 |	    			    | 时间戳			    |

请求响应实例	

```javascript
api请求数据: 
    https://api.showmoney.app/showMANDB/api/v1/metanet/getChildren/8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86
    
响应数据：
{
  "result": [
    {
      "nodeTxId": "c37ee0eef4a98a192c42f28d8c66d3b10bd07a4c84d6a50445c9c9674b1179ed",
      "nodeAddress": "1GimPAbPAkmexbbdWqe9fQCQpgZdGNdjy7",
      "nodePublicKey": "NULL",
      "parentTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
      "parentAddress": "13DQH5o2WwH72ojKi2GRQAhUuEBUs4euhs",
      "parentPublicKey": "",
      "outputIndex": 0,
      "blockHeight": 631827,
      "timestamp": 1588043791083
    },
    {
      "nodeTxId": "e24fd7d979e73528707ed8af267e5d453bb8cf65e5cb51a04234347e9d27c539",
      "nodeAddress": "196iPAgmCyFRtt4MsdKvtcKZDVRpMdKFMc",
      "nodePublicKey": "NULL",
      "parentTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
      "parentAddress": "13DQH5o2WwH72ojKi2GRQAhUuEBUs4euhs",
      "parentPublicKey": "",
      "outputIndex": 0,
      "blockHeight": 631827,
      "timestamp": 1588043791086
    }
  ],
  "code": 200,
  "msg": "success",
  "time": 1588226921645,
  "error": "null"
}
```

## 获取节点树

`/api/v1/metanet/getTree/<txId>`

请求参数

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId          | string 	 | 	否           |	    			    |     txId           |

********************************响应参数 ************************************************

***data***

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| txId              | string 	    | 	否           |	    			    | 节点txId                        |
| deep              | int64 	    | 	否           |	    			    | 树总层数                        |
| nodeTotal         | int64 	    | 	否           |	    			    | 树总节点数                        |
| nodeTree          | []*NodeTree 	| 	是      	 |	    			    | 树结构			|

***NodeTree***

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| nodeTxId          | int64 	 | 	否           |	    			    | 节点txId              |
| nodeAddress       | string 	 | 	否      	 |	    			    | 节点地址		        |
| nodePublicKey     | string 	 | 	否      	 |	    			    | 节点公钥			    |
| parentTxId        | string 	 | 	否      	 |	    			    | 父节点txId			|
| parentAddress     | string 	 | 	否      	 |	    			    | 父节点地址			|
| parentPublicKey   | string 	 | 	否      	 |	    			    | 父节点公钥			|
| outputIndex       | int64 	 | 	否      	 |	    			    | 所在索引			    |
| blockHeight       | int64 	 | 	否      	 |	    			    | 块高			        |
| timestamp         | int64 	 | 	否      	 |	    			    | 时间戳			    |
| isSelf            | bool 	     | 	否      	 |	    			    | 是否所查询的txId自己	|
| children          | []*NodeTree| 	是      	 |	    			    | 树结构		    	|

请求响应实例	

```javascript
api请求数据: 
    https://api.showmoney.app/showMANDB/api/v1/metanet/getTree/8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86
    
响应数据：
{
  "result": {
    "txId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
    "deep": 4,
    "nodeTotal": 5,
    "nodeTree": {
      "nodeTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
      "nodeAddress": "13DQH5o2WwH72ojKi2GRQAhUuEBUs4euhs",
      "nodePublicKey": "NULL",
      "parentTxId": "NULL",
      "parentAddress": "NULL",
      "parentPublicKey": "NULL",
      "outputIndex": 0,
      "blockHeight": 631827,
      "timestamp": 1587633554015,
      "isSelf": true,
      "children": [
        {
          "nodeTxId": "c37ee0eef4a98a192c42f28d8c66d3b10bd07a4c84d6a50445c9c9674b1179ed",
          "nodeAddress": "1GimPAbPAkmexbbdWqe9fQCQpgZdGNdjy7",
          "nodePublicKey": "NULL",
          "parentTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
          "parentAddress": "13DQH5o2WwH72ojKi2GRQAhUuEBUs4euhs",
          "parentPublicKey": "NULL",
          "outputIndex": 0,
          "blockHeight": 631827,
          "timestamp": 1587633554055,
          "isSelf": false,
          "children": [
            {
              "nodeTxId": "9f0fa21bfe7706fe51decd468069cd8610d7ceb1a1265f2e17559b75d95cc93c",
              "nodeAddress": "1KrXEiKZtri9DnndD1MVDG5e1yXA5HNChn",
              "nodePublicKey": "NULL",
              "parentTxId": "c37ee0eef4a98a192c42f28d8c66d3b10bd07a4c84d6a50445c9c9674b1179ed",
              "parentAddress": "1GimPAbPAkmexbbdWqe9fQCQpgZdGNdjy7",
              "parentPublicKey": "NULL",
              "outputIndex": 0,
              "blockHeight": 631827,
              "timestamp": 1587633554062,
              "isSelf": false,
              "children": null
            }
          ]
        },
        {
          "nodeTxId": "e24fd7d979e73528707ed8af267e5d453bb8cf65e5cb51a04234347e9d27c539",
          "nodeAddress": "196iPAgmCyFRtt4MsdKvtcKZDVRpMdKFMc",
          "nodePublicKey": "NULL",
          "parentTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
          "parentAddress": "13DQH5o2WwH72ojKi2GRQAhUuEBUs4euhs",
          "parentPublicKey": "NULL",
          "outputIndex": 0,
          "blockHeight": 631827,
          "timestamp": 1587633554058,
          "isSelf": false,
          "children": [
            {
              "nodeTxId": "f678722820b8aa8136bf6f41228d8e6f4983c7747f14b014a61df2dd2d1a41fb",
              "nodeAddress": "1J7e9Y6jTPnDoCkfFsmvzxketgDCf8Km7X",
              "nodePublicKey": "NULL",
              "parentTxId": "e24fd7d979e73528707ed8af267e5d453bb8cf65e5cb51a04234347e9d27c539",
              "parentAddress": "196iPAgmCyFRtt4MsdKvtcKZDVRpMdKFMc",
              "parentPublicKey": "NULL",
              "outputIndex": 0,
              "blockHeight": 631827,
              "timestamp": 1587633554116,
              "isSelf": false,
              "children": [
                {
                  "nodeTxId": "487aa4deecaa5eabd24d7dfb97ded646e71503b26ac9100ff411822459b28daa",
                  "nodeAddress": "12cLrusqwuq6Waryp2u5bmvZ6jskYAnb2W",
                  "nodePublicKey": "NULL",
                  "parentTxId": "f678722820b8aa8136bf6f41228d8e6f4983c7747f14b014a61df2dd2d1a41fb",
                  "parentAddress": "1J7e9Y6jTPnDoCkfFsmvzxketgDCf8Km7X",
                  "parentPublicKey": "NULL",
                  "outputIndex": 0,
                  "blockHeight": 631827,
                  "timestamp": 1587633554120,
                  "isSelf": false,
                  "children": null
                }
              ]
            }
          ]
        }
      ]
    }
  },
  "code": 200,
  "msg": "success",
  "time": 1590031505103,
  "error": "null"
}
```

## 根据address获取节点

 `/api/v1/metanet/getMetaNodeByAddress/<address>`  

请求参数

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| address          | string 	 | 	否           |	    			    |     txId           |

响应参数

***data***

|	参数名称     |	类型	 |	是否可空     |	长度限制			|	描述				            |
|----------------|-----------|---------------|----------------------|-----------------------------------|
| nodeTxId          | int64 	 | 	否           |	    			    | 节点txId              |
| nodeAddress       | string 	 | 	否      	 |	    			    | 节点地址		        |
| nodePublicKey     | string 	 | 	否      	 |	    			    | 节点公钥			    |
| parentTxId        | string 	 | 	否      	 |	    			    | 父节点txId			|
| parentAddress     | string 	 | 	否      	 |	    			    | 父节点地址			|
| parentPublicKey   | string 	 | 	否      	 |	    			    | 父节点公钥			|
| outputIndex       | int64 	 | 	否      	 |	    			    | 所在索引			    |
| blockHeight       | int64 	 | 	否      	 |	    			    | 块高			        |
| timestamp         | int64 	 | 	否      	 |	    			    | 时间戳			    |

请求响应实例

```javascript
api请求数据: 
    https://api.showmoney.app/showMANDB/api/v1/metanet/getMetaNodeByAddress/1GimPAbPAkmexbbdWqe9fQCQpgZdGNdjy7
    
响应数据：
{
  "result": [
    {
      "nodeTxId": "c37ee0eef4a98a192c42f28d8c66d3b10bd07a4c84d6a50445c9c9674b1179ed",
      "nodeAddress": "1GimPAbPAkmexbbdWqe9fQCQpgZdGNdjy7",
      "nodePublicKey": "NULL",
      "parentTxId": "8e9b396eb52752c95cfd45b86f9aa90e07e804ac38ff7f7f87669b0af2f06c86",
      "parentAddress": "NULL",
      "parentPublicKey": "NULL",
      "outputIndex": 0,
      "blockHeight": 631827,
      "rootTxId": "",
      "rootAddress": "",
      "rootPublicKey": "",
      "timestamp": 1588043791083
    },
    {
      "nodeTxId": "a5c05146de8fa49d8641cf34ae556c982048cd74a22731285dd744a48b5ed400",
      "nodeAddress": "1GimPAbPAkmexbbdWqe9fQCQpgZdGNdjy7",
      "nodePublicKey": "021a50ef584fa34b6d4067cd8457d38e8e20c9550b0cdc4fd7f00b2d67177128d6",
      "parentTxId": "57fab4aab7af94f7ed885cfc32ff6b15a4d90d400dea652f85390b4bec7b1051",
      "parentAddress": "NULL",
      "parentPublicKey": "NULL",
      "outputIndex": 0,
      "blockHeight": 632379,
      "rootTxId": "",
      "rootAddress": "",
      "rootPublicKey": "",
      "timestamp": 1588044715641
    }
  ],
  "code": 200,
  "msg": "success",
  "time": 1588254263493,
  "error": "null"
}
```

