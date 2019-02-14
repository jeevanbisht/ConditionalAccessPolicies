---
title: "Get Policy"
description: "Retrieve the properties of a Conditional Access Policy."
localization_priority: Normal
---

# Get Policy

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Retrieve the properties of a [Conditional Access Policy](../resources/ConditionalAccessPolicies.md).

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
GET /conditionalaccesspolicies/{id}
```
## Request headers
| Name       | Type | Description|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer {token}. Required. |

## Request body
Do not supply a request body for this method.

## Response

If successful, this method returns `200 OK` response code and a [Conditional Access Policy](../resources/ConditionalAccessPolicies.md) object in the response body. If unsucccessful...

## Example
The following example retrieves a specific policy.

##### Request
Here is an example of the request.

```http
GET https://graph.microsoft.com/beta/conditionalaccesspolicies/<id>

```

##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#conditionalAccessPolicies/$entity",
    "id": "94f8bf38-27b1-46d0-a745-9dac7e22c7d1",
    "displayName": "Test Sample Policy",
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
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!--
{
  "type": "#page.annotation",
  "description": "message: createReply",
  "keywords": "",
  "section": "documentation",
  "tocPath": "",
  "suppressions": [
    "Error: /api-reference/beta/api/policy-get.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->