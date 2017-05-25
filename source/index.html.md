---
title: Yuansfer POS API Reference

language_tabs:
  - Response Example

toc_footers:
  - <a href='#'>@Yuansfer</a>
  - <a href='#'>All Right Reserved</a>

includes:
  - errors
  - basicparameter

search: true
---

# Introduction

Welcome to the Yuansfer POS API! You can use our API to access Yuansfer API endpoints.

# Notice


# API List

## Check a store whether exists

> The above command returns JSON structured like this:

```json
{
    "ret_code": "000100",
    "ret_msg": "店铺存在"
}
```

At first, you should check the store whether exists by this API

### HTTP Request

`POST https://mapi.yuansfer.com/appStore/check`

### Post Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeNo | true | The No of the store.


## Login

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

After the check store procedure, You can login by the store account, and get the token that need by all APIs.

### HTTP Request

`POST https://mapi.yuansfer.com/appLogin`

### Post Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
username | true | The user name of the store.
password | true | The password of the store, you should MD5 the "@yuanex + raw_password" before POST.

### Response

Parameter | Description
--------- | -----------
ret_code  | The code of the result, "000100" indicate success, error code refer to the error section.
ret_msg  | The message of the result.
storeNo  | The No of the store.
storeName  | The name the store.
token  | The API pass token that need by all APIs.
storeAdminId  | The administrator ID of the store.
merchantName  | The merchant name.
accountNo  | The account No.
merchantId  | The merchant ID.
storeUserName  | The user name of the store.
storeId  | The ID of the store.

## Change Password Step 1

When you need to change password, you should call two API, this is the first API that you should call and get the password token(different from the login token).

### HTTP Request

`POST https://mapi.yuansfer.com/appStoreAdmin/changePwd_step1`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID of the store.
token | true | The login token.
accountNo | true | The account No.
password | true | The old password of the store, you should MD5 the "@yuanex + raw_password" before POST.

### Response

Parameter | Description
--------- | -----------
pwdToken  | The token to modify the password, need in Step 2.


## Change Password Step 2

When you need to change password, you should call two API, this is the second API that you should call.

### HTTP Request

`POST https://mapi.yuansfer.com/appStoreAdmin/changePwd_step2`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID of the store.
token | true | The login token.
accountNo | true | The account No.
password | true | The new password of the store, you should MD5 the "@yuanex + raw_password" before POST.
pwdToken | true | Get it in Step 1.

## Create New Order

### HTTP Request

`POST https://mapi.yuansfer.com/appTransaction/add`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID of the store.
token | true | The login token.
amount | true | The amount of money(USD).
tip | true | The tips of this transaction.
transactionCurrency | true | Currency.

### Response

Parameter | Description
--------- | -----------
transactionNo  | The transaction No.
merchantId  | The merchant ID.
storeId  | The ID of the store.
storeAdminId  | The administrator ID of the store.

## Pay

After scan QR-Code of the customer's Phone, call this API to get the pay(money).

### HTTP Request

`POST https://mapi.yuansfer.com/appTransaction/pay`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID of the store.
token | true | The login token.
transactionNo | true | The transaction No.
paymentBarcode | true |

### Response

Parameter | Description
--------- | -----------
supplierPartnerId  |
supplierTransId  |
supplierUserLoginId  |
exchangeRate  |
supplierPayTime  |


## Refund a transaction

When you need to refund a transaction, call this API.

### HTTP Request

`POST https://mapi.yuansfer.com/appTransaction/refund`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID of the store.
token | true | The login token.
transactionNo | true | The transaction No
refundAmount | true | The refund amount(USD).
refundAdmAccId | true |
refundPassword | true | The refund password, you should MD5 the raw password before POST.

### Response

Parameter | Description
--------- | -----------
originalTransactionNo  |
supplierPartnerId  |
supplierTransId  |
supplierUserLoginId  |
exchangeRate  |
supplierPayTime  |

## Transaction History

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

Get the store's transaction history

### HTTP Request

`POST https://mapi.yuansfer.com/appTransaction/list`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID.
token | true | The login token.
page   | true | The page number of the transaction list.
size | true | The page size.
transactionNo   | false | Search for this transaction No.
refundStatus | false | Search the transaction of the refund status.

### Response

