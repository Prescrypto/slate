# Errors

<aside class="notice"> If you need help write us at CG contact email</aside>

The CG API uses the following error codes:


Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request sucks
401 | Unauthorized -- Your API key is wrong
403 | Forbidden -- Page requested is hidden for administrators only
404 | Not Found -- The specified endpoint could not be found
405 | Method Not Allowed -- You tried to access a cg endpoint with an invalid method
406 | Not Acceptable -- You requested a format that isn't json
429 | Too Many Requests -- You're requesting too many requests! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.
