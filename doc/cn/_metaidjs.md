# MetaID

MetaID npm插件，方便开发者导入安装，操作和用户相关的MetaID信息

<aside class="notice">
需要先完成oauth2.0认证
</aside>
## Setup

npm 安装 MetaID

```shell
$ npm install --save metaidjs
```

## Usage

导入对应的包 metaidjs，实例化对象

```javascript
// 导入对应的包
import MetaIdJs from "metaidjs"
```

```javascript
// 实例化对象
const metaIdJs = new MetaIdJs({
  oauthSettings: {
    clientId: CLIENT_ID,
    redirectUri: REDIRECT_URI
  },
  onLoaded: () => {
  },
  onError: (res) => {
    console.log(res)
  }
})

```

实例化参数说明

| 参数        | 必须 | 类型   | 默认值 | 描述 |
| ----------- | ---- | ------ | ---- | ---- |
| oauthSettings | 是   | Object |      | Oauth2.0登录信息，包含 clientId 和 redirectUri 内容 |
| onLoaded | 否   | Function |      | 脚本加载完成的回调函数  |
| onError | 否   | Function |      | 通用错误回调函数，用于自定义处理不同的错误类型  |

基本响应参数格式说明

| 参数        | 必须 | 类型   | 默认值 | 描述 |
| ----------- | ---- | ------ | ---- | ---- |
| code | 是   | number |      | 响应结果代码：<br> 200:  操作成功 <br> 201: 用户认证失败  <br> 202: 用户认证已经过期 <br> 204: 通用错误   |
| status | 是   | string |      |   |
| data | 是   | Object |      | 实际响应内容，如果是错误响应，里面会包含错误信息 message  |


## Methods
### getUserInfo()

获取用户metaid-info信息



```javascript
metaIdJs.getUserInfo({
  accessToken: ACCESS_TOKEN,
  callback: (res) => {
  }
})
```


调用参数说明

| 参数        | 必须 | 类型   | 默认值 | 描述 |
| ----------- | ---- | ------ | ---- | ---- |
| accessToken | 是   | string |      |    |
| callback | 否   | Function |      | 回调函数  |

```javascript
// 返回
{
  code: 200,
  status: 'success',
  data: {
    address: "14ZAj2BpLSB1nSd24TXUhu3jX1X42R89d9"
    email: ""
    emailEncrypt: ""
    headUrl: ""
    headUrlEncrypt: "0"
    infoTxId: "e3d3fc6392cb61e99168598dd7ebb1c8043aeed4170186ceccb181a79fdbc200"
    name: "秀"
    nameEncrypt: "0"
    phone: "13712345671"
    phoneEncrypt: "1"
    protocolTxId: "64c7b76a82b070042c817a55b897b133a87afa067ded0081f1173f0197a9a82f"
    showId: "0a9d30a38c44aba79b2d023d667ca4558350727eb0b71efdff6aa6695200f78f"
    timestamp: 1589185608226
    xpub: "xpub6CuZbuP1UX7VyA8NBXQdhQr93h5Eerr8RNGi2DfjyPTukqmNbYB"
  }
}
```

### addProtocolNode()

发起Protocols node操作

```javascript
// 生成Protocols node
metaIdJs.addProtocolNode({
  accessToken: ACCESS_TOKEN,
  nodeName: 'ShowText',
  brfcId: 'a851d46702dc',
  data: JSON.stringify({
    "title": "test title",
    "content": 'test content',
    "contentType": "text/plain",
  }),
  dataType: 'application/json',
  callback: (res) => {
  }
})
```

调用参数说明

| 参数        | 必须 | 类型   | 默认值 | 描述 |
| ----------- | ---- | ------ | ---- | ---- |
| accessToken | 是   | string |      |    |
| nodeName | 是   | string |      | 对应metaID node_name   |
| data | 是   | string |      |  对应metaID data  |
| encrypt | 是   | number |   0   | 对应metaID encryp   |
| version | 是   | string |   0.0.9   |  对应metaID version  |
| dataType | 是   | string |   text/plain   |  对应metaID data_type  |
| encoding | 是   | string |  UTF-8   |  对应metaID encoding  |
| isFirstProtocolChild | 是   | boolean |  true    | 是否是第一层protocols子节点   |
| brfcId | 否   | string |      | 如果是第一层protocols子节点需要带上brfc，将忽略data字段   |
| path | 否   | string |      | 如果不是第一层protocols子节点, 需要带上完整路径 比如/Protocols/ShowBuzz 将在这个节点下创建Node   |
| payTo | 否   | Array |      | 同时向指定地址转账，交易输出格式为 [{address: 'XXXXXXXXXX', amount: 1000}], 单位是聪   |
| callback | 否   | Function |      | 回调函数  |

```javascript
// 回调响应
{
  code: 200,
  status: 'success',
  data: {
  }
}
```