Parameter | Description
--------- | -----------
transactionNo  | The token to modify the password, need in Step 2.
amount  | The token to modify the password, need in Step 2.
refundAmount  | The token to modify the password, need in Step 2.
netReceivable  | The token to modify the password, need in Step 2.
exchangeRate  | The token to modify the password, need in Step 2.
alipayUserLoginId  | The token to modify the password, need in Step 2.
refundInfo  | The token to modify the password, need in Step 2.
hasRefund  | The token to modify the password, need in Step 2.
supplierTransactionNo  | The token to modify the password, need in Step 2.
transactionReferNo  | The token to modify the password, need in Step 2.
currency  | The token to modify the password, need in Step 2.
originalTransactionNo  | The token to modify the password, need in Step 2.
refundTimeV2  | The token to modify the password, need in Step 2.


## Transaction Detail

> The above command returns JSON structured like this:

```json
{
    "ret_code": "000100",
    "transaction": {
        "id": 814,
        "transactionNo": "297245667968233821",
        "amount": 0.01,
        "refundAmount": 0,
        "netReceivable": 0.01,
        "exchangeRate": "6.90310000",
        "alipayUserLoginId": "131****7666",
        "refundInfo": "",
        "supplierPayTime": "20170523062656",
        "hasRefund": 0,
        "supplierTransactionNo": "2017052321001004980294191655",
        "transactionReferNo": "1000",
        "currency": "USD",
        "originalTransactionNo": null,
        "refundTime": null,
        "refundTimeV2": null
    },
    "ret_msg": "查询成功"
}
```

Get the transaction detail

### HTTP Request

`POST https://mapi.yuansfer.com/appTransaction/detail`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID.
token | true | The login token.
transactionNo | true | The transaction No.

## Transaction Statistics

> The above command returns JSON structured like this:

```json
{
    "ret_code": "000100",
    "stats": {
        "sales": 10.01,
        "salesQty": 2,
        "refund": 11.0,
        "refundQty": 2,
        "netSales": -0.99,
        "netSalesQty": 4,
        "startDate": 1495468800000,
        "endDate": 1495468800000,
        "merchantId": 42,
        "storeId": 13,
        "transactionType": 2,
        "diff_hour": 0
    },
    "ret_msg": "查询成功"
}
```

### HTTP Request

`POST https://mapi.yuansfer.com/appTransaction/stats`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID.
token | true | The login token.
startDate | true | Statistics start date in "yyyy-MM-dd" format.
endDate | true | Statistics end date in "yyyy-MM-dd" format.
diff_hour | true | The value that diff from the Beijing Timezone(GMT +8) in hour, e.g: diff_hour=(customer timezone)-8.

### Response

Parameter | Description
--------- | -----------
sales  | Total sales amount.
salesQty  | Total sales quantity.
refund  | Total refund amount.
refundQty  | Total refund quantity.
netSales  | Net sales amount.
netSalesQty  | Net sales quantity.

## Refund List

> The above command returns JSON structured like this:

```json
{
    "ret_code": "000100",
    "ret_msg": "查询成功",
    "list": [
        {
            "id": 817,
            "transactionNo": "297245668050617422",
            "amount": -0.01,
            "refundAmount": null,
            "netReceivable": null,
            "exchangeRate": null,
            "alipayUserLoginId": null,
            "refundInfo": "SUCCESS",
            "supplierPayTime": "20170524051958",
            "hasRefund": 0,
            "supplierTransactionNo": null,
            "transactionReferNo": null,
            "currency": null,
            "originalTransactionNo": null,
            "refundTime": "2017-05-24 05:19:58",
            "refundTimeV2": "20170524051958"
        }
    ]
}
```

Get the refund list

### HTTP Request

`POST https://mapi.yuansfer.com/appTransaction/refundList`

### POST Parameters

Parameter | Necessary | Description
--------- | ------- | -----------
storeId | true | The ID of the store.
merchantId | true | The merchant ID.
storeAdminId   | true | The administrator ID of the store.
token | true | The login token.
originalTransactionNo | true | .

### Response

Parameter | Description
--------- | -----------
transactionNo  | Transaction No.
amount  | The transaction amount.
refundAmount  | The refund amount.
netReceivable  | The token to modify the password, need in Step 2.
exchangeRate  | Exchange Rate.
alipayUserLoginId  | The token to modify the password, need in Step 2.
refundInfo  | The refund status in text.
supplierPayTime  | The token to modify the password, need in Step 2.
hasRefund  | The token to modify the password, need in Step 2.
supplierTransactionNo  | The token to modify the password, need in Step 2.
currency  | Currency.
originalTransactionNo  | Original Transaction No.
refundTimeV2  | The refund time in "YYMMDDhhmmss"(20170524051958) format.
