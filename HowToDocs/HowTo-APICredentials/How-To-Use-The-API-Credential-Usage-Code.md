# How to use the API Credential Usage Code

This Section will describe how to use the API Credential Usage Code in selecting the API Credential Record for an API Call.  The [API Credential][APICredentialDef] Usage Code (PK2) field is used situations where the [API Credential][APICredentialDef] could change based on the applications needs.  For example, you could have a number of Shopify Stores, each requiring their own specific credentials, but the API definitions do not change, only the credentials change.

At run time, the SuiteEngine API Engine will assign a credential record to the [API Message][APICredentialDef]: created for an individual API Call.  It will do so by resolving the [API Credential][APICredentialDef] primary key values (API Set Code, Usage Code, API Function Code).  As part of this process, the API Engine will look for an [API Parameter][APIParameterDef] assigned to the [API Message][APICredentialDef] that has a key of _**CredentialUsageCode**_ and if found, it will use its value as the Usage Code.

The API Engine will then try a series of Gets on the Credential Table to find the most specific [API Credential][APICredentialDef] Record to assign to the message and use for Authentication for the API Call. For more information, see: [How the API Engine Assigns an API Credential to an API Call](https://github.com/SuiteEngine/APIEngine/wiki/How-APIEngine-Assigns-API-Credential-To-API-Calls).

Example:  
:construction: Coming Soon - Walkthrough example of using the API Credential Usage Code.

[APICredentialDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential "Definition of API Credential"
[APIMessageDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-message "Definition of API Message"
[APIParameterDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-parameter "Definition of API Parameter"