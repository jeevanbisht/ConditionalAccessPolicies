---
title: "Conditional Access Policy resource type"
description: "Represents an Azure AD Conditional Access policy. Conditional access Policies are custom rules that define and access scenario:"
localization_priority: Normal
---

# Conditional Access policy resource type

[!INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)]

Represents an Azure AD Conditional Access policy. Conditional access Policies are custom rules that define and access scenario






This policy is described in further detail below.

## Methods
| Method       | Return Type  |Description|
|:---------------|:--------|:----------|
| [Get policy](../api/CAPolicies-get.md) |Policy|Read properties and relationships of Conditional Access Policy object.|
|[Create policy](../api/CAPolicies-post.md)|Policy|Create a new Conditional Access policy object.|
|[Update policy](../api/CAPolicies-update.md)|None|Update Conditional Access policy object.|
|[Delete policy](../api/CAPolicies-delete.md)|None|Delete Conditional Access policy object.|
|[List policies](../api/CAPolicies-list.md)|Policy collection|Get all Conditional Access policy objects in the organization.|



### Common Properties
| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|id|String|Specifies id of a policy. Read-only|
|displayName|String|Specifies A human-readable name of the policy.|
|createdDateTime|DateTimeOffset|Specifies creation datetime of the policy. Read-only|
|modifiedDateTime|DateTimeOffset|Specifies last modification datetime of the policy. Read-only|
|state|microsoft.graph.conditionalAccessPolicyState |Specifies state of the policy, including Enabled, Disabled, and LogOnly.|
|sessionControls|microsoft.graph.conditionalAccessSessionControls|Specifies complex type of session controls that will be enforced after sign-in.|
|conditions|[microsoft.graph.conditionalAccessConditions](#microsoftgraphconditionalaccessconditions)|Specifies complex type of conditions that govern when the policy applies.|
|grantControls|microsoft.graph.conditionalAccessGrantControls|Specifies complex type of grant controls that must be fulfilled to pass the policy.|

## JSON representation
Here is a JSON representation of the Conditional Access Policy.

```json

{
    "id": "94f8bf38-27b1-46d0-a745-9dac7e22c7d1",
    "displayName": "Test Policy",
    "createdDateTime": null,
    "modifiedDateTime": null,
    "state": "enabled",
    "sessionControls": null,
    "conditions": {
        "signInRiskLevels": [
                ],
        "clientAppTypes": [
                ],
        "applications": {
            "includeApplications": [
                    ],
            "excludeApplications": [
                    ],
            "includeAuthenticationContext": [
			]
        },
        "users": {
            "includeUsers": [],
            "excludeUsers": [],
            "includeGroups": [],
            "excludeGroups": [],
            "includeRoles": [],
            "excludeRoles": [],
        },
        "platforms": {
            "includePlatforms": [
			],
            "excludePlatforms": [
			]
        },
        "locations": {
            "includeLocations": [
			],
            "excludeLocations": [
			]
        },
        "times": {
            "includeRange": null,
            "excludeRange": null,
            "allTimes": false,
            "includeDays": {
                "daysOfWeek": [],
                "timeZone": "Pacific Standard Time",
                "startTime": "11:00:00",
                "endTime": "11:20:00",
                "allDay": false
            },
            "excludeDays": {
                "daysOfWeek": [],
                "timeZone": "Pacific Standard Time",
                "startTime": "11:00:00",
                "endTime": "11:01:00",
                "allDay": false
            }
        },
        "deviceStates": {
            "includeStates": [
                            ],
            "excludeStates": [
                            ]
        }
    },
    "grantControls": {
        "operator": "OR",
        "builtInControls": [
		],
        "customControls": [
		]
    }
}

```

### microsoft.graph.conditionalAccessConditions 
| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|applications|[microsoft.graph.conditionalAccessApplications](#microsoftgraphconditionalaccessapplications)|applications and ACRS tags included in and excluded from the policy scope. Must be populated.|
|clientAppTypes|Collection([microsoft.graph.conditionalAccessClientApps]((#microsoftgraphconditionalaccessapplications))|client application types included in the policy scope. Optionally populated.|
|deviceStates|microsoft.graph.conditionalAccessDeviceStates|device states in the policy scope.|
|locations|microsoft.graph.conditionalAccessLocations|locations included in and excluded from the policy scope. Optionally populated.|
|platforms|microsoft.graph.conditionalAccessPlatforms|platforms included in and excluded from the policy scope. Optionally populated..|
|signInRiskLevels|Collection(microsoft.graph.riskLevel)|risk levels included in the policy scope. Optionally populated.|
|times|microsoft.graph.conditionalAccessTimes|times in scope of the policy.|
|users|microsoft.graph.conditionalAccessUsers|users, groups, and roles included in and excluded from the policy scope. Must be populated.|

### microsoft.graph.conditionalAccessApplications 
| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|includeApplications|Collection of String|Application IDs in scope of policy unless explicitly excluded.|
|excludeApplications|Collection of String|Application IDs excluded from scope of policy.|
|includeAuthenticationContext|ACRS URIs in scope of policy unless explicitly exclude, or ALL.|

### microsoft.graph.conditionalAccessClientApps 
| Property	   | Description|
|:---------------|:----------|
|browser|Browser applications.|
|modern|Modern authentication applications.|
|easSupported|EAS applications on supported platforms.|
|easUnsupported|EAS applications on unsupported platforms.|
|other|Other legacy protocol applications.|
|easSupported|ACRS URIs in scope of policy unless explicitly exclude, or ALL.|





#### Common Relationships
|Relationship|Type|Description|
|:-------------|:-----------|:-----------|
|appliesTo|[directoryObject](../resources/directoryobject.md) collection|The applications, service principals, groups, or organization the policy applies to.|

## Token Lifetime Policy
Specifies the lifetimes of tokens issued for various purposes. This kind of policy can be [assigned](../api/policy-assign.md) to applications and service principals. There are four kinds of tokens whose lifetimes can be configured. Access/Refresh token pairs are obtained during authentication through a client, whereas ID/Session token pairs are obtained during authentication through a browser.

- **Access Token** contains information about the identity and privileges associated with a user account that is used by clients to access protected resources like applications.
- **Refresh Token** is obtained together with the access token when a user authenticates against Azure AD through a client to access a protected resource. While it is not revoked or left unused for more than the MaxInactiveTime (below), it can be used to obtain a new access/refresh token pair when the current access token expires.
- **ID Token** behaves like an access token, but obtained through the browser.
- **Session Token** behaves like a refresh token, but obtained through the browser.

## Properties
The properties below form the JSON object that represents a token lifetime policy. This JSON object must be **converted to a string with quotations escaped** to be inserted into the "definition" common policy property. An example is shown below.

>Note: All time durations in these properties are specified in the format "dd.hh:mm:ss".

>Note: Max values for properties denoted in "days" are 1 second short of the denoted number of days. For example, the max value of 1 days is specified as "23:59:59".

| Property	   | Type	|Description| Min Value | Max Value | Default Value|
|:---------------|:--------|:----------|:--------|:--------|:----|
|AccessTokenLifetime|String|Controls how long **both access and ID tokens** are considered valid.|10 minutes|1 day|1 hour|
|MaxInactiveTime|String|Controls how old a refresh token can be before a client can no longer use it to retrieve a new access/refresh token pair to access a resource.|10 minutes|90 days|14 days|
|MaxAgeSingleFactor|String|Controls how long a user can continue to use refresh tokens to get new access/refresh token pairs after the last time they authenticated successfully with only a single factor. Because single-factor is considered less secure than multi-factor authentication, it is recommended that this policy is set to an equal or lesser value than the MultiFactorRefreshTokenMaxAge.|10 minutes|until-revoked|365 days or until-revoked|
|MaxAgeMultiFactor|String|Controls how long a user can continue to use refresh tokens to get new access/refresh token pairs after the last time they authenticated successfully with multi factors.|10 minutes|until-revoked|365 days or until-revoked|
|MaxAgeSessionSingleFactor|String|Controls how long a user can continue to use session tokens to get new ID/session tokens after the last time they authenticated successfully with only a single factor. Because single-factor is considered less secure than multi-factor authentication, it is recommended that this policy is set to an equal or lesser value than the MultiFactorSessionTokenMaxAge|10 minutes|until-revoked|365 or until-revoked|
|MaxAgeSessionMultiFactor|String|Controls how long a user can continue to use session tokens to get new ID/session tokens after the last time they authenticated successfully with multi factors.|10 minutes|until-revoked|365 or until-revoked|
|Version|Integer|Set value of 1. Required.|None|None|None|



<!--
{
  "type": "#page.annotation",
  "suppressions": [
    "Error: /api-reference/beta/resources/policy.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->