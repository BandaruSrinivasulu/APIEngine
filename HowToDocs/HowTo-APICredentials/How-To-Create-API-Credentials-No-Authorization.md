# How to Create an API Credential with No Authentication

This Section will describe how to add a default Credential to an [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) where the API Host does not require authentication to execute API Calls.  Note that at least one API Credential is required for each [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) that serves as the default credential for the API Engine to use for all API Calls defined by the [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set).

From the [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) List Page, select the API Set that you would like to maintain API Credentials for and press the API Credentials navigation action button.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APICredentials/HowTo-CreateAPICredential-Assets/OpenAPICredentialsFromAPISetListPage.png)

Press the New Action to create a new API Credential Record for the Postman Echo API Set. For this exercise, we are creating an API Credential for API calls to Postman Echo that do not require Authorization.  Only fields in the General fast tab will be used in this exercise.  The other fast tabs that supply additional information based on the Authorization Type can be left empty.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APICredentials/HowTo-CreateAPICredential-Assets/APICredential-NoAuth-Example.png)

1.  **API Set Code** - The API Set Code of the API Set this Credential is related to.
2.  **Usage Code** - For this basic example, we will leave this field blank. For more information on how the Usage Code can be used to pick from different credentials see: [How to use the API Credential Usage Code](https://github.com/SuiteEngine/APIEngine/wiki/How-To-Use-The-API-Credential-Usage-Code).
3.  **Function Code** - For this basic example, we will leave this field blank. The Function Code can be used to specify a Credential to be used for a specific API Function of the API Set.
4.  **Description** - A user defined description of this API Credential Record. The maximum description length is 250 characters.
5.  **Authorization Type** - Defines how authorization / authentication should be handled for an API call using this credential. For this how to, select No Authorization.
6.  **Auth Data Placement** - Designates where Authorization / Authentication Data should be placed in the request. For our how to, the value of the field can be ignored since we do not have any Authentication for API calls using this credential.
7.  **Shared Session** - Allows this credential record to be tied to a shared session, this is necessary where credentials expire over time and a new authorization needs to be optained automatically. Leave this field blank for our No Authorization use case.
8.  **API Endpoint URL** - This represents the default base url for all calls using this credential record, it is the base portion of the API Endpoint URL which does not change. In our example, we would enter https://postman-echo.com. This base URL can be overridden at the API Function level by a Base URL override variable.
9.  **API Scope** - This is a field for an application defined purpose where some information maybe needed to tell the host API the scope of the API Call. For example, the URL may need to indicate whether we want information for a particular store, or information for the whole site (defaults for each store).

Now that you have created a Credential for your API Set, you can proceed with adding an [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) for this API Set.
