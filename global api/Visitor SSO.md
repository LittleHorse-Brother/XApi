# Visitor SSO

  You need `Manage Settings` permission to set sso for a site.

- `GET /api/v3/globalSettings/visitorSSO` - [Get Visitor SSO](#get-visitor-sso)
- `PUT /api/v3/globalSettings/visitorSSO` - [update Visitor SSO](#update-visitor-sso)

## Related Object JSON format

### Visitor SSO Object

  Visitor SSO Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - |- | :-: | :-: | :-: | - |
  | `isEnabled` | bool  | | no | no | false | |
  | `loginUrl` | string  | | no | yes | | |
  | `artifactResolutionService` | string  | | no | no | | |
  | `signOutUrl` | string  | | no | no | | |
  | `SAMLCertificate` | string  | | no | yes | | Base64 data of certificate file. |
  | `fieldMappings` | [Field Mapping](#field-Mapping-object)[]  | | no | no | | |
  | `perCampaign` | [Visitor SSO Campaign](#visitor-SSO-Campaign-object)[]  |  | no | no | | |

### Field Mapping Object

Field Mapping is represented as simple flat JSON objects with the following keys:

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - |- | :-: | :-: | :-: | - |
  | `attribute` | string | | no | yes | | SSO attribute name. |
  | `comm100Field` | string | | no | yes | | The Comm100 field name.|

### Visitor SSO Campaign Object

Visitor SSO Campaign is represented as simple flat JSON objects with the following keys:

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - |- | :-: | :-: | :-: | - |
  | `campaignId` | Guid |  | no | yes | | Identifier of the campaign.|
  | `campaign` | [Campaign](./Livechat%20API.md#campaign-object)  | yes | no | no | | Available only when campaign is included. |
  | `signInOption` | string |  | no | no | `noSignIn` | Type of the sign in, including `noSignIn`, `signInOptional` and `signInRequired`. |
  | `isPrechatFromSkipped` | bool |  | no | no | true | Whether the pre-chat form is skipped when visitors sign in. |
  | `ifOpenSignInPageEmbeddedWindow` | bool |  | no | no | true | Whether the SSO sign-in is in embedded window. |


## Visitor SSO Endpoints

### Get Visitor SSO

  `GET /api/v3/globalSettings/visitorSSO`

#### Parameters

Query string

  | Name  | Type | Required | Default | Description |
  | - | - | :-: | :-: | - |
  | `include` | string | no  | |  Available value: `campaign`.|

#### Response

The response is a [Visitor SSO](#visitor-SSO-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/visitorSSO?include=campaign
```
Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
    "isEnabled": true,
    "loginUrl": "http://www.xzcs11ffffffff1a",
    "artifactResolutionService":"",
    "signOutUrl":"",
    "SAMLCertificate": "amdoamdoaGdmcnRk",
    "fieldMappings": [
        {
            "attribute": "test999",
            "comm100Field": "{!Visitor.Name}"
        },
        {
            "attribute": "test666",
            "comm100Field": "{!Prechat.Company}"
        }
    ],
    "perCampaign": [
        {
            "campaignId": "cdab2038-1d6c-4fa0-bbf0-17be2e5b39ec",
            "campaign": { //include campaign
                "id":"cdab2038-1d6c-4fa0-bbf0-17be2e5b39ec",
                "name":"testCampaign",
                ...
            },
            "signInOption": "noSignIn",
            "isPrechatFromSkipped": false,
            "ifOPenSignInPageEmbeddedWindow":true
        }
    ]
}
```

### Update Visitor SSO

  `PUT /api/v3/globalSettings/visitorSSO`

#### Parameters

Request Body

  The request body contains data with the [Visitor SSO](#visitor-SSO-object) structure.

example:
```Json
  {
    "isEnabled": true,
    "loginUrl": "http://www.xzcs11ffffffff1a",
    "artifactResolutionService":"",
    "signOutUrl":"",
    "SAMLCertificate": "amdoamdoaGdmcnRk",
    "fieldMappings": [
        {
            "attribute": "test999",
            "comm100Field": "{!Visitor.Name}"
        },
        {
            "attribute": "test666",
            "comm100Field": "{!Prechat.Company}"
        }
    ],
    "perCampaign": [
        {
            "campaignId": "cdab2038-1d6c-4fa0-bbf0-17be2e5b39ec",
            "signInOption": "noSignIn",
            "isPrechatFromSkipped": false,
            "ifOPenSignInPageEmbeddedWindow":true
        }
    ]
  }
```

#### Response

The response is a [Visitor SSO](#visitor-SSO-object) object.

#### Example
Using curl
```
curl -H "Content-Type: application/json" -d '{
    "isEnabled": true,
    "loginUrl": "http://www.xzcs11ffffffff1a",
    "artifactResolutionService":"",
    "signOutUrl":"",
    "SAMLCertificate": "amdoamdoaGdmcnRk",
    "fieldMappings": [
        {
            "attribute": "test999",
            "comm100Field": "{!Visitor.Name}"
        },
        {
            "attribute": "test666",
            "comm100Field": "{!Prechat.Company}"
        }
    ],
    "perCampaign": [
        {
            "campaignId": "cdab2038-1d6c-4fa0-bbf0-17be2e5b39ec",
            "signInOption": "noSignIn",
            "isPrechatFromSkipped": false,
            "ifOPenSignInPageEmbeddedWindow":true
        }
    ]
  }' -X PUT https://api1.comm100.io/api/v3/globalSettings/visitorSSO
```
Response
```Json
  HTTP/1.1 200 OK
  Content-Type:  application/json

  {
    "isEnabled": true,
    "loginUrl": "http://www.xzcs11ffffffff1a",
    "artifactResolutionService":"",
    "signOutUrl":"",
    "SAMLCertificate": "amdoamdoaGdmcnRk",
    "fieldMappings": [
        {
            "attribute": "test999",
            "comm100Field": "{!Visitor.Name}"
        },
        {
            "attribute": "test666",
            "comm100Field": "{!Prechat.Company}"
        }
    ],
    "perCampaign": [
        {
            "campaignId": "cdab2038-1d6c-4fa0-bbf0-17be2e5b39ec",
            "signInOption": "noSignIn",
            "isPrechatFromSkipped": false,
            "ifOPenSignInPageEmbeddedWindow":true
        }
    ]
  }
```
