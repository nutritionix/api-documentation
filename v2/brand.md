V2 Brand Model
========================

Example URL

https://api.nutritionix.com/v2/brand/:brand_id


### Response Parameters

The response from this endpoint will be of `Content-Type: application/json`<br>

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| id              | A {String} as the identifier for the brand |  
| name            | A {String} as the name of the brand |  
| website         | A {String} as the website for the brand |  
| logo            | A {String} as the url to the brand logo |  
| type            | An {Integer} as the brand type (1=restaurant, 2=CPG, 3=USDA / Nutritionix) |  
| item_count      | An {Integer} as the total number of items this brand has |  


### Example Response

```json
{
  "id": "xd6",
  "name": "McDonald's",
  "website": "http://www.mcdonalds.com",
  "logo": "https://d1r9wva3zcpswd.cloudfront.net/533d7bf65b8015402e5ce097.jpg",
  "type": 1,
  "item_count": 363
}
```


Next: [Error Handling][1]

[1]: https://developer.nutritionix.com/docs/v2/error_handling