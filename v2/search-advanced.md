API V2: Search - Advanced Usage
======================================

If you have not already explored the basic usage of the V2 Search endpoint please visit [this page][1].

### Filtering Results

One of the most common tasks we do when searching for something is reduce the noise of our search results. Filtering is only supported for JSON encoded requests. To let us know you are sending JSON please set your `Content-Type` header to `application/json`.

### Filtering parameters

| Parameter       | Description                          |
|-----------------|--------------------------------------|
| filters         | An {Object} where each key represents a filed that will be filtered by |

**Example Filter Parameters**

```json 
{
    "filters":{
        "nf_calories":{
            "gt": 100
        }
    }
}
```


Next: [Brand Search][1]

[1]: https://developer.nutritionix.com/docs/v2/brand_search