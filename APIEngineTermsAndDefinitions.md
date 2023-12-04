# API Set

The API Set is a table of records that represents a collection of [API Functions][APIFunctionDef] and one or more [API Credentials][APICredentialDef]. The API Set allows for some referential information about the collection. Most often, the API Set is used to contain many API end points that work together for a functional platform. Example: The Shopify Admin API.

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APISet)

# API Credential

The API Credential record is associated with an API set and defines the authentication type and associated credentials for making API Calls.  The Credential Record also contains the base url, which serves as a default base url for [API Functions][APIFunctionDef] that use the Credential Record.  The key to the API Credential Record is API Set Code, API Function Code, and Usage Code.  Each [API Set][APISetDef] must have at least one Credential Record that has an empty API Function Code and Usage code, this record would be the default Credential Record for all [API Functions][APIFunctionDef] tied to the API Set.  API Credential Records that have the API Function Code populated are used by the [API Function][APIFunctionDef] Record that the API Function Code represents. For more information on the Usage Code (PK2) field and how it can be used, see [API Credential Usage Code](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential-usage-code).

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APICredential)

# API Credential Usage Code

The [API Credential][APICredentialDef] Usage Code (PK2) field is used situations where the [API Credential][APICredentialDef] could change based on the applications needs.  For example, you could have a number of Shopify Stores, each requiring their own specific credentials, but the API definitions do not change, only the credentials change. In this case, it is necessary to supply the API Engine with the correct usage code at run time with an [API Parameter](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-parameter) Record added to the API Message Record which represents the API Call.  The API Parameter record needs to have the Record Parameter Type with key = CredentialUsageCode and the value containing the usage code to use in getting the appropriate [API Credential][APICredentialDef] to use.

Learn More  
[How to use the API Credential Usage Code](https://github.com/SuiteEngine/APIEngine/wiki/How-To-Use-The-API-Credential-Usage-Code)

# API Function

API Functions serves as a definition of how to make a particular API call.  You can construct many API calls tailored to what you want to happen for that particular piece of functionality.  For Example, you may have one API Function to retrieve orders from an E-commerce platform, and another API Function to send product information to an E-commerce platform.  All API functions relating to a particular E-commerce Platform would be tied together by the [API Set][APISetDef] related to those functions.  While simple API calls could be made by just the information present on the API Function record, API Functions also have related tables called API Variables and API Mappings.  API Variables help you in constructing complex requests to the API Host, while API Mappings define how the response received from the API host can be processed by inserting or modifying Business Central Table Records.

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APIFunction)

# API Variable

API Variables are records that are used to construct an API Request for an API Function.  There are different types of API Variables for different purposes.

- URL - Overrides the Base URL portion of the API Call URL endpoint.  The Base URL normally comes from the [API Credential][APICredentialDef] Record that is chosen at runtime, however using this Variable type will override that value for this [API Function][APIFunctionDef].
- URL Path - Variables that construct the API Call URL Endpoints Variable Path. (versus the fixed path that can be specified directly on the [API Function][APIFunctionDef].
- URL Parameter  - Variables that construct the API Call URL Endpoints Query Parms or Tags.
- Header  - Variables that construct the API Call Request Headers.
- Body - Variables that construct the API Call Request Body.

# API Function Mapping

:Construction: Under Construction

# API Parameter

Under Construction

# API Message

Under Construction

[APISetDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set "Definition of an API Set"
[APICredentialDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential "Definition of an API Credential"
[APIFunctionDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function "Definition of an API Function"
[APIParameterDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-parameter "Definition of an API Parameter"
