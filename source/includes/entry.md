# Entry



## Add Entry

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"incident": "test", "explanation": "test reason", "chainId": "df81c9fd-7b90-4098-a084-8dff1e0e1e79"}' \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entry": {
        "id": "d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "hash": "0xc0dbcf141450cbe2e0be538db7b7a1242f464660bf8bc580bc1b86b84d1407d2",
        "_ts": "2017-07-24T11:53:20.108Z",
        "revision": 1,
        "chainId": null,
        "entityId": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
        "values": {
          "incident": "test",
          "explanation": "test reason"
        }
      }
    }
  }

```

Use this method to adds a specific Entry of data as key value pairs. This is the normal method utilized by an Integrator to push data into ComplianceGuard.

### HTTP Request

`POST /api/v1/entries/<entityId>`

### Payload Attributes

| Attribute | Description |
|----------|-----------|
| ENTITYID    | Id of the corresponding entity      |
| CHAINID    | [Optional] Id of the target entry to update. No data actually changed, and chain of changes created instead      |




## Add Entry (Using Form)

```shell

 curl \
   -X POST \
   -F "incident=test" \
   -F "explanation=test reason" \
   -F "file_1=/path/to/file.txt" \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/form

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entry": {
        "id": "d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "hash": "0xc0dbcf141450cbe2e0be538db7b7a1242f464660bf8bc580bc1b86b84d1407d2",
        "_ts": "2017-07-24T11:53:20.108Z",
        "revision": 1,
        "chainId": null,
        "entityId": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
        "values": {
          "incident": "test",
          "explanation": "test reason"
          "file_1": {
            "name": "file.txt",
            "type": "application/octet-stream",
            "size": 6430,
            "lastModifiedDate": "2017-07-24T00:00:00+00:00",
            "digest": {
              "type": "Buffer",
              "data": [214,17,224,87,199,78,236,218,56,189,136,63,35,93,2,57,29,144]
            },
            "link": {
              "type": "Buffer",
              "link": [57,102,50,48,52,51,97,49,49,53,97,53,53,101,100,57,100,52,54]
            }
          }
        }
      }
    }
  }

```

Use this method to add a specific Entry of data using the ComplianceGuard User Interface (such as the CCO Logbook). The parameters are the same as those used in the plain Add Entry method, but in this case data is used from a form, rather than plain JSON.

### HTTP Request

`POST /api/v1/entries/<entityId>/form`

### Payload Attributes

| Parameter  | Description |
|----------|-----------|
| ENTITYID    | Id of the corresponding entity      |
| [OPTIONAL]    | chainId Id of the target entry to update. No data actually changed, and chain of changes created instead      |




## Add Entry (Using Form, where one Field can contain multiple files)

```shell

 curl \
   -X POST \
   -F "incident=test" \
   -F "file_1=/path/to/file.txt" \
   -F "file_1=/path/to/another/file.jpg" \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/formmultiple

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entry": {
        "_ts": "2017-07-24T11:53:20.108Z",
        "revision": 1,
        "chainId": null,
        "entityId": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
        "hash": "0xc0dbcf141450cbe2e0be538db7b7a1242f464660bf8bc580bc1b86b84d1407d2",
        "id": "d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "values": {
          "incident": "test",
          "file_1": {
            "name": "file.txt",
            "type": "application/octet-stream",
            "size": 6430,
            "lastModifiedDate": "2017-07-24T00:00:00+00:00",
            "digest": {
              "type": "Buffer",
              "data": [214,17,224,87,199,78,236,218,56,189,136,63,35,93,2,57,29,144]
            },
            "link": {
              "type": "Buffer",
              "link": [57,102,50,48,52,51,97,49,49,53,97,53,53,101,100,57,100,52,54]
            }
          },
          "file_2": {
            "name": "file.jpg",
            "type": "image/jpeg",
            "size": 12340,
            "lastModifiedDate": "2017-07-25T00:00:00+00:00",
            "digest": {
              "type": "Buffer",
              "data": [214,17,224,87,199,78,236,218,56,189,136,63,35,93,2,57,29,144]
            },
            "link": {
              "type": "Buffer",
              "link": [57,102,50,48,52,51,97,49,49,53,97,53,53,101,100,57,100,52,54]
            }
          }
        }
      }
    }
  }

