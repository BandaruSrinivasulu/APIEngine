# How to Create a URL Query Parm with an API Variable

This Section will describe how to add query parms to a request URL in an API Function.  To achieve this, we can add an API Variable to the API Function we are constructing.  API Variables define how the request will be built for the API Function.  Different types of API Variables are used to build differnt parts of the request (URL, URL Path, URL Parameter, Header, Body).  In this case, we will add an API Variable of type URL Parameter to add a Query Parm to our URL.  As a prerequisite to this article, you may want to read [How the SuiteEngine API Engine Builds the API Endpoint URL](https://github.com/SuiteEngine/APIEngine/wiki/How-APIEngine-Builds-Endpoint-URL) to see where a Query Parm fits into the API Engines process on building the Request URL.

First we will create a static value query parm (hand=wave) to a url, then we will add a query parm with a value from a Customer Record - custid=x, where x will be the Customer No. from the Business Central Customer Table.

Let's get started!

For demo purposes, we will again build off the [Create an API Function](https://github.com/SuiteEngine/APIEngine/wiki/How-To-Create-API-Function) wiki article using the Postman Echo GET API function.  At the completion of this article, we should end up with an endpoint url of:  [https://postman-echo.com/get?**hand=wave&custid=30000**](https://postman-echo.com/get?hand=wave&custid=30000)

To add our static hand=wave query parm to the URL, from the API Functions list page for the API Set, activate the API Variables Action Ribbon and press the Action URL Parameters.

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Navigate-URLParameters-From-APIFunction.png)

Add a new line to the API Variables as follows:

![](https://github.com/SuiteEngine/APIEngine/wiki/HowToDocs/HowTo-APIFunctions/HowTo-APIFunctions-Assets/Example-APIVariable-URLParm-Static-HandWave.png)

Definition of  the fields entered for this hand=wave URL Parameter Value:

1.  **Auto Build Sequence (PK1)** - An integer value that determines the order that the URL Parameters should be positioned after the ? delimiter of the URL.  For this example API Variable, enter:  *10.*
2.  **Variable Scope (PK2)** - An Option (Enumeration) value that indicates how this variable is used in building the end point url.  In our case, we want this variable to add a query parm, so the Variable scope will be:  _URL Parameter._
3.  **Name (PK3)** - The name of the API Variable.  This mostly likely will be the key of the query parm presented in the URL.  Note that when you enter this field for the first time, the field (API) Static Name also populates with the same value.  The API Static Name however can be changed to something different or even changed by API Name Processing Type.  Think of this Name field as being an API Engine Name which needs to be unique, however the Name (or key in this case) be what is contained in the URL.  Although they are rarely different, there are use cases for this, especially with Body API Variables that involve arrays of data. For this example API Variable, enter:  *hand.*
4.  **Variable Value Type** - This indicates how the variable value will be presented by this API Variable, for Query Parameters, the only valid values should be _Key Value Text_ or _Text Value_ .  Since we want a key value query parm (hand=wave) enter _Key Value Text_ for this variable.
5.  **Value Processing Type** - This is an option (enumeration) for how the value of the API Variable will be derived.  For this exercise, we use the _**Static**_ Value Processing Type since the value will always be the same (hard coded, fixed, static) for every API Call made by this function.  Other possible values that come with the API Engine will be explained in other documentation, but it maybe good to note that value processing can be extended by custom codeunits that implement the **SENAPIValueProcessing.Interface**.
6.  **Static Value** - This field is the fixed/static/hardcoded value that will always be sent for a API Variable with a Value Processing Type of Static.  In our example, we will enter _wave_.
7.  **API Name Processing** - This is an option (enumeration) for how the name (key) of the API Variable will be derived.  For this exercise, we use the _**Static**_ Value Processing Type since the value will always be the same (hard coded, fixed, static) for every API Call made by this function.  Other possible types that come with the API Engine will be explained in other documentation, but it maybe good to note that value processing can be extended by custom codeunits that implement the **SENAPIValueProcessing.Interface**.  Note that in the vast majority of API variables, the choice will be Static since normally the keys are known and do not change.  An Example of when to use something other than static would be when the Variable represents meta data and both the key and the value of the query parm will come from data in a table.
8.  **Static Name**\- This field is the fixed/static/hardcoded value that will always be sent for a API Variable with a API Name Value Processing Type of Static.  In our example, the value defaulted to _Name_ when the Name field was entered (validated).

Definition of  the fields we left empty  (or at there default value) for this hand=wave URL Parameter Value:

1.  **Do Not Encode** - By default, the API Engine will URL Encode data according to the Variable Scope of the variable, checking this box will override this default behavior.
2.  **Parent** - The Parent field is used in API Variables with variable scope = body, it allow for nested objects and arrays.
3.  **Variable Value Null Behavior** - This indicates the behavior of this variable if after Value Processing, the resulting value is blank or null.  With this setting, if the value is blank or null, the query parm will still be sent with an empty string value.  There are other behaviors that can be choosen, null value, undefined value, or Do not Include which will essentially just skip your API variable all together and not include it in the URL's query parms.
4.  **Value Processing Function Name** - This is only used for certain Value Processing type, see other Wiki articles dealing with Variable Value Processing.
5.  **Value Table No.** - This field would have the BC Table Number to be used with other Value Processing Types (See below for an example of this).  The Adjacent field Value Table Name is a display only field showing the Caption of the Table specified in this field.
6.  **Value Field No.** - This field would have the BC Field Number of the field from the Value Table No. to be used in Variable Value Processing  The Adjacent field Value Field Name is a display only field showing the Caption of the Field specified in this field.
7.  **API Message Masked Value.** - This field is used for sensitive information that you want to hide in the API Message result.  The actual value is processed, but the masked value is written to the API message in its place to prevent users from viewing the actual values.

If we were to execute our API Function now, we can see that our first Query Parameter objective has been satisfied by looking at the API Message Query Request value:  [https://postman-echo.com/get?hand=wave.](https://postman-echo.com/get?hand=wave.)

Now lets add the Customer Id Query Parameter.  In this exercise, I have chosen to [Copy te API Function](https://github.com/SuiteEngine/APIEngine/wiki/How-To-Copy-API-Function) we started with, to a new API Function in which we will add the Business Central Customer ID Query Parameter.   First, lets navigate to a page that shows us all the API Variables for this API Function.
