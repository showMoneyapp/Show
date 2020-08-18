# query查询

### query查询 接口

`/api/v1/query/queryFindMetaData/<content>` 

请求参数


| 参数名称 | 类型                 | 是否可空 | 长度限制 | 描述                                 |
| -------- | -------------------- | -------- | -------- | ------------------------------------ |
| find     | map[string]interface | 否       |          | 查询条件                             |
| skip     | int64                | 是       |          | 数据偏移量                           |
| limit    | int64                | 是       |          | 数据限制量，**默认10，负数为无限制** |
| sort     | map[string]int       | 是       |          | 排序，-1为倒序，1为顺序              |
| format   | map[string]string    | 是       |          | 返回格式                             |

响应参数

***data***

| 参数名称 | 类型                | 是否可空 | 长度限制 | 描述     |
| -------- | ------------------- | -------- | -------- | -------- |
| page     | int64               | 否       |          | 当前页数 |
| pageSize | int64               | 否       |          | 页容量   |
| total    | int64               | 否       |          | 数据总量 |
| data     | []map[string]string | 否       |          | 数据     |

***ShowMetaData***

| 参数名称    | 类型         | 是否可空 | 长度限制 | 描述             |
| ----------- | ------------ | -------- | -------- | ---------------- |
| metanetId   | string       | 否       |          | metanet ID       |
| rootTxId    | string       | 否       |          | 所属顶点TxId     |
| txId        | string       | 否       |          | 交易id           |
| vouts       | []*MetaTxOut | 否       |          | vouts            |
| parts       | []string     | 是       |          | metanet 的数据   |
| address     | string       | 是       |          | address          |
| publicKey   | string       | 是       |          | publicKey        |
| parentTxTd  | string       | 否       |          | 父txId           |
| metaId      | string       | 否       |          | metaId tag       |
| nodeName    | string       | 否       |          | 协议名称         |
| data        | interface    | 否       |          | 数据             |
| encrypt     | string       | 否       |          | 加密方式         |
| version     | string       | 否       |          | 版本             |
| dataType    | string       | 否       |          | 数据类型         |
| encoding    | string       | 否       |          | 编码格式         |
| blockHeight | int64        | 否       |          | 所在块高         |
| timestamp   | int64        | 否       |          | 时间戳           |
| isValid     | bool         | 否       |          | 是否有效         |
| isNew       | bool         | 否       |          | 是否最新         |
| fee         | uint64       | 否       |          | 该meta数据的费用 |

***MetaTxOut***

| 参数名称     | 类型   | 是否可空 | 长度限制 | 描述   |
| ------------ | ------ | -------- | -------- | ------ |
| txId         | string | 否       |          | 交易id |
| index        | uint64 | 否       |          | 索引   |
| address      | string | 是       |          | 地址   |
| value        | uint64 | 否       |          | 金额   |
| scriptPubKey | string | 否       |          | 脚本   |
| type         | string | 否       |          | 类型   |

api请求数据: 
将全球json `{"find":{"data.content":"这是一个测试内容"}, "skip":0, "limit":1} `经过Base64编码之后作为参数请求。

```json
  https://api.showmoney.app/showMANDB/api/v1/query/queryFindMetaData/eyJmaW5kIjp7ImRhdGEuY29udGVudCI6Iui_meaYr-S4gOS4qua1i-ivleWGheWuuSJ9LCAic2tpcCI6MCwgImxpbWl0IjowfQ==
```

