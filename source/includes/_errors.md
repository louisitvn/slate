# Errors

For reference, the following error codes should be used by the server side scripting to better communicate with BuilderJS

Error Code | Meaning
---------- | -------
400 | Bad Request -- Your request is invalid.
401 | Unauthorized -- Your API key is wrong.
403 | Forbidden -- The kitten requested is hidden for administrators only.
404 | Not Found -- The specified kitten could not be found.
405 | Method Not Allowed -- You tried to access a kitten with an invalid method.
406 | Not Acceptable -- You requested a format that isn't json.
410 | Gone -- The kitten requested has been removed from our servers.
418 | I'm a teapot.
429 | Too Many Requests -- You're requesting too many kittens! Slow down!
500 | Internal Server Error -- We had a problem with our server. Try again later.
503 | Service Unavailable -- We're temporarily offline for maintenance. Please try again later.

<aside class="notice">
As of version 4.0, there are two cases when BuilderJS makes an Ajax request to the server end. The first is for saving latest changes of the design view (see Storage section for more details), and the second is when it sends an asset (image or video). Server script should return <code>HTTP 200</code> for successful job and one of the error code above for failure
</aside>