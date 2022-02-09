# Whitelisted Login IP Range

You need `Manage Security` permission to manage whitelisted login ip restrictions.

   When Login IP Whitelist is enabled, site administrator can add IP range for this site and only agents within the IP range can log in successfully.

  + `GET /api/v3/globalSettings/whitelistedLoginIPRanges` - [Get a list of whitelisted login IP ranges in site](#get-all-whitelisted-login-ip-ranges)
  + `GET /api/v3/globalSettings/whitelistedLoginIPRanges/{id}` - [Get a whitelisted login IP range by id](#get-a-whitelisted-login-ip-ranges)
  + `POST /api/v3/globalSettings/whitelistedLoginIPRanges` - [create a new whitelisted login IP range](#create-a-new-whitelisted-login-ip-range)
  + `PUT /api/v3/globalSettings/whitelistedLoginIPRanges/{id}` - [update a whitelisted login IP range](#update-a-whitelisted-login-ip-range)
  + `DELETE /api/v3/globalSettings/whitelistedLoginIPRanges/{id}` - [delete a whitelisted login IP range](#delete-a-whitelisted-login-ip-range)

## Whitelisted Login IP Range Related Object JSON format

### Whitelisted Login IP Range Object

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - | :-: | :-: | :-: | :-: | - |
  |`id` | Guid | | yes | no | | |
  |`ipFrom` | string | | no | yes | | Where an IP range starts.|
  |`ipTo` | string | | no | yes | | Where an IP range ends.|
  |`createdTime` | DateTime | | no | no |  |  |

## Whitelisted Login IP Range Endpoints

### Get all Whitelisted Login IP Ranges

  `GET /api/v3/globalSettings/whitelistedLoginIPRanges`

  #### Parameters
    No parameters

  #### Response

  The response is a list of [Whitelisted Login IP Range](#whitelisted-login-ip-range-object) Objects

#### Example
Using curl
```
curl -H "Content-Type: application/json" -X GET https://api1.comm100.io/api/v3/globalSettings/whitelistedLoginIPRanges
```
Response
```json
HTTP/1.1 200 OK
Content-Type:  application/json[
{
  "id": "42dwdaww-92e6-4487-a2e8-92e68d6892e6",
  "ipFrom": "201.195.21.5",
  "ipTo": "201.195.21.8",
  "createdTime": "2020-01-01",
},
...,
]
```

### Get a Whitelisted Login IP Ranges

  `GET /api/v3/globalSettings/whitelistedLoginIPRanges/{id}`

#### Parameters
Path parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  |`id` | Guid | yes  |  Identifer of the whitelisted Login IP Ranges. |

#### Response

The response is a [Whitelisted Login IP Range](#whitelisted-login-ip-range-object) Object.

#### Example
Using curl
```
curl -H "Content-Type: application/json" -X GET https://api1.comm100.io/api/v3/globalSettings/whitelistedLoginIPRanges/42dwdaww-92e6-4487-a2e8-92e68d6892e6
```
Response
```json
HTTP/1.1 200 OK
Content-Type:  application/json
  {
  "id": "42dwdaww-92e6-4487-a2e8-92e68d6892e6",
  "ipFrom": "201.195.21.5",
  "ipTo": "201.195.21.8",
  "createdTime": "2020-01-01",
  }
```

### Create a new whitelisted Login IP Range

  `POST /api/v3/globalSettings/whitelistedLoginIPRanges`

####  Parameters

Request body
  The request body contains data with the [Whitelisted Login IP Range](#whitelisted-login-ip-range-object) structure.

  example:
```json
 {
    "ipFrom": "201.195.21.5",
    "ipTo": "201.195.21.8",
  }
```

#### Response

The response is a [Whitelisted Login IP Range](#whitelisted-login-ip-range-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d ' {
      "ipFrom": "201.195.21.5",
      "ipTo": "201.195.21.8",
    }' -X POST https://api1.comm100.io/api/v3/globalSettings/whitelistedLoginIPRanges
```
Response
```json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/whitelistedLoginIPRanges/42dwdaww-92e6-4487-a2e8-92e68d6892e6
 {
    "id": "42dwdaww-92e6-4487-a2e8-92e68d6892e6",
    "ipFrom": "201.195.21.5",
    "ipTo": "201.195.21.8",
    "createdTime": "2020-01-01",
  }
```


### Update a whitelisted Login IP Range
  `PUT /api/v3/globalSettings/whitelistedLoginIPRanges/{id}`

####  Parameters

Path parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  |`id` | Guid | yes  |  Identifier of the whitelisted Login IP Range. |

Request body

  The request body contains data with the [Whitelisted Login IP Range](#whitelisted-login-ip-range-object) structure.

  example:
```json
 {
    "ipFrom": "201.195.21.5",
    "ipTo": "201.195.21.8",
  }
```

#### Response

The response is a [Whitelisted Login IP Range](#whitelisted-login-ip-range-object) Object.

#### Example
Using curl
```
curl -H "Content-Type: application/json" -d ' {
      "ipFrom": "201.195.21.5",
      "ipTo": "201.195.21.8",
    }' -X PUT https://api1.comm100.io/api/v3/globalSettings/whitelistedLoginIPRanges/42dwdaww-92e6-4487-a2e8-92e68d6892e6
```
Response
```json
  HTTP/1.1 200 OK
  Content-Type: https://api1.comm100.io/api/v3/globalSettings/whitelistedLoginIPRanges/42dwdaww-92e6-4487-a2e8-92e68d6892e6
 {
    "id": "42dwdaww-92e6-4487-a2e8-92e68d6892e6",
    "ipFrom": "201.195.21.5",
    "ipTo": "201.195.21.8",
    "createdTime": "2020-01-01",
  }
```

### Delete a whitelisted Login IP Range

  `DELETE /api/v3/globalSettings/whitelistedLoginIPRanges/{id}`

#### Parameters

Path parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  |`id` | Guid | yes  |  Identifier of the whitelisted Login IP Range.|

#### Response
HTTP/1.1 204 No Content

#### Example
Using curl
```
curl -X DELETE https://api1.comm100.io/api/v3/globalSettings/whitelistedLoginIPRanges/4487fc9d-92e6-4487-a2e8-92e68d6892e6
```
Response
```json
HTTP/1.1 204 No Content
```