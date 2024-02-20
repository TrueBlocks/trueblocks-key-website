---
title: "Appearance Index API"
meta_title: ""
description: "TrueBlocks Key Appearance Index API documentation"
categories: ["Docs", "API", "Appearances"]
draft: false
---

Appearance Index API lets you fetch appearances (**block number**, **transaction ID**) of any Ethereum address. You can also get a total number of appearances. The API is compatible with Ethereum standard JSON-RPC.

{{< toc >}}

## `tb_getAppearances` method

Returns appearances of the given address.

### Parameters

```javascript
"params": [{
  "address": "0x52bc44d5378309ee2abf1539bf71de1b7d7be3b5",
  "page": 1,
  "perPage": 100
}]
```

1. `Object`
    - `address`: Address - address for which to return the appearances
    - `page`: Uint - (optional) data page to return
    - `perPage`: Uint - (optional) number of items per page

### Returns

An array of appearances (from the earliest block to the latest). If nothing is found, an empty array.

### Example

```bash
# Request
curl -X POST --data '{"jsonrpc":"2.0","method":"tb_getAppearances","params":[{see above}],"id":1}'
# Result
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": {
    "data": [
      {
        "blockNumber": 4053179,
        "transactionId": 1
      },
      {
        "blockNumber": 4053179,
        "transactionId": 2
      },
      {
        "blockNumber": 4053180,
        "transactionId": 8
      }
    ],
    "meta": {
      "lastIndexedBlock": 19268245,
      "address": "0x52bc44d5378309ee2abf1539bf71de1b7d7be3b5"
    }
  }
}
```

## `tb_getAppearanceCount` method

Returns number of appearances of the given address.

### Parameters


```javascript
"params": [{
  "address": "0x52bc44d5378309ee2abf1539bf71de1b7d7be3b5"
}]
```

1. `Object`
    - `address`: Address - address for which to return the number of appearances

### Returns

Number (decimal) of appearances

### Example

```bash
# Request
curl -X POST --data '{"jsonrpc":"2.0","method":"tb_getAppearanceCount","params":[{see above}],"id":1}'
# Result
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": {
    "data": 5302,
    "meta": {
      "lastIndexedBlock": 19268245,
      "address": "0x52bc44d5378309ee2abf1539bf71de1b7d7be3b5"
    }
  }
}
```

## `tb_status` method

Returns index status, i.e. last indexed block number.

### Parameters

None

### Returns

Returns only `meta` object (with last indexed block number as a decimal)

### Example

```bash
# Request
curl -X POST --data '{"jsonrpc":"2.0","method":"tb_lastIndexedBlock","params":[],"id":1}'
# Result
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": {
    "data": null,
    "meta": {
      "lastIndexedBlock": 19268245
    }
  }
}
```
