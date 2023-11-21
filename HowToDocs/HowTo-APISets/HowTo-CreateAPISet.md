# How to Create an API Set

Navigate to the API Set List Page

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APISets/HowTo-CreateAPISet-Assets/CreateAPISet-01.png)

Enter your **API Set Code** on a new list line.  Note that the code is user defined with a maximum length of 20 characters.  Example: POSTMANECHO.  
![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APISets/HowTo-CreateAPISet-Assets/CreateAPISet-02.png)  
Complete the Line with the remaining fields on the line.

1.  **Description** - A user defined description of the API Set, maximum text length of 250 Characters.  Use this to describe the purpose of the API Set.  Example: _Postman Echo is a service you can use to test your REST clients and make sample API calls._
2.  **API Target** - A selection from a set of concrete (target) values.  The API Engine out of the box only supplies one choice for the value of this field: Generic.  However, this is an Enumeration which is extensible by dependent applications to the API Engine.  Since the API Set Code is user defined, this is sometimes used to give a more concrete "type" to the API Set so that its value can be used in other areas of the application.  For example, your application may need to behave differently if you were dealing with an API Set that contained functions for the Amazon Selling Partner API's vs. Ebay API calls.
3.  **API Platform** - A user defined designation for the platform that the API set represents.  Example: Apple ITunes.
4.  **API Version** - A user defined field to document the version of the API this API Set targets.
5.  **API Documentation URL** - A user defined field to document a url that will navigate to documentation regarding this collection of API calls.  Example: [https://postman-echo.com](https://postman-echo.com)
6.  **Request Message Encoding** - The default encoding method for API requests that will be used for each [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) related to this API Set.  The API Functions Request Message Encoding will be defaulted to this value, however, each [API function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) can be changed to have a different encoding method from this default.  Example: UTF8
7.  **Response Message Encoding** - The default encoding method for API responses that will be used for each [API Function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) related to this API Set.  The API Functions Response Message Encoding will be defaulted to this value, however, each [API function](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) can be changed to have a different encoding method from this default.  Example: UTF8  
    ![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APISets/HowTo-CreateAPISet-Assets/CreateAPISet-03.png)  
    Now that you have created the API Set, you can proceed with adding one or more [API Credential](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-credential) Records as well as the [API Functions](https://github.com/SuiteEngine/APIEngine/wiki/APIEngineTermsAndDefinitions#api-function) for this API Set.
