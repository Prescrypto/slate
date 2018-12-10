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

First you need to create an account on: 

[https://api.wpci.io/docs/register](https://api.wpci.io/docs/register)

> Then you can get the API Token by using your user name and password as following:

```python
import requests

url = "https://api.wpci.io/api/v1/login"

payload = {
    "username": "youruser@yourcompany.com",
    "password": "password"
}
headers = {
    'Content-Type': "application/json",
}

response = requests.post(url, json=payload, headers=headers)

print(response.text)
```

```shell
curl -X POST \
  https://api.wpci.io/api/v1/login \
  -d '{"username":"youruser@yourcompany.com","password":"password"}'
```

> Make sure to replace the user name and password with your own credentials.
> The above command returns JSON structured like this:

```json
{
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc"
}
```

WPCI expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <TOKEN>`

<aside class="notice">
You must replace <code><span><</span>TOKEN></code> with your personal API Token key.
</aside>

# Documents

## Create or delete a document link

You can dynamically create or delete unique links to your already created documents with the following code:

```shell
curl -X POST \
  https://api.wpci.io/api/v1/doc_edit \
   -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json' \
  -d '{"doc_id":"<DOCUMENT ID>","action":"create"}'
```

```python
import requests

url = "https://api.wpci.io/api/v1/doc_edit"

payload = {
   "doc_id":"<DOCUMENT ID>",
   "action":"create"
}
headers = {
'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
}

response = requests.post(url, json=payload, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
    "status":"created", 
    "doc_link": "https://api.wpci.io/docs/pdf/myDocumentIDandVersion"
}
```
> or

```json
{
    "status":"deleted", 
}
```


Parameter | Description
--------- | -----------
action | "create" or "delete" are the two options to interact with the document 
doc_id | This is the ID of the document, provided in your dashboard 
token | Bearer <Token> setup on headers 



## Document status

You can get the current status of your document 

```python
import requests

url = "http://api.wpci.io/api/v1/doc_status"

payload = {
    "doc_id":"<DOCUMENT ID>"
    }
headers = {
    'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
    }

response = requests.post(url, json=payload, headers=headers)

print(response.text)
```

```shell
curl -X POST \
  http://api.wpci.io/api/v1/doc_status \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json' \
  -d '{"doc_id":"<DOCUMENT ID>"}'
```

> The above command returns JSON structured like this:

```json
{"status": "signed"}
```

> or

```json
{"status": "unsigned"}
```



Parameter | Description
--------- | -----------
token | Bearer <Token> setup on headers
doc_id | This is the ID of the document, provided in your dashboard 



## Get the Document

This endpoint will respond with the document as a base 64 PDF file, to get it you need to include the corresponding document ID as following:

```python
import requests

url = "http://api.wpci.io/api/v1/doc_get"

payload = {
    "doc_id":"<DOCUMENT ID>"
    }
headers = {
    'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
    }

response = requests.post(url, json=payload, headers=headers)

print(response.text)
```

```shell
curl -X POST \
  http://api.wpci.io/api/v1/doc_get \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json' \
  -d '{"doc_id":"<DOCUMENT ID>"}'
```

> The above command returns JSON structured like this:

```json
{"document": "<BASE64 Bytes>"}
```


Parameter | Description
--------- | -----------
ID | The ID of the document to retrieve
token | Bearer <Token> setup on headers    

