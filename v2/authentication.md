API V2: Authentication
======================

This version of the API requires HTTPS so all requests to the `http` request scheme will be rewriten to `https`.

To authenticate to any routes that match this prefix `/v2` you must include propper authentication headers.

| Header       | Value        |
|--------------|--------------|
| X-APP-ID     | YOUR_APP_ID  |
| X-APP-KEY    | YOUR_APP_KEY |

These headers are required on every request.

Next: [Autocomplete][1]

[1]: https://developer.nutritionix.com/v2/autocomplete