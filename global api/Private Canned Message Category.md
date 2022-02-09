# Private Canned Message Category

You need `Manage Private Canned Messages` permission to manage the canned message category.

- `GET /api/v3/globalSettings/privateCannedMessageCategories` - [Get all private canned message categories in site](#get-all-Private-Canned-Message-Categories-in-site)
- `GET /api/v3/globalSettings/privateCannedMessageCategories/{id}` - [Get a private canned message category by id](#get-a-Private-Canned-Message-Category-by-id)
- `POST /api/v3/globalSettings/privateCannedMessageCategories` - [create a new private canned message category](#create-a-new-Private-Canned-Message-Category)
- `PUT /api/v3/globalSettings/privateCannedMessageCategories/{id}` - [update a private canned message category](#update-a-Private-Canned-Message-Category)
- `DELETE /api/v3/globalSettings/privateCannedMessageCategories/{id}` - [delete a private canned message category](#delete-a-Private-Canned-Message-Category)

## Related Object JSON format

### Private Canned Message Category Object

  Private Canned Message Category Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory | Default | Description |
  | - | - | :-: | :-: | :-: | - |
  | `id` | Guid | yes | no | | Identifier of the current item.  |
  | `name` | string  | no | yes | | Name of the canned message category. |
  | `parentId` | Guid  | no | yes | | Parent of the canned message category. |

## Private Canned Message Category Endpoints

### Get all Private Canned Message Categories in site

  `GET /api/v3/globalSettings/privateCannedMessageCategories`

#### Parameters

    No parameters

#### Response

The response is an array of [Private Canned Message Category](#private-Canned-Message-Category-object) objects.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/privateCannedMessageCategories
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

[
    {
        "id": "119043D0-76A6-D3C1-B594-493111CE1552",
        "name": "tstestsetsteset",
        "parentId": "841193BB-8A51-E4F3-EB17-6B4C222D744F"
    },
    ...
]
```

### Get a Private Canned Message Category by id

  `GET /api/v3/globalSettings/privateCannedMessageCategories/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the private canned message category. |

#### Response

The response is a [Private Canned Message Category](#private-Canned-Message-Category-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/privateCannedMessageCategories/119043D0-76A6-D3C1-B594-493111CE1552
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "119043D0-76A6-D3C1-B594-493111CE1552",
  "name": "tstestsetsteset",
  "parentId": "841193BB-8A51-E4F3-EB17-6B4C222D744F"
}
```

### Create a new Private Canned Message Category

  `POST /api/v3/globalSettings/privateCannedMessageCategories`

#### Parameters

Request Body

  The request body contains data with the [Private Canned Message Category](#private-Canned-Message-Category-object) structure.

example:
```Json
{
  "name": "testtest111111",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
}
```

#### Response

The response is a [Private Canned Message Category](#private-Canned-Message-Category-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "testtest111111",
  "parentId": "841193BB-8A51-E4F3-EB17-6B4C222D744F"
  }' -X POST https://api1.comm100.io/api/v3/globalSettings/privateCannedMessageCategories
```

Response
```Json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/privateCannedMessageCategories/FFD377AA-81FA-EC53-1E57-DD73C0B36F6C
{
  "id": "FFD377AA-81FA-EC53-1E57-DD73C0B36F6C",
  "name": "testtest111111",
  "parentId": "841193BB-8A51-E4F3-EB17-6B4C222D744F"
}
```

### Update a Private Canned Message Category

  `PUT /api/v3/globalSettings/privateCannedMessageCategories/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the private canned message category. |

Request Body

  The request body contains data with the [Private Canned Message Category](#private-Canned-Message-Category-object) structure.

example:
```Json
{
  "name": "testtest22222",
  "parentId": "841193BB-8A51-E4F3-EB17-6B4C222D744F"
}
```

#### Response

The response is a [Private Canned Message Category](#private-Canned-Message-Category-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "testtest22222",
  "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
  }' -X PUT https://api1.comm100.io/api/v3/globalSettings/privateCannedMessageCategories/FFD377AA-81FA-EC53-1E57-DD73C0B36F6C
```

Response
```Json
  HTTP/1.1 200 OK
  Content-Type:  application/json

{
  "id": "FFD377AA-81FA-EC53-1E57-DD73C0B36F6C",
  "name": "testtest22222",
  "parentId": "841193BB-8A51-E4F3-EB17-6B4C222D744F"
}
```

### Delete a Private Canned Message Category

  `DELETE /api/v3/globalSettings/privateCannedMessageCategories/{id}`

#### Example

Using curl
```
curl -X DELETE https://api1.comm100.io/api/v3/globalSettings/privateCannedMessageCategories/FFD377AA-81FA-EC53-1E57-DD73C0B36F6C
```

Response
```Json
  HTTP/1.1 204 No Content
```

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the private canned message category. |

#### Response

HTTP/1.1 204 No Content