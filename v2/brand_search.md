V2 Brand Search
===============

The V2 Brand Search API gives you the capability to query thousands of brands.

### HTTP GET to `/v2/search/brand`

To perform a basic search make an HTTP `GET` request to the endpoint above.

**Note** that all parameters must be properly URL encoded.

### Request Parameters

**Optional Parameters**

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| q               | A {String} as the search phrase in plain text |
| limit           | An {Integer} as the maximum rendered results  **Requires `offset`** |
| offset          | An {Integer} as the search offset for paging through results **Requires `limit`** |
| type            | An {Integer} (1=restaurant, 2=CPG, 3=USDA / Nutritionix) |
| mobile_calc     | A {Boolean String} set to `mobile_calc=true` to include mobile restaurant caclulator url |
| desktop_calc    | A {Boolean String} set to `desktop_calc=true` to include desktop restaurant calculator url |

**limiting to more than one type** you can use the `type` parameter numerous times. <br>
Ex. `?type=1&type=3`

### Example Request in CURL

```sh
# Note that authentication headers have been excluded for brevity.
curl -XGET "https://api.nutritionix.com/v2/search/brands?q=mcdon&limit=1&offset=0&type=1"
```

#### Example Response
```json
// notice the `q` param was only a partial search.
// the search supports fuzziness
{
  "status": 200,
  "total": 1,
  "results": [
    {
      "id": "513fbc1283aa2dc80c000053",
      "name": "McDonald's",
      "item_count": 363,
      "type": 1,
      "website": "http://www.mcdonalds.com"
    }
  ]
}
```