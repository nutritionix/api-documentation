API V2: Natural
=================================

The `natural` endpoint allows you to translate plane text into a full spectrum analysis.

### HTTP POST to `/v2/natural`

To perform an analysis you must make an HTTP POST request to the endpoint above. The body of the request must be plain text
with each phrase seperated by a new line.

### Ex. POST Body

**Required**

```
1 tbsp sugar
16 fl oz water
1/2 lemon
```

### Headers

**Required**

If you do not include this header we will not attempt to consume the plain text request and it will fail.

| Parameter       | Value                                |
|-----------------|--------------------------------------|
| Content-Type    | text/plain                           |

### Query Params

**Optional**

These options must be properly url encoded.

| Parameter       | Value                                |
|-----------------|--------------------------------------|
| gram_weight      | An {Integer} that will be used as a multiplier when calculating `total.nutrients` |


### Example request in CURL

```sh
curl -XPOST 'https://api.nutritionix.com/v2/natural?gram_weight=20' \
-H 'X-APP-ID: YOUR_APP_ID' \
-H 'X-APP-KEY: YOUR_APP_KEY' \
-H 'Content-Type: text/plain' \
-d'
1 tbsp sugar
16 fl oz water
1/2 lemon
'
```

### Response {Object}

| Parameter        | Description                          |
|------------------|--------------------------------------|
| results          | An {Array} of Ingredient{Objects}    |
| total            | A Sum {Object}                       |


### Sum {Object}
This object represents a compound item constructed from the sums of the values
from each ingredent.

| Parameter        | Description                             |
|------------------|-----------------------------------------|
| serving_weight   | An {Integer} as weight in grams of all ingredients |
| nutrients        | An {Array} of Nutrient {Objects} |

### Ingredient {Object}

Each ingredeint in the `results {Array}` will match each line sent to the endpoint.
If you split the request body by the `\n` character into an array, each element
position should match the position of each ingredient.

| Parameter        | Description                             |
|------------------|-----------------------------------------|
| serving_weight   | An {Integer} as weight in grams         |
| est_calories     | An {Integer} as estimated enegy         |
| serving_qty      | An {Integer} as the recommended serving |
| ndb_no           | An {Integer} as the USDA NDB Number     |
| serving_unit     | A {String} as the unit of measurment    |
| tier             | An {Integer} as the search tier         |
| nutrients        | An {Array} of Nutrient {Objects}        |
| parsed_query     | A Parsed Query {Object}                 |  

###  Parsed Query {Object}

This object represents how we interpereted the raw query on a given line.

| Parameter        | Description                             |
|------------------|-----------------------------------------|
| qty              | An {Integer} as the parsed quantity     |
| unit             | A {String} as the parsed unit of measurement |
| food             | A {String} as the parsed food |
| query            | A {String} as the raw query input from the line |


#### Nutrient {Object}

These objects represent the estimated value of each nutrient for each ingredient that was parsed.
When they are viewed in the context of `total.nutrients` they represent the value of all the ingredients summed.

| Parameter        | Description                          |
|------------------|--------------------------------------|
| value            | An {Integer} as numerical value of a nutrient |
| unit             | A {String} nutrients unit of measurement |
| name             | A {String} as nutrients name |
| attr_id          | An {Integer} refering to the id of a nutrient in the USDA `NUTR_DEF` table |
| usda_tag         | A {String} as the tag name assigned by the USDA |

### Example Response

```json
{
  "results": [
    {
      "serving_weight": 200,
      "serving_qty": 1,
      "ndb_no": 19335,
      "serving_unit": "cup",
      "tier": 1,
      "usda_fields_v2_grams": 0,
      "nutrients": [
        {
          "attr_id": 255,
          "value": 0.03999999818347749,
          "unit": "g",
          "name": "Water",
          "usda_tag": "WATER"
        }
        /// ...
      ],
      "parsed_query": {
        "qty": 1,
        "unit": "cup",
        "food": "sugar",
        "query": "1 cup sugar"
      },
      "idx": 0
    }
  ],
  "total": {
    "nutrients": [
      {
        "name": "Protein",
        "unit": "g",
        "usda_tag": "PROCNT",
        "attr_id": "203",
        "value": 0
      }
      // ...
    ],
    "serving_weight_grams": 1384
  }
}
```
