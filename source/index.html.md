---
title: CGB XMLENDPOINT API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='https://www.cgblockchain.com/'>About CGB</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the CGB Xmlendpoint API!

We have language bindings in Shell(Curl)! You can view code examples on the right panel.

Let's get started! Follow the next steps to know how to use our API

# Authentication

> To get an auth token, use this code:

```shell
curl -X POST \
  https://cgb-pw.herokuapp.com/api/v1/user/login \
  -H 'Content-Type: application/json' \
  -d '{
      "email": "user@company.com",
      "password": "adminpassword"
    }'
```

> The above command returns JSON structured like this:

```json
{
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJjcmVhdGVkQXQiOjE1Mjg5MDUyNzM1MjMsInVwZGF0ZWRBdCI6MTUyODkwNTI3MzUyMywiaWQiOiI1YjIxM2UzOTNmNTljYTAwMTRiZmFmNzMiLCJlbWFpbCI6Implc3VzQHByZXNjcnlwdG8uY29tIiwiaWF0IjoxNTI4OTIyODM3LCJleHAiOjE1Mjg5MjY0Mzd9.CsSQDQonYQqphi9BNKaWDt6lXJ5-vSa09B5MRBwIV-o"
}
```

> The value of key `"token"` is your API key.

XMLEndpoint uses API keys to allow access to the API.

XMLEndpoint expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Bearer <TOKEN>`

<aside class="notice">
You must replace <strong>TOKEN</strong> with your personal API key.
</aside>

# Users

> To create a new user, use this code:

```shell
curl -X POST \
  https://cgb-pw.herokuapp.com/api/v1/user \
  -H 'Content-Type: application/json' \
  -d '{
      "email": "user@company.com",
      "password": "userpassword"
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

A new user neds to be created prior to authentication and the use of our API.

Following the below steps to create a user with `email` and `password`

Parameter | Description
--------- | -----------
email | String email of user
password | String password to be stored in a safe place



# XMLendpoint

## Create XML POST

```shell
curl -X POST \
  https://cgb-pw.herokuapp.com/api/v1/xmlendpoint \
  -H 'Authorization: Bearer <TOKEN>' \
  -H 'Content-Type: text/xml' \
  -d '<check check_log_detail_count="0">
    <check_log A_CHKID="CHK9320" A_CHKSTA="0" A_CHKACT="-1" A_CHKUSRID="mveevers" A_CHKSTRTME="20180430150057327" A_CHKENDTME="20180430150057327" A_ORDID="O84395" A_PLCID="O84395" A_EXEID="" A_INSID="RMV LN Equity-LT" A_INSNAM="RIGHTMOVE PLC" A_PARINSID="" A_PARINSNAM="" A_RULID="" A_RULNAM="" A_RULDSC="" A_RULCATID="" A_PSTTRD="N" A_PREORD="N" A_PREEXE="N" A_PREPLC="Y" A_OBJLISID="" A_CCYCDE="" A_MINVAL="" A_MAXVAL="" A_MINTLRVAL="" A_MAXTLRVAL="" A_NTE="No applicable rules defined">
        <check_log_details></check_log_details>
    </check_log>
</check>'
```

> The above command returns `200 OK status` and a JSON structured like this:

```json
{
    "content": "<check check_log_detail_count=\"0\">\n    <check_log A_CHKID=\"CHK9320\" A_CHKSTA=\"0\" A_CHKACT=\"-1\" A_CHKUSRID=\"mveevers\" A_CHKSTRTME=\"20180430150057327\" A_CHKENDTME=\"20180430150057327\" A_ORDID=\"O84395\" A_PLCID=\"O84395\" A_EXEID=\"\" A_INSID=\"RMV LN Equity-LT\" A_INSNAM=\"RIGHTMOVE PLC\" A_PARINSID=\"\" A_PARINSNAM=\"\" A_RULID=\"\" A_RULNAM=\"\" A_RULDSC=\"\" A_RULCATID=\"\" A_PSTTRD=\"N\" A_PREORD=\"N\" A_PREEXE=\"N\" A_PREPLC=\"Y\" A_OBJLISID=\"\" A_CCYCDE=\"\" A_MINVAL=\"\" A_MAXVAL=\"\" A_MINTLRVAL=\"\" A_MAXTLRVAL=\"\" A_NTE=\"No applicable rules defined\">\n        <check_log_details></check_log_details>\n    </check_log>\n</check>",
    "createdAt": 1528923315784,
    "updatedAt": 1528923315784,
    "id": "5b2184b32b68440014bf661f"
}
```

To create a XML post, follow the below steps

Send payload with XML data, with the correct headers, see our example on the right panel.

Parameter | Default | Description
--------- | ------- | -----------
`<check></check>` | `<check></check>` | Accepted with any XML valid data!


<aside class="success">
This endpoint use schemeless structure to store to XML data, so you can send your XML data in any structure!
</aside>


## Retrieve a Specific XML data

```shell
curl -X GET \
  https://cgb-pw.herokuapp.com/api/v1/xmlendpoint/5b2184b32b68440014bf661f \
  -H 'Authorization: Bearer <TOKEN>'
```

> The above command returns JSON structured like this:

```json
{
    "content": "<check check_log_detail_count=\"0\">\n    <check_log A_CHKID=\"CHK9320\" A_CHKSTA=\"0\" A_CHKACT=\"-1\" A_CHKUSRID=\"mveevers\" A_CHKSTRTME=\"20180430150057327\" A_CHKENDTME=\"20180430150057327\" A_ORDID=\"O84395\" A_PLCID=\"O84395\" A_EXEID=\"\" A_INSID=\"RMV LN Equity-LT\" A_INSNAM=\"RIGHTMOVE PLC\" A_PARINSID=\"\" A_PARINSNAM=\"\" A_RULID=\"\" A_RULNAM=\"\" A_RULDSC=\"\" A_RULCATID=\"\" A_PSTTRD=\"N\" A_PREORD=\"N\" A_PREEXE=\"N\" A_PREPLC=\"Y\" A_OBJLISID=\"\" A_CCYCDE=\"\" A_MINVAL=\"\" A_MAXVAL=\"\" A_MINTLRVAL=\"\" A_MAXTLRVAL=\"\" A_NTE=\"No applicable rules defined\">\n        <check_log_details></check_log_details>\n    </check_log>\n</check>",
    "createdAt": 1528923315784,
    "updatedAt": 1528923315784,
    "id": "5b2184b32b68440014bf661f"
}
```

Parameter | Default | Description
--------- | ------- | -----------
`<ID>` | `hashid` | This refers to eh ID of the XML data stored on our API server!

This endpoint retrieves specific XML data.
