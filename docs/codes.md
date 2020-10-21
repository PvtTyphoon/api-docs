## Last.fm Error Codes

In addition to return [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) along with every response from the Last.fm API, failed responses include errors. [Last.fm often does not return HTTP Status Codes that accurately reflect the state of your request](https://lastfm-docs.github.io/api-docs/bugs/#status-codes). 
This page provides a comprehensive list of error codes returned by Last.fm, along with a short description of them.

??? warning "Example response of an error"

    HTTP status: `404 NOT FOUND`
    ```json
    {
        "error": 6,
        "message": "User not found"
    }
    ```
 
 ## HTTP Status Codes
 !!! warning
    Some API calls return HTTP 200 OK status codes even when the response contains an error.
    For this reason make sure to check your response payload to validate it.

---

### Last.fm Error Code 2: Service Unavailable/Service Unavailable
This error usually emits when Last.fm is having server issues. However this may also happen because of a malformed request with invalid endpoints.


### Last.fm Error Code 3: Invalid Method
This error emits when a request is made to an endpoint with a method that does not exist. For example, `artist.getSomeData`. While the endpoint you're making a request to might be perfectly valid, a malformed method name will prevent Last.fm from returning the data you want. For a comprehensive list of every method, refer to the API docs on this site.


### Last.fm Error Code 4: Authentication Failed
This error emits when a request is made signed with a session token that has been generated for an account that has revoked access to your application.

### Last.fm Error Code 5: Invalid Response Format
A `format` parameter is necessary in addition to the documented parameters, this may either have a value of `XML` or `JSON` (case insensitive). Requesting data in another format will emit this error. Some methods do support more than these 2 formats, the methods that do have their formats listed in this documentation.

### Last.fm Error Code 6: Parameter Error
The Last.fm API returns this error code in response to multiple types of failed request. This error can occur because:
 - Your search returned no results
 - Your request used an invalid parameter
 - Your request has a parameter with an invalid value (for example, an invalid type)
 - The requested resource is not available
 
 ### Last.fm Error Code 7: Invalid Resource Specified 
This error emits when a method requests data from a resource that does not exist, for example, an artist or album that cannot have the data you requested. This might be due to using a method that is not valid on an endpoint despite being documented.
 
### Last.fm Error Code 8: Generic Error
This error is emitted when something unexpected causes your request to fail but unfortunately Last.fm can't quite tell you what. This is a generic error. This is similar to [HTTP Error 500](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/500).

### Last.fm Error Code 9: Invalid Session Token
This error emits when a request tries to authenticate with an invalid session key, or similar missing/malformed parameters. For a guide to auth and signing your calls, refer to [this part](https://lastfm-docs.github.io/api-docs/auth/signature/) of the site. Make sure that your session key is hashed using UTF-8 encoding in addition to MD5