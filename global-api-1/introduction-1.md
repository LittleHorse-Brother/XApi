# Introduction (1)

### title: Introduction createdAt: 2022-02-08T07:54:04.000Z updatedAt: 2022-02-09T04:31:44.000Z

Welcome to the Comm100 RESTful API help guide. Our APIs make it possible for you to integrate your applications with Comm100 Live Chat to achieve seamless data sharing. It is our goal to help the business to automate and enhance their customer support with innovative projects you can create using Comm100 API.

Note: Comm100 currently has two versions of our customer engagement platform.

* If you started using Comm100 before Apr 19, 2021, and not yet upgraded to the latest platform, this is the correct API version(3.0) for you. Please use 3 as the version number in each API call.
* If you started using Comm100 on/after Apr 19, 2021, ,or you have been upgraded to the latest platform, you need to use the API 4.0 documentation .

### The Basics

Comm100 RESTful API must use **https** protocol. What the API requests should start with depends on your platform domain, which can be accessed from both your Control Panel and web version Agent Console after successful login. For example:

* If your Control Panel domain is portal1.comm100.io, all API requests (except for the API request in generating the access token) should start with [https://api1.comm100.io/api/v3/](https://api1.comm100.io/api/v3/).
* If your Control Panel domain is portal2.comm100.io, all API requests (except for the API request in generating the access token) should start with [https://api2.comm100.io/api/v3/](https://api2.comm100.io/api/v3/).
* If your Control Panel domain is portal3.comm100.io, all API requests (except for the API request in generating the access token) should start with [https://api3.comm100.io/api/v3/](https://api3.comm100.io/api/v3/).
* If your Control Panel domain is portal5.comm100.io, all API requests (except for the API request in generating the access token) should start with [https://api5.comm100.io/api/v3/](https://api5.comm100.io/api/v3/).
* If your Control Panel domain is portal7.comm100.io, all API requests (except for the API request in generating the access token) should start with [https://api7.comm100.io/api/v3/](https://api7.comm100.io/api/v3/).

### Authentication

Comm100 provides two authentication methods.

/

* API\_key Authentication
* [OAuth Authentication](broken-reference)

```html
```

### API\_key Authentication

For each method call, you must use your email and API\_KEY.Authentication to the API is done via HTTP Basic Auth. Provide your email as the basic auth username and API\_KEY as the password. You must authenticate for API requests.

Note:Comm100 recommends using OAuth authentication even though it supports the API\_KEY type of authentication.

```html
```

### OAuth Authentication

You can use OAuth2 to authenticate all your API requests to Comm100. OAuth provides a more secure way for your application to access your account data without requiring that sensitive information, like email and password to be sent with the requests. There are different OAuth flows for different types of API.

Note that while generating an access token, the API request should start with your platform domain, which is different from the other API requests. For example:

* If your Control Panel domain is portal1.comm100.io, the API requests should start with [https://portal1.comm100.io/](https://portal1.comm100.io).
* If your Control Panel domain is portal2.comm100.io, the API requests should start with [https://portal2.comm100.io/](https://portal2.comm100.io).
* If your Control Panel domain is portal3.comm100.io, the API requests should start with [https://portal3.comm100.io/](https://portal3.comm100.io).
* If your Control Panel domain is portal5.comm100.io, the API requests should start with [https://portal5.comm100.io/](https://portal5.comm100.io).
* If your Control Panel domain is portal7.comm100.io, the API requests should start with [https://portal7.comm100.io/](https://portal7.comm100.io).

#### How to get the access token?

#### Using curl

Params:

* email - the email of the agent account.
* password - the password of the agent account.
* grant\_type - specify `password` as the value.

```bash
    curl https://portal1.comm100.io/oauth/token -H "Content-Type:application/x-www-form-urlencoded"  
     -d 'grant_type=password&email={comm100_agent_email}&password={comm100_agent_password}'  
     -x POST
```

#### Example Response

```bash
  HTTP/1.1 200 OK
  Content-Type: application/json
  {
    "access_token":"vQAQmLX8jvtsG71ItN2QAisqI_F7cDIE0yaX0FfS3RX6g-HR4gfHSVMaOukomYJiJX0Q"
    ,"token_type":"bearer"
    ,"expires_in":43199
    ,"refresh_token":"91a728cdd4c64fb7b128f74f4855c3daee44167ef60542a2b45c21e16373ed02"
  }
```

#### Notes

The token has an expiration time. If the token has expired, call the API again to obtain a new token.

#### How to call the comm100 v3 api by the access token?

You can use the access token to call the comm100 v3 api. For example.

#### Example

#### Using curl

```bash
    curl -H "Authorization: Bearer eyJhbGciOiJodHRwOi8vd3d3LnczLm9yZy8yMDAxLzA0L3htbGRzaWctbW9yZSNyc2Etc2hhMjU2IiwidHlwIjoiSldUIn0.eyJqdGkiOiI1NjIzNDFjZS0zZDkyLTRlZDYtOGY3ZS0zYTQ0NTdlYjQ0OTEiLCJhZ2VudElkIjoiMSIsInNpdGVJZCI6IjEwMDAxMDAwIiwidGh1bWJwcmludCI6IjhBNjhBOThBQzg0MUI1QTc5OEQ5RkE1MTY1QUU0Nzk3NEVERkIyRjYiLCJzdWNjZXNzIjoiVHJ1ZSIsIm5iZiI6MTU4NzY5NTk4MSwiZXhwIjoxNTg3NzAzMTgxLCJpc3MiOiJwb3J0YWwxLmNvbW0xMDAuaW8ifQ.MKuNrAqkbX5HMPwGH9hT-LlZp__CrNJpavXN7UR2qwM2C5TKG1ooghriQruaEBNDFwV8d7mjuwUMcydII2ayngX5jneabirqlhEu0O3LxGitR7P8NyQMDRMEh2ssJmIIJiCKwz9Mr_IzbtNgBZ5yAJ59jQ3hZZErrs62tlhPcMDAxOvTd9wAePUsISb3_-MbUU_WM9cLIKmQi9XWAUw0U4Lvxqp2dopkTLFyynahQGKbKMP934MMwRlKDQko0GZzcjIokYMWfqhesW9iZnJHP-_JQYjbkd4YL1IGUrD2BygD_trcm6Tk2odcYQKPx8vFvR62lU2_pm8i66ECvN-sAA" 
         -H "Content-Type: application/json"
      -d '{
            "name": "livechat15293908029",
            "color": "339FD9",
            "isEnable": false,
            "order": 1,
            "description": "",
            "conditionMetType": "all",
            "logicalExpression": "",
            "conditions": [
              {
                "field": "CurrentPageUrl",
                "operator": "include",
                "value": "live",
                "order": 1
              }
            ],
            "alertTo":{
                "agentIds":[4,5],
                "departmentIds":[]
              }
          }' 
      -X POST https://api1.comm100.io/api/v3/livechat/customerSegments
```

#### Example Response

```bash
  HTTP/1.1 201 Created
  Location: https://api1.comm100.io/api/v3/livechat/customerSegments/1487fc9d-92e6-4487-a2e8-92e68d6892e6
  Content-Type:  application/json
  {
    "name": "livechat15293908029",
    "color": "339FD9",
    "isEnable": false,
    "order": 1,
    "description": "",
    "conditionMetType": "all",
    "logicalExpression": "",
    "conditions": [
      {
        "field": "CurrentPageUrl",
        "operator": "include",
        "value": "live",
        "order": 1
      }
    ],
    "alertTo":{
        "agentIds":[4,5],
        "departmentIds":[]
    }
  }
```

### Data Format

Comm100 RESTful API returns data in [JSON](https://en.wikipedia.org/wiki/JSON) format.

### Error Handling

Errors are returned using standard HTTP error code syntax. Generally, codes in the `2xx` range indicate success; codes in the `4xx` range indicate an error (bad or missing parameters, not authenticated, etc.); codes in the `5xx` range indicate an error with Comm100 Live Chat servers.

* `400` - Bad Request. The request cannot be fulfilled due to bad syntax. You need to make sure that passed arguments are matching format in the method's documentation.
* `401` - Unauthorized. The username or API key you provide is invalid. Please make sure that you authenticate with the correct username or API key.
* `403` - Forbidden. Your permission to access the requested resource has been denied or the number of your API requests has exceeded the limit of the day.
* `404` - Not Found. The requested resource could not be found but may be available at a later time.
* `500` - Internal Server Error. The request was incorrect. You need to make sure that the passed arguments match the formats in the method's documentation.

An error including `code` and `message` is returned in JSON format when an API request fails. For example:

```bash
{ code: 400000, message: "Parameter 'timeFrom' is required." }
```
