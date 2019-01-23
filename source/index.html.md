---
title: WPCI API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python

toc_footers:
  - <a href='https://api.wpci.io/api/v1/register'>Sign Up for a Developer Key</a>
  - <a href='https://www.prescrypto.com'>WPCI is Powered by Prescrypto</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the WPCI API! You can use this API to create new, custom links, review a document's status.

The process is the following:

- You need to create an account on wpci.io, register and get your access token,
- Once your account is created, register your company's details and create a document, you should get a distinct document id. This involves granting access to a Github or Google Docs template,
- Using this document id, you can create new links for the document using the [**"Create, get or delete a document link"**](#to-create "Create, get or delete a document link") endpoint, check the status (signed or not signed) and cancel links,
- Check statistics and status of links whenever you want from your [wpci.io](https://api.wpci.io "WPCI Admin Panel") admin panel.
- Ask for help, we're here to make it easy for you: hola (at) prescrypto.com

Please check back soon on our guide to creating templates. You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right. Feel free to contact us at: hola (at) prescrypto.com with any questions.


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

##To Get the document information

This endpoint will respond with all the document information, to get it you need to include the corresponding document ID as following:

```shell
curl -X GET \
  https://api.wpci.io/api/v1/documents/<DOCUMENT_ID> \
   -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json'
```

```python
import requests

url = "https://api.wpci.io/api/v1/documents/<DOCUMENT_ID>"
payload = ""
headers = {
'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
}

response = requests.get(url, data=payload, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
	"org_id": "ORGANIZATION ID", 
	"wp_name": "NAME", 
	"wp_url": "https://docs.google.com/presentation/d/<YOUR DOCUMENT ID>/edit?usp=sharing", 
	"redirect_url": "", 
	"wp_description": "Click on the Get it! button and enter your email so we can send you a copy of                         this document to your email.", 
	"wp_getit_btn": "To get the complete document please check this box and fill the following fields", 
	"main_tex": "main.tex", 
	"nda_url": "", 
	"render": "google", 
	"link_count": 4, 
	"view_count": 0, 
	"down_count": 0, 
	"date": 1547489479, 
	"doc_id": "<DOCUMENT_ID>"
}
```

| Parameter | Description                        |
| --------- | ---------------------------------- |
| ID        | The ID of the document to retrieve |
| token     | Bearer <Token> setup on headers    |


## To get the PDF

This endpoint will respond with the document as a base 64 PDF file, to get it you need to include the corresponding document ID as following:

```python
import requests

url = "http://api.wpci.io/api/v1/documents/pdf/<DOCUMENT_ID>"

payload = ""
headers = {
    'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
    }

response = requests.get(url, json=payload, headers=headers)

print(response.text)
```

```shell
curl -X POST \
  http://api.wpci.io/api/v1/documents/pdf/<DOCUMENT_ID> \
  -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json' 
```

> The above command returns JSON structured like this:

```json
{"document": "<BASE64 Bytes>"}
```


Parameter | Description
--------- | -----------
ID | The ID of the document to retrieve
token | Bearer <Token> setup on headers    


# Links

##To create

This endpoint will create a new link from an already created document

```shell
curl -X POST \
  https://api.wpci.io/api/v1/documents/links/<DOCUMENT_ID> \
   -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json'
```

```python
import requests

url = "https://api.wpci.io/api/v1/documents/links/<DOCUMENT_ID>"
payload = ""
headers = {
'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
}

response = requests.post(url, data=payload, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
	"doc_id": "<DOCUMENT_ID>", 
	"status": "unsigned", 
	"view_count": 0, 
	"signed_count": 0, 
	"version": "0", 
	"link": "https://api.wpci.io/docs/pdf/<LINK_ID>"
	}
```
Parameter | Description
--------- | -----------
ID | The ID of the document to retrieve
token | Bearer <Token> setup on headers   

##To get the information

```shell
curl -X GET \
  https://api.wpci.io/api/v1/documents/links/<LINK_ID> \
   -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json'
```

```python
import requests

url = "https://api.wpci.io/api/v1/documents/links/<LINK_ID>"
payload = ""
headers = {
'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
}

response = requests.get(url, data=payload, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{
	"doc_id": "<DOCUMENT_ID>", 
	"status": "unsigned", 
	"view_count": 0, 		
	"signed_count": 0, 
	"version": "0", 
	"link": "https://api.wpci.io/docs/pdf/<LINK_ID>"
	}
```

Parameter | Description
--------- | -----------
link_id | This is the ID of the link, provided in your dashboard 
token | Bearer <Token> setup on headers 

##To delete the link

```shell
curl -X DELETE \
  https://api.wpci.io/api/v1/documents/links/<LINK_ID> \
   -H 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc' \
  -H 'Content-Type: application/json'
```

```python
import requests

url = "https://api.wpci.io/api/v1/documents/links/<LINK_ID>"
payload = ""
headers = {
'Authorization': "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1niJ9.eyJleHAiOjE1NDQzMTI3MTQsImlhdCI6MTU0NDIyMjcxNCwidXNlcm5hbWUiOiJqZXN1cyt0ZXN0QHByZXNjcnlwdG8uY29tIiwicGFzc3dvcmQiOiJhZG1pbjEyMzQifQ.oJGDZuVQbiUrw2j3eGZW_liyV9kWUQKGAlIMszIEwSc",
    'Content-Type': "application/json"
}

response = requests.request("DELETE", url, data=payload, headers=headers)

print(response.json())
```

> The above command returns JSON structured like this:

```json
{"response": "link deleted"}
```


Parameter | Description
--------- | -----------
link_id | This is the ID of the link, provided in your dashboard 
token | Bearer <Token> setup on headers 

