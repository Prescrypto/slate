---
title: CryptoSign API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - python

toc_footers:
  - <a href='http://www.cryptosign.info/login/'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the CryptoSign API Documentation! You can use our API to access Cryptosign API endpoints, which can get information about how auth and to send payloads to retrieve a pdf signed.

We have language bindings in curl on shell and Python! You can view code examples in the dark area to the right, and you can switch the programming language of the examples with the tabs in the top right.

# Authentication

> To authorize, use this code:

```shell
# With curl, you can just pass the correct header with each request
curl -X POST \
  -d "grant_type=password&username=<username>&password=<password>" \
  -u "<client_id>:<client_secret>" http://www.cryptosign.info/oauth/token/

```

```python
import requests
from requests.auth import HTTPBasicAuth
headers = {
  "Content-Type" : "application/json"
}
data = {
  "grant_type" : "password",
  "username" : "<username>",
  "password" : "<password>"
}
auth = HTTPBasicAuth('<client_id>', '<client_secret>')

response = requests.post('http://www.cryptosign.info/oauth/token/',
            auth=auth, json=data, headers=headers)

```

> The above command returns JSON structured like this:

```json
{
    "scope": "cryptosign write read",
    "access_token": "12hRiSaV7M97hILdzEBpc3IgIBhyKB",
    "expires_in": 36000,
    "refresh_token": "MF7sNeG7AoCnGhpyJxncyjDRvr5Mn5",
    "token_type": "Bearer"
}
```

> Make sure to replace `<username>` with your username, `<password>` with your password, `<client_id>` with your client ID and `<client_secret>` with your client secret key.

Cryptosign uses API keys with Oauth authetication to allow access to the API. You can register a new Cryptosign API key at our [developer portal](http://www.cryptosign.info/oauth/applications/).

Cryptosign expects for the Token Access to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer meowmeowmeow`

<aside class="notice">
You must replace <code>meowmeowmeow</code> with your personal API key.
Just be sure that <code>Authorization grant type</code> is set to <code>Resource owner password-cased</code> when create a new Application API.
</aside>

# Payload

## Get the PDF Crypto Signed!

```shell
curl -X POST \
  http://www.cryptosign.info/api/v1/sign/ \
  -H 'authorization: Bearer 12hRiSaV7M97hILdzEBpc3IgIBhyKB' \
  -H 'content-type: application/json' \
  -d '{
  "timezone": "America/Mexico_City",
  "pdf":"JVBERi0xLjcKCjEgMCBvYmogICUgZW50cnkgcG9pbnQKPDwKICAvVHlwZSAvQ2F0YWxvZwogIC9QYWdlcyAyIDAgUgo+PgplbmRvYmoKCjIgMCBvYmoKPDwKICAvVHlwZSAvUGFnZXMKICAvTWVkaWFCb3ggWyAwIDAgMjAwIDIwMCBdCiAgL0NvdW50IDEKICAvS2lkcyBbIDMgMCBSIF0KPj4KZW5kb2JqCgozIDAgb2JqCjw8CiAgL1R5cGUgL1BhZ2UKICAvUGFyZW50IDIgMCBSCiAgL1Jlc291cmNlcyA8PAogICAgL0ZvbnQgPDwKICAgICAgL0YxIDQgMCBSIAogICAgPj4KICA+PgogIC9Db250ZW50cyA1IDAgUgo+PgplbmRvYmoKCjQgMCBvYmoKPDwKICAvVHlwZSAvRm9udAogIC9TdWJ0eXBlIC9UeXBlMQogIC9CYXNlRm9udCAvVGltZXMtUm9tYW4KPj4KZW5kb2JqCgo1IDAgb2JqICAlIHBhZ2UgY29udGVudAo8PAogIC9MZW5ndGggNDQKPj4Kc3RyZWFtCkJUCjcwIDUwIFRECi9GMSAxMiBUZgooSGVsbG8sIHdvcmxkISkgVGoKRVQKZW5kc3RyZWFtCmVuZG9iagoKeHJlZgowIDYKMDAwMDAwMDAwMCA2NTUzNSBmIAowMDAwMDAwMDEwIDAwMDAwIG4gCjAwMDAwMDAwNzkgMDAwMDAgbiAKMDAwMDAwMDE3MyAwMDAwMCBuIAowMDAwMDAwMzAxIDAwMDAwIG4gCjAwMDAwMDAzODAgMDAwMDAgbiAKdHJhaWxlcgo8PAogIC9TaXplIDYKICAvUm9vdCAxIDAgUgo+PgpzdGFydHhyZWYKNDkyCiUlRU9G",
  "signatures" : [
  {
    "hash" : "asdldsalkdsaj21j31kl321jk312jk312",
    "email" : "prueba1@mycompany.io",
    "name" : "Prueba 1"
  },
  {
    "hash" : "sdaklkk213hkj312jkh123hjk123hj2hjk31h",
    "email" : "prueba2@mycompany.io",
    "name" : "Prueba 2"
  }],
  "params" : {
    "title" : "Titulo",
    "file_name" : "prueba.pdf",
    "logo": "YijhuYIOYGkjiphUYIOdgUTdfxYFLAdfKSHdfUOPpY=="
  }
}'
```

> Make sure to replace Bearer 12hRiSaV7M97hILdzEBpc3IgIBhyKB with your own Access Token, get it in the previous step.

```python
import requests

