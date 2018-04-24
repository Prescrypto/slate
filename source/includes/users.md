# User



## Add User

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"username": "first.last", "fullName": "First Last", "email": "first.last__hedgefund.com", "password": "pwd"}' \
   https://compliance-guard.lan/api/v1/system/users

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "user": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "username": "first.last",
        "fullName": "First Last",
        "email": "first.last__hedgefund.com",
        "signingKeyPublic": "-----BEGIN PUBLIC KEY----- -----END PUBLIC KEY-----",
        "type": "local"
      }
    }
  }

```

Use this endpoint method to add a User to the system.

### HTTP Request

`POST /api/v1/system/users`

### Payload Attributes

| Attribute | Description |
|----------|------------|
| USERNAME     | Name of the new user      |
| FULLNAME     | Human-readable name of the new user      |
| EMAIL     | Email address of the new user      |
| PASSWORD     | Password of the new user      |




## Add Users from LDAP

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"users": ["user1", "user2", "user3"]}' \
   https://compliance-guard.lan/api/v1/system/users/ldap

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "users": [
        {
          "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
          "username": "user1",
          "fullName": "User #1",
          "email": "user1__hedgefund.com",
          "signingKeyPublic": "-----BEGIN PUBLIC KEY----- -----END PUBLIC KEY-----",
          "type": "local",
        }
      ]
    }
  }

```

Use this method to add UI Users by using data from LDAP.

### HTTP Request

`POST /api/v1/system/users/ldap`

### Payload Attributes

| Parameter  | Description |
|----------|------------|
| USERS     | Array of users, that need to be added to the system      |





## Add Role to the existing User

```shell

 curl \
   -X POST \
   -H "Content-Type: application/json" \
   -d '{"role": "1cedf4ab-befd-44aa-b31b-86d612f4068e"}' \
   https://compliance-guard.lan/api/v1/system/users/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3/roles

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "role": {
        "id": "1cedf4ab-befd-44aa-b31b-86d612f4068e"
        "slugname": "admin",
        "name": "admin",
        "permissions": [],
      }
    }
  }

```

Use this method to add a Role to a User.

### HTTP Request

`POST /api/v1/system/users/<id>/roles`

### Payload Attributes

| Parameter  | Description |
|----------|------------|
| ID     | ID of the target user      |
| ROLEID     | String[] | Role id      |




## Get list of LDAP Users

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/users/ldap

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "users": [
        {
          "username": "user1",
          "fullName": "Use #1",
          "alreadyPresence": false
        },
        {
          "username": "user2",
          "fullName": "Use #2",
          "alreadyPresence": true
        },
        {
          "username": "user3",
          "fullName": "Use #3",
          "alreadyPresence": true
        }
      ]
    }
  }

```

This endpoint returns an array of LDAP Users.

### HTTP Request

`GET /api/v1/system/users/ldap`




## Generate new private/public keys pair for User

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/users/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3/generate

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

This endpoint generates a signingKeyPrivate and signingKeyPublic pair for the target User.

### HTTP Request

`GET /api/v1/system/users/<id>/generate`

### URL Parameters

| Parameter  | Description |
|----------|------------|
| ID     | ID of the target user      |





## Get list of Roles for the User

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/users/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3/roles

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "roles": [
        {
          "id": "1cedf4ab-befd-44aa-b31b-86d612f4068e",
          "slugname": "admin",
          "name": "admin",
          "permissions": []
        }
      ]
    }
  }

```

This endpoint returns the array of Roles that have been assigned to a User.

### HTTP Request

`GET /api/v1/system/users/<id>/roles`

### URL Parameters

| Parameter  | Description |
|----------|------------|
| ID     | ID of the target user      |





## Get User

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/users/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "user": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "username": "first.last",
        "fullName": "First Last",
        "email": "first.last__hedgefund.com",
        "signingKeyPublic": "-----BEGIN PUBLIC KEY----- -----END PUBLIC KEY-----",
        "type": "local"
      }
    }
  }

```

This endpoint returns User data, excluding private information.

### HTTP Request

`GET /api/v1/system/users/<id>`

### URL Parameters

| Parameter  | Description |
|----------|------------|
| ID     | ID of the target user      |





## Get list of Users

```shell

 curl \
   -X GET \
   https://compliance-guard.lan/api/v1/system/users&limit=1

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "users": [
        {
          "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
          "username": "first.last",
          "fullName": "First Last",
          "email": "first.last__hedgefund.com",
          "signingKeyPublic": "-----BEGIN PUBLIC KEY----- -----END PUBLIC KEY-----",
          "type": "local"
        }
      ]
    }
  }

```

This endpoint returns an array of Users that have been created within a particular Client’s system (or imported from LDAP).

### HTTP Request

`GET /api/v1/system/users`

### URL Parameters

| Parameter  | Description |
|----------|------------|
| LIMIT     | [Optional] Limit of number of fetched drafts. Default value: 0      |
| OFFSET     | [Optional] Number of drafts to skip. Default value: 5      |




## Update User

```shell

 curl \
   -X PUT \
   -H "Content-Type: application/json" \
   -d '{"fullName": "New First Last", "password": "pwd"}' \
   https://compliance-guard.lan/api/v1/system/users/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": {
      "user": {
        "id": "6a2017db-6f7c-45e8-ab28-ebe9e589b4b3",
        "username": "first.last",
        "fullName": "New First Last",
        "email": "first.last__hedgefund.com",
        "signingKeyPublic": "-----BEGIN PUBLIC KEY----- -----END PUBLIC KEY-----",
        "type": "local"
      }
    }
  }

```

Use this method to updated User data.

### HTTP Request

`PUT /api/v1/system/users/<id>`

### URL Parameters

| Parameter  | Description |
|----------|------------|
| ID     | ID of the desired user      |
| USERNAME     | [Optional] Name of the user      |
| FULLNAME     | [Optional] Human-readable name of the user      |
| EMAIL     | [Optional] Email address of the user      |
| PASSWORD     | [Optional] Password of the user      |




## Delete Role from User's list

```shell

 curl \
   -X DELETE \
   https://compliance-guard.lan/api/v1/system/users/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3/roles/1cedf4ab-befd-44aa-b31b-86d612f4068e

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

Use this method to delete a Role from a User's list.

### HTTP Request

`DELETE /api/v1/system/users/<id>/roles/<roleId>`

### URL Parameters

| Parameter  | Description |
|----------|------------|
| ID     | ID of the user      |
| ROLEID     | ID of the desired role      |




## Delete User

```shell

 curl \
   -X DELETE \
   https://compliance-guard.lan/api/v1/system/users/6a2017db-6f7c-45e8-ab28-ebe9e589b4b3

```

> The above command returns JSON structured like this:

```json

  {
    "status": "success",
    "data": null
  }

```

Use this method to delete a User.

### HTTP Request

`DELETE /api/v1/system/users/<id>`

### URL Parameters

| Parameter  | Description |
|----------|------------|
| ID     | ID of the user      |



