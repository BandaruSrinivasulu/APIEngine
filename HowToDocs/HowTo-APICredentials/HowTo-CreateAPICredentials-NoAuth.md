# How to Create an API Credential with No Authentication

This Section will describe how to add a default Credential to an [API Set][APISetDef] where the API Host does not require authentication to execute API Calls.  Note that at least one API Credential is required for each [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) that serves as the default credential for the API Engine to use for all API Calls defined by the [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set).

From the [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) List Page, select the API Set that you would like to maintain API Credentials for and press the API Credentials navigation action button.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APICredentials/HowTo-CreateAPICredential-Assets/OpenAPICredentialsFromAPISetListPage.png)

Press the New Action to create a new API Credential Record for the Postman Echo API Set. For this exercise, we are creating an API Credential for API calls to Postman Echo that do not require Authorization.  Only fields in the General fast tab will be used in this exercise.  The other fast tabs that supply additional information based on the Authorization Type can be left empty.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APICredentials/HowTo-CreateAPICredential-Assets/APICredential-NoAuth-Example.png)

1.  **API Set Code** - The API Set Code of the API Set this Credential is related to.
2.  **Usage Code** - For this basic example, we will leave this field blank.  For more information on how the Usage Code can be used to pick from different credentials see: How to use the API Credential Usage Code.
3.  **Function Code** - For this basic example, we will leave this field blank.  The Function Code can be used to specify a Credential to be used for a specific API Function of the API Set.
4.  **API Version** - A user defined field to document the version of the API this API Set targets.
5.  **API Documentation URL** - A user defined field to document a url that will navigate to documentation regarding this collection of API calls.  Example: [https://postman-echo.com](https://postman-echo.com)
6.  **Request Message Encoding** - The default encoding method for API requests that will be used for each [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) related to this API Set.  The API Functions Request Message Encoding will be defaulted to this value, however, each [API function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) can be changed to have a different encoding method from this default.  Example: UTF8
7.  **Response Message Encoding** - The default encoding method for API responses that will be used for each [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) related to this API Set.  The API Functions Response Message Encoding will be defaulted to this value, however, each [API function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) can be changed to have a different encoding method from this default.  Example: UTF8  
    ![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APISets/HowTo-CreateAPISet-Assets/CreateAPISet-03.png)  
    Now that you have created the API Set, you can proceed with adding one or more [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential) Records as well as the [API Functions](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) for this API Set.

[APISetDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set "API Set Definition"
[APIFunctionDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function "API Function Definition"