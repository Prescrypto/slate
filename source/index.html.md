---
title: WPCI API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python

toc_footers:
  - <a href='https://api.wpci.io/api/v1/signin'>Sign Up for a Developer Key</a>
  - <a href='https://www.prescrypto.com'>WPCI is Powered by Prescrypto</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the WPCI API! You can use our API to access WPCI API endpoints.

You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.


# Authentication

> To authorize, use this code:

```python
import requests

url = "https://api.wpci.io/api/v1/login"

payload = {
    "username": "youruser@yourcompany.com",
    "password": "password"
}
headers = {
    'Authorization': "Bearer <TOKEN>",
    'Content-Type': "application/json",
}

response = requests.post(url, json=payload, headers=headers)

print(response.text)
```

```shell
curl -X POST \
  https://api.wpci.io/api/v1/login \
  -H 'Authorization: Bearer <TOKEN>' \
  -d '{"username":"youruser@yourcompany.com","password":"password"}'
```


> Make sure to replace `<TOKEN>` with your API key.


> The above command returns JSON structured like this:

```json
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc"
}
```

WPCI uses API keys to allow access to the API. You can register a new WPCI API key at our [developer portal](https://).

WPCI expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <TOKEN>`

<aside class="notice">
You must replace <code><span><</span>TOKEN></code> with your personal API Token key.
</aside>

## Create user account

```shell
curl -X POST \
  https://api.wpci.io/api/v1/signin \
  -d '{"email":"youruser@yourcompany.com","password":"password"}'
```

```python
import requests

url = "https://api.wpci.io/api/v1/signin"

payload = {
    "email": "youruser@yourcompany.com",
    "password": "password"
}
headers = {
    'Content-Type': "application/json"
}

response = requests.post(url, json=payload, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{"response": "user created successfully"}
```

To get an access token you must have your user and password for WPCI but if you don't have any you can create a new account following next steps.


Parameter | Description
--------- | -----------
email | Valid Email (String)
password | Keep safe your password (String)


# Kittens

## Users

```python
import WPCI

api = WPCI.authorize('<TOKEN>')
api.kittens.get()
```

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: <TOKEN>"
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

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/api/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```python
import WPCI

api = WPCI.authorize('<TOKEN>')
api.kittens.get(2)
```

```shell
curl "http://example.com/api/kittens/2"
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

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

## Delete a Specific Kitten

```python
import WPCI

api = WPCI.authorize('<TOKEN>')
api.kittens.delete(2)
```

```shell
curl "http://example.com/api/kittens/2"
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

`DELETE http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to delete