```
// 返回结果
{
  "result": {
    "page": 0,
    "pageSize": 0,
    "total": 2,
    "data": [
      {
        "metanetId": "",
        "txId": "487aa4deecaa5eabd24d7dfb97ded646e71503b26ac9100ff411822459b28daa",
        "vouts": [
          {
            "txId": "487aa4deecaa5eabd24d7dfb97ded646e71503b26ac9100ff411822459b28daa",
            "index": 0,
            "address": "",
            "value": 0,
            "scriptPubKey": "006a046d657461223132634c72757371777571365761727970327535626d765a366a736b59416e6232574066363738373232383230623861613831333662663666343132323864386536663439383363373734376631346230313461363164663264643264316134316662064d6574614944223132634c72757371777571365761727970327535626d765a366a736b59416e623257417b22636f6e74656e74223a22e8bf99e698afe4b880e4b8aae6b58be8af95e58685e5aeb9222c2263726561746554696d65223a313538373631303632323132337d013004302e30390a746578742f706c61696e055554462d38",
            "type": "NullData"
          },
          {
            "txId": "487aa4deecaa5eabd24d7dfb97ded646e71503b26ac9100ff411822459b28daa",
            "index": 1,
            "address": "1J7e9Y6jTPnDoCkfFsmvzxketgDCf8Km7X",
            "value": 2183,
            "scriptPubKey": "76a914bbbba49b5ba95f9fcbf1f2a1b325999fc357963f88ac",
            "type": "P2PKH"
          }
        ],
        "parts": [
          "OP_0",
          "OP_RETURN",
          "meta",
          "12cLrusqwuq6Waryp2u5bmvZ6jskYAnb2W",
          "f678722820b8aa8136bf6f41228d8e6f4983c7747f14b014a61df2dd2d1a41fb",
          "MetaID",
          "12cLrusqwuq6Waryp2u5bmvZ6jskYAnb2W",
          "{\"content\":\"这是一个测试内容\",\"createTime\":1587610622123}",
          "0",
          "0.09",
          "text/plain",
          "UTF-8"
        ],
        "address": "12cLrusqwuq6Waryp2u5bmvZ6jskYAnb2W",
        "publicKey": "NULL",
        "parentTxTd": "f678722820b8aa8136bf6f41228d8e6f4983c7747f14b014a61df2dd2d1a41fb",
        "metaId": "MetaID",
        "nodeName": "12cLrusqwuq6Waryp2u5bmvZ6jskYAnb2W",
        "data": {
          "content": "这是一个测试内容",
          "createTime": 1587610622123
        },
        "encrypt": "0",
        "version": "0.09",
        "dataType": "text/plain",
        "encoding": "UTF-8",
        "blockHeight": 631827,
        "timestamp": 1587633554
      },
      {
        "metanetId": "53d2a9e3437b45933a3a37ffb81d23a81724d50649aea0afc8ff3c30a34fad84",
        "txId": "87b06ecfa3783a41c34235c1846b9f6daee773be7d74d65e482f6805b43b7422",
        "vouts": [
          {
            "txId": "87b06ecfa3783a41c34235c1846b9f6daee773be7d74d65e482f6805b43b7422",
            "index": 0,
            "address": "",
            "value": 0,
            "scriptPubKey": "006a046d657461423033666230316131363533396639613635633265303865353439616134393862643238623133373032613434653762663931313865623366646235633132653630374065393935626265623734646130353839303065396665633432653164336265343636383962376235656530633338393963343833613932323933323361663962064d657461494442303366623031613136353339663961363563326530386535343961613439386264323862313337303261343465376266393131386562336664623563313265363037417b22636f6e74656e74223a22e8bf99e698afe4b880e4b8aae6b58be8af95e58685e5aeb9222c2263726561746554696d65223a313538373631303632323132337d013004302e30390a746578742f706c61696e055554462d38",
            "type": "NullData"
          },
          {
            "txId": "87b06ecfa3783a41c34235c1846b9f6daee773be7d74d65e482f6805b43b7422",
            "index": 1,
            "address": "1J7e9Y6jTPnDoCkfFsmvzxketgDCf8Km7X",
            "value": 1677,
            "scriptPubKey": "76a914bbbba49b5ba95f9fcbf1f2a1b325999fc357963f88ac",
            "type": "P2PKH"
          }
        ],
        "parts": [
          "OP_0",
          "OP_RETURN",
          "meta",
          "03fb01a16539f9a65c2e08e549aa498bd28b13702a44e7bf9118eb3fdb5c12e607",
          "e995bbeb74da058900e9fec42e1d3be46689b7b5ee0c3899c483a9229323af9b",
          "MetaID",
          "03fb01a16539f9a65c2e08e549aa498bd28b13702a44e7bf9118eb3fdb5c12e607",
          "{\"content\":\"这是一个测试内容\",\"createTime\":1587610622123}",
          "0",
          "0.09",
          "text/plain",
          "UTF-8"
        ],
        "address": "12cLrusqwuq6Waryp2u5bmvZ6jskYAnb2W",
        "publicKey": "03fb01a16539f9a65c2e08e549aa498bd28b13702a44e7bf9118eb3fdb5c12e607",
        "parentTxTd": "e995bbeb74da058900e9fec42e1d3be46689b7b5ee0c3899c483a9229323af9b",
        "metaId": "MetaID",
        "nodeName": "03fb01a16539f9a65c2e08e549aa498bd28b13702a44e7bf9118eb3fdb5c12e607",
        "data": {
          "content": "这是一个测试内容",
          "createTime": 1587610622123
        },
        "encrypt": "0",
        "version": "0.09",
        "dataType": "text/plain",
        "encoding": "UTF-8",
        "blockHeight": 632379,
        "timestamp": 1587951949
      }
    ]
  },
  "code": 200,
  "msg": "success",
  "time": 1589189378703,
  "error": "null"
}
```

