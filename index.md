<!-- vscode-markdown-toc -->
* 1. [请求方式](#请求方式)
* 2. [安全要求](#安全要求)
* 3. [授权机制](#授权机制)
  * 3.1. [client 端](#client-端)
  * 3.2. [server 端](#server-端)
  * 3.3. [举例](#举例)
* 4. [请求格式](#请求格式)
* 5. [签名过程](#签名过程)
* 6. [请求代码示例](#请求代码示例)
* 7. [返回格式](#返回格式)
* 8. [错误码说明](#错误码说明)
* 9. [接口定义](#接口定义)
  * 9.1. [用户主账户](#用户主账户)
    * 9.1.1. [创建主账户](#创建主账户)
    * 9.1.2. [获取账户绑定信息](#获取账户绑定信息)
    * 9.1.3. [修改账户绑定手机号](#修改账户绑定手机号)
    * 9.1.4. [修改账户绑定邮箱](#修改账户绑定邮箱)
    * 9.1.5. [修改账户密码](#修改账户密码)
    * 9.1.6. [检测账户密码](#检测账户密码)
    * 9.1.7. [根据手机号查找用户名](#根据手机号查找用户名)
    * 9.1.8. [根据邮箱查找用户名](#根据邮箱查找用户名)
  * 9.2. [用户子账户](#用户子账户)
    * 9.2.1. [获取用户账户下所有的子账户名](#获取用户账户下所有的子账户名)
    * 9.2.2. [批量获取子账户基本信息](#批量获取子账户基本信息)
    * 9.2.3. [创建子账户](#创建子账户)
    * 9.2.4. [批量获取子账户的费率信息](#批量获取子账户的费率信息)
    * 9.2.5. [修改子账户费率信息](#修改子账户费率信息)
    * 9.2.6. [获取子账户的收款设置信息](#获取子账户的收款设置信息)
    * 9.2.7. [设置子账户收款设置](#设置子账户收款设置)
    * 9.2.8. [获取子账户的人民币收款设置信息](#获取子账户的人民币收款设置信息)
    * 9.2.9. [设置子账户人民币收款设置](#设置子账户人民币收款设置)
    * 9.2.10. [获取子账户挖矿收益自动兑换人民币设置信息](#获取子账户挖矿收益自动兑换人民币设置信息)
    * 9.2.11. [设置子账户挖矿收益自动兑换人民币设置信息](#设置子账户挖矿收益自动兑换人民币设置信息)
    * 9.2.12. [获取子账户观察者链接信息](#获取子账户观察者链接信息)
    * 9.2.13. [添加子账户观察者链接信息](#添加子账户观察者链接信息)
    * 9.2.14. [修改子账户观察者链接信息](#修改子账户观察者链接信息)
    * 9.2.15. [删除子账户观察者链接信息](#删除子账户观察者链接信息)
  * 9.3. [收益](#收益)
    * 9.3.1. [获取子账户的收益汇总信息](#获取子账户的收益汇总信息)
    * 9.3.2. [获取账户全部子账户的收益汇总信息](#获取账户全部子账户的收益汇总信息)
    * 9.3.3. [获取子账户的出账信息](#获取子账户的出账信息)
  * 9.4. [算力](#算力)
    * 9.4.1. [获取子账户的日算力信息](#获取子账户的日算力信息)
    * 9.4.2. [获取子账户的小时算力信息](#获取子账户的小时算力信息)
    * 9.4.3. [获取子账户的实时算力信息](#获取子账户的实时算力信息)
    * 9.4.4. [获取矿机的日算力信息](#获取矿机的日算力信息)
    * 9.4.5. [获取矿机的小时算力信息](#获取矿机的小时算力信息)
    * 9.4.6. [批量获取子账号下所有矿机的小时算力信息](#批量获取子账号下所有矿机的小时算力信息)
    * 9.4.7. [获取系统的日算力信息(最近 30 天)](#获取系统的日算力信息(最近-30-天))
    * 9.4.8. [获取系统的小时算力信息(最近 24 小时)](#获取系统的小时算力信息(最近-24-小时))
    * 9.4.9. [获取系统的实时算力信息](#获取系统的实时算力信息)
  * 9.5. [矿机](#矿机)
    * 9.5.1. [获取用户矿机详细信息](#获取用户矿机详细信息)
    * 9.5.2. [获取用户矿机汇总信息](#获取用户矿机汇总信息)
    * 9.5.3. [获取用户矿机分组信息](#获取用户矿机分组信息)
    * 9.5.4. [创建矿机分组](#创建矿机分组)
    * 9.5.5. [修改矿机分组](#修改矿机分组)
    * 9.5.6. [删除矿机分组](#删除矿机分组)
    * 9.5.7. [批量设置矿机所属分组](#批量设置矿机所属分组)
    * 9.5.8. [获取子账户所属矿机的在线情况](#获取子账户所属矿机的在线情况)

<!-- vscode-markdown-toc-config
	numbering=true
	autoSave=true
	/vscode-markdown-toc-config -->
<!-- /vscode-markdown-toc -->
##  1. <a name='请求方式'></a>请求方式

统一使用 HTTP 请求（基于 HTTP1.0/1.1 标准）的 POST 方法。

##  2. <a name='安全要求'></a>安全要求

如果在公网则请求及响应数据采用 HTTPS 加密传输，内网可以使用 HTTP。

##  3. <a name='授权机制'></a>授权机制

###  3.1. <a name='client-端'></a>client 端

在 HTTP header 中添加 Authorization 字段，其值为根据颁发的 clientId 和 secretKey 生成的 jwt token 值。
其中 jwt token 的 playload 格式为：

| 字段     | 类型           | 描述                                                                                                        |
| -------- | -------------- | ----------------------------------------------------------------------------------------------------------- |
| clientId | string         | 从授权处获取的 clientId 编号                                                                                |
| rnd      | number         | 为了防止重放攻击使用的随机数，不得小于 8 位                                                                 |
| exp      | unix timestamp | 该 jwt token 的过期时间时间戳，建议比当前时间大 3 到 5 分钟，如果对安全要求高的可以缩小范围，不建议太大了。 |

###  3.2. <a name='server-端'></a>server 端

验证 client 端发送的 HTTP 请求中 header 里面的 Authorization 字段内容是否为合法授权的 jwt token。

###  3.3. <a name='举例'></a>举例

client 端发送一个请求给 server，并在其 http header 中加上有效的 jwt token：

```javascript
const _ = require('lodash');
const jwt = require('jsonwebtoken');
const request = require('request-promise-native');

const url = 'http://service_url'; // server端api的URL地址
const clientId = 'xxxxxxxxx';     // 授权处颁发的clientId
const secretKey = 'xxxxx';        // 授权处颁发的secretKey，注意保密

const random = _.random(1000000000, 9999999999);    // 随机数
const exp = Date.now() / 1000 + 180;                 // 有效期180秒
const playload = { clientId: clientId, rnd: random, exp: exp };    // jwt token的playload内容

const parameters = {...}; // 接口请求参数内容

const token = jwt.sign(playload, secretKey);    // 产生授权jwt token

request.post(url, {
    headers: { Authorization: token },         // 在client的http header中设置Authorization字段，其值为前面产生的jwt token
    body: parameters,
    json: true,
}).then(function (resp) {
    // 结果处理
});

```

##  4. <a name='请求格式'></a>请求格式

数据采用 JSON 格式，请注意在 HTTP 请求的 header 中设置：`Content-Type: application/json`。
为了提高安全性，需对请求内容进行数字签名，请求内容格式如下：

| 字段      | 类型          | 描述                                         |
| --------- | ------------- | -------------------------------------------- |
| action    | string        | 执行操作名，具体见后面接口列表中的接口操作名 |
| at        | unixTimestamp | 请求的时间戳                                 |
| data      | string        | 请求参数内容的 JSON 字符串                   |
| signNonce | string        | 签名唯一随机数                               |
| sign      | string        | 请求的签名，签名过程见后面文档               |

##  5. <a name='签名过程'></a>签名过程

1. 生成需要签名的字符串：
   将请求内容按照 `action` `at` `data` `signNonce` 的顺序拼接起来，并在末尾在拼上授权处颁发的`secretSalt`。

2. 生成签名：
   对需要签名的字符串进行 HMAC-SHA256 签名得到的 hex 编码的字符串。

##  6. <a name='请求代码示例'></a>请求代码示例

```javascript
const crypto = require('crypto');
const _ = require('lodash');
const jwt = require('jsonwebtoken');
const request = require('request-promise-native');

const url = 'http://service_url'; // server端api的URL地址
const clientId = 'xxxxxxxxx';     // 授权处颁发的clientId
const secretKey = 'xxxxx';  // 授权处颁发的secretKey，注意保密
const secretSalt = 'xxxxx'; // 授权处颁发的secretSalt，注意保密

const random = _.random(1000000000, 9999999999);    // 随机数
const exp = Date.now() / 1000 + 180;                 // 有效期180秒
const playload = { clientId: clientId, rnd: random, exp: exp };    // jwt token的playload内容

const parameters = {...}; // 接口请求参数内容

const token = jwt.sign(playload, secretKey);    // 产生授权jwt token

const action = 'action-xxx';
const at = Date.now() / 1000;
const data = JSON.stringify(parameters);
const signNonce = _.random(1000000000, 9999999999).toString(); // 随机数;

const needSignContent = action + at.toString() + data + signNonce + secretSalt;
const sign = crypto.createHmac('sha256', secretKey).update(needSignContent).digest('hex'); // 生成签名

request.post(url, {
    headers: { Authorization: token },         // 在client的http header中设置Authorization字段，其值为前面产生的jwt token
    body: {
      action,
      at,
      data,
      signNonce,
      sign
    },
    json: true,
}).then(function (resp) {
    // 结果处理
});

```

##  7. <a name='返回格式'></a>返回格式

返回内容统一为 JSON 格式，包括的字段如下：

| 字段    | 类型   | 描述                                                   |
| ------- | ------ | ------------------------------------------------------ |
| code    | int    | 执行结果错误码，如果执行成功，为 0，否则为对应的错误码 |
| data    | any    | 接口返回数据内容                                       |
| message | string | 错误信息                                               |

##  8. <a name='错误码说明'></a>错误码说明

错误码对照表如下：

| 值   | 描述             |
| ---- | ---------------- |
| 0    | 执行成功         |
| 5010 | 输入内容无效     |
| 5020 | 用户身份验证失败 |
| 5030 | 操作失败         |
| 5040 | 权限不足         |
| 5050 | 系统错误         |

##  9. <a name='接口定义'></a>接口定义

###  9.1. <a name='用户主账户'></a>用户主账户

####  9.1.1. <a name='创建主账户'></a>创建主账户

**action:** Account.Create

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| account  | 是       | string | 用户主账户名 |
| phone    | 否       | string | 用户手机号   |
| mail     | 否       | string | 用户邮箱     |
| password | 是       | string | 用户密码     |

注意：phone 和 mail 两项有一项不能为空。

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.1.2. <a name='获取账户绑定信息'></a>获取账户绑定信息

**action:** Account.GetBindInfo

**参数:**

| 字段    | 是否必须 | 类型   | 描述         |
| ------- | -------- | ------ | ------------ |
| account | 是       | string | 用户主账户名 |

**返回值:**

| 字段 | 类型   | 描述           |
| ---- | ------ | -------------- |
| data | object | 主账户绑定信息 |

**主账户绑定信息:**

| 字段  | 类型   | 描述                                                 |
| ----- | ------ | ---------------------------------------------------- |
| phone | string | 用户绑定的手机号，在用户只绑定了邮箱的情况下可能为空 |
| mail  | string | 用户绑定的邮箱，在用户只绑定了手机的可能为空         |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": {
    "phone": "13811012345",
    "mail": "hello@gmail.com"
  }
}
```

####  9.1.3. <a name='修改账户绑定手机号'></a>修改账户绑定手机号

**action:** Account.UpdatePhone

**参数:**

| 字段    | 是否必须 | 类型   | 描述         |
| ------- | -------- | ------ | ------------ |
| account | 是       | string | 用户主账户名 |
| phone   | 是       | string | 用户手机号   |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.1.4. <a name='修改账户绑定邮箱'></a>修改账户绑定邮箱

**action:** Account.UpdateMail

**参数:**

| 字段    | 是否必须 | 类型   | 描述         |
| ------- | -------- | ------ | ------------ |
| account | 是       | string | 用户主账户名 |
| mail    | 是       | string | 用户邮箱     |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.1.5. <a name='修改账户密码'></a>修改账户密码

**action:** Account.UpdatePassword

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| account  | 是       | string | 用户主账户名 |
| password | 是       | string | 用户密码     |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.1.6. <a name='检测账户密码'></a>检测账户密码

**action:** Account.CheckPassword

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| account  | 是       | string | 用户主账户名 |
| password | 是       | string | 用户密码     |

**返回值:**

| 字段 | 类型 | 描述         |
| ---- | ---- | ------------ |
| data | bool | 密码是否正确 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": false
}
```

####  9.1.7. <a name='根据手机号查找用户名'></a>根据手机号查找用户名

**action:** Account.QueryUserNameByPhone

**参数:**

| 字段  | 是否必须 | 类型   | 描述       |
| ----- | -------- | ------ | ---------- |
| phone | 是       | string | 用户手机号 |

**返回值:**

| 字段 | 类型     | 描述       |
| ---- | -------- | ---------- |
| data | string[] | 用户名数组 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": ["username1", "username2"]
}
```

####  9.1.8. <a name='根据邮箱查找用户名'></a>根据邮箱查找用户名

**action:** Account.QueryUserNameByMail

**参数:**

| 字段 | 是否必须 | 类型   | 描述     |
| ---- | -------- | ------ | -------- |
| mail | 是       | string | 用户邮箱 |

**返回值:**

| 字段 | 类型     | 描述       |
| ---- | -------- | ---------- |
| data | string[] | 用户名数组 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": ["username1", "username2"]
}
```

###  9.2. <a name='用户子账户'></a>用户子账户

####  9.2.1. <a name='获取用户账户下所有的子账户名'></a>获取用户账户下所有的子账户名

**action:** SubAccount.GetUserAll

**参数:**

| 字段    | 是否必须 | 类型   | 描述         |
| ------- | -------- | ------ | ------------ |
| account | 是       | string | 用户主账户名 |

**返回值:**

| 字段 | 类型     | 描述         |
| ---- | -------- | ------------ |
| data | string[] | 子账户名数组 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": ["username1", "username2"]
}
```

####  9.2.2. <a name='批量获取子账户基本信息'></a>批量获取子账户基本信息

**action:** SubAccount.BulkGetBasicInfo

**参数:**

| 字段      | 是否必须 | 类型     | 描述             |
| --------- | -------- | -------- | ---------------- |
| userNames | 是       | string[] | 用户子账户名数组 |

**返回值:**

| 字段 | 类型  | 描述               |
| ---- | ----- | ------------------ |
| data | array | 子账户基本信息数组 |

**子账户基本信息:**

| 字段        | 类型   | 描述              |
| ----------- | ------ | ----------------- |
| userName    | string | 用户名            |
| theorySpeed | double | 额定算力，单位：P |
| description | string | 提示名            |
| workerCount | int    | 理论矿机数量      |
| master      | string | 主账户名          |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "userName": "username1",
      "theorySpeed": 0.1,
      "workerCount": 10,
      "description": "四川",
      "master": "username1"
    },
    {
      "userName": "username2",
      "theorySpeed": 0.11,
      "workerCount": 12,
      "description": "四川1",
      "master": "username1"
    }
  ]
}
```

####  9.2.3. <a name='创建子账户'></a>创建子账户

**action:** SubAccount.Create

**参数:**

| 字段        | 是否必须 | 类型   | 描述              |
| ----------- | -------- | ------ | ----------------- |
| master      | 是       | string | 用户主账户名      |
| userName    | 是       | string | 用户子账户名      |
| theorySpeed | 否       | double | 额定算力，单位：P |
| description | 否       | string | 提示名            |
| workerCount | 否       | int    | 理论矿机数量      |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.2.4. <a name='批量获取子账户的费率信息'></a>批量获取子账户的费率信息

**action:** SubAccount.BulkGetFeeInfo

**参数:**

| 字段      | 是否必须 | 类型     | 描述             |
| --------- | -------- | -------- | ---------------- |
| userNames | 是       | string[] | 用户子账户名数组 |

**返回值:**

| 字段 | 类型  | 描述               |
| ---- | ----- | ------------------ |
| data | array | 子账户费率信息数组 |

**子账户费率信息数组:**

| 字段          | 类型   | 描述                  |
| ------------- | ------ | --------------------- |
| userName      | string | 用户名                |
| feeType       | string | 费率类型：PPS 或 FPPS |
| fee           | double | 费率                  |
| refer         | string | 推荐人用户名          |
| commission    | double | 推荐人费率            |
| bchPpsFee     | double | BCH 收益的 PPS 费率   |
| bchCommission | double | 推荐人 BCH 费率       |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "userName": "username1",
      "feeType": "FPPS",
      "fee": 0.01,
      "bchPpsFee": 0.01,
      "commission": 0.01,
      "bchCommission": 0.01,
      "refer": "username110"
    },
    {
      "userName": "username2",
      "feeType": "FPPS",
      "fee": 0.01,
      "bchPpsFee": 0.01,
      "commission": 0.01,
      "bchCommission": 0.01,
      "refer": "username110"
    }
  ]
}
```

####  9.2.5. <a name='修改子账户费率信息'></a>修改子账户费率信息

**action:** SubAccount.UpdateFeeInfo

**参数:**

| 字段          | 是否必须 | 类型   | 描述                  |
| ------------- | -------- | ------ | --------------------- |
| userName      | 是       | string | 用户子账户名          |
| feeType       | 否       | string | 费率类型：PPS 或 FPPS |
| fee           | 否       | double | 费率                  |
| refer         | 否       | string | 推荐人用户名          |
| commission    | 否       | double | 推荐人费率            |
| bchPpsFee     | 否       | double | BCH 收益的 PPS 费率   |
| bchCommission | 否       | double | 推荐人 BCH 费率       |

注意：上面参数传需要修改的内容的值就行，不需要修改的可以不传。

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.2.6. <a name='获取子账户的收款设置信息'></a>获取子账户的收款设置信息

**action:** SubAccount.GetCoinHarvestSetting

**参数:**

| 字段     | 是否必须 | 类型   | 描述           |
| -------- | -------- | ------ | -------------- |
| userName | 是       | string | 用户子账户名   |
| coinType | 是       | string | 币种：btc、bch |

**返回值:**

| 字段 | 类型   | 描述               |
| ---- | ------ | ------------------ |
| data | object | 子账户收款设置信息 |

**子账户收款设置信息:**

| 字段      | 类型     | 描述                                      |
| --------- | -------- | ----------------------------------------- |
| address   | string   | 收币地址                                  |
| min       | double   | 自动收币最小额，如果为 0 则表示不自动收币 |
| updatedAt | datetime | 最后更新时间                              |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": {
    "address": "coin-address-xxx",
    "min": 0.01,
    "updatedAt": "2020-03-23 10:13:01"
  }
}
```

####  9.2.7. <a name='设置子账户收款设置'></a>设置子账户收款设置

**action:** SubAccount.SetCoinHarvestSetting

**参数:**

| 字段     | 是否必须 | 类型   | 描述                                                                     |
| -------- | -------- | ------ | ------------------------------------------------------------------------ |
| userName | 是       | string | 用户子账户名                                                             |
| coinType | 是       | string | 币种：btc、bch                                                           |
| address  | 是       | string | 收币地址                                                                 |
| min      | 是       | double | 自动收币最小额，可选值为：0，0.001，0.01，0.1；如果为 0 则表示不自动收币 |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.2.8. <a name='获取子账户的人民币收款设置信息'></a>获取子账户的人民币收款设置信息

**action:** SubAccount.GetMoneyHarvestSetting

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型   | 描述                     |
| ---- | ------ | ------------------------ |
| data | object | 子账户人民币收款设置信息 |

**子账户收款设置信息:**

| 字段      | 类型     | 描述                                      |
| --------- | -------- | ----------------------------------------- |
| address   | object   | 收款地址（银行信息）                      |
| min       | double   | 自动收币最小额，如果为 0 则表示不自动收币 |
| updatedAt | datetime | 最后更新时间                              |

**收款地址（银行信息）:**

| 字段     | 类型   | 描述   |
| -------- | ------ | ------ |
| province | string | 省     |
| city     | string | 市     |
| name     | string | 银行   |
| branch   | string | 支行   |
| owner    | string | 开户人 |
| no       | string | 卡号   |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": {
    "address": {
      "province": "北京",
      "city": "北京",
      "name": "中国银行",
      "branch": "西二旗支行",
      "owner": "李鸿章",
      "no": "6223211231313123"
    },
    "min": 500,
    "updatedAt": "2020-03-23 10:13:01"
  }
}
```

####  9.2.9. <a name='设置子账户人民币收款设置'></a>设置子账户人民币收款设置

**action:** SubAccount.SetMoneyHarvestSetting

**参数:**

| 字段     | 是否必须 | 类型   | 描述                                                                     |
| -------- | -------- | ------ | ------------------------------------------------------------------------ |
| userName | 是       | string | 用户子账户名                                                             |
| province | 是       | string | 省                                                                       |
| city     | 是       | string | 市                                                                       |
| name     | 是       | string | 银行                                                                     |
| branch   | 是       | string | 支行                                                                     |
| owner    | 是       | string | 开户人                                                                   |
| no       | 是       | string | 卡号                                                                     |
| min      | 是       | double | 自动收币最小额，可选值为：0，0.001，0.01，0.1；如果为 0 则表示不自动收币 |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.2.10. <a name='获取子账户挖矿收益自动兑换人民币设置信息'></a>获取子账户挖矿收益自动兑换人民币设置信息

**action:** SubAccount.GetCoin2MoneySetting

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型   | 描述                   |
| ---- | ------ | ---------------------- |
| data | object | 自动兑换人民币设置信息 |

**自动兑换人民币设置信息:**

| 字段 | 类型 | 描述         |
| ---- | ---- | ------------ |
| auto | bool | 是否自动兑换 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": {
    "auto": true
  }
}
```

####  9.2.11. <a name='设置子账户挖矿收益自动兑换人民币设置信息'></a>设置子账户挖矿收益自动兑换人民币设置信息

**action:** SubAccount.SetCoin2MoneySetting

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |
| auto     | 是       | bool   | 是否自动兑换 |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.2.12. <a name='获取子账户观察者链接信息'></a>获取子账户观察者链接信息

**action:** SubAccount.GetObserverList

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型  | 描述                 |
| ---- | ----- | -------------------- |
| data | array | 子账户观察者链接信息 |

**子账户观察者链接信息:**

| 字段   | 类型     | 描述                                                                                              |
| ------ | -------- | ------------------------------------------------------------------------------------------------- |
| link   | string   | 链接                                                                                              |
| remark | string   | 备注名                                                                                            |
| linkId | int      | 链接编号                                                                                          |
| rights | string[] | 观察者具备的权限项数组，目前包括 3 个权限项：dashboard_observer、worker_observer、profit_observer |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "link": "https://btc.top/ob/xxxxx",
      "remark": "运维",
      "linkId": 123,
      "rights": ["worker_observer"]
    },
    {
      "link": "https://btc.top/ob/xxxxxxx",
      "remark": "财务",
      "linkId": 124,
      "rights": ["dashboard_observer", "profit_observer"]
    }
  ]
}
```

####  9.2.13. <a name='添加子账户观察者链接信息'></a>添加子账户观察者链接信息

**action:** SubAccount.AddObserverInfo

**参数:**

| 字段     | 是否必须 | 类型     | 描述                                                                                              |
| -------- | -------- | -------- | ------------------------------------------------------------------------------------------------- |
| userName | 是       | string   | 用户子账户名                                                                                      |
| rights   | 是       | string[] | 观察者具备的权限项数组，目前包括 3 个权限项：dashboard_observer、worker_observer、profit_observer |
| remark   | 是       | string   | 观察者备注                                                                                        |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.2.14. <a name='修改子账户观察者链接信息'></a>修改子账户观察者链接信息

**action:** SubAccount.UpdateObserverInfo

**参数:**

| 字段   | 是否必须 | 类型     | 描述                                                                                              |
| ------ | -------- | -------- | ------------------------------------------------------------------------------------------------- |
| linkId | 是       | int      | 链接编号                                                                                          |
| rights | 是       | string[] | 观察者具备的权限项数组，目前包括 3 个权限项：dashboard_observer、worker_observer、profit_observer |
| remark | 是       | string   | 观察者备注                                                                                        |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.2.15. <a name='删除子账户观察者链接信息'></a>删除子账户观察者链接信息

**action:** SubAccount.DeleteObserverInfo

**参数:**

| 字段   | 是否必须 | 类型 | 描述     |
| ------ | -------- | ---- | -------- |
| linkId | 是       | int  | 链接编号 |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

###  9.3. <a name='收益'></a>收益

####  9.3.1. <a name='获取子账户的收益汇总信息'></a>获取子账户的收益汇总信息

**action:** Profit.GetSubAccountSummary

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型  | 描述                     |
| ---- | ----- | ------------------------ |
| data | array | 子账户的收益汇总信息数组 |

**子账户的收益汇总信息:**

| 字段      | 类型   | 描述                                                                                             |
| --------- | ------ | ------------------------------------------------------------------------------------------------ |
| latestPay | double | 最近支付                                                                                         |
| total     | double | 累计收益                                                                                         |
| remain    | double | 账户余额                                                                                         |
| autoPay   | int    | 是否自动付款。这里保持的自动支付下限。若值为 0 则表示不自动支付，若值为-1 则表示未设置收款地址。 |
| type      | string | 账户类型：btc、bch、cny                                                                          |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "latestPay": 0.0112,
      "total": 50.123,
      "remain": 0.000123,
      "autoPay": 0.01,
      "type": "btc"
    },
    {
      "latestPay": 0.0114,
      "total": 5.123,
      "remain": 0.000123,
      "autoPay": 0.01,
      "type": "bch"
    }
  ]
}
```

####  9.3.2. <a name='获取账户全部子账户的收益汇总信息'></a>获取账户全部子账户的收益汇总信息

**action:** Profit.GetAccountSummary

**参数:**

| 字段    | 是否必须 | 类型   | 描述         |
| ------- | -------- | ------ | ------------ |
| account | 是       | string | 用户主账户名 |

**返回值:**

| 字段 | 类型  | 描述                         |
| ---- | ----- | ---------------------------- |
| data | array | 账户全部子账户的收益汇总信息 |

**子账户的收益汇总信息:**

| 字段   | 类型   | 描述                    |
| ------ | ------ | ----------------------- |
| total  | double | 累计收益                |
| remain | double | 账户余额                |
| type   | string | 账户类型：btc、bch、cny |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "total": 50.123,
      "remain": 0.000123,
      "type": "btc"
    },
    {
      "total": 5.123,
      "remain": 0.000123,
      "type": "bch"
    }
  ]
}
```

####  9.3.3. <a name='获取子账户的出账信息'></a>获取子账户的出账信息

**action:** Profit.GetByDay

**参数:**

| 字段     | 是否必须 | 类型   | 描述                |
| -------- | -------- | ------ | ------------------- |
| userName | 是       | string | 用户子账户名        |
| coinType | 是       | string | 币种：btc、bch、cny |
| start    | 是       | date   | 开始日期            |
| end      | 是       | date   | 截止日期            |

**返回值:**

| 字段 | 类型  | 描述     |
| ---- | ----- | -------- |
| data | array | 出账信息 |

**出账信息:**

| 字段       | 类型   | 描述                                                                 |
| ---------- | ------ | -------------------------------------------------------------------- |
| at         | string | 出账日期                                                             |
| profitPerP | double | 1P 理论产出                                                          |
| speed      | double | 日均算力，单位 P                                                     |
| total      | double | 总收益                                                               |
| status     | string | 付款状态：saved-存入余额;paying-付款中;finish-付款完成;none-无需支付 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "at": "2020-04-01",
      "profitPerP": 0.000123,
      "speed": 1.0,
      "total": 0.000123
    },
    {
      "at": "2020-04-02",
      "profitPerP": 0.00012401,
      "speed": 1.0,
      "total": 0.00012401
    }
  ]
}
```

###  9.4. <a name='算力'></a>算力

####  9.4.1. <a name='获取子账户的日算力信息'></a>获取子账户的日算力信息

**action:** Speed.GetSubAccountDailySpeed

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |
| start    | 是       | date   | 开始日期     |
| end      | 是       | date   | 截止日期     |

**返回值:**

| 字段 | 类型  | 描述       |
| ---- | ----- | ---------- |
| data | array | 日算力信息 |

**日算力信息:**

| 字段       | 类型   | 描述   |
| ---------- | ------ | ------ |
| time       | string | 日期   |
| validSpeed | int    | 算力   |
| rejectRate | double | 拒绝率 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "time": "2020-04-01",
      "validSpeed": 11234342234231434,
      "rejectRate": 0.00123
    },
    {
      "time": "2020-04-02",
      "validSpeed": 11234342234231424,
      "rejectRate": 0.00122
    }
  ]
}
```

####  9.4.2. <a name='获取子账户的小时算力信息'></a>获取子账户的小时算力信息

**action:** Speed.GetSubAccountHourlySpeed

**参数:**

| 字段     | 是否必须 | 类型     | 描述         |
| -------- | -------- | -------- | ------------ |
| userName | 是       | string   | 用户子账户名 |
| start    | 是       | datetime | 开始时间     |
| end      | 是       | datetime | 截止时间     |

**返回值:**

| 字段 | 类型  | 描述         |
| ---- | ----- | ------------ |
| data | array | 小时算力信息 |

**小时算力信息:**

| 字段       | 类型   | 描述       |
| ---------- | ------ | ---------- |
| time       | string | 时间(小时) |
| validSpeed | int    | 算力       |
| rejectRate | double | 拒绝率     |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "time": "2020-04-01 00:00:00",
      "validSpeed": 11234342234231434,
      "rejectRate": 0.00123
    },
    {
      "time": "2020-04-01 01:00:00",
      "validSpeed": 11234342234231424,
      "rejectRate": 0.00122
    }
  ]
}
```

####  9.4.3. <a name='获取子账户的实时算力信息'></a>获取子账户的实时算力信息

**action:** Speed.GetSubAccountRealtimeSpeed

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型   | 描述         |
| ---- | ------ | ------------ |
| data | object | 实时算力信息 |

**实时算力信息:**

| 字段     | 类型   | 描述        |
| -------- | ------ | ----------- |
| speed5m  | object | 5 分钟算力  |
| speed10m | object | 10 分钟算力 |
| speed30m | object | 30 分钟算力 |

**算力格式:**

| 字段       | 类型  | 描述          |
| ---------- | ----- | ------------- |
| validSpeed | int   | 有效算力(H/s) |
| rejectRate | float | 拒绝率        |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": {
    "speed5m": { "validSpeed": 24561271905291252, "rejectRate": 0.007 },
    "speed10m": { "validSpeed": 24388516638335084, "rejectRate": 0.001 },
    "speed30m": { "validSpeed": 24559043561725624, "rejectRate": 0 }
  }
}
```

####  9.4.4. <a name='获取矿机的日算力信息'></a>获取矿机的日算力信息

**action:** Speed.GetWorkerDailySpeed

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |
| worker   | 是       | string | 矿机名       |
| start    | 是       | date   | 开始日期     |
| end      | 是       | date   | 截止日期     |

**返回值:**

| 字段 | 类型  | 描述       |
| ---- | ----- | ---------- |
| data | array | 日算力信息 |

**日算力信息:**

| 字段       | 类型   | 描述   |
| ---------- | ------ | ------ |
| time       | string | 日期   |
| validSpeed | int    | 算力   |
| rejectRate | double | 拒绝率 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "time": "2020-04-01",
      "validSpeed": 11234342234231434,
      "rejectRate": 0.00123
    },
    {
      "time": "2020-04-02",
      "validSpeed": 11234342234231424,
      "rejectRate": 0.00122
    }
  ]
}
```

####  9.4.5. <a name='获取矿机的小时算力信息'></a>获取矿机的小时算力信息

**action:** Speed.GetWorkerHourlySpeed

**参数:**

| 字段     | 是否必须 | 类型     | 描述         |
| -------- | -------- | -------- | ------------ |
| userName | 是       | string   | 用户子账户名 |
| worker   | 是       | string   | 矿机名       |
| start    | 是       | datetime | 开始时间     |
| end      | 是       | datetime | 截止时间     |

**返回值:**

| 字段 | 类型  | 描述         |
| ---- | ----- | ------------ |
| data | array | 小时算力信息 |

**小时算力信息:**

| 字段       | 类型   | 描述       |
| ---------- | ------ | ---------- |
| time       | string | 时间(小时) |
| validSpeed | int    | 算力       |
| rejectRate | double | 拒绝率     |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "time": "2020-04-01 00:00:00",
      "validSpeed": 11234342234231434,
      "rejectRate": 0.00123
    },
    {
      "time": "2020-04-01 01:00:00",
      "validSpeed": 11234342234231424,
      "rejectRate": 0.00122
    }
  ]
}
```

####  9.4.6. <a name='批量获取子账号下所有矿机的小时算力信息'></a>批量获取子账号下所有矿机的小时算力信息

**action:** Speed.GetSubAccountAllWorkersHourlySpeedBulk

**参数:**

| 字段     | 是否必须 | 类型     | 描述         |
| -------- | -------- | -------- | ------------ |
| userName | 是       | string   | 用户子账户名 |
| start    | 是       | datetime | 开始时间     |
| end      | 是       | datetime | 截止时间     |

**返回值:**

| 字段 | 类型  | 描述         |
| ---- | ----- | ------------ |
| data | array | 小时算力信息 |

**小时算力信息:**

| 字段       | 类型   | 描述       |
| ---------- | ------ | ---------- |
| worker     | string | 矿机名     |
| time       | string | 时间(小时) |
| validSpeed | int    | 算力       |
| rejectRate | double | 拒绝率     |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "worker": "100x001",
      "time": "2020-04-01 00:00:00",
      "validSpeed": 11234342234231434,
      "rejectSpeed": 0.00123
    },
    {
      "worker": "100x002",
      "time": "2020-04-01 01:00:00",
      "validSpeed": 11234342234231424,
      "rejectRate": 0.00122
    }
  ]
}
```

####  9.4.7. <a name='获取系统的日算力信息(最近-30-天)'></a>获取系统的日算力信息(最近 30 天)

**action:** Speed.GetSystemDailySpeed

**参数:**

无

**返回值:**

| 字段 | 类型  | 描述       |
| ---- | ----- | ---------- |
| data | array | 日算力信息 |

**日算力信息:**

| 字段       | 类型   | 描述   |
| ---------- | ------ | ------ |
| time       | string | 日期   |
| validSpeed | int    | 算力   |
| rejectRate | double | 拒绝率 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "time": "2020-04-01",
      "validSpeed": 11234342234231434,
      "rejectRate": 0.00123
    },
    {
      "time": "2020-04-02",
      "validSpeed": 11234342234231424,
      "rejectRate": 0.00122
    }
  ]
}
```

####  9.4.8. <a name='获取系统的小时算力信息(最近-24-小时)'></a>获取系统的小时算力信息(最近 24 小时)

**action:** Speed.GetSystemHourlySpeed

**参数:**

无

**返回值:**

| 字段 | 类型  | 描述         |
| ---- | ----- | ------------ |
| data | array | 小时算力信息 |

**小时算力信息:**

| 字段       | 类型   | 描述       |
| ---------- | ------ | ---------- |
| time       | string | 时间(小时) |
| validSpeed | int    | 算力       |
| rejectRate | double | 拒绝率     |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "time": "2020-04-01 00:00:00",
      "validSpeed": 11234342234231434,
      "rejectRate": 0.00123
    },
    {
      "time": "2020-04-01 01:00:00",
      "validSpeed": 11234342234231424,
      "rejectRate": 0.00122
    }
  ]
}
```

####  9.4.9. <a name='获取系统的实时算力信息'></a>获取系统的实时算力信息

**action:** Speed.GetSystemRealtimeSpeed

**参数:**

| 字段     | 是否必须 | 类型   | 描述                                   |
| -------- | -------- | ------ | -------------------------------------- |
| coinType | 是       | string | 币种：btc、bch，如果要获取全部请传 all |

**返回值:**

| 字段 | 类型   | 描述         |
| ---- | ------ | ------------ |
| data | object | 实时算力信息 |

**实时算力信息:**

| 字段     | 类型   | 描述        |
| -------- | ------ | ----------- |
| speed5m  | object | 5 分钟算力  |
| speed10m | object | 10 分钟算力 |
| speed30m | object | 30 分钟算力 |

**算力格式:**

| 字段       | 类型  | 描述          |
| ---------- | ----- | ------------- |
| totalSpeed | int   | 总效算力(H/s) |
| rejectRate | float | 拒绝率        |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "speed5m": { "totalSpeed": 24561271905291252, "rejectRate": 0.007 },
      "speed10m": { "totalSpeed": 24388516638335084, "rejectRate": 0.001 },
      "speed30m": { "totalSpeed": 24559043561725624, "rejectRate": 0 }
    },
    {
      "speed5m": { "totalSpeed": 24561271905291252, "rejectRate": 0.007 },
      "speed10m": { "totalSpeed": 24388516638335084, "rejectRate": 0.001 },
      "speed30m": { "totalSpeed": 24559043561725624, "rejectRate": 0 }
    }
  ]
}
```

###  9.5. <a name='矿机'></a>矿机

####  9.5.1. <a name='获取用户矿机详细信息'></a>获取用户矿机详细信息

**action:** Worker.GetSubAccountWorkerList

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型  | 描述         |
| ---- | ----- | ------------ |
| data | array | 矿机详细信息 |

**矿机详细信息:**

| 字段           | 类型   | 描述                        |
| -------------- | ------ | --------------------------- |
| name           | string | 矿机名称                    |
| speed5m        | object | 5 分钟算力                  |
| speed30m       | object | 30 分钟算力                 |
| speed24h       | object | 24 小时算力                 |
| lastCommitTime | string | 最近提交时间                |
| status         | number | 状态：1-在线;2-停机;3-失效; |
| group          | object | 矿机所属分组信息            |

**算力格式:**

| 字段       | 类型  | 描述          |
| ---------- | ----- | ------------- |
| validSpeed | int   | 有效算力(H/s) |
| rejectRate | float | 拒绝率        |

**矿机所属分组信息:**

| 字段 | 类型   | 描述         |
| ---- | ------ | ------------ |
| id   | int    | 分组编号     |
| name | string | 矿机分组名称 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "name": "worker1x100",
      "speed5m": { "validSpeed": 24561271905291252, "rejectRate": 0.007 },
      "speed24h": { "validSpeed": 24388516638335084, "rejectRate": 0.001 },
      "speed30m": { "validSpeed": 24559043561725624, "rejectRate": 0 },
      "lastCommitTime": "2020-04-01 10:02:12",
      "status": 1,
      "group": {
        "id": 1,
        "name": "四川"
      }
    },
    {
      "name": "worker1x101",
      "speed5m": { "validSpeed": 24561271905291252, "rejectRate": 0.007 },
      "speed24h": { "validSpeed": 24388516638335084, "rejectRate": 0.001 },
      "speed30m": { "validSpeed": 24559043561725624, "rejectRate": 0 },
      "lastCommitTime": "2020-04-01 10:02:13",
      "status": 1,
      "group": {
        "id": 1,
        "name": "四川"
      }
    }
  ]
}
```

####  9.5.2. <a name='获取用户矿机汇总信息'></a>获取用户矿机汇总信息

**action:** Worker.GetSubAccountWorkerSummary

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型   | 描述         |
| ---- | ------ | ------------ |
| data | object | 矿机汇总信息 |

**矿机汇总信息:**

| 字段    | 类型 | 描述   |
| ------- | ---- | ------ |
| running | int  | 运行中 |
| stopped | int  | 停机数 |
| invalid | int  | 失效数 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": {
    "running": 123,
    "stopped": 1,
    "invalid": 2
  }
}
```

####  9.5.3. <a name='获取用户矿机分组信息'></a>获取用户矿机分组信息

**action:** Worker.GetSubAccountWorkerGroupList

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |

**返回值:**

| 字段 | 类型  | 描述         |
| ---- | ----- | ------------ |
| data | array | 矿机分组信息 |

**矿机分组信息:**

| 字段 | 类型   | 描述         |
| ---- | ------ | ------------ |
| id   | int    | 分组编号     |
| name | string | 矿机分组名称 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
    {
      "id": 1,
      "name": "四川"
    },
    {
      "id": 2,
      "name": "重庆"
    }
  ]
}
```

####  9.5.4. <a name='创建矿机分组'></a>创建矿机分组

**action:** Worker.CreateGroup

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |
| name     | 是       | string | 分组名       |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.5.5. <a name='修改矿机分组'></a>修改矿机分组

**action:** Worker.UpdateGroup

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |
| name     | 是       | string | 分组名       |
| groupId  | 是       | int    | 分组编号     |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.5.6. <a name='删除矿机分组'></a>删除矿机分组

**action:** Worker.DeleteGroup

**参数:**

| 字段     | 是否必须 | 类型   | 描述         |
| -------- | -------- | ------ | ------------ |
| userName | 是       | string | 用户子账户名 |
| groupId  | 是       | int    | 分组编号     |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.5.7. <a name='批量设置矿机所属分组'></a>批量设置矿机所属分组

**action:** Worker.SetWorkerGroupBulk

**参数:**

| 字段     | 是否必须 | 类型     | 描述         |
| -------- | -------- | -------- | ------------ |
| userName | 是       | string   | 用户子账户名 |
| groupId  | 是       | int      | 分组编号     |
| workers  | 是       | string[] | 矿机名数组   |

**返回值:**

请根据执行结果错误码判断操作是否成功。

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": null
}
```

####  9.5.8. <a name='获取子账户所属矿机的在线情况'></a>获取子账户所属矿机的在线情况

**action:** Worker.GetSubAccountWorkerHourlyActiveNumList

**参数:**

| 字段     | 是否必须 | 类型     | 描述         |
| -------- | -------- | -------- | ------------ |
| userName | 是       | string   | 用户子账户名 |
| start    | 是       | date   | 开始日期     |
| end      | 是       | date   | 截止日期     |

**返回值:**

| 字段 | 类型  | 描述         |
| ---- | ----- | ------------ |
| data | array | 每小时小时矿机在线信息 |

**每小时小时矿机在线信息:**

| 字段       | 类型   | 描述        |
| --------- | ------ | ---------- |
| at        | string | 时间(小时)  |
| workerNum | int    | 在线矿机数量 |

**举例:**

```json
{
  "code": 0,
  "message": null,
  "data": [
     {
        "at": "2020-04-01 00:00:00",
        "workerNum": 100
     },
     {
        "at": "2020-04-01 01:00:00",
        "workerNum": 100
     }
  ]
}
``````

