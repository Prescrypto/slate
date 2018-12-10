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

<aside class="notice">
Notice that a token only will send to valid emails
</aside>


# Documents

## Document with Github URL or Overleaf URL

```python
import requests

url = "http://api.wpci.io/api/v1/renderrepohash"

payload = {
    "remote_url":"https://git.overleaf.com/22178387mvzzshhfsypt",
    "email":"name@organization.com",
     "email_body_html":"<p>New body for email</p>"
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
  http://api.wpci.io/api/v1/renderrepohash \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json' \
  -d '{"remote_url":"https://git.overleaf.com/22178387mvzzshhfsypt", 		 "email":"name@organization.com",
   "email_body_html":"<p>New body for email</p>"}'
```


> The above command returns JSON structured like this:

```json
{"response": "done"}
```

This endpoint will send the document to the email specified in the payload.

Parameter | Description
--------- | -----------
token | Bearer <Token> setup on headers
remote_url | The url for github or Overleaf document (String)
email | The url of the person you want to send the document rendered and signed 
email_body_html | A customized HTML body for the email sent with the document (this is optional) 

### Render or share a document
> This is an example of the full Url to render a Document

```html
https://api.wpci.io/docs/pdf/<DOCUMENT ID>
```

To render a document already created you just need the document ID and the Base url.

You can get the Document ID or the full url path by clicking the copy button on 

` https://api.wpci.io/docs/view_docs`

The base url is:

` https://api.wpci.io/docs/pdf/`

And the ID would look like the following:

` Rexchain_1538518131252`



This full URL will render the PDF and ask you to sign so you can get the document and if present, the NDA.

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve
Base Url | The main Url of the Document 
