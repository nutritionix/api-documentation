API V2: Search
======================================

The V2 search API gives you fast, responsive, and accurate results for cpg (consumer package goods), USDA, and restaurant foods.
This version of search is based on `autocomplete` principles making it easy for you to show your users exactly what they're looking for.
The API also attempts to find an `exact_match` for the search phrase and will explicitly tell you when a match has been found along side your standard results.

### HTTP GET to `/v2/search`

To perform a basic search make an HTTP `GET` request to the v2 search endpoint. `/v2/search`<br>
**Note** that all parameters must be properly URL encoded.

### Request Parameters

**Required Parameters**

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| q               | A {String} as the search phrase in plain text |

**Optional Parameters**

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| limit           | An {Integer} as the maximum rendered results  **Requires `offset`** |
| offset          | An {Integer} as search offset for paging through results **Requires `limit`** |
| search_type     | A {String} representing the search mode. Must be one of the following (recipe, grocery, restaurant, usda) |
| search_nutrient | A {String} representing the nutrient returned in search defaults to `calories`. Can be(calories, fat, protein, carb) |


### Example Request in CURL

```sh
# Note that authentication headers have been excluded for brevity.
curl -XGET "https://api.nutritionix.com/v2/search?q=greek%20yogurt&limit=10&offset=0&search_type=grocery"
```

### Response Parameters

The response from this endpoint will be of `Content-Type: application/json`<br>

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| exact           | A {Boolean} attribute representing if we found an exact match for the search phrase. |
| total           | An {Integer} as the total number of hits for the search query |
| results         | An [Array] of `Item{Objects}` representing items that matched the search phrase passed in the requests `q` parameter |
| status          | An {Integer} as the http status code. We will supply status code mappings to help you look up common issues |

**If `exact` is `true`** the first element in the `results[Array]` will have an `[Array] of Nutrient{Objects}`.

### Item{Object} Parameters

| Parameter            | Description                          |
|--------------------- |--------------------------------------|
| item_name            | A {String} as the name of the product or food item |
| brand_name           | A {String} as the name of the item's brand |
| nutrient_name        | A {String} as the name of the selected nutrient to be returned in search. |
| nutrient_value       | An {Integer} as the numeric value of the selected nutrient |
| nutrient_uom         | A {String} as the unit of measurment for the selected nutrient |
| serving_qty          | An {integer} as the items serving quantity |
| serving_uom          | A {String} as the unit of measurement for the `serving_qty`   |
| resource_id          | A {String} as a tracking id that links searches to individual items |
| thumbnail            | A {String} the url to an items thumbnail image |
| nutrients            | An {Array} of `Nutrient{Object}` which will be null unless `response.exact` is `true` |


### Nutrient{Object} Parameters

| Parameter            | Description                          |
|--------------------- |--------------------------------------|
| attr_id              | An {Integer} representing the usda attribute id of the nutrient |
| value                | A {Float} representing the nutritional value of a nutrient |
| unit                 | A {String} as the nutrients unit of measurement |
| name                 | A {String} as the nutrients proper name |
| usda_tag             | A {String} as the nutrients usda given abbreviation |

### Example Response

```json
{
  "exact": true,
  "total": 1,
  "status": 200,
  "results": [
    {
      "item_name": "1 cup celery",
      "brand_name": "Nutritionix",
      "thumbnail": "https://nixdotcom.s3.amazonaws.com/assets/nix-icon-small.png",
      "nutrient_name": "Energy",
      "nutrient_value": 16.16,
      "nutrient_uom": "kcal",
      "serving_qty": 1,
      "serving_uom": "cup",
      "resource_id": null,
      "nutrients": [
        {
          "attr_id": 255,
          "value": 96.38430000000001,
          "unit": "g",
          "name": "Water",
          "usda_tag": "WATER"
        },
        {
          "attr_id": 208,
          "value": 16.16,
          "unit": "kcal",
          "name": "Energy",
          "usda_tag": "ENERC_KCAL"
        }
        // ..
      ]
    }
  ]
}
```

Next: [More advanced usage of search endpoint][1]

[1]: /docs/v2/advanced_search