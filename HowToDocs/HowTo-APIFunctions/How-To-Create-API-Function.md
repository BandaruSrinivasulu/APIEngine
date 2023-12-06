# How to Create an API Function

This Section will describe how to add simple API Function to an [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set).  In this how to document, our example API Call will use the [Postman Echo Get Request method](https://www.postman.com/postman/workspace/published-postman-templates/request/631643-078883ea-ac9e-842e-8f41-784b59a33722?ctx=documentation) to send the following url to the postman echo api: [https://postman-echo.com/get?hand=wave.](https://postman-echo.com/get?hand=wave.)  But first, lets look at the anatomy of the url we want to send.

- The base url is: [https://postman-echo.com](https://postman-echo.com)
- The url path is: **get**
- The Query Parameters are: **hand=wave**

In this How To, we will see how the API Engine can construct the API Endpoint URL for data stored in [API Credentials](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential) and the [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function).

First, navigate to the [API Set](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-set) that you wish to add the API Function to and then Navigate to API Functions.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Navigate-From-APISet-To-APIFunctions.png)

Then type in Function Code: GET_HANDWAVE and press the Edit action.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Edit-API-Function-Action.png)  
Note: The function code does not necessarily need to be GET-HANDWAVE, it can be whatever code you want to assign to this function. For the sake of this exercise, please use GET_HANDWAVE

Next, fill out the fields on the API Variable card page as follows:

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/APIFunction_Echo_Get_Hand_Wave.png)

Definition of  the fields entered for this How-To:

1.  **Description** - A user defined description of this API Function Record. The maximum description length is 1024 characters.  For this example API Function, enter:  *Calls the Postman Echo Get Request Method with query parameter hand=wave*
2.  **HTTP Method** - The HTTP method to use in the request for this API Function.  This is an enumeration with choices of GET, POST, DELETE, PUT, or PATCH.  For our example, choose GET.
3.  **API Path** - This field is used in building the URL for the API Call, it is considered the fixed path just after the base URL.  In our example, enter get which will become the part of the path shown in bold -  [https://postman-echo.com/**get**?hand=wave](https://postman-echo.com/get?hand=wave)
4.  **Request Data Type** - This chooses the format and methods used for generating the request.  Current choices are None, form-data, x-www-form-urlencoded, JSON, or XML.  For our example, choose JSON.  Technical / Developers Note:  This enumeration controls which codeunit is implementing the SENAPIRequestDataType interface and is extendable.  It controls the format of the body of the request.  Since it is extendable, a developer could create new formats or even create a variation of the implementations that are part of the base API Engine product.
5.  **Request Message Encoding** - Specifies the encoding to be performed on the request body, current choices are UTF8, UTF16, Windows, or MSDos.  For our example, choose UTF8.
6.  **Buffer Processing Type** - This chooses the format and methods used for processing the API Response into the API Data Buffer.  Current choices are JSON, or XML.  For our example, choose JSON.  Technical / Developers Note:  This enumeration controls which codeunit is implementing the SENAPIDatabufferProcessing interface and is extendable.  It controls how the data buffer is built by knowing the format of the response received in an API Call.  Since it is extendable, a developer could create new formats or even create a variation of the implementations that are part of the base API Engine product.

Definition of  the fields we left empty on this How-To:

1.  **Http Accept** - If a value is entered into this field, the API Engine will automatically create an Accept request header with this value.  Max characters = 100.
2.  **Content Type Text** -  If a value is entered into this field, the API Engine will automatically create a Content-Type request header with this value.  Max characters = 100.
3.  **Request Processing** - This chooses the logic used for generating the request.  There is only one choice with the version of the API Engine at time of this writing: Default.  Developers Note:  This enumeration controls which codeunit is implementing the SENAPIRequestProcessing interface and is extendable.  It controls the overall process of building and processing the API request.  Since it is extendable, a developer could create a custom process for generating the API request.  Also note that the Default is quite powerful on its own, and it would be rare where customer request processing logic would need to be created.
4.  **Save Http Request Headers** - By default, the API Engine does not store Http Request Headers as part of the API Message after the API Call has been made.  This is for security reasons as it is often that authentication data is transmitted in request headers.  However, by switching this field to true, the request header information will be saved with the API Message and can be viewed.  We recommend that in a production environment this value be left to false and it should only be true in a troubleshooting circumstance.
5.  **Throttle Fields** - These 3 fields are used when the API calls are called in sequence base on the Next Function Code specified on the API Function. They will throttle the calls for a specified period of time after a number of calls have been made.
    1.  **Throttle Max Request** - The maximum number of API Calls that can be made in a period of time before waiting.
    2.  **Throttle Refresh Duration** - The duration that the API Engine should wait before resuming the API Calls.
    3.  **Throttle Refresh Rate** - Number of API Calls that can be made after a Throttle (wait) has occured
6.  **Response Root Object Name** - The name of the root object to be used for the response.  For JSON responses this is required, for XML responses it is optional.  Defaults to RESPONSEOBJECT.
7.  **Save Http Response Headers** - By default, the API Engine does not store Http Response Headers as part of the API Message after the API Call has been made.  By switching this field to true, the Response header information will be saved with the API Message and can be viewed.
8.  **Use Mappings From Function** - Allows one API Function to share API Mappings from another API Function, this is useful when the reponse has the same structure in more that one API Function.  For example, GETORDERSFORSTATUS may have the same response structure as GETORDERSAFTERDATETIME.  Although the API Functions may have different request data, the response structure would be the same.
9.  **Next Function Code** - Specifies the next API Function that should be called after this API Function completes.  Note that the next function could be this API Function when the same API Call is made repeatably.  This is useful when the external API has limits on the number of records you can retrieve in one API Call, but provides pagination tools to bring large amounts of data via a series of API calls.
10. **Next Token Processing Function** - This field provides a developer the means to specify the logic for how Next Token or pagination logic should be implemented by this function.  Since different API Platforms have different approaches to how this occurs, the API Engine does not provide this logic out of the box.  However you can extend this enumeration and provide an implementation CodeUnit that uses the SENAPINextTokenWebRequestProcessing Interface.

Next lets complete our how to by adding the Hand=Wave query parameter to the URL.

From the API Functions list page for the API Set, activate the API Variables Action Ribbon and press the Action URL Parameters.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Navigate-URLParameters-From-APIFunction.png)

Add a new line to the API Variables as follows:

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Example-APIVariable-URLParm-Static-HandWave.png)

See other wiki documentation for more information on how API Variables work in building the API request.  For this example, we just add a static (fixed / hardcoded) value = wave to the URL Parameter API Variable named hand.  This API Variable will take care of the last piece of the URL we need to build.  https://postman-echo.com/get?**hand=wave**

Now lets see if we have a working API Call, close the API Variable list page and return to the API Functions list for our example API Set.  Select the GET_HANDWAVE API Function and press the Execute Action from the Home action ribbon.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Execute-APIFunction-HandWave.png)

Click Yes on the Dialog asking if you want to open the API Message.

Remember there is an API Message for every API Call executed, and it records the request information sent, as well as the response received as a result of a successful call being made.

As you can see from the below API Message information, we have successfully called the Postman Echo API with the Get Request Method and a valid key value parameter: hand=wave.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/APIMessage-Success-HandWave.png)