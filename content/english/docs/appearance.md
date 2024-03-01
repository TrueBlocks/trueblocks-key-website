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
  "perPage": 100
}]
```

1. `Object`
    - `address`: Address - address for which to return the appearances
    - `perPage`: Uint - (optional) number of items per page
    - `pageId`: PageId - (optional) page to return. See [Pagination](#pagination).

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
      "address": "0x52bc44d5378309ee2abf1539bf71de1b7d7be3b5",
      "previousPageId": "QVl3ZUp3SEJRTzBBZVFBQUFIaXFJQUVRQVFBQWlKVUJBSitHQVFBPQ==",
      "nextPageId": null
    }
  }
}
```

## `tb_getBounds` method

Returns the latest and earliest appearance for the given address.

### Parameters


```javascript
"params": [{
  "address": "0x52bc44d5378309ee2abf1539bf71de1b7d7be3b5"
}]
```

1. `Object`
    - `address`: Address - address for which to return the number of appearances

### Returns

`Bounds` object with exactly 2 appearances.

### Example

```bash
# Request
curl -X POST --data '{"jsonrpc":"2.0","method":"tb_getBounds","params":[{see above}],"id":1}'
# Result
{
  "id": 1,
  "jsonrpc": "2.0",
  "result": {
    "data": {
      "latest": {
        "blockNumber": 19325230,
        "transactionIndex": 17
      },
      "earliest": {
        "blockNumber": 8854723,
        "transactionIndex": 61
      }
    },
    "meta": {
      "lastIndexedBlock": 19268245,
      "address": "0x52bc44d5378309ee2abf1539bf71de1b7d7be3b5",
      "previousPageId": null,
      "nextPageId": null
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

## Pagination

The API uses _keyset pagination model_. It means that there are ids of next and previous page attached to every response, in its `meta` section:
```json
{
  "meta": {
    "previousPageId": "QVl3ZUp3RzRRTzBBOWdBQUFIaXFJQUVRQVFBQWlKVUJBSitHQVFBPQ==",
    "nextPageId": "QUl3ZUp3SEJRTzBBZUFBQUFIaXFJQUVRQVFBQWlKVUJBSitHQVFBPQ=="
  }
}
```
To fetch another page, you have to set `pageId` in your request to one of the returned ids.
If there is no previous page, `previousPageId` will be `null`. Similarly, the request for the latest page will return `null` as  `nextPageId`.

If `pageId` is not set, the API returns the **latest** page.
You can set `pageId` to `"earliest"` to fetch the earliest page.