# Draft



## Add Draft

```shell

 curl \
  -X POST \
  -H "Content-Type: application/json" \
  -d '{"name": "logbook", "mixins": [], "fields": [{"name": "incident", "type": "text"}]}' \
  https://compliance-guard.lan/api/v1/drafts

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "draft": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3"
        "name": "logbook",
        "mixins": [],
        "fields": [
          {
            "type": "text",
            "name": "incident"
          }
        ]
      }
    }
  }

```

Use this method to construct new Entities or new versions of an Entity.

### HTTP Request

`POST /api/v1/drafts`

### Payload Attributes

| Attribute | Description |
|-----------|-------------|
| NAME    | Name of the draft      |
| MIXINS   | Array of used mixins      |
| FIELDS   | Array of fields, which entries of this type will have      |




## Get Draft

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/drafts/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "draft": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "name": "logbook",
        "mixins": [],
        "fields": [
          {
            "type": "text",
            "name": "incident"
          }
        ]
      }
    }
  }

```

Use this method to get the information about a Draft.

### HTTP Request

`GET /api/v1/drafts/<id>`

### URL Parameters

| Parameter | Description |
|-----------|-------------|
| ID    | ID of the desired draft      |





## Get list of Drafts

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entities?name=logbook&limit=5

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "drafts": [
        {
          "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
          "name": "logbook",
          "mixins": [],
          "fields": [
            {
              "type": "text",
              "name": "incident"
            }
          ]
        }
      ]
    }
  }

```

This endpoint returns a list of all the current Drafts.

### HTTP Request

`GET /api/v1/drafts`

### URL Parameters

| Parameter | Description |
|-----------|--------|
| NAME    | [Optional] Name of the desired draft
| LIMIT    | [Optional] Limit of number of fetched drafts. Default value: 0
| OFFSET    | [Optional] Number of drafts to skip. Default value: 5




## Update Draft

```shell

 curl \
   -X PUT \
   -H "Content-Type: application/json" \
   -d '{"name": "logbook", "mixins": [], "fields": [{"name": "timestamp", "type": "date"}]}' \
   https://compliance-guard.lan/api/v1/drafts/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "draft": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "name": "logbook",
        "mixins": [],
        "fields": [
          {
            "type": "date",
            "name": "timestamp"
          }
        ]
      }
    }
  }

```

Use this method to update a Draft.

### HTTP Request

`PUT /api/v1/drafts/<id>`

### Payload Attributes

| Parameter | Description |
|-----------|-------------|
| ID     | ID of the desired draft      |
| NAME     | [Optional] New name of the draft      |
| MIXINS   | [Optional] New array of used mixins      |
| FIELDS   | [Optional] New array of fields, which entries of this type will have      |




## Delete Draft

```shell

 curl \
   -X DELETE \
   https://compliance-guard.lan/api/v1/drafts/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

Use this method to delete a Draft.

### HTTP Request

`DELETE /api/v1/drafts/<id>`

### URL Parameters

| Parameter | Description |
|-----------|-------------|
| ID     | ID of the desired draft  |



