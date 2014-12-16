V2 Error Handling
========================

The new error handling is simple and intuitive. When an error occurs the API will respond with a uniform output.

#### Example Response `GET https://apibeta.nutritionix.com/v2/item/:id`

```json
{
  "errors": [
    {
      "message": "unknown resource itmess",
      "code": "resource_unknown",
      "status": 404
    }
  ],
  "status": 404
}
```

#### Response {Object}

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| errors          | An {Array} of Error Objects          |
| status          | An {Integer} representing the HTTP status          |


#### Response.errors []Errors {Object}

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| message         | A {String} displaying a description of the error |
| code            | A {String} displaying an error identifier |
| status          | An {Integer} representing a possible HTTP status |

The `Response.status` will be elevated to the highest status of any of the `Response.errors`.
Meaning, if we have multiple errors; one with `"status":400` and another with `"status":500`; the `Response.status` will be `500`.
