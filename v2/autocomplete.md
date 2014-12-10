API V2: Autocomplete
====================

The V2 autocomplete API aims to allow users the convenience of "as you type" suggestions.

### HTTP GET to `/v2/autocomplete`

To make perform a search, make an HTTP GET request to the `/v2/autocomplete` endpoint.

### GET Parameters

**Required Parameters**

These parameters must be properly URL encoded and used in the query string

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| q               | A search phrase prefix in plain text |


### Example request in CURL
This is an example for greek yogurt. Using the prefix `greek y`.

```sh
curl -XGET "https://api.nutritionix.com/v2/autocomplete?q=greek%20y" -H 'X-APP-ID: YOUR_APP_ID' -H 'X-APP-KEY: YOUR_APP_KEY'
```

### Response {Array} of Phrases

These are the attributes that will be available on each phrase returned

#### Phrase {Object}

| Parameter        | Description                          |
|------------------|--------------------------------------|
| id               | An {Integer} as the id of the phrase |
| text             | A {String} as the phrase itself |
| exact_match_id   | A {String} as the id of the resource that was matched to that phrase |
| exact_match_type | An {Integer} as the type of the exact matched resource |
| score            | An {Integer} as the phrases search ranking |

### Example Response

```json
[
  {
    "id": 130,
    "text": "greek yogurt",
    "exact_match_id": "63",
    "exact_match_type": 3,
    "score": 352.36896
  },
  {
    "id": 1401,
    "text": "dannon greek yogurt",
    "exact_match_id": null,
    "exact_match_type": null,
    "score": 281.89517
  }
]
```



Next: [Natural][1]

[1]: https://developer.nutritionix.com/docs/v2/natural