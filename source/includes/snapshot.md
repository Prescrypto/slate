# Snapshot



## Get Snapshot

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/snapshots/d0691c48-ad21-45db-bbd6-f32aa264d1ad
  ```

> The above command returns JSON structured like this:



Use this method to obtain a full download of the data stored on a Client’s Device or collection of Devices. This data can then be given to an auditor for analysis.

### HTTP Request

`GET /api/v1/system/snapshots/<id>`

### URL Parameters

| Attribute | Description |
|----------|-----------|
| ID   | Id of the desired snapshot      |





## Start Building Snapshot

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"phone": "3752901234567"}' \
   https://compliance-guard.lan/api/v1/system/snapshots

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "snapshot": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3"
      }
    }
  }

```

Use this method to initiate the process of building a Snapshot. This starts the background task of dumping the blockchain and returns an id of this task.

### HTTP Request

`POST /api/v1/system/snapshots`

### Payload Attributes

| Parameter  | Description |
|----------|-----------|
| PHONE   | Phone number, to which SMS notification will be send, with private key to decrypt snapshot      |



