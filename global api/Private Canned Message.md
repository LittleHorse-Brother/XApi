# Private Canned Message

You need `Manage Private Canned Messages` permission to manage the canned message.

- `GET /api/v3/globalSettings/privateCannedMessages` - [Get all private canned messages in site](#get-all-Private-Canned-Messages-in-site)
- `GET /api/v3/globalSettings/privateCannedMessages/{id}` - [Get a private canned message by id](#get-a-Private-Canned-Message-by-id)
- `POST /api/v3/globalSettings/privateCannedMessages` - [create a new private canned message](#create-a-new-Private-Canned-Message)
- `POST /api/v3/globalSettings/publicCannedMessages/{id}/similarQuestions`  - [create a new private similar questions](#create-a-new-private-similar-questions)
- `PUT /api/v3/globalSettings/privateCannedMessages/{id}` - [update a private canned message](#update-a-Private-Canned-Message)
- `DELETE /api/v3/globalSettings/privateCannedMessages/{id}` - [delete a private canned message](#delete-a-Private-Canned-Message)

## Related Object JSON format

### Private Canned Message Object

  Private Canned Message Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - |- | :-: | :-: | :-: | - |
  | `id` | Guid | | yes | no | | Identifier of the current item.  |
  | `name` | string  | | no | no | | Name of the canned message. |
  | `message` | string  | | no | no | | |
  | `IfSetHtmlMessageForEmail` | bool | | no | no | false | |
  | `htmlMessage` | string  | | no | no | | |
  | `categoryId` | Guid | | no | no | | |
  | `category` | [Private Canned Message Category](#private-Canned-Message-Category-object)  | yes | no | no | |  Category can be blank. Note that this is different from Intent Category and Article Category. Available only when `privateCannedMessageCategory` is included. |
  | `shortcuts` | string  | | no | no | | Whether the custom away status is system or not. |
  | `similarQuestions` | string[]  | | no | no | | Available when Agent Assist is enabled. |


## Private Canned Message Endpoints

### Get all Private Canned Messages in site

  `GET /api/v3/globalSettings/privateCannedMessages`

#### Parameters

Query string

  | Name  | Type | Required  | Default | Description |
  | - | - | - | - | - |
  | `include` | string | no  |  | Available value: `privateCannedMessageCategory`. |

#### Response

The response is a list of [Private Canned Message](#private-Canned-Message-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages?include=privateCannedMessageCategory
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

[
    {
        "id": "AB71E95A-1FA5-E19D-9BA4-9C2144598C57",
        "name": "privateCannedMessageCategory",
        "message": "privateCannedMessageCategory",
        "IfSetHtmlMessageForEmail": false,
        "htmlMessage": "",
        "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
        "category":    { // include private canned message category
          "id": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
          "name": "justfortest",
         "parentId": "A73FA2EB-4CE3-B195-94C6-567A24F7BDDC"
        },
        "shortcuts": "",
        "similarQuestions": ["are you ok?"]
    },
    ...
]
```

### Get a Private Canned Message by id

  `GET /api/v3/globalSettings/privateCannedMessages/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  | Unique identifier of the private canned message. |

Query string

  | Name  | Type | Required  | Default | Description |
  | - | - | - | - | - |
  | `include` | string | no  |  | Available value: `privateCannedMessageCategory`. |

##### Response

The response is a [Private Canned Message](#private-Canned-Message-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages/AB71E95A-1FA5-E19D-9BA4-9C2144598C57?include=privateCannedMessageCategory
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "C354EA75-BAAF-9994-9307-D001FBE1882A",
  "name": "privateCannedMessageCategory",
  "message": "privateCannedMessageCategory",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
  "category":    { // include private canned message category
    "id": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
    "name": "puddddtresult",
    "parentId": "A73FA2EB-4CE3-B195-94C6-567A24F7BDDC"
  },
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

### Create a new Private Canned Message

  `POST /api/v3/globalSettings/privateCannedMessages`

#### Parameters

Request Body

  The request body contains data with the [Private Canned Message](#private-Canned-Message-object) structure.

example:
```Json
{
  "name": "privateCannedMessageCategorytest1111",
  "message": "privateCannedMessageCategorytest1111",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

#### Response

The response is a [Private Canned Message](#private-Canned-Message-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "privateCannedMessageCategorytest1111",
  "message": "privateCannedMessageCategorytest1111",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
  }' -X POST https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages
```

Response
``` json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages/822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F

{
  "id": "822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F",
  "name": "privateCannedMessageCategorytest1111",
  "message": "privateCannedMessageCategorytest1111",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

### Create a new private similar questions

  `POST /api/v3/globalSettings/privateCannedMessages/{id}/similarQuestions`

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
  }' -X POST https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages/822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F/similarQuestions
```

Response
``` json
HTTP/1.1 201 Created
Content-Type:  application/json
Location: https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages/822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F/similarQuestions

{
  "id": "822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F",
  "name": "publicCannedMessageCategorytest",
  "message": "publicCannedMessageCategorytest",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "5A563046-374D-3C4E-4D4A-2CA3812A42C8",
  "shortcuts": "",
  "similarQuestions": ["are you ok?","not ok?"]
}
```
### Update a Private Canned Message

  `PUT /api/v3/globalSettings/privateCannedMessages/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the private canned message. |

Request Body

  The request body contains data with the [Private Canned Message](#private-Canned-Message-object) structure.

example:
```Json
{
  "name": "privateCannedMessageCategorytest2222",
  "message": "privateCannedMessageCategorytest2222",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

#### Response

The response is a [Private Canned Message](#private-Canned-Message-object) Object.

#### Example

Using curl
```
curl -H "Content-Type: application/json" -d '{
  "name": "privateCannedMessageCategorytest2222",
  "message": "privateCannedMessageCategorytest2222",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
  }' -X PUT https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages/822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F",
  "name": "privateCannedMessageCategorytest2222",
  "message": "privateCannedMessageCategorytest2222",
  "IfSetHtmlMessageForEmail": false,
  "htmlMessage": "",
  "categoryId": "579BCAE9-F43A-CD32-CAF8-BD56786F1447",
  "shortcuts": "",
  "similarQuestions": ["are you ok?"]
}
```

### Delete a Private Canned Message

  `DELETE /api/v3/globalSettings/privateCannedMessages/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes  |  Unique identifier of the private canned message. |

#### Response

HTTP/1.1 204 No Content

#### Example

Using curl
```
curl -X DELETE https://api1.comm100.io/api/v3/globalSettings/privateCannedMessages/822B7B6A-05E9-5DA2-A1B0-1D0FB034AA0F
```

Response
```Json
  HTTP/1.1 204 No Content
```
