# Audit Log
  You need `View Audit Log` permission to view audit logs.

  + `GET /api/v3/globalSettings/auditLogs` - [Get audit logs list](#get-audit-logs-list)

## Audit Log Object JSON format

### Audit Log Object

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - | :-: | :-: | :-: | :-: | - |
  |`id` | integer | | yes | no | |  |
  |`category` | string| | no | no | | The value options include: liveChat, ticketingAndMessaging, bot, globalSettings, and knowledge base.|
  |`actionTime` | DateTime | | no | no |  |  |
  |`actionType` | string | | no  | no  | | [action types for different applications](#action-types-for-different-applications) |
  |`actionSummary` | string| | no  | no  | |  |
  |`actionDetails` | string| | no  | no  | |  |
  |`createdBy` | integer | | no  | no  | | Identifier of the oprator agent. |
  |`agent` | [Agent](#agent) | yes | no  | no  | | The oprator agent. |

### Audit Log List Response Object

  Agent List Object for agent list Response, include count and page information.

  | Name | Type | Include | Read-only | Mandatory | Default | Description |
  | - | - | :-: | :-: | :-: | :-: | - |
  |`count` | integer  | no | yes | no | | The total count of the query.  |
  |`nextPage` | string  | no | yes | no | | The next page url of the query.  |
  |`previousPage` | string  | no | yes | no | | The previous page url of the query.  |
  |`auditLogs`| [AuditLog](#audit-log-object)[]| no | yes| 0 | | A list of Audit Log. |

### Action types for different applications

  | Live Chat | Ticketing And Messaging | Knowledge Base | Bot|	Global |
  | - | - | - | - | - |
  | audioAndVideoChatManagement | autoAllocationManagement | categoryManagement | agentAssistLearningManagement | accountProfileManagement |
  | autoAcceptSetting | blockSenderManagement | articleManagement | agentAssistSettingManagement | agentManagement |
  | autoInvitationManagement | channelIntegrationManagement | tagManagement | agentAssistSynonymManagement | agentRoleManagement |
  | autoTranslationManagement | conversationManagement | imageManagement | botSettings | applicationsManagement |
  | banManagement | fieldsAndMappingsManagement | designManagement | botsManagement | billingInfoManagement |
  | campaignsManagement |ticketAndMessagingRoutingRulesManagement | customPageManagement | entitiesManagement | cannedMessageManagement |
  | chatsAuto-AllocationManagement | slaPoliciesManagement | knowledgeBaseManagement | intentsManagement | customAwayStatusManagement |
  | chatSettingsManagement | triggerManagement | | quickRepliesManagement | customerAccountsManagement |
  | cobrowsingManagement | workingTimeAndHolidaysManagement | | smartTriggersManagement | departmentManagement |
  | conversionManagement | | | visitorQuestioninLearningDelete | integrationAndAPIManagement |
  | customVariableManage | | | | licenseManagement |
  | dashboardCustomMetricManagement | | | | manageAccountStatusorState |
  | liveChatRoutingRulesManagement | | | | manuallyChargeandActiveAccount |
  | secureFormManagement | | | | restrictedWordsManagement |
  | segmentationManagement | | | | securityManagement |
  | shiftsManagement | | | | siteProfileManagement |
  | transcriptDelete | | | |   |
  | visitorSSOManagement | | | |   |

## Audit Log Endpoints

### Get audit logs list

  `GET /api/v3/globalSettings/auditLogs`

  #### Parameters

   Query stringno

  | Name  | Type | Required  | Default | Description |
  | - | - | - | - | - |
  |`dateFrom`|DateTime|no||The date from which agent did the action, format as yyyy-MM-ddTHH:mm:ss. |
  |`dateTo`|DateTime|no||The date when an agent ended the action, format as yyyy-MM-ddTHH:mm:ss. |
  |`category`|string|no||The category, which the action belongs to |
  |`actionType`|string|no||The action type. |
  |`agentId`|integer |no|| Identifier of the agent who did the action. |
  |`keywords`|string|no||The keywords associated with the action. |
  |`pageIndex`|integer|no| 1 | The page index of the query. |
  |`pageSize`|integer|no| 10 |The page size of the query. |
  |`include`|string|no||Available value: `agent`. |


#### Response

  The response is a list of [Audit Log List Response](#audit-log-list-response-object) Objects

  #### Example
Using curl
```
curl -H "Content-Type: application/json" -X GET https://api1.comm100.io/api/v3/globalSettings/auditLogs
```
Response
```json
HTTP/1.1 200 OK
Content-Type:  application/json
{
    "count": 1234,
    "nextPage": "https://api1.comm100.io/api/v3/globalSettings/auditLogs?pageIndex=2",
    "previousPage": "",
    "auditLogs": [
      {
        "id": 201,
        "name": "add Agent",
        "category": "My Account Global Settings",
        "actionTime": "2020-02-02",
        "createdBy": 68,
        "actionType": "Add Agent",
        "actionSummary": "Add Agent",
        "actionDetails": "Add Agent for Live Chat",
      },
      ...,
      ]
}
```