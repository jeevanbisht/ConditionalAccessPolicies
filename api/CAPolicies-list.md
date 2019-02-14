---
title: "List Policies"
description: "Retrieve all Conditional Access Policy objects in the directory."
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#conditionalAccessPolicies",
    "@odata.count": 12,
    "value": [
        {
            "id": "94f8bf38-27b1-46d0-a745-9dac7e22c7d1",
            "displayName": "Test Policy Sample",
            "createdDateTime": null,
            "modifiedDateTime": null,
            "state": "enabled",
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




