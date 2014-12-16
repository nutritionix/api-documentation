V2 Item
========================

### Request Parameters

**Required Parameters**

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| resource_id     | A {String} as a path parameter can be an (item_id, resource_id, or UPC) |

### Response Parameters

The response from this endpoint will be of `Content-Type: application/json`<br>

| Parameter            | Description                          |
|----------------------|--------------------------------------|
| id                   | A {String} as the item id |
| name                 | A {String} as the item name |
| type                 | An {Integer} as the items type (1=restaurant, 2=CPG, 3=USDA / Nutritionix) |
| tags                 | An [Array]{Strings} as the tags assigned to that item |
| ingredient_statement | A {String} as the ingredient statement **may be null** |
| brand                | A {Brand} an {Object} representing the items brand |
| images               | An {Images} an {Object} listing the images available for this item |
| label                | A {Label} an {Object} representing the nutrition label |


### Brand {Object}

| Parameter      | Description                          |
|----------------|--------------------------------------|
| id             | A {String} as the identifier for the brand |  
| name           | A {String} as the name of the brand |  
| website        | A {String} as the website for the brand |  
| logo           | A {String} as the url to the brand logo |  


### Images {Object}

| Parameter      | Description                          |
|----------------|--------------------------------------|
| front.full     | A {String} representing the full size front of package photo |
| front.thumb    | A {String} representing the thumbnail of the front of package photo |
| label.full     | A {String} representing the full size nutrition label photo |

### Label {Object}

| Parameter      | Description                          |
|----------------|--------------------------------------|
| serving        | A {Serving} {Object}                 |
| nutrients      | An [Array] of {Nutrient} {Objects}   |

### Serving {Object}

| Parameter      | Description                          |
|----------------|--------------------------------------|
| qty            | An {Integer} as the quantity of a serving |
| uom            | A {String} as the unit of measurement of a serving |
| per_container  | An {Integer} representing the number of servings per container |
| metric.qty     | An {Integer} as the `metric` quantity of a serving |
| metric.uom     | A {String} as the unit of measurement of a servings `metric` |

### Nutrient {Object}

| Parameter      | Description                          |
|----------------|--------------------------------------|
| attr_id        | An {Integer} representing the usda attribute id of the nutrient |
| value          | A {Float} representing the nutritional value of a nutrient |
| unit           | A {String} as the nutrients unit of measurement |
| name           | A {String} as the nutrients proper name |
| usda_tag       | A {String} as the nutrients usda given abbreviation |


### Example Request in CURL

```sh
# Note that authentication headers have been excluded for brevity.
# This request looks up an item by its UPC
# In this case `resource_id` is `52200004265`
curl -XGET "https://apibeta.nutritionix.com/v2/item/52200004265"
```


#### Example Response

```json
{
  "id": "keVD",
  "name": "Turkey Burger",
  "type": 1,
  "tags": [],
  "ingredient_statement": null,
  "brand": {
    "id": "ga",
    "name": "Burger King",
    "website": "http://www.burgerking.com",
    "logo": "https://d1r9wva3zcpswd.cloudfront.net/533d7b92bf66c42a2eec2a94.png"
  },
  "images": {
    "front": {
      "full": "https://d1r9wva3zcpswd.cloudfront.net/533d7b92bf66c42a2eec2a94.png",
      "thumb": "https://d1r9wva3zcpswd.cloudfront.net/533d7b92bf66c42a2eec2a94.png"
    },
    "label": {
      "full": null
    }
  },
  "label": {
    "serving": {
      "qty": 252,
      "uom": "Grams",
      "per_container": null,
      "metric": {
        "qty": 252,
        "uom": "g"
      }
    },
    "nutrients": [
      {
        "attr_id": 203,
        "value": 27,
        "unit": "g",
        "name": "Protein",
        "usda_tag": "PROCNT"
      },
      {
        "attr_id": 204,
        "value": 26,
        "unit": "g",
        "name": "Total Fat",
        "usda_tag": "FAT"
      }
      //..
    ]
  }
}
```

Next: [View whole Brand Record][1]

[1]: https://developer.nutritionix.com/docs/v2/brand