```

Use this method to add a specific Entry where Clients can attach files (such as PDFs or .doc files). In this method one Field can contain multiple files.

### HTTP Request

`POST /api/v1/entries/<entityId>/form`

### Payload Attributes

| Parameter  | Description |
|----------|-----------|
| ENTITYID    | Id of the corresponding entity      |
| [OPTIONAL]    | chainId Id of the target entry to update. No data actually changed, and chain of changes created instead      |




## Get list of Entries of a specific type

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e?limit=5

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entries": [
        {
          "id": "d0691c48-ad21-45db-bbd6-f32aa264d1ad",
          "hash": "0xc0dbcf141450cbe2e0be538db7b7a1242f464660bf8bc580bc1b86b84d1407d2",
          "_ts": "2017-07-24T11:53:20.108Z",
          "revision": 1,
          "chainId": null,
          "entityId": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
          "values": {
            "incident": "test",
            "explanation": "test reason"
          }
        }
      ]
    }
  }

```

This endpoint returns an array of specific Entries.

### HTTP Request

`GET /api/v1/entries/<entityId>`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| ENTITYID    | Id of the corresponding entity      |
| LIMIT    | [Optional] Limit of number of fetched devices. Default value: 0      |
| OFFSET    | [Optional] Number of devices to skip. Default value: 5      |




## Get history of changes for a specific Entry

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/history?limit=5

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entries": [
        {
          "id": "d0691c48-ad21-45db-bbd6-f32aa264d1ad",
          "hash": "0xc0dbcf141450cbe2e0be538db7b7a1242f464660bf8bc580bc1b86b84d1407d2",
          "_ts": "2017-07-24T11:53:20.108Z",
          "revision": 1,
          "chainId": null,
          "entityId": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
          "values": {
            "incident": "test",
            "explanation": "test resason"
          }
        }
      ]
    }
  }

```

This endpoint returns an array of Entries, each of which describes a single changeset of the original Entry.

### HTTP Request

`GET /api/v1/entries/<entityId>/history`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| CHAINID    | Id of the original entry      |
| LIMIT    | [Optional] Limit of number of fetched devices. Default value: 0      |
| OFFSET    | [Optional] Number of devices to skip. Default value: 5      |




## Get linked items to the latest version of a specific Entry

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/latest/links

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "links": [
        {
          "id": "243cbe46-2cce-402d-9307-c8c16ed07b26",
          "hash": "0xfaf04d916adc4ed24bd5e1a035b2f2369dbf7538498ba9e69fe2499d13422336",
          "_ts": "2017-08-21T07:35:44.937Z",
          "revision": 1,
          "chainId": null,
          "entityId": "3feb4353-393c-4021-afdb-2e1f8ef1aa6b",
          "links": [ ],
          "tx": {
            "blockHash": "0xfab1d2c44eb709c3fd2e145b9485d9633f6ea156d65ec2d814e6ac2ec4140af8",
            "blockNumber": "0x4db4",
            "condition": null,
            "creates": "0xa4756da0eff5cdd8c558c4aba715ee03f677c9b0",
            "from": "0x0004a1af9de734f8ddab0d47c803cf301038d874",
            "gas": "0xe57e0",
            "gasPrice": "0x0",
            "hash": "0xfaf04d916adc4ed24bd5e1a035b2f2369dbf7538498ba9e69fe2499d13422336",
            "input": "0x3339613838653834313234313939383233737656656636303133646163643235656637386161",
            "networkId": 8995,
            "nonce": "0x232236",
            "publicKey": "0x16dbef0da60ba94f7583b79d6b9b1d40eca9854529ac2c23cd9b5e0e92be344e38aae5c7",
            "r": "0x1c471fcdd60ac0c8e0903624aec1481e635069d561004a69faa4234a4150d752",
            "raw": "0xf891656634300ac0c8e0903624aec1481e635069d5447de7c64a374b23118e5404b69847b47eaa",
            "s": "0x7efc4ed33b3f2fb49251e1b14587447de7c64a374b23118e5404b69847b47eaa",
            "standardV": "0x0",
            "to": null,
            "transactionIndex": "0x0",
            "v": "0x4669",
            "value": "0x0"
          },
          "values": {
            "_ts": "2017-07-24T11:53:20.108Z",
            "target": "1cedf4ab-befd-44aa-b31b-86d612f4068e"
            "incident": "test"
          }
        }
      ]
    }
  }

```

This endpoint returns list of Entries that are associated with the latest version of a specific Entry.

### HTTP Request

`GET /api/v1/entries/<entityId>/latest/links`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| CHAINID    | Id of the original entry      |
| ENTITYID    | Id of the entity, which items you want to see      |
| LIMIT    | [Optional] Limit of number of fetched devices. Default value: 0      |
| OFFSET    | [Optional] Number of devices to skip. Default value: 5      |




## Get latest version of the specific Entry

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/latest

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entry": {
        "id": "d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "hash": "0xc0dbcf141450cbe2e0be538db7b7a1242f464660bf8bc580bc1b86b84d1407d2",
        "_ts": "2017-07-24T11:53:20.108Z",
        "revision": 1,
        "chainId": null,
        "entityId": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
        "values": {
          "incident": "test",
          "explanation": "test reason"
        }
      }
    }
  }

