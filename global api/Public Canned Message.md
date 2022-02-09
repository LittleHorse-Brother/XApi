# Public Canned Message

  You need `Manage Public Canned Messages` permission to manage the canned message.

- `GET /api/v3/globalSettings/publicCannedMessages` - [Get all public canned messages in site](#get-all-Public-Canned-Messages-in-site)
- `GET /api/v3/globalSettings/publicCannedMessages/{id}` - [Get a public canned message by id](#get-a-Public-Canned-Message-by-id)
- `POST /api/v3/globalSettings/publicCannedMessages` - [create a new public canned message](#create-a-new-Public-Canned-Message)
- `POST /api/v3/globalSettings/publicCannedMessages/{id}/similarQuestions`  - [create a new public similar questions](#create-a-new-public-similar-questions)
- `PUT /api/v3/globalSettings/publicCannedMessages/{id}` - [update a public canned message](#update-a-Public-Canned-Message)
- `DELETE /api/v3/globalSettings/publicCannedMessages/{id}` - [delete a public canned message](#delete-a-Public-Canned-Message)

## Related Object JSON format

### Public Canned Message Object

  Public Canned Message Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - |- | :-: | :-: | :-: | - |
  | `id` | Guid | | yes | no | | Identifier of the canned message.  |
  | `name` | string | | no | yes | | Name of the canned message. |
  | `message` | string | | no | yes | | |
  | `IfSetHtmlMessageForEmail` | boolean  | | no | no | false | |
  | `htmlMessage` | string  | | no | no | | |
  | `categoryId` | Guid | | no | yes | | |
  | `category` | [Public Canned Message Category](#public-Canned-Message-Category-object)  | yes | no | no | |  Category can be blank. Please note that this is different from Intent Category and Article Category. Available only when `publicCannedMessageCategory` is included. |
  | `shortcuts` | string  | | no | no | | Whether the custom away status is system or not. |
  | `similarQuestions` | string[]  | | no | no | | Available when Agent Assist is enabled. |

## Public Canned Message Endpoints

### Get all Public Canned Messages in site

  `GET /api/v3/globalSettings/publicCannedMessages`

#### Parameters

Query string

  | Name  | Type | Required  | Default | Description |
  | - | - | - | - | - |
  | `include` | string | no  |  | Available value: `publicCannedMessageCategory` |

#### Response

The response is an array of [Public Canned Message](#public-Canned-Message-object) objects.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages?include=publicCannedMessageCategory
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

[
    {
        "id": "C354EA75-BAAF-9994-9307-D001FBE1882A",
        "name": "publicCannedMessageCategory",
        "message": "publicCannedMessageCategory",
        "IfSetHtmlMessageForEmail": false,
        "htmlMessage": "",
        "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
        "category":    { // include public canned message category
          "id": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
          "name": "puddddtresult",
         "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
        },
        "shortcuts": "",
        "similarQuestions": ["are you ok?"]
    },
    ...
]
```

### Get a Public Canned Message by id

  `GET /api/v3/globalSettings/publicCannedMessages/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the public canned message. |

Query string

  | Name  | Type | Required  | Default | Description |
  | - | - | - | - | - |
  | `include` | string | no  |  | Available value: `publicCannedMessageCategory`. |

#### Response

The response is a [Public Canned Message](#public-Canned-Message-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages/C354EA75-BAAF-9994-9307-D001FBE1882A?include=publicCannedMessageCategory
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "C354EA75-BAAF-9994-9307-D001FBE1882A",
  "name": "publicCannedMessageCategory",
  "message": "publicCannedMessageCategory",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "category":    { // include public canned message category
    "id": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
    "name": "puddddtresult",
    "parentId": "D5673FC9-9B1A-7030-C7C5-0B4C7A641EFC"
  },
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

### Create a new Public Canned Message

  `POST /api/v3/globalSettings/publicCannedMessages`

#### Parameters

Request Body

  The request body contains data with the [Public Canned Message](#public-Canned-Message-object) structure.

example:
```Json
{
  "name": "publicCannedMessageCategorytest",
  "message": "publicCannedMessageCategorytest",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

#### Response

The response is a [Public Canned Message](#public-Canned-Message-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "publicCannedMessageCategorytest",
  "message": "publicCannedMessageCategorytest",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
  }' -X POST https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages
```

Response
``` json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages/19B21FEE-B0C5-2A61-0D34-26FB057D15EE

{
  "id": "19B21FEE-B0C5-2A61-0D34-26FB057D15EE",
  "name": "publicCannedMessageCategorytest",
  "message": "publicCannedMessageCategorytest",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

### Create a new public similar questions

  `POST /api/v3/globalSettings/publicCannedMessages/{id}/similarQuestions`

#### Parameters

Request Body

  The request body contains data with the string array.

example:
```Json
 ["not ok?"]
```

#### Response

The response is a [Public Canned Message](#public-Canned-Message-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  ["not ok?"]
  }' -X POST https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages/19B21FEE-B0C5-2A61-0D34-26FB057D15EE/similarQuestions
```

Response
``` json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages/19B21FEE-B0C5-2A61-0D34-26FB057D15EE/similarQuestions

{
  "id": "19B21FEE-B0C5-2A61-0D34-26FB057D15EE",
  "name": "publicCannedMessageCategorytest",
  "message": "publicCannedMessageCategorytest",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?","not ok?"]
}
```

### Update a Public Canned Message

  `PUT /api/v3/globalSettings/publicCannedMessages/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the public canned message. |

Request Body

  The request body contains data with the [Public Canned Message](#public-Canned-Message-object) structure.

example:
```Json
{
  "name": "test11111",
  "message": "test11111",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

#### Response

The response is a [Public Canned Message](#public-Canned-Message-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "test11111",
  "message": "test11111",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
  }' -X PUT https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages/19B21FEE-B0C5-2A61-0D34-26FB057D15EE
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "19B21FEE-B0C5-2A61-0D34-26FB057D15EE",
  "name": "test11111",
  "message": "test11111",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

### Delete a Public Canned Message

  `DELETE /api/v3/globalSettings/publicCannedMessages/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the public canned message. |

#### Response

HTTP/1.1 204 No Content

#### Example

Using curl
```
curl -X DELETE https://api1.comm100.io/api/v3/globalSettings/publicCannedMessages/19B21FEE-B0C5-2A61-0D34-26FB057D15EE
```

Response
```Json
  HTTP/1.1 204 No Content