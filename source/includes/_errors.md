# Errors

<aside class="notice">
This is a list of common errors that can be reach by our server!
</aside>

The XML Endpoint API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The XML requested is hidden for administrators only.
404 | Not Found -- The specified XML could not be found.
405 | Method Not Allowed -- You tried to access a XML with an invalid method.
429 | Too Many Requests -- Exceeds Limit requests!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
