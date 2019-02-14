---
title: "Create Conditional Access Policy"
description: "Create a new Conditional Access Policy object by specifying display name and minimum required parameters."
localization_priority: Normal
---

# Create Policy

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Create a new [Conditional Access policy](../resources/ConditionalAccessPolicies.md) object by specifying display name, policy type, and policy description.

>Note: The policy details will be validated before being stored. If it does not pass validation, a 400 Bad Request will be returned.

## Permissions
One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](/graph/permissions-reference).

|Permission type      | Permissions (from least to most privileged)              |
|:--------------------|:---------------------------------------------------------|
|Delegated (work or school account) | Directory.AccessAsUser.All    |
|Delegated (personal Microsoft account) | Not supported.    |
|Application | Not supported. |

## HTTP request

```http
POST /ConditionalAccessPolicies
```
## Request headers
| Name       | Type | Description|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer {token}. Required. |
| Content-Type | application/json  | Nature of the data in the body of an entity. Required. |

## Request body
In the request body, provide a JSON representation of [Conditional Access policy](../resources/ConditionalAccessPolicies.md) object.

The following table shows the properties that are required when you create a policy.

| Parameter	   | Type	|Description|
|:---------------|:--------|:----------|
|definition|String|The string version of the [policy](../resources/ConditionalAccessPolicies.md) object.|
|displayName|String|A custom name for the Conditional Access Policy.|


## Response

If successful, this method returns `201 Created` response code and [Conditional Access Policy](../resources/ConditionalAccessPolicies.md) object in the response body. If unsuccessful, a `4xx` error will be returned with specific details.  

## Example
The following example creates a new token lifetime Policy. Notice the string definition parameter
has escaped double quotes.

##### Request
Here is an example of the request.

```http
POST https://graph.microsoft.com/beta/ConditionalAccessPolicies
Content-Type: application/json

{


}
```

##### Response
Here is an example of the response. Note: The response object shown here may be truncated for brevity. All of the properties will be returned from an actual call.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context":"https://graph.microsoft.com/beta/$metadata#policies/$entity",
  "id":"id-value",
  "alternativeIdentifier":null,
  "definition":["{\"TokenLifetimePolicy\":{\"Version\":1,\"AccessTokenLifetime\":\"8:00:00\"}}"],
  "displayName":"name-value",
  "isOrganizationDefault":false,
  "keyCredentials",
  "type":"TokenLifetimePolicy"
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
    "Error: /api-reference/beta/api/policy-post.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->