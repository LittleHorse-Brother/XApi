# Agent SSO

  You need `Manage Security` permission to set sso for a site.

- `GET /api/v3/globalSettings/agentSSO` - [Get Agent SSO](#get-agent-sso)
- `PUT /api/v3/globalSettings/agentSSO` - [update Agent SSO](#update-agent-sso)

## Related Object JSON format

### Agent SSO Object

  `Agent SSO` Object is represented as simple flat JSON objects with the following keys:

  | Name | Type | Include | Read-only| Mandatory| Default | Description |
  | - | - | - | :-: | :-: | :-: | - |
  | `isEnabled` | bool  | | no | no|false| |
  | `protocolType` | string |  | no | yes | | Including `SAML` and `JWT`. |
  | `samlSSOURL` | string |  | no |yes | |Mandatory when type is `SAML`. |
  | `samlLogoutURL` | string |  | no | no | | Only available when type is `SAML`. |
  | `samlCertificate` | string |  | no | yes | | SAML certificate, mandatory when type is `SAML`.|
  | `jwtLoginURL` | string |  | no | yes | | Mandatory when type is `JWT`. |
  | `jwtLogoutURL` | string |  | no | no | | Only available when type is `JWT`.  |
  | `jwtSecret` | string |  | no | no | | Mandatory when type is `JWT`.  |

## Agent SSO Endpoints

### Get Agent SSO

  `GET /api/v3/globalSettings/agentSSO`

#### Parameters

    No parameters

#### Response

The response is an [Agent SSO](#agent-SSO-object) object.

#### Example

Using curl
```
curl -H "Content-Type: application/json"
-X GET https://api1.comm100.io/api/v3/globalSettings/agentSSO
```
Response
``` json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "isEnabled": true,
  "protocolType": "SAML",
  "samlSSOURL": "https://api1.comm100.io/SAML/SSOLogin",
  "samlLogoutURL": "https://api1.comm100.io/SAML/SSOLogout",
  "samlCertificate": "9F4709DB-C391-4896-94BA-3A17BE12D9E2jji-----",
  "jwtLoginURL": "",
  "jwtLogoutURL": "",
  "jwtSecret": ""
}
```

### Update Agent SSO

  `PUT /api/v3/globalSettings/agentSSO`

#### Parameters

Request Body

  The request body contains data with the [Agent SSO](#agent-SSO-object) structure.

 example:
```Json
  {
    "isEnabled": true,
    "protocolType": "JWT",
    "jwtLoginURL": "https://api1.comm100.io/JWT/SSOLogin",
    "jwtLogoutURL": "https://api1.comm100.io/JWT/SSOLogout",
    "jwtSecret": "9F4709DB-C391-4896-94BA-3A17BE12D9E2jji-----"
  }
```

#### Response

The response is an [Agent SSO](#agent-SSO-object) object.

#### Example
Using curl
```
curl -H "Content-Type: application/json" -d '{
    "isEnabled": true,
    "protocolType": "JWT",
    "jwtLoginURL": "https://api1.comm100.io/JWT/SSOLogin",
    "jwtLogoutURL": "https://api1.comm100.io/JWT/SSOLogout",
    "jwtSecret": "9F4709DB-C391-4896-94BA-3A17BE12D9E2jji-----"
  }' -X PUT https://api1.comm100.io/api/v3/globalSettings/agentSSO
```
Response
```Json
HTTP/1.1 200 OK
Content-Type:  application/json

{
  "isEnabled": true,
  "protocolType": "JWT",
  "samlSSOURL": "",
  "samlLogoutURL": "",
  "samlCertificate": "",
  "jwtLoginURL": "https://api1.comm100.io/JWT/SSOLogin",
  "jwtLogoutURL": "https://api1.comm100.io/JWT/SSOLogout",
  "jwtSecret": "9F4709DB-C391-4896-94BA-3A17BE12D9E2jji-----"
}
```