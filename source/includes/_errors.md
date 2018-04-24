# Errors

<aside class="notice"> If you require any assistance, please write to us at <a href="https://www.cgblockchain.com/contact">CG contact page</a>. Providing the request identifier would help to ensure a quicker resolution.</aside>

In some scenarios, the CG API may return error codes. The table below helps you understand the common error codes and their respective descriptions.

In general, error codes in the 4xx range indicate a request that has failed with the information provided, such as a missing parameter. Codes in the 5xx range indicate an error with CG’s servers.


Error Code | Description
---------- | -----------
400 | Bad Request -- The request was unacceptable, please check for a missing parameter.
401 | Unauthorized -- Unauthorized - No valid API key provided
403 | Forbidden -- Page requested is hidden for administrators only
404 | Not Found -- The specified endpoint could not be found
405 | Method Not Allowed -- You tried to access a cg endpoint with an invalid method
406 | Not Acceptable -- You requested a format that isn't JSON
429 | Too Many Requests -- Too Many Requests - Too many requests hit the API too quickly! We recommend an exponential backoff of your requests.
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
