# Error codes

For reference, the following error codes should be used by the server side scripting to better communicate with Emotsy Builder. When the server-side script returns the correct error code in the AJAX response, Emotsy Builder will be able to display the corresponding messages in the appropriate format.

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
As you can see, getting Builder up and running involves a few steps. This is because Builder was intentionally designed to be fully customizable. While the documentation is continuously being updated, please feel free to contact the development team for further details on integrating Builder with your application. Thank you!
</aside>