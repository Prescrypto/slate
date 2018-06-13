---
title: CGB XMLENDPOINT API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

toc_footers:
  - <a href='https://www.cgblockchain.com/'>About CGB</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the CGB Xmlendpoint API! 

We have language bindings in Shell(Curl)! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

Follow the next steps to know how to use our API. Let's doing!

# Authentication

> To authorize, use this code:

```shell
curl -X POST \
  https://cgb-pw.herokuapp.com/user/login \
  -H 'Content-Type: application/json' \
  -d '{
      "email": "jesus@prescrypto.com",
      "password": "admin1234"
    }'
```

> The above command returns JSON structured like this:

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjcmVhdGVkQXQiOjE1Mjg5MDUyNzM1MjMsInVwZGF0ZWRBdCI6MTUyODkwNTI3MzUyMywiaWQiOiI1YjIxM2UzOTNmNTljYTAwMTRiZmFmNzMiLCJlbWFpbCI6Implc3VzQHByZXNjcnlwdG8uY29tIiwiaWF0IjoxNTI4OTIyODM3LCJleHAiOjE1Mjg5MjY0Mzd9.CsSQDQonYQqphi9BNKaWDt6lXJ5-vSa09B5MRBwIV-o"
}
```

> Make sure to replace `<TOKEN>` with your API key.

XMLEndpoint uses API keys to allow access to the API. 

XMLEndpoint expects for the API key to be included in all API requests to the server in a header that looks like the following: 

`Authorization: Bearer <TOKEN>`

<aside class="notice">
You must replace <code><TOKEN></code> with your personal API key.
</aside>

# Users

> To create new user, use this code:

```shell
curl -X POST https://cgb-pw.herokuapp.com/user \
  -H 'Content-Type: application/json' \
  -d '{
      "email": "user@company.com",
      "password": "adminpassword"
    }'
```

> The above command returns JSON structured like this:

```json
{
    "createdAt": 1528922588700,
    "updatedAt": 1528922588700,
    "id": "5b2181dc2b68440014bf661e",
    "email": "user@company.com"
}
```

Must have an user before authenticate, and use our API.

So following the next steps you will have an `user` and `password`

Parameter | Description
--------- | -----------
email | String email of user
password | String password keep in safe place 



# xmlendpoint

## Get All XMLs



```shell

```


> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Max",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all xmlendpoint.

### HTTP Request

`GET https://cgb-pw.herokuapp.com/xmlendpoint`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include xmlendpoint that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```shell
curl "https://cgb-pw.herokuapp.com/xmlendpoint/2"
  -H "Authorization: <TOKEN>"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/xmlendpoint/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten


```shell
curl "https://cgb-pw.herokuapp.com/xmlendpoint/<ID>"
  -X DELETE
  -H "Authorization: <TOKEN>"
```


> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "deleted" : ":("
}
```

This endpoint deletes a specific kitten.

### HTTP Request

`DELETE http://example.com/xmlendpoint/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

