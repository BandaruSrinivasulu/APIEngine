# How to Create an API Function

This Section will describe how to add simple API Function to an [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) .  In this how to document, our example API Call will use the [Postman Echo Get Request method](https://www.postman.com/postman/workspace/published-postman-templates/request/631643-078883ea-ac9e-842e-8f41-784b59a33722?ctx=documentation) to send the following url to the postman echo api: [https://postman-echo.com/get?hand=wave.](https://postman-echo.com/get?hand=wave.)  But first, lets look at the anatomy of the url we want to send.

- The base url is: [https://postman-echo.com](https://postman-echo.com)
- The url path is: **get**
- The Query Parameters are: **hand=wave**

First, navigate to the [API Set][APISetDef] that you wish to add the API Function to and then Navigate to API Functions.  
![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Navigate-From-APISet-To-APIFunctions.png)

Then type in Function Code: GET_HANDWAVE and press the Edit action.
![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Edit-API-Function-Action.png)
Note: The function code does not necessarily need to be GET-HANDWAVE, it can be whatever code you want to assign to this function.  For the sake of this exercise, please use GET_HANDWAVE


Next, fill out the fields on the API Variable card page as follows:
![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/APIFunction_Echo_Get_Hand_Wave.png)

[APISetDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set "Definition of an API Set"
[APICredentialDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential "Definition of an API Credential"
[APIFunctionDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function "Definition of an API Function"
[APIParameterDef]: https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-parameter "Definition of an API Parameter"