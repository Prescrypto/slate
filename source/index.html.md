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
    "token": "<TOKEN>"
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
      "password": "userpassword",
      "violationEmail": "user@company.com"
    }'
```

> The above command returns JSON structured like this:

```json
{
    "createdAt": 1528922588700,
    "updatedAt": 1528922588700,
    "id": "5b2181dc2b68440014bf661e",
    "email": "user@company.com",
    "violationEmail": "user@company.com"
}
```

A new user neds to be created prior to authentication and the use of our API.

Following the below steps to create a user with `email` and `password`

Parameter | Description
--------- | -----------
email | String email of user
password | String password to be stored in a safe place
violationEmail | String email of the recipient for the violation notifications 



# XMLendpoint

## Create XML POST

```shell
curl -X POST \
  https://cgb-pw.herokuapp.com/api/v1/xmlendpoint \
  -H 'Authorization: Bearer <TOKEN>' \
  -H 'Content-Type: text/xml' \
  -d '<Check ClientID="CG" ClientName="CG Blockchain" Count="2"><CheckResult UserID="anuli" OrderID="123" InstrumentId="11914" Account="UK EQUITY" Instrument="HSBC 4 3/4 03/24/46" AccountId="A000001" RuleId="R308" Reason="Incorrect rule coding"/></Check>'
```

> **Success Response:**

> On sucess The above command returns `200 OK status` and a JSON structured like this:

```json
{
    "response": "success on post"
}
```

> **Error Response:**
>
> On error The above command returns `200 OK status` and the following posible error responses:

```json
{
    "response": "No response or error on post"
}
```

>  If there was an error at compliance guard endpoint

```json
{
    "response": "error on post"
}
```

>  If there is an unknown error

```json
{
    "response": "Authorization reloaded please try again"
}
```

>  If somehow the Token has failed to be loaded and we need to get a new one

```json
{
    "response":"error on db insert"
}
```

> When there's an error on the db insert

```xml
<!DOCTYPE html>
<html>
    <head>
        <title>CG Blockchain 403</title>
        <link href="/public/app.css" rel="stylesheet">
    </head>
    <body>
        <div id="content">
        Unauthorised access
    </div>
    </body>
</html>
```

>  If there was an error at compliance guard and the response is not in JSON format we'll get a response like the above.

To create a XML post, follow the below steps

Send payload with XML data, with the correct headers, see our example on the right panel.

Parameter | Default | Description
--------- | ------- | -----------
`<check></check>` | `<check></check>` | Accepted with any XML valid data!

<aside class="success">
This endpoint use schemeless structure to store to XML data, so you can send your XML data in any structure!
</aside>

## Check the Posts

To check if the XML file has been correctly posted you can login to compliance guard on the link:
	[https://cg-dev-1.app.cgblockchain.com](https://cg-dev-1.app.cgblockchain.com)
then on the top menu select the left dropdown option and click on research & documentation
this will load all the documents posted in datetime order or we can make a GET to the compliance guard endpoint including the entity ID from the files we are trying to retrieve for example:

> To get the XML information.

```shell
curl -X GET \
  https://cg-dev-1.app.cgblockchain.com/api/v1/entries/9c8e2eea-4003-4e8e-b47b-7fcfbc1e9fd8 \
  -H 'Authorization: Bearer <TOKEN>' \
  -H 'Content-Type: application/json' \
