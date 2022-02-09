# Agent Away Status

  You need `Manage Custom Away Status` permission to manage `Agent Away Status`.

- `GET /api/v3/globalSettings/agentAwayStatuses` - [Get all agent away statuses in site](#get-all-Agent-Away-Statuses-in-site)
- `GET /api/v3/globalSettings/agentAwayStatuses/{id}` - [Get an agent away status by id](#get-an-Agent-Away-Status-by-id)
- `POST /api/v3/globalSettings/agentAwayStatuses` - [create a new agent away status](#create-a-new-Agent-Away-Status)
- `PUT /api/v3/globalSettings/agentAwayStatuses/{id}` - [update an agent away status](#update-an-Agent-Away-Status)
- `DELETE /api/v3/globalSettings/agentAwayStatuses/{id}` - [delete an agent away status](#delete-an-Agent-Away-Status)

## Related Object JSON format

### Agent Away Status Object

  Agent Away Status Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory| Default | Description |
  | - | - | :-: | :-: | :-: | - |
  | `id` | Guid | yes | no | | Identifier of the current item.  |
  | `name` | string  | no | yes | | Name of the agent away status. |
  | `isSystem` | boolean  | yes | no | false | Whether the agent away status is system or not. |
  | `order` | integer  | yes | no | | The order of the agent away status. |

## Agent Away Status Endpoints

### Get all Agent Away Statuses of a site

  `GET /api/v3/globalSettings/agentAwayStatuses`

#### Parameters

    No parameters

#### Response

The response is an array of [Agent Away Status](#agent-Away-Status-object) objects.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/agentAwayStatuses
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

[
    {
        "id": "BAACB779-2E41-27C5-B23D-1C8F2058862D",
        "name": "agentAwayStatuses",
        "isSystem": false,
        "order": 1
    },
    ...
]
```

### Get an Agent Away Status by id

  `GET /api/v3/globalSettings/agentAwayStatuses/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifer of the agent away status. |

#### Response

The response is an [Agent Away Status](#agent-Away-Status-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/agentAwayStatuses/BAACB779-2E41-27C5-B23D-1C8F2058862D
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "BAACB779-2E41-27C5-B23D-1C8F2058862D",
  "name": "agentAwayStatuses",
  "isSystem": false,
  "order": 1
}
```

### Create a new Agent Away Status

  `POST /api/v3/globalSettings/agentAwayStatuses`

#### Parameters

Request Body

  The request body contains data with the [Agent Away Status](#agent-Away-Status-object) structure.

example:
```Json
{
  "name": "agentAwayStatuses11",
  "isSystem": false,
  "order": 1
}
```

#### Response

The response is an [Agent Away Status](#agent-Away-Status-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "agentAwayStatuses11"
  }' -X POST https://api1.comm100.io/api/v3/globalSettings/agentAwayStatuses
```

Response
``` json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/agentAwayStatuses/D4F6BA7F-9BB6-C509-8BB9-0705B3E500F2

{
  "id": "D4F6BA7F-9BB6-C509-8BB9-0705B3E500F2",
  "name": "agentAwayStatuses11",
  "isSystem": false,
  "order": 5
}
```

### Update an Agent Away Status

  `PUT /api/v3/globalSettings/agentAwayStatuses/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the agent away status.|

Request Body

  The request body contains data with the [Agent Away Status](#agent-Away-Status-object) structure.

example:
```Json
{
  "name": "agentAwayStatuses23",
}
```

#### Response

The response is an [Agent Away Status](#agent-Away-Status-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "agentAwayStatuses22",
  "isSystem": false,
  "order": 1
  }' -X PUT https://api1.comm100.io/api/v3/globalSettings/agentAwayStatuses/D4F6BA7F-9BB6-C509-8BB9-0705B3E500F2
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "D4F6BA7F-9BB6-C509-8BB9-0705B3E500F2",
  "name": "agentAwayStatuses23",
  "isSystem": false,
  "order": 5
}
```

### Delete an Agent Away Status

  `DELETE /api/v3/globalSettings/agentAwayStatuses/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the agent away status.|

#### Response

HTTP/1.1 204 No Content

#### Example

Using curl
```
curl -X DELETE https://api1.comm100.io/api/v3/globalSettings/agentAwayStatuses/D4F6BA7F-9BB6-C509-8BB9-0705B3E500F2
```

Response
```Json
  HTTP/1.1 204 No Content
```