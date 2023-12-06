# How the API Engine Builds and Endpoint URL for an API Call

This Section will describe how the API Engine builds the Endpoint URL for an API Call.

URLs can be broken down into logical pieces, the SuiteEngine API Engine breaks down the API Endpoint URL into the following pieces and puts them all together.

1.  Base URL - https://my.baseurl.com
2.  Fixed Path - my/fixed/path
3.  Variable Path - myaccountnumber
4.  Query Parameters
    1.  Tags - just a text parameter - safemode
    2.  Key Value - Parameters that have both a key and a value component. - foo=bar

Put them all together and you have a endpoint url:   [https://my.baseurl.com/my/fixed/path/myaccountnumber?myaccountnumber&foo=bar](https://my.baseurl.com/my/fixed/path/myaccountnumber?myaccountnumber&foo=bar)

For a new API Message where the Query Request is empty, the API Engine takes the following steps to build the Endpoint URL

1.  Determine the value of the base url, this normally comes from the selected API Credential Record, unless there is an URL Override API variable associated with the API Function, then its value is used.
2.  Next, if the API Function has a value for the Static Path value, a / and the Static Path value is appended to the base url.
3.  Then, if the API Function has API Variables of type URL Path, they are added sequentially to the url in auto build sequence order.  Slashes are added automatically where appropriate.
4.  Finaly, if the API Function has API Variables of type URL Parameter, a ? is appended to the url and URL Parameter records are added sequentially to the url in auto build sequence order.  & are added automatically where appropriate.  Note that key value query parameters use Variable Value type Key Value Text, and Tag parameters use Variable Value type Text Value.

If you are re-executing an API Message that already has a Query Request defined, then that Query Request stored on the message is used and the API Endpoint url.

Technical Note: As of this writing, there are 2 published events that allow developers to create or modify the endpoint url via extension code.

> SENAPIRequestProcessingEvent.OnBeforeGetURL(SENAPIFunction, SENAPIMessage, BaseURL, URLText, IsHandled);
>
> SENAPIRequestProcessingEvent.OnAfterGetURL(SENAPIFunction, SENAPIMessage, BaseURL, URLText);
