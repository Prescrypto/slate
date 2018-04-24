# Field



## Add Field

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"name":"text", "type":"text", "encodings":["utf8", "ascii", "base64", "binary"], "transformers":["trim", "replace"], "validators":["notEmpty", "maxLength", "minLength"]}' \
   "https://compliance-guard.lan/api/v1/fields"

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "field": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "name": "text",
        "type": "text",
        "validators": [
          "notEmpty",
          "maxLength",
          "minLength"
        ],
        "transformers": [
          "trim",
          "replace"
        ],
        "encodings": [
          "utf8",
          "ascii",
          "base64",
          "binary"
        ]
      }
    }
  }

```

This endpoint adds a Field, that can later be used to describe as part of an Entity structure.

### HTTP Request

`POST /api/v1/fields`

### Payload Attributes

| Attribute | Description |
|----------|-----------|
| NAME     | Field name      |
| TYPE     | Base types associated to this field      |
| ENCODINGS     | Available encodings      |
| TRANSFORMERS     | Available transformers      |
| VALIDATORS     | Available validators      |




## Get Field

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/fields/text

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "field": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3"
        "name": "text",
        "type": "text",
        "validators": [
          "notEmpty",
          "maxLength",
          "minLength"
        ],
        "transformers": [
          "trim",
          "replace"
        ],
        "encodings": [
          "utf8",
          "ascii",
          "base64",
          "binary"
        ]
      }
    }
  }

```

This endpoint returns a Field, by its given Name.

### HTTP Request

`GET /api/v1/fields/<name>`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| NAME     | Field name      |





## Get list of Fields

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/fields?limit=5

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "fields": [
        {
          "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3"
          "name": "text",
          "type": "text",
          "validators": [
            "notEmpty",
            "maxLength",
            "minLength"
          ],
          "transformers": [
            "trim",
            "replace"
           ],
          "encodings": [
            "utf8",
            "ascii",
            "base64",
            "binary"
          ],
        }
      ]
    }
  }

```

This endpoint returns an array of Fields

### HTTP Request

`GET /api/v1/fields`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| LIMIT     | [Optional] Limit of number of fetched drafts. Default value: 0      |
| OFFSET     | [Optional] Number of drafts to skip. Default value: 5      |




## Update Field

```shell

 curl \
   -X PUT \
   -H "Content-Type: application/json" \
   -d '{"name":"text", "type":"text", "encodings":["utf8", "ascii", "base64", "binary"], "transformers":["trim", "replace"], "validators":["notEmpty", "maxLength", "minLength"]}' \
   https://compliance-guard.lan/api/v1/drafts/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
      "field": {
        "name": "text",
        "type": "text",
        "validators": [
          "notEmpty",
          "maxLength",
          "minLength"
        ],
        "transformers": [
          "trim",
          "replace"
        ],
        "encodings": [
          "utf8",
          "ascii",
          "base64",
          "binary"
        ]
      }
    }
  }

```

Use this method to update a Field.

### HTTP Request

`PUT /api/v1/fields/<name>`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| NAME     | Field name      |
| TYPE     | [Optional] Base types associated to this field      |
| ENCODINGS     | [Optional] Available encodings      |
| TRANSFORMERS     | [Optional] Available transformers      |
| VALIDATORS     | [Optional] Available validators      |




## Delete Field

```shell

 curl \
   -X DELETE \
   https://compliance-guard.lan/api/v1/fields/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

Use this method to delete a Field.

### HTTP Request

`DELETE /api/v1/drafts/<name>`

### URL Parameters

| Parameter  | Description |
|----------|-----------|
| NAME     | Field name      |



