# Devices



## Add New Device

> To create new Order, use this code:

```shell
 # With curl, you can just pass the correct header with each request
 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"name": "cgbox1", "hash": "0x0004a1af9de734f8ddab0d47c803cf301038d874"}' \
   https://compliance-guard.lan/api/v1/system/device

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "device": {
        "id":"d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "name": "cgbox1",
        "hash":"0x0004a1af9de734f8ddab0d47c803cf301038d874"
      }
    }
  }

```

This can be used to establish a new ComplianceGuard hardware unit. This endpoint stores the new Device’s info to the ComplianceGuard database for authorization. Usually the Integrator who connects the EMS or OMS to ComplianceGuard is resposible for this.

### HTTP Request

`POST /api/v1/system/devices`

### Payload Attributes

| Attribute | Description |
|---------|-----------|
| NAME  | Human-readable name of device      |
| HASH  | Blockchain hash of an account, associated with this device      |




## Get Device

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/devices/d0691c48-ad21-45db-bbd6-f32aa264d1ad

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "device": {
        "id":"d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "name": "cgbox1",
        "hash":"0x0004a1af9de734f8ddab0d47c803cf301038d874"
      }
    }
  }

```

This endpoint will return the basic information about the Device.

### HTTP Request

`GET /api/v1/system/devices/<id>`

### URL Parameters

| Parameter | Description |
|-----------|-------------|
| ID    | Id of the desired device      |





## Get list of Devices

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/devices?name=cgbox1&limit=5

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "devices": [
        {
          "id":"d0691c48-ad21-45db-bbd6-f32aa264d1ad",
          "name": "cgbox1",
          "hash":"0x0004a1af9de734f8ddab0d47c803cf301038d874"
        }
      ]
    }
  }

```

This endpoint returns an array of all the Devices defined in one Client’s system.

### HTTP Request

`GET /api/v1/system/devices`

### URL Parameters

| Parameter | Description |
|-----------|-------------|
| NAME     | [Optional] Human-readable name of device      |
| HASH     | [Optional] Blockchain hash of an account, associated with this device      |
| LIMIT     | [Optional] Limit of number of fetched devices. Default value: 0      |
| OFFSET     | [Optional] Number of devices to skip. Default value: 5      |




## Update Device

```shell

 curl \
   -X PUT \
   -H "Content-Type: application/json" \
   -d '{"name": "cgbox2"}' \
   https://compliance-guard.lan/api/v1/system/devices/d0691c48-ad21-45db-bbd6-f32aa264d1ad

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "device": {
        "id":"d0691c48-ad21-45db-bbd6-f32aa264d1ad",
        "name": "cgbox2",
        "hash":"0x0004a1af9de734f8ddab0d47c803cf301038d874"
      }
    }
  }

```

Use this method to updates the information about a specific Device.

### HTTP Request

`PUT /api/v1/system/devices/<id>`

### URL Parameters

| Parameter | Type   | Description |
|---------|-----------|
| ID     | of the desired device      |





## Delete Device

```shell

 curl \
   -X DELETE \
   https://compliance-guard.lan/api/v1/system/devices/d0691c48-ad21-45db-bbd6-f32aa264d1ad

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

Use this method to delete the information about a specific Device.

### HTTP Request

`DELETE /api/v1/system/devices/<id>`

### URL Parameters

| Parameter | Type   | Description |
|---------|-------------|
| ID     | of the desired device      |



