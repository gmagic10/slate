---
title: Yuansfer POS API Reference

language_tabs:
  - iOS
  - Android

toc_footers:


includes:
  - errors
  - basicparameter

search: true
---

# Introduction

Welcome to the Yuansfer POS API! You can use our API to access Yuansfer API endpoints.

# Notice

> To authorize, use this code:

> Make sure to replace `meowmeowmeow` with your API key.

Kittn uses API keys to allow access to the API. You can register a new Kittn API key at our [developer portal](http://example.com/developers).

Kittn expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
</aside>

# API List

## Check a store whether exists

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

> The above command returns JSON structured like this:

```json
{
    "ret_code": "000100",
    "ret_msg": "店铺存在"
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://mapi.yuansfer.com/appStore/check`

### Post Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeNo | true | The No of the store.


## Login

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get()
```

> The above command returns JSON structured like this:

```json
{
    "storeNo": "300001",
    "ret_code": "000100",
    "storeName": "TMS1",
    "token": "e28a630ec05c431f4b515b5f30857d76",
    "storeAdminId": 12,
    "ret_msg": "login success ",
    "merchantName": "TM1",
    "accountNo": "3000010001",
    "merchantId": 42,
    "storeUserName": "STOT1",
    "storeId": 13
}
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://mapi.yuansfer.com/appLogin`

### Post Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
username | true | The user name of the store.
password | true | The password of the store.

### Response

Parameter | Description
--------- | -----------
ret_code  | The code of the result, "000100" indicate success, error code refer below.
ret_msg  | The message of the result.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Change Password Step 1

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Change Password Step 2

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Create New Order

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Pay

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Refund

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Transaction History

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```
> The above command returns JSON structured like this:

```json
{
    "ret_code": "000100",
    "page": 1,
    "income": 2.3,
    "ret_msg": "查询成功",
    "list": [
        {
            "id": 814,
            "transactionNo": "297245667968233821",
            "amount": 0.01,
            "refundAmount": 0.0,
            "netReceivable": null,
            "exchangeRate": null,
            "alipayUserLoginId": null,
            "refundInfo": "SUCCESS",
            "supplierPayTime": "20170523062656",
            "hasRefund": 0,
            "supplierTransactionNo": null,
            "transactionReferNo": null,
            "currency": null,
            "originalTransactionNo": null,
            "refundTime": null,
            "refundTimeV2": null
        },
        {
            "id": 807,
            "transactionNo": "297245667956145999",
            "amount": 5.0,
            "refundAmount": 5.0,
            "netReceivable": null,
            "exchangeRate": null,
            "alipayUserLoginId": null,
            "refundInfo": "REFUND FULLY",
            "supplierPayTime": "20170523030528",
            "hasRefund": 0,
            "supplierTransactionNo": null,
            "transactionReferNo": null,
            "currency": null,
            "originalTransactionNo": null,
            "refundTime": null,
            "refundTimeV2": null
        }
    ],
    "totalSize": 178,
    "totalPage": 12,
    "size": 15
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Transaction Detail

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Transaction Statistics

```iOS
require 'kittn'

api = Kittn::APIClient.authorize!('meowmeowmeow')
api.kittens.get(2)
```

```Android
import kittn

api = kittn.authorize('meowmeowmeow')
api.kittens.get(2)
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve
