---
title: "Update Policy"
description: "Update properties in a preexisting Conditional Access Policy."
localization_priority: Normal
---

# Update Policy

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Update properties in a preexisting [Conditional Access Policy](../resources/ConditionalAccessPolicies.md).

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Directory.AccessAsUser.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Not supported. |

## HTTP request

```http
PATCH /conditionalaccesspolicies/{id}
```
## Request headers
| Name       | Type | Description|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer {token}. Required. |
| Content-Type | application/json  | Nature of the data in the body of an entity. Required. |

## Request body
In the request body, provide a JSON object with the parameters that need to be updated. The following table shows the possible parameters.

## JSON representation
Here is a sample JSON representation of the microsoft.graph.conditionalAccessApplications Complex type, below are the minimum parameters required for the update operation.

```json

{
    "conditions": {
        "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ],
            "excludeApplications": [],
            "includeAuthenticationContext": []
        },
        "users": {
            "includeUsers": [
                "All"
            ],
            "excludeUsers": [ "Guests"],
            "includeGroups": [],
            "excludeGroups": [],
            "includeRoles": [],
            "excludeRoles": []
        }
}
```

## Response

If successful, this method returns `204 No Content` response code. If unsuccessful, a `4xx` error will be returned with specific details.

## Example
The following example updates the definition of the token lifetime policy and sets it as the organization default.

##### Request
Here is an example of the request. Where we update the Policy displayName

```http
PATCH https://graph.microsoft.com/beta/conditionalaccesspolicies/{id}
Content-Type: application/json
{
      "displayName": "Sample - UpdateTest1",
      "conditions": {
            "applications": {
            "includeApplications": [
                "00000002-0000-0ff1-ce00-000000000000"
            ],
            "excludeApplications": [],
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
        }
    }
}

```

##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 204 No Content
```
<!--
{
  "type": "#page.annotation",
  "suppressions": [
    "Error: /api-reference/beta/api/policy-update.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->