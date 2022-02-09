# Visitor

  You need `Manage Settings` permission to manage visitor.

- `GET /api/v3/globalSettings/visitors` - [Get all visitors in site](#get-all-visitors-in-site)
- `GET /api/v3/globalSettings/visitors/{id}` - [Get a visitor by id](#get-a-visitor-by-id)

## Related Object JSON format

### Visitor Object

  Visitor Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Read-only | Mandatory | Default | Description |
  | - | - | :-: | :-: | :-: | - |
  | `id` | Guid | yes | no | | Identifier of the current item.  |
  | `name` | string  | no | no | | Name of the visitor. |
  | `email` | string  | no | no | | Email of the visitor. |
  | `numberOfVisits` | integer  | no | no | | The total number of web pages the visitor viewed on your website. |
  | `numberOfChats` | integer  | no | no | | The total times of chats a visitor has made on your website from the first time to present. |
  | `firstVisitTime` | datetime  | no | no | | The time the visitor first visited a web page pasted with Comm100 Live Chat code. |

## Visitor Endpoints

### Get all visitors in site

  `GET /api/v3/globalSettings/visitors`

#### Parameters

Query string

| Name  | Type | Required | Default | Description |
| - | - | :-: | :-: | - |
| `requestedTime` | datetime | no  | today |  The time range of query time, defaults to today, format as `yyyy-MM-ddTHH:mm:ss`. |
| `pageIndex` | integer | no  | 1 | The page index of query. |
| `pageSize` | integer | no  | 50 | Page size.  |
| `keywords` | string | no  |  | Filter by keywords in visitor name and email address. |

#### Response

The response body contains data with the follow structure:

| Name | Type | Required | Default | Description |
| - | - | :-: | :-: | - |
| `totalCount` | integer | no | no | Total count of the list. |
| `previousPage` | string | no | no | Url of the previous page. |
| `nextPage` | string | no | no | Url of the next page. |
| `visitors` | [Visitor](#visitor-Object)[] | no | no |  |

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/visitors
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
    "totalCount": 28,
    "previousPage": "",
    "nextPage": "/api/v3/globalSettings/visitors?pageIndex=2",
    "visitors": [{
        "id": "7273e957-02cb-4c03-a84c-44283fcfd47d",
        "name": "test",
        "email": "",
        "numberOfVisits": 4,
        "numberOfChats": 1,
        "firstVisitTime": "2019-06-12T07:41:40.486Z"
    },
    ...
    ]
}
```

### Get a visitor by id

  `GET /api/v3/globalSettings/visitors/{id}`

#### Parameters

Path Parameters

  | Name  | Type | Required  | Description |
  | - | - | - | - |
  | `id` | Guid | yes |  Identifier of the visitor. |

#### Response

The response is a [Visitor](#visitor-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/visitors/7273e957-02cb-4c03-a84c-44283fcfd47d
```

Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "id": "7273e957-02cb-4c03-a84c-44283fcfd47d",
  "name": "test",
  "email": "",
  "numberOfVisits": 4,
  "numberOfChats": 1,
  "firstVisitTime": "2019-06-12T07:41:40.486Z"
}
```