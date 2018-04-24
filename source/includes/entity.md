# Entity



## Get table constructor

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entities/table-description/<NAME>

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entity": {
        "id": "0dc26cc0-335c-40a7-ba5b-7f754693736a",
        "hash": "0x8b52b173e82b57487c16c701bea5f4fb18088f11de10345e300baa7d55659865",
        "name": <name>,
        "version": 1,
        "archived": false,
        "mixins": [ ],
        "fields": [
          {
            "type": "text",
            "name": "incident"
          },
          {
            "type": "text",
            "name": "explanation"
          },
        ]
      }
    }
  }

```

This endpoint returns an Entity with the entire set of Fields, that are needed to show to Users.

### HTTP Request

`GET /api/v1/entities/table-description/<name>`

### URL Parameters

| Attribute | Description |
|----------|-----------|
| NAME    | Name of the entity      |





## Add Entity

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"name": "logbook", "mixins": [], "fields": [{"name": "incident", "type": "text"}]}' \
   https://compliance-guard.lan/api/v1/entities

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entity": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "hash": "0x75d1ca7acd7ef942e062022c944ef99b34ead44fb7e134970b9c292cfc432891",
        "name": "logbook",
        "version": 1,
        "archived": false,
        "mixins": [],
        "fields": [
          {
            "type": "text",
            "name": "incident"
          },
          {
            "type": "text",
            "name": "explanation"
          },
        ]
      }
    }
  }

```

This endpoint adds an Entity.

### HTTP Request

`POST /api/v1/entities`

### Payload Attributes

| Parameter | Type   | Description |
|----------|-----------|
| NAME    | Name of the entity      |
| MIXINS     | String[] | Array of used mixins      |
| FIELDS     | String[] | Array of fields, which entries of this type will have      |




## Link Entities to each other

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"local": "3feb4353-393c-4021-afdb-2e1f8ef1aa6b", "localField": "target", "target": "9c8e2eea-4003-4e8e-b47b-7fcfbc1e9fd8", "targetField": "id"}'
   https://compliance-guard.lan/api/v1/entities/links

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "link": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "hash": "0x75d1ca7acd7ef942e062022c944ef99b34ead44fb7e134970b9c292cfc432891",
        "local" : "3feb4353-393c-4021-afdb-2e1f8ef1aa6b",
        "localField" : "target",
        "target" : "9c8e2eea-4003-4e8e-b47b-7fcfbc1e9fd8",
        "targetField" : "id"
      }
    }
  }

```

This endpoint links two Entities between to each other.

### HTTP Request

`POST /api/v1/entities/links`

### URL Parameters

| Parameter | Type   | Description |
|----------|-----------|
| local    | Id of an entity, which must be linked      |
| localField    | Name of field, which will be contain foreign key value      |
| target    | Id of an entity, to which 'local' entity is linked      |
| targetField    | Name of field, which one will be foreign key field      |




## Get Entity by ID

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entities/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entity": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "hash": "0x75d1ca7acd7ef942e062022c944ef99b34ead44fb7e134970b9c292cfc432891",
        "name": "logbook",
        "version": 1,
        "archived": false,
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

This endpoint returns an Entity when its ID is provided.

### HTTP Request

`GET /api/v1/entities/<id>`

### URL Parameters

| Parameter | Type   | Description |
|----------|-----------|
| id    | Id of the desired entity      |





## Get Entity by Name

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/entities/logbook

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "entity": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "hash": "0x75d1ca7acd7ef942e062022c944ef99b34ead44fb7e134970b9c292cfc432891",
        "name": "logbook",
        "version": 1,
        "archived": false,
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

This endpoint returns an Entity when its given Name is provided.

### HTTP Request

`GET /api/v1/entities/<name>`

### URL Parameters

| Parameter | Type   | Description |
|----------|-----------|
| NAME    | Name of the desired entity      |





## Get list of Entities

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
      "entities": [
        {
          "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
          "hash": "0x75d1ca7acd7ef942e062022c944ef99b34ead44fb7e134970b9c292cfc432891",
          "name": "logbook",
          "version": 1,
          "archived": false,
          "mixins": [],
          "fields": [
            {
              "type": "text",
              "name": "incident"
            }
          ],
        }
      ]
    }
  }

```

This endpoint returns an array of Entities.

### HTTP Request

`GET /api/v1/entities`

### URL Parameters

| Parameter | Description |
|----------|-----------|
| NAME    | [Optional] Name of the desired entity      |
| LIMIT    | [Optional] Limit of number of fetched entities. Default value: 0      |
| OFFSET    | [Optional] Number of entities to skip. Default value: 5      |




## Send Entity to archive

```shell

 curl \
   -X DELETE \
   https://compliance-guard.lan/api/v1/entities/logbook

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

Use this method to archive an Entity.

### HTTP Request

`DELETE /api/v1/entities/<name>`

### URL Parameters

| Parameter | Type   | Description |
|----------|-----------|
| NAME    | Name of the desired entity      |