ACCESS_TOKEN = "12hRiSaV7M97hILdzEBpc3IgIBhyKB" # Get it with the previous step.

headers = {
  "Authorization": "Bearer {}".format(ACCESS_TOKEN),
  "Content-Type" : "application/json"
}

data ={
  "timezone" : "America/Mexico_City",
  "pdf":"JVBERi0xLjcKCjEgMCBvYmogICUgZW50cnkgcG9pbnds+aP==",
  "signatures" : [
  {
    "hash" : "asdldsalkdsaj21j31kl321jk312jk312=",
    "email" : "test@mail.io",
    "name" : "Prueba 1"
  },
  {
    "hash" : "sdaklkk213hkj312jkh123hjk123hj2hjk31h=",
    "email" : "hola@mail.io",
    "name" : "Prueba 2"
  }],
  "params" : {
    "title" : "Titulo",
    "file_name" : "Titulo.pdf",
    "logo": "YijhuYIOYGkjiphUYIOdgUTdfxYFLAdfKSHdfUOPpY=="
  }
}

response = requests.post('http://www.cryptosign.info/api/v1/sign/',json=data, headers=headers)

# save it
with open("./myfile.pdf", "wb") as f:
    f.write(response.content)

# or display it
print(response.content)

```


> Your response will be the pdf, just can save it wherever you want.

This endpoint retrieves the pdf crypto signed.

### HTTP Request

`POST http://www.cryptosign.info/api/v1/sign/`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
timezone | "UTC" | A valid timezone string code, Optional field by default "UTC"
pdf | A base64 File String | This is your pdf who is attach it to the signed doc, will be signed every page.
params.title | String | The title of the given pdf
params.file_name | String title | The filename with his extension, `mytitle.pdf`
params.logo | A png base 64 File String | This is your logo who will be show on the signed pdf.
signatures.hash | A hash string | This hash string is the sign of a person, represented as string.
signatures.email | Email String | The email of the person.
signatures.name | String | The name of the person.


<aside class="success">
  Thats all, enjoy creating crypto signed pdf's!
</aside>
<aside class="info">
  You can see what timezones are available here `GET http://www.cryptosign.info/api/v1/timezones/` with your bearer token as Authorization or visit <a href="https://en.wikipedia.org/wiki/List_of_tz_database_time_zones" target="_blank">wikipedia tz list</a>
</aside>
