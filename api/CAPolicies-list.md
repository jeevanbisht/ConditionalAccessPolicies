---
title: "List Policies"
description: "Retrieve all policy objects in the directory."
localization_priority: Normal
---

# List Policies

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Retrieve all [Condition Access policy](../resources/ConditionalAccessPolicies.md) objects in the directory.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Directory.AccessAsUser.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Not supported. |

## HTTP request
<!-- { "blockType": "ignored" } -->
```http
GET /conditionalaccesspolicies/
```
## Request headers
| Name       | Type | Description|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns `200 OK` response code and [Conditional Access Policy](../resources/ConditionalAccessPolicies.md) objects in the response body. If unsuccessful...

## Example
The following example retrieves all policies.

##### Request
Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/conditionalaccesspolicies/
```

##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-type: application/json
  {
  "@odata.context": "https://graph.microsoft-ppe.com/beta/$metadata#conditionalAccessPolicies",
    "@odata.count": 12,
    "value": [
        {
            "id": "94f8bf38-27b1-46d0-a745-9dac7e22c7d1",
            "displayName": "EXO - Outside362DS",
            "createdDateTime": null,
            "modifiedDateTime": null,
            "state": "enabled",
		}
	]
}
```
<!--
{
  "type": "#page.annotation",
  "suppressions": [
    "Error: /api-reference/beta/api/policy-list.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->



















{
    "@odata.context": "https://graph.microsoft-ppe.com/beta/$metadata#conditionalAccessPolicies",
    "@odata.count": 12,
    "value": [
        {
            "id": "94f8bf38-27b1-46d0-a745-9dac7e22c7d1",
            "displayName": "EXO - Outside362DS",
            "createdDateTime": null,
            "modifiedDateTime": null,
            "state": "enabled",
            "conditions": {
                "signInRiskLevels": [
                    "high",
                    "medium",
                    "low",
                    "none"
                ],
                "clientAppTypes": [
                    "browser",
                    "modern",
                    "easSupported",
                    "other"
                ],
                "applications": {
                    "includeApplications": [
                        "00000002-0000-0ff1-ce00-000000000000"
                    ],
                    "excludeApplications": [
                        "0000000a-0000-0000-c000-000000000000"
                    ],
                    "includeAuthenticationContext": []
                },
                "users": {
                    "includeUsers": [],
                    "excludeUsers": [
                        "Guests"
                    ],
                    "includeGroups": [
                        "796f8da4-21f2-4148-a34b-9735811d5852",
                        "5fad529d-b4a2-4d4d-89c5-e72be11a8ab5"
                    ],
                    "excludeGroups": [
                        "46756a9c-01c0-4526-96e1-5f343c240567"
                    ],
                    "includeRoles": [
                        "cf1c38e5-3621-4004-a7cb-879624dced7c"
                    ],
                    "excludeRoles": []
                },
                "platforms": {
                    "includePlatforms": [
                        "android",
                        "iOS"
                    ],
                    "excludePlatforms": [
                        "windowsPhone"
                    ]
                },
                "locations": {
                    "includeLocations": [
                        "d474030c-f7a0-4adc-9993-2b0de2414818"
                    ],
                    "excludeLocations": [
                        "c7f88cf7-7417-4462-b120-edb3ba512397"
                    ]
                },
                "times": {
                    "excludeDays": null,
                    "includeRange": null,
                    "allTimes": false,
                    "includeDays": {
                        "daysOfWeek": [
                            "Sunday",
                            "Monday",
                            "Tuesday",
                            "Wednesday",
                            "Thursday",
                            "Friday",
                            "Saturday"
                        ],
                        "timeZone": "Pacific Standard Time",
                        "startTime": "11:00:00",
                        "endTime": "11:20:00",
                        "allDay": false
                    },
                    "excludeRange": {
                        "timeZone": "Pacific Standard Time",
                        "startDateTime": "2/14/2019 12:00:00 AM",
                        "endDateTime": "2/15/2019 12:00:00 AM"
                    }
                },
                "deviceStates": {
                    "includeStates": [
                        "All"
                    ],
                    "excludeStates": [
                        "Compliant",
                        "DomainJoined"
                    ]
                }
            },
            "grantControls": {
                "operator": "OR",
                "builtInControls": [
                    "mfa",
                    "compliantDevice",
                    "domainJoinedDevice",
                    "approvedApplication"
                ],
                "customControls": [
                    "IRISCsan"
                ]
            },
            "sessionControls": {
                "persistentBrowser": null,
                "applicationEnforcedRestrictions": {
                    "isEnabled": true
                },
                "cloudAppSecurity": {
                    "isEnabled": true
                },
                "signInFrequency": {
                    "value": 14,
                    "type": "days",
                    "isEnabled": true
                }
            }
        },
        {
            "id