# Public Canned Message Category

  You need `Manage Public Canned Messages` permission to manage the canned message category.

- `GET /api/v3/globalSettings/publicCannedMessageCategories` - [Get all public canned message categories in site](#get-all-Public-Canned-Message-Categories-in-site)
- `GET /api/v3/globalSettings/publicCannedMessageCategories/{id}` - [Get a public canned message category by id](#get-a-Public-Canned-Message-Category-by-id)
- `POST /api/v3/globalSettings/publicCannedMessageCategories` - [create a new public canned message category](#create-a-new-Public-Canned-Message-Category)
- `PUT /api/v3/globalSettings/publicCannedMessageCategories/{id}` - [update a public canned message category](#update-a-Public-Canned-Message-Category)
- `DELETE /api/v3/globalSettings/publicCannedMessageCategories/{id}` - [delete a public canned message category](#delete-a-Public-Canned-Message-Category)

## Related Object JSON format

### Public Canned Message Category Object

  Public Canned Message Category Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory | Default | Description |
  | - | - | :-: | :-: | :-: | - |
  | `id` | Guid | yes | no | | Identifier of the current item.  |
  | `name` | string  | no | yes | | Name of the canned message category. |
  | `parentId` | Guid | no | yes | | Identifier of the public canned message category. If it does not have parent category, parentId is '00000000-0000-0000-0000-000000000000'.|

## Public Canned Message Endpoints

### Get all Public Canned Message Categories in site

  `GET /api/v3/globalSettings/publicCannedMessageCategories`

#### Parameters

    No parameters

#### Response

The response is an array of [Public Canned Message Category](#Public-Canned-Message-Category-Object) objects.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/publicCannedMessageCategories
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

[
  {
    "id": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
    "name": "puddddtresult",
    "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
  },
  ...
]
```

### Get a Public Canned Message Category by id

  `GET /api/v3/globalSettings/publicCannedMessageCategories/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Identifier of the public canned message category. |

#### Response

The response is a [Public Canned Message Category](#public-Canned-Message-Category-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/publicCannedMessageCategories/5A563046-374D-3C4E-4D4A-2CA3812A42C8
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "name": "puddddtresult",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
}
```

### Create a new Public Canned Message Category

  `POST /api/v3/globalSettings/publicCannedMessageCategories`

#### Parameters

Request Body

  The request body contains data with the [Public Canned Message Category](#public-Canned-Message-Category-object) structure.

example:
```Json
{
  "name": "testtest",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
}
```

#### Response

The response is a [Public Canned Message Category](#public-Canned-Message-Category-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "testtest",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
  }' -X POST https://api1.comm100.io/api/v3/globalSettings/publicCannedMessageCategories
```

Response
```Json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/publicCannedMessageCategories/7D3E7435-F956-29FE-C089-57241AFBB297

{
  "id": "7D3E7435-F956-29FE-C089-57241AFBB297",
  "name": "testtest",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
}
```

### Update a Public Canned Message Category

  `PUT /api/v3/globalSettings/publicCannedMessageCategories/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  | Unique identiifer of the public canned message category. |

Request Body

  The request body contains data with the [Public Canned Message Category](#public-Canned-Message-Category-object) structure.

example:
```Json
{
  "name": "testtest22222",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
}
```

#### Response

The response is a [Public Canned Message Category](#public-Canned-Message-Category-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "testtest22222",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
  }' -X PUT https://api1.comm100.io/api/v3/globalSettings/publicCannedMessageCategories/7D3E7435-F956-29FE-C089-57241AFBB297
```

Response
```Json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "7D3E7435-F956-29FE-C089-57241AFBB297",
  "name": "testtest22222",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
}
```

### Delete a Public Canned Message Category

  `DELETE /api/v3/globalSettings/publicCannedMessageCategories/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  | Unique identifier of the public canned message category.|

#### Response

HTTP/1.1 204 No Content

#### Example

Using curl
```
curl -X DELETE https://api1.comm100.io/api/v3/globalSettings/publicCannedMessageCategories/7D3E7435-F956-29FE-C089-57241AFBB297
```
Response
```json
HTTP/1.1 204 No Content