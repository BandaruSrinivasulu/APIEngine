# How the API Engine Assigns an API Credential to an API Call

This Section will describe how the API Engine assigns an API Credential to an API Call at runtime.

At run time, the SuiteEngine API Engine will assign a credential record to the API Message created for an individual API Call.  It will do so by resolving the API Credential primary key values (API Set Code, Usage Code, API Function Code).  As part of this process, the API Engine will look for an API Parameter assigned to the API Message that has a key of _**CredentialUsageCode**_ and if found, it will use its value as the Usage Code.

The API Engine will then try a series of Reads (Get) on the Credential Table to find the most specific API Credential Record to assign to the message and use for Authentication for the API Call.  Remember that every API Call is represented by an API Message which has a valid API Function Code belonging to an API Set.  API Parameters can also be attached to the API Message.

1.  The API Engine firsts looks for an API Parameter with Parameter Type = Record, Record = APIMessage.RecordId, Key = 'CredentialUsageCode', Key Index = 0.  If found, UsageCode = APIParameter.Value, if not found, CredentialUsageCode will be left empty.
2.  The API Engine then retrieve the API Function Record from the API Message.API Function Code field, The API Set Code, and Function Code values are taken from this record.
3.  The API Engine makes 6 attempts to find a matching credential record to assign to the message and add as an API Parameter to the API Message
    1.  if not SENAPICredential.GET(API Set Code, CredentialUsageCode, Function Code) then
    2.  if not SENAPICredential.GET(API Set Code, "", Function Code) then
    3.  if not SENAPICredential.GET('"", CredentialUsageCode, Function Code) then
    4.  if not SENAPICredential.GET("", "", Function Code) then
    5.  if not SENAPICredential.GET(API Set Code, CredentialUsageCode, "") then
    6.  if not SENAPICredential.GET(API Set Code, "","") then CLEAR(SENAPICredential);

Note: The first successful read of the API Credential stops the attempts, and the Credential record is used for the API Call. If the API Credential is not found after those attempts, then an empty credential record is used in the API Call.