```

Send payload with XML data, with the correct headers, see our example on the right panel.

| Parameter       | Default         | Description           |
| --------------- | --------------- | --------------------- |
| ```<EntryID>``` | ```<EntryID>``` | Entry Id of the file. |





> It will return a JSON array with the xml information like the following:

```json
"status": "success",
    "data": {
        "entries": [
            {
                "_ts": "2018-06-28T19:51:52.102Z",
                "revision": 1,
                "chainId": null,
                "entityId": "9c8e2eea-4003-4e8e-b47b-7fcfbc1e9fd8",
                "hash": "0x4e1f4787bf20031588c26f3e417d8724257a90be1a942c4fdb2f9d3c9642a5e3",
                "userId": "76ac40e6-b47f-4f42-ba2b-44bc5eaea651",
                "links": [],
                "id": "40a21ce6-53e3-49a6-9904-fc60819949ae",
                "user": "76ac40e6-b47f-4f42-ba2b-44bc5eaea651",
                "tx": {
                    "blockHash": "0x1e69e69699147bc70598dacdda610fdc3e4bdd62ed9096fd485509c94f132207",
                    "blockNumber": "0x95",
                    "condition": null,
                    "creates": "0x406a317ef14944e119c35390101853eb61001632",
                    "from": "0x1eed8b83260bc5076b79f45621e650af4dd73e3b",
                    "gas": "0xe57e0",
                    "gasPrice": "0x0",
                    "hash": "0x4e1f4787bf20031588c26f3e417d8724257a90be1a942c4fdb2f9d3c9642a5e3",
                    "input": "0x38363834333338636335363365373437643135653331333334623964336339323530373062383764336432396261626432313334363336633563643034653131",
                    "networkId": 8995,
                    "nonce": "0x1e1",
                    "publicKey": "0x6325b037a4cef9c2a63755f4bb796da3fb9ac816c1cdba4f9d471cdad5566313d7e78767cb402f182cd6ba3ac8ea8bd3da35d1b86f2c5e2a71062930bac358dc",
                    "r": "0x10cf638a43f5e212d6ae9c178f122c31a9f48766dd84822a6a0f1d3a5d48cc25",
                    "raw": "0xf8918201e180830e57e08080b84038363834333338636335363365373437643135653331333334623964336339323530373062383764336432396261626432313334363336633563643034653131824669a010cf638a43f5e212d6ae9c178f122c31a9f48766dd84822a6a0f1d3a5d48cc25a03c47b9bdd05edd0e961c86119a0fa84da2bf0e806b0b361454a00dadce225809",
                    "s": "0x3c47b9bdd05edd0e961c86119a0fa84da2bf0e806b0b361454a00dadce225809",
                    "standardV": "0x0",
                    "to": null,
                    "transactionIndex": "0x3",
                    "v": "0x4669",
                    "value": "0x0"
                },
                "values": {
                    "file_1": {
                        "name": "file.xml",
                        "type": "application/xml",
                        "size": 187,
                        "lastModifiedDate": "2018-06-28T19:51:52+00:00",
                        "digest": {
                            "type": "Buffer",
                            "data": [
                                255,
                                93,
                                133,
                                125,
                                111,
                                102,
                                136,
                                157,
                                133,
                                251,
                                189,
                                85,
                                94,
                                73,
                                205,
                                216,
                                84,
                                121,
                                157,
                                187,
                                33,
                                215,
                                87,
                                62,
                                43,
                                75,
                                137,
                                41,
                                187,
                                247,
                                191,
                                214
                            ]
                        },
                        "link": "0xd4178107bf1e10602e70116d6a8fe0878995df42c0d5f32d4bcd02f94a748fbe"
                    },
                    "description": "file.xml Posted by user2@test.com time: Thu Jun 28 2018 19:51:51 GMT+0000 (UTC)",
                    "_ts": "Jun 28, 2018 3:51 PM"
                }
            },
```

If the XML file has a *CheckOverride* TAG on it's information then it will search for the previous failure and send an email to the violation email address from the user, this email will contain both the Check Override information and the Check Entity information, it will also include a link to the previous failure XML file 
on Compliance Guard if there was one.

## Example Notification

**Dear Recipient Name, This is a Violation CheckOverride Notification Date: Tue Jun 26 2018 22:16:48 GMT+0000 (UTC)**

**CheckOverride information:**

| Name         | Value                 |
| ------------ | --------------------- |
| UserID       | anuli                 |
| OrderID      | 1                     |
| InstrumentId | 11914                 |
| Account      | UK EQUITY             |
| Instrument   | HSBC 4 3/4 03/24/46   |
| AccountId    | A000001               |
| RuleId       | R308                  |
| Reason       | Incorrect rule coding |

**CheckEntity information:**

| Name             | Value      |
| ---------------- | ---------- |
| AccountID        | A000001    |
| CustodianID      | K5344      |
| Condition        | Market     |
| CreateCashOffset | Yes        |
| Broker           | CS         |
| EntityType       | Order      |
| ExposureValue    | 1165440.00 |
| FxCurrencyType   | NotFx      |
| IsSynthetic      | No         |
| InstrumentId     | 10077      |
| InstrType        | Equity     |
| IsAmend          | Yes        |
| IsShort          | No         |
| LogResults       | Yes        |
| Manager          | dlyons     |
| OrderID          | 1          |
| UserID           | rpicciau   |
| Value            | 1165440.00 |
| ValidationType   | Compliance |

**Link to File: [https://cg-dev-1.app.cgblockchain.com/app/research_and_documentation/bf1b239d-bcff-4cf3-a66f-e7843c647dfb](https://cg-dev-1.app.cgblockchain.com/app/research_and_documentation/bf1b239d-bcff-4cf3-a66f-e7843c647dfb)**

**Regards**




## Retrieve a Specific XML data

```shell
curl -X GET \
  https://cgb-pw.herokuapp.com/api/v1/xmlendpoint/5b2184b32b68440014bf661f \
  -H 'Authorization: Bearer <TOKEN>'
```

> The above command returns JSON structured like this:

```json
{
    "content": '<Check ClientID="CG" ClientName="CG Blockchain" Count="2"><CheckResult UserID="anuli" OrderID="123" InstrumentId="11914" Account="UK EQUITY" Instrument="HSBC 4 3/4 03/24/46" AccountId="A000001" RuleId="R308" Reason="Incorrect rule coding"/></Check>',
    "createdAt": 1528923315784,
    "updatedAt": 1528923315784,
    "id": "5b2184b32b68440014bf661f"
}
```

Parameter | Default | Description
--------- | ------- | -----------
`<ID>` | `hashid` | This refers to eh ID of the XML data stored on our API server!

This endpoint retrieves specific XML data.
