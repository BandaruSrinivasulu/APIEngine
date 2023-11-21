# API Set

The API Set is a table of records that represents a collection of [API Functions](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) and one or more [API Credentials](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#def-api-credential). The API Set allows for some referential information about the collection. Most often, the API Set is used to contain many API end points that work together for a functional platform. Example: The Shopify Admin API.

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APISet)

# API Credential

The API Credential record is associated with an API set and defines the authentication type and associated credentials for making API Calls.  The Credential Record also contains the base url, which serves as a default base url for [API Functions](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) that use the Credential Record.  The key to the API Credential Record is API Set Code, API Function Code, and Usage Code.  Each [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) must have at least one Credential Record that has an empty API Function Code and Usage code, this record would be the default Credential Record for all [API Functions](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) tied to the API Set.  API Credential Records that have the API Function Code populated are used by the [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) Record that the API Function Code represents. For more information on the Usage Code (PK2) field and how it can be used, see [API Credential Usage Code](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential-usage-code).

# API Credential Usage Code

The [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#def-api-credential) Usage Code (PK2) field is used situations where the [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#def-api-credential) could change based on the applications needs.  For example, you could have a number of Shopify Stores, each requiring their own specific credentials, but the API definitions do not change, only the credentials change. In this case, it is necessary to supply the API Engine with the correct usage code at run time with an [API Parameter](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#def-api-parameter) Record added to the API Message Record which represents the API Call.  The API Parameter record needs to have the Record Parameter Type with key = CredentialUsageCode and the value containing the usage code to use in getting the appropriate [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#def-api-credential) to use .

# API Function

Under Construction

# API Function Variable

Under Construction

# API Function Mapping

Under Construction
# API Parameter

Under Construction