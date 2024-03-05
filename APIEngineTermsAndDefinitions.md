# API Set

The API Set is a table of records that represents a collection of [API Functions](#api-function) and one or more [API Credentials](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential). The API Set allows for some referential information about the collection. Most often, the API Set is used to contain many API end points that work together for a functional platform. Example: The Shopify Admin API.

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APISet)

# API Credential

The API Credential record is associated with an API set and defines the authentication type and associated credentials for making API Calls.  The Credential Record also contains the base url, which serves as a default base url for [API Functions](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) that use the Credential Record.  The key to the API Credential Record is API Set Code, API Function Code, and Usage Code.  Each [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) must have at least one Credential Record that has an empty API Function Code and Usage code, this record would be the default Credential Record for all [API Functions](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) tied to the API Set.  API Credential Records that have the API Function Code populated are used by the [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) Record that the API Function Code represents. For more information on the Usage Code (PK2) field and how it can be used, see [API Credential Usage Code](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential-usage-code).

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APICredential)

# API Credential Usage Code

The [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential) Usage Code (PK2) field is used situations where the [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential) could change based on the applications needs.  For example, you could have a number of Shopify Stores, each requiring their own specific credentials, but the API definitions do not change, only the credentials change. In this case, it is necessary to supply the API Engine with the correct usage code at run time with an [API Parameter](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-parameter) Record added to the API Message Record which represents the API Call.  The API Parameter record needs to have the Record Parameter Type with key = CredentialUsageCode and the value containing the usage code to use in getting the appropriate [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential) to use.

Learn More  
[How to use the API Credential Usage Code](https://github.com/SuiteEngine/APIEngine/wiki/How-To-Use-The-API-Credential-Usage-Code)

# API Function

API Functions serves as a definition of how to make a particular API call.  You can construct many API calls tailored to what you want to happen for that particular piece of functionality.  For Example, you may have one API Function to retrieve orders from an E-commerce platform, and another API Function to send product information to an E-commerce platform.  All API functions relating to a particular E-commerce Platform would be tied together by the [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) related to those functions.  While simple API calls could be made by just the information present on the API Function record, API Functions also have related tables called API Variables and API Mappings.  API Variables help you in constructing complex requests to the API Host, while API Mappings define how the response received from the API host can be processed by inserting or modifying Business Central Table Records.

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APIFunction)

# API Variable

API Variables are records that are used to construct an API Request for an [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function).  There are different types of API Variables for different purposes.

- URL - Overrides the Base URL portion of the API Call URL endpoint.  The Base URL normally comes from the [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential) Record that is chosen at runtime, however using this Variable type will override that value for this [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function).
- URL Path - Variables that construct the API Call URL Endpoints Variable Path. (versus the fixed path that can be specified directly on the [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function).
- URL Parameter  - Variables that construct the API Call Endpoints Query Parms or Tags.
- Header  - Variables that construct the API Request Headers.
- Body - Variables that construct the API Request Body.

[Learn More](https://github.com/SuiteEngine/APIEngine/wiki/LearnMore-APIVariable)


# API Mapping

API Mappings are records that are used to process an API Responses for an API Function.  API Mappings make it possible to marshall the response body to records in Business Central.  With API Mappings it is possible to insert new records or update existing records.

:Construction: Learn More

# API Message

The API Message is the central figure in an individual API Call, for every API Call, there is one (and only one) API Message.  API Functions can have many API Messages associated, each representing a unique call that used that function to create the request and process the response.

As and API Call is processed, the message progresses through a life cycle:

1.  API Message is initialized for an API Function.
2.  API Parameters are added to the API Message as required
3.  API Message builds the API Call request
4.  API Message sends the API Call
5.  API Message receives the Response
6.  API Message builds and API Data Buffer with the response payload.
7.  API Message processes the API Mappings using the API Data Buffer.
8.  API Message finialization

:Construction: Learn More

# API Parameter

An API Parameter serves as an API call information link between an API Message and an API Functions variables and mappings.  The API Parameter is a flexible data structure that can provide data as part of the API Message life cycle.  This data can be key value, or can reference a record in a BC table (RecordRef).  The API Parameter can be added to an API Message via the API Message card page, or programatically.

`SENAPIMessage := SENAPIMessageManagement.CreateNewAPIMessage('TWILIODIRECTIONSDEMO', 'DEMO_3_UPD_SMS_TEXT_STATUS');`

`//Add the SMS Text Record to the API Message Parameters`

`MyRecordRef.Get(SMSText.RecordId);`

`SENAPIMessageManagement.AddNewRecordParamterToAPIMessage(SENAPIMessage, MyRecordRef);`

`//Execute the API Message to do this action`

`SENAPIMessageManagement.ExecuteAPIMessage(SENAPIMessage);`

You can also add arrays of records as API Parameters as well and create parent / child relationships of API Parameters.

:Construction: Learn More

# API Data Buffer

The API Data Buffer is a table that stores structured information received in an API Message response.  It is essentially a key value data structure with parent and child relationships. An API Message can have numerous API Data Buffer entries associated with it.  The API Engine logic knows how to parce JSON and XML payloads into the API Data Buffer structure.

:Construction: Learn More