### 路径解析

路径是一系列被.分隔的key拼接而成.
路径可能包含通配符'*'和'?'.
通过下标访问数组值.
通过'#'来获取值在元素中的排位或访问子路径.
.和通配符可以通过'\'来转义.
你同样能通过#[...]来查询数组中的第一个匹配的项, 或通过'#[...]#'查询所有匹配的项.
查询支持==, !=, <, <=, >, >=比较运算符和'%'模糊匹配.



例如 请求数据: 

```json
{"find":{"metaId":"TestShowID","nodeName":"ShowText"}, "skip":0, "limit":0, "format":{"myTag":"metaId","have":"data","myIn":"data.content","h":"blockHeight", "t":"timestamp" ,"address of out":"vouts.0.address"}}
```

```
https://api.showmoney.app/showMANDB/api/v1/query/queryFindMetaData/eyJmaW5kIjp7Im1ldGFJZCI6IlRlc3RTaG93SUQiLCJub2RlTmFtZSI6IlNob3dUZXh0In0sICJza2lwIjowLCAibGltaXQiOjAsICJmb3JtYXQiOnsibXlUYWciOiJtZXRhSWQiLCJoYXZlIjoiZGF0YSIsIm15SW4iOiJkYXRhLmNvbnRlbnQiLCJoIjoiYmxvY2tIZWlnaHQiLCAidCI6InRpbWVzdGFtcCIgLCJhZGRyZXNzIG9mIG91dCI6InZvdXRzLjAuYWRkcmVzcyJ9fQ==
```

```
// 响应数据：
{
  "result": {
    "page": 0,
    "pageSize": 0,
    "total": 10,
    "data": [
      {
        "address of out": "15b5g9trRPpCBygtyFqXFWxwmH1iksV8tE",
        "h": "631962",
        "have": "000000000000",
        "myIn": "",
        "myTag": "TestShowID",
        "t": 1587713749118
      },
      {
        "address of out": "1HyBrokj77qS5dDQTTAXi14KTBhVJp8TT1",
        "h": "632243",
        "have": "000000000000",
        "myIn": "",
        "myTag": "TestShowID",
        "t": 1587874038054
      },
      {
        "address of out": "1AfeGEqwfg2e6jXCtq66LHprhZdN2YUSja",
        "h": "632383",
        "have": "{"content":"ShowText test data"}",
        "myIn": "ShowText test data",
        "myTag": "TestShowID",
        "t": 1587957048472
      },
      {
        "address of out": "1HqFY514e4BHJWhoLQSAYt8PApyt6S3iuX",
        "h": "632406",
        "have": "000000000001",
        "myIn": "",
        "myTag": "TestShowID",
        "t": 1587986958930
      },
      {
        "address of out": "1AESm8paj4uUYTqyPEsjSM1w3bfWRFRfw1",
        "h": "632406",
        "have": "{"content":"ShowText test data"}",
        "myIn": "ShowText test data",
        "myTag": "TestShowID",
        "t": 1587986959013
      },
      ...
    ]
  },
  "code": 200,
  "msg": "success",
  "time": 1590030882788,
  "error": "null"
}
```
