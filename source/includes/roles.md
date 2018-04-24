# Role



## Add Role

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"name":"Manager Role", "slugname":"manager", "permissions":[]}' \
   https://compliance-guard.lan/api/v1/system/roles

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "role": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "name": "Manager Role",
        "slugname": "manager",
        "permissions": [ ]
      }
    }
  }

```

This endpoint adds a User Role to the system.

### HTTP Request

`POST /api/v1/system/roles`

### Payload Attributes

| Attribute | Description |
|----------|------------|
| SLUGNAME    | Role name      |
| NAME    | Human-readable name      |
| PERMISSIONS     | Object[] Permissions granted to this role      |




## Get Role

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/roles/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "role": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "name": "Manager Role",
        "slugname": "manager",
        "permissions": [ ]
      }
    }
  }

```

Use this method to get the basic information about a User Role.

### HTTP Request

`GET /api/v1/fields/<id>`

### URL Parameters

| Parameter | Description |
|----------|------------|
| ID    | Role id      |





## Get list of Roles

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/roles?name=manager&limit=5

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "fields": [
        {
          "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
          "name": "Manager Role",
          "slugname": "manager",
          "permissions": [ ]
        }
      ]
    }
  }

```

This endpoint returns an array of User Roles.

### HTTP Request

`GET /api/v1/system/roles`

### URL Parameters

| Parameter | Description |
|----------|------------|
| NAME    | Human-readable name      |
| LIMIT    | [Optional] Limit of number of fetched drafts. Default value: 0      |
| OFFSET    | [Optional] Number of drafts to skip. Default value: 5      |




## Update Role

```shell

 curl \
   -X PUT \
   -H "Content-Type: application/json" \
   -d '{"name":"Manager Role", "slugname":"manager", "permissions":[]}' \
   https://compliance-guard.lan/api/v1/system/roles/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "role": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "name": "Manager Role",
        "slugname": "manager",
        "permissions": [ ]
      }
    }
  }

```

Use this method to update the name and permissions of a Role.

### HTTP Request

`PUT /api/v1/system/roles/<id>`

### URL Parameters

| Parameter | Description |
|----------|------------|
| ID    | Role id      |
| SLUGNAME    | [Optional] Role name      |
| NAME    | [Optional] Human-readable name      |
| PERMISSIONS     | Object[] | [Optional] Permissions granted to this role      |




## Delete Role

```shell

 curl \
   -X DELETE \
   https://compliance-guard.lan/api/v1/roles/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

Use this method to delete a Role.

### HTTP Request

`DELETE /api/v1/drafts/<id>`

### URL Parameters

| Parameter | Description |
|----------|------------|
| ID    | Role id      |



