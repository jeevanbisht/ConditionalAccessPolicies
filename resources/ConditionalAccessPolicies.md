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
|`id`|String|Specifies id of a policy. Read-only|
|`displayName`|String|Specifies A human-readable name of the policy.|
|`createdDateTime`|DateTimeOffset|Specifies creation datetime of the policy. Read-only|
|`modifiedDateTime`|DateTimeOffset|Specifies last modification datetime of the policy. Read-only|
|`state`|[`microsoft.graph.conditionalAccessPolicyState`](#microsoftgraphconditionalaccesspolicystate) |Specifies state of the policy, including Enabled, Disabled, and LogOnly.|
|`sessionControls`|[`microsoft.graph.conditionalAccessSessionControls`](#microsoftgraphconditionalaccesssessioncontrols)|Specifies complex type of session controls that will be enforced after sign-in.|
|`conditions`|[`microsoft.graph.conditionalAccessConditions`](#microsoftgraphconditionalaccessconditions)|Specifies complex type of conditions that govern when the policy applies.|
|`grantControls`|[`microsoft.graph.conditionalAccessGrantControls`](#microsoftgraphconditionalaccessgrantcontrols)|Specifies complex type of grant controls that must be fulfilled to pass the policy.|

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

### microsoft.graph.conditionalAccessPolicyState

| Value           | Description |
|:----------------|:------------|
|`Enabled`| Policy is enabled and enforced|
|`Disabled`| Policy is not enabled or enforced|
|`EnabledForReportingButNotEnforced`| Policy is evaluated and logged but controls are not enforced|





### microsoft.graph.conditionalAccessGrantControls

| Property   | Type|Description|
|:---------------|:--------|:----------|
|`operator`|`String`| Acceptable values: `AND` and `OR`, defines relationship of controls|
|`builtInControls`|Collection of [`microsoft.graph.conditionalAccessGrantControl`](#microsoftgraphconditionalaccessgrantcontrol)| List of enum values of built-in controls specified by the policy|
|`customControls`|Collection of `String`| List of string IDs of custom controls specified by the policy|


#### microsoft.graph.conditionalAccessGrantControl


| Property   | Description|
|:---------------|:----------|
|`Block`| Block sign-in|
|`Mfa`| Require Azure MFA|
|`CompliantDevice`| Require Intune-compliant device|
|`DomainJoinedDevice`| Require AADJ domain-joined device|
|`ApprovedApplication`| Require approved application|
|`CompliantApplication`| Require Intune-compliant application|
|`FederatedMfa`| Require MFA via federation|
|`FederatedCertAuth`| Required certificate authentication via federation|




## JSON representation
Here is a sample JSON representation of the microsoft.graph.conditionalAccessGrantControls Complex type .

```json

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
    }
```


### microsoft.graph.conditionalAccessSessionControls

| Property   | Type|Description|
|:---------------|:--------|:----------|
|`applicationEnforcedRestrictions`|[`microsoft.graph.applicationEnforcedRestrictionsSessionControl`](#microsoftgraphapplicationenforcedrestrictionssessioncontrol)| Session control to enforce application restrictions.|
|`cloudAppSecurity`|[`microsoft.graph.cloudAppSecuritySessionControl`](#microsoftgraphcloudappsecuritysessioncontrol)| Session control to apply cloud app security.|
|`signInFrequency`|[`microsoft.graph.signInFrequencySessionControl`](#microsoftgraphsigninfrequencysessioncontrol)| Session control to enforce signin frequency.|
|`persistentBrowser`|[`microsoft.graph.persistentBrowserSessionControl`](#microsoftgraphpersistentbrowsersessioncontrol)| Session control to define whether to persist cookies or not.|
















### microsoft.graph.applicationEnforcedRestrictionsSessionControl
Session control used to enforce application specific restrictions (e.g. Sharepoint limited access).




### microsoft.graph.cloudAppSecuritySessionControl
Session control used to enforce cloud app security checks.


| Property   | Type|Description|
|:---------------|:--------|:----------|
|`type`|[`microsoft.graph.cloudAppSecuritySessionControlType`](#microsoftgraphcloudappsecuritysessioncontroltype)| Type of check to be performed by the cloud app security service.|


#### microsoft.graph.cloudAppSecuritySessionControlType

This Property is the Enum which can have any of the below defined values. 

| Property	   | 
|:---------------|
|`McasConfigured`| 
|`MonitorOnly`| 
|`BlockDownloads`|
|`ProtectDownloads`| 


### microsoft.graph.signInFrequencySessionControl
Session control used to enforce signin frequency.


| Property   | Type|Description|
|:---------------|:--------|:----------|
|`value`|`Edm.Int32`| Numeric value corresponding to the given type (e.g. 8 hours, 1 day).|
|`type`|[`microsoft.graph.signinFrequencyType`](#microsoftgraphsigninfrequencytype)| Defines the signin frequency type. |

#### microsoft.graph.signinFrequencyType

This Property is the Enum which can have any of the below defined values. 

| Property	   | 
|:---------------|
|`Days`| 
|`Hours`| 





### microsoft.graph.persistentBrowserSessionControl


| Property   | Type|Description|
|:---------------|:--------|:----------|
|`mode`|[`microsoft.graph.persistentBrowserSessionMode`](#microsoftgraphpersistentbrowsersessionmode)| Type of persistent browser session mode (e.g. `always`, `never`).|


#### microsoft.graph.persistentBrowserSessionMode



| Property   | Description|
|:---------------|:----------|
|`always`| Users remain signed in after closing and reopening browser window. Requires policy assignment to All Cloud Apps|
|`never`| Users are signed out after closing and reopening browser window. Requires policy assignment to All Cloud Apps|




## JSON representation
Here is a sample JSON representation of the microsoft.graph.conditionalAccessSessionControls Complex type .

```json

 "sessionControls": {
        "applicationEnforcedRestrictions": null,
        "persistentBrowser": null,
        "cloudAppSecurity": {
            "isEnabled": true
        },
        "signInFrequency": {
            "value": 14,
            "type": "days",
            "isEnabled": true
        }
    }
```






### microsoft.graph.conditionalAccessConditions 
| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|`applications`|[`microsoft.graph.conditionalAccessApplications`](#microsoftgraphconditionalaccessapplications)|applications and ACRS tags included in and excluded from the policy scope. Must be populated.|
|`clientAppTypes`|Collection([`microsoft.graph.conditionalAccessClientApps`](#microsoftgraphconditionalaccessclientapps))|client application types included in the policy scope. Optionally populated.|
|`deviceStates`|[`microsoft.graph.conditionalAccessDeviceStates`](#microsoftgraphconditionalaccessdevicestates)|device states in the policy scope.|
|`locations`|[`microsoft.graph.conditionalAccessLocations`](#microsoftgraphconditionalaccesslocations)|locations included in and excluded from the policy scope. Optionally populated.|
|`platforms`|[`microsoft.graph.conditionalAccessPlatforms`](#microsoftgraphconditionalaccessplatforms)|platforms included in and excluded from the policy scope. Optionally populated..|
|`signInRiskLevels`|Collection([`microsoft.graph.riskLevel`](#microsoftgraphrisklevel))|risk levels included in the policy scope. Optionally populated.|
|`times`|[`microsoft.graph.conditionalAccessTimes`](#microsoftgraphconditionalaccesstimes)|times in scope of the policy.|
|`users`|[`microsoft.graph.conditionalAccessUsers`](#microsoftgraphconditionalaccessusers)|users, groups, and roles included in and excluded from the policy scope. Must be populated.|




#### microsoft.graph.conditionalAccessApplications 
| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|`includeApplications`|Collection of `String`|Application IDs in scope of policy unless explicitly excluded.|
|`excludeApplications`|Collection of `String`|Application IDs excluded from scope of policy.|
|`includeAuthenticationContext`|ACRS URIs in scope of policy unless explicitly exclude, or ALL.|

#### microsoft.graph.conditionalAccessClientApps 
This Property is the Enum which can have any of the below defined values.

| Property	   | Description|
|:---------------|:----------|
|`Browser`|Browser applications.|
|`Modern`|Modern authentication applications.|
|`EasSupported`|EAS applications on supported platforms.|
|`EasUnsupported`|EAS applications on unsupported platforms.|
|`Other`|Other legacy protocol applications.|

Note : The values are case sensitive



#### microsoft.graph.conditionalAccessDeviceStates 

| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|`includeStates`|Collection of `String`|States in scope of policy (ALL only allowed value).|
|`excludeStates`|Collection of `String`|States excluded from scope of policy. Only supports values are  `Compliant` or/and `DomainJoined` |



#### microsoft.graph.conditionalAccessLocations 

| Property	   | Type	|Description|
|:---------------|:--------|:----------|
|`includeLocations`|Collection of `String`|Location IDs in scope of policy unless explicitly excluded, or ALL, or AllTrusted.|
|`excludeLocations`|Collection of `String`|Location IDs excluded from scope of policy |




#### microsoft.graph.conditionalAccessPlatforms	 
This Property is the Enum which can have any of the below defined values. 

| Property	   | Description|
|:---------------|:----------|
|`All`|All platforms.|
|`Android`|Android.|
|`Ios`|iOS.|
|`Windows`|Windows platforms.|
|`WindowsPhone`|Windows Phone.|
|`MacOs`|MacOS.|

Note : The values are case sensitive



#### microsoft.graph.riskLevel	 
This Property is the Enum which can have any of the below defined values. 

| Property	   | Description|
|:---------------|:----------|
|`High`| High Risk .|
|`Medium`| Medium Risk .|
|`Low`| Low Risk.|
|`None`| No Risk.|


Note : The values are case sensitive



#### microsoft.graph.conditionalAccessTimes	 

| Property   | Type|Description|
|:---------------|:--------|:----------|
|`allTimes`|`Boolean`| Apply to all times. If true, overrides all other time/day settings |
|`includeDays`|[`microsoft.graph.conditionalAccessDays`](#microsoftgraphconditionalaccessdays)| Set of days of the week and times to include in scope of policy|
|`excludeDays`|[`microsoft.graph.conditionalAccessDays`](#microsoftgraphconditionalaccessdays)| Set of days of the week and times to exclude from scope of policy|
|`includeRange`|[`microsoft.graph.conditionalAccessTimeRange`](#microsoftgraphconditionalaccesstimerange)| A time range to include in scope of policy|
|`excludeRange`|[`microsoft.graph.conditionalAccessTimeRange`](#microsoftgraphconditionalaccesstimerange)| A time range to exclude from scope of policy|


##### microsoft.graph.conditionalAccessDays


| Property   | Type|Description|
|:---------------|:--------|:----------|
|`daysOfWeek`|Collection of [`microsoft.graph.dayOfWeek`](#microsoftgraphdayofweek)| Which days of the week are included|
|`timeZone`|`String`| Time zone in +HH or -HH formatv (ISO 8601)|
|`startTime`|`String`| Start time each day in HH:MM:SS format (ISO 8601)|
|`endTime`|`String`| End time each day in HH:MM:SS format (ISO 8601)|


###### microsoft.graph.dayOfWeek
This Property is the Enum which can have any of the below defined values. 

| Property	   | 
|:---------------|
|`Sunday`| 
|`Monday`| 
|`Tuesday`|
|`Wednesday`| 
|`Thursday`| 
|`Friday`|
|`Saturday`|




##### microsoft.graph.conditionalAccessTimeRange


| Property   | Type|Description|
|:---------------|:--------|:----------|
|`timeZone`|`String`| Time zone in +HH:MM or -HH:MM format (ISO 8601)|
|`startDateTime`|`String`| Start time each day in YYYY-MM-DDTHH:MM:SS format (ISO 8601)|
|`endDateTime`|`String`| End time each day in YYYY-MM-DDTHH:MM:SS format (ISO 8601)|







#### microsoft.graph.conditionalAccessUsers 
| Property   | Type|Description|
|:---------------|:--------|:----------|
|`includeUsers`|Collection of `String`| User IDs in scope of policy unless explicitly excluded, or `ALL` or `GUEST`|
|`excludeUsers`|Collection of `String`| User IDs excluded from scope of policy and/or `GUEST`|
|`includeGroups`|Collection of `String`| Group IDs in scope of policy unless explicitly excluded, or `ALL`|
|`excludeGroups`|Collection of `String`| Group IDs excluded from scope of policy|
|`includeRoles`|Collection of `String`| Role IDs in scope of policy unless explicitly excluded, or `ALL`|
|`excludeRoles`|Collection of `String`| Role IDs excluded from scope of policy|


## JSON representation
Here is a sample JSON representation of the microsoft.graph.conditionalAccessApplications Complex type .

```json

"conditions": {
        "signInRiskLevels": [
            "High",
            "Medium",
            "Low",
            "None"
        ],
        "clientAppTypes": [
            "Browser",
            "Modern",
            "EasSupported",
            "Other"
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
                "Android",
                "Ios"
            ],
            "excludePlatforms": [
                "WindowsPhone"
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
                    "Monday",
                    "Tuesday",
                    "Wednesday",
                    "Thursday",
                    "Friday"
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

```



<!--
{
  "type": "#page.annotation",
  "suppressions": [
    "Error: /api-reference/beta/resources/policy.md:\r\n      Exception processing links.\r\n    System.ArgumentException: Link Definition was null. Link text: !INCLUDE [beta-disclaimer](../../includes/beta-disclaimer.md)\r\n      at ApiDoctor.Validation.DocFile.get_LinkDestinations()\r\n      at ApiDoctor.Validation.DocSet.ValidateLinks(Boolean includeWarnings, String[] relativePathForFiles, IssueLogger issues, Boolean requireFilenameCaseMatch, Boolean printOrphanedFiles)"
  ]
}
-->