```

This endpoint returns the latest version of an Entry, showing all the changes made to the original Entry.

### HTTP Request

`GET /api/v1/entries/<entityId>/latest`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| CHAINID    | Id of the original entry      |





## Get parameters necessary for validating stored data

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/1cedf4ab-befd-44aa-b31b-86d612f4068e/validate

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entry": {
         data: "AhBWsvywZT5F4IPs50j54l1VCOCh57fTKxEAAAAAAADwPxqUAQIETmV3cw",
         signature: "82e9922a839d666733d93b077b7e67d858122bd7ef21c8ddbb8e26a8",
         key: "-----BEGIN PUBLIC KEY----- -----END PUBLIC KEY-----"
      }
    }
  }

```

This endpoint returns the sender’s public key, data signature, and payload so the Client can validate them.

### HTTP Request

`GET /api/v1/entries/<entityId>/<id>/validate`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| CHAINID    | Id of the original entry      |
| ID    | Id of the specific changeset      |




## Get linked items to the specific revision of an Entry

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/1cedf4ab-befd-44aa-b31b-86d612f4068e/links

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "links": [
        {
          "id": "243cbe46-2cce-402d-9307-c8c16ed07b26",
          "hash": "0xfaf04d916adc4ed24bd5e1a035b2f2369dbf7538498ba9e69fe2499d13422336",
          "_ts": "2017-08-21T07:35:44.937Z",
          "revision": 1,
          "chainId": null,
          "entityId": "3feb4353-393c-4021-afdb-2e1f8ef1aa6b",
          "links": [ ],
          "tx": {
            "blockHash": "0xfab1d2c44eb709c3fd2e145b9485d9633f6ea156d65ec2d814e6ac2ec4140af8",
            "blockNumber": "0x4db4",
            "condition": null,
            "creates": "0xa4756da0eff5cdd8c558c4aba715ee03f677c9b0",
            "from": "0x0004a1af9de734f8ddab0d47c803cf301038d874",
            "gas": "0xe57e0",
            "gasPrice": "0x0",
            "hash": "0xfaf04d916adc4ed24bd5e1a035b2f2369dbf7538498ba9e69fe2499d13422336",
            "input": "0x3339613838653834313234313939383233737656656636303133646163643235656637386161",
            "networkId": 8995,
            "nonce": "0x232236",
            "publicKey": "0x16dbef0da60ba94f7583b79d6b9b1d40eca9854529ac2c23cd9b5e0e92be344e38aae5c7",
            "r": "0x1c471fcdd60ac0c8e0903624aec1481e635069d561004a69faa4234a4150d752",
            "raw": "0xf891656634300ac0c8e0903624aec1481e635069d5447de7c64a374b23118e5404b69847b47eaa",
            "s": "0x7efc4ed33b3f2fb49251e1b14587447de7c64a374b23118e5404b69847b47eaa",
            "standardV": "0x0",
            "to": null,
            "transactionIndex": "0x0",
            "v": "0x4669",
            "value": "0x0"
          },
          "values": {
            "_ts": "2017-07-24T11:53:20.108Z",
            "target": "1cedf4ab-befd-44aa-b31b-86d612f4068e"
            "incident": "test"
          }
        }
      ]
    }
  }

```

This endpoint returns a list of Entries that are associated with a specific Entry in the revision chain.

### HTTP Request

`GET /api/v1/entries/<entityId>/<id>/links`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| CHAINID    | Id of the original entry      |
| ID    | Id of the specific changeset      |
| ENTITYID    | Id of the entity, which items you want to see      |
| LIMIT    | [Optional] Limit of number of fetched devices. Default value: 0      |
| OFFSET    | [Optional] Number of devices to skip. Default value: 5      |




## Get specific revision of the Entry

```shell

 curl \
   -X GET \
   "https://compliance-guard.lan/api/v1/entries/1cedf4ab-befd-44aa-b31b-86d612f4068e/1cedf4ab-befd-44aa-b31b-86d612f4068e"

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entry": {
        "id": "d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "hash": "0xc0dbcf141450cbe2e0be538db7b7a1242f464660bf8bc580bc1b86b84d1407d2",
        "_ts": "2017-07-24T11:53:20.108Z",
        "revision": 1,
        "chainId": null,
        "entityId": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
        "values": {
          "incident": "test",
          "explanation": "test reason"
        }
      }
    }
  }

```

This endpoint returns a specific revision of an Entry in a revision chain.

### HTTP Request

`GET /api/v1/entries/<entityId>/<id>`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| CHAINID    | Id of the original entry      |
| ID    | Id of the specific changeset      |


