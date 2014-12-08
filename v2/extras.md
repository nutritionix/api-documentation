**Note about URL Encoded Parameters**
>Any parameters sent as a query strings in the url must be properly URL encoded. 
For example the phrase `cob salad from just salad` properly URL encoded should look like `cob%20salad%20from%20just%20salad`.
Every programming language has a function for URL encoding strings. In javascript this would look like `encodeURIComponent('cob salad from just salad')`.
If you are sending data with the `ContentType` as `application/json` or `multipart/form-data` then we will not attempt to decode any of the sent parameters
and we will assume the data was sent in plain text.


| Parameter       | Description                          |
|-----------------|--------------------------------------|
| nutrient_id     | An id representing the nutrient you want to see with each search result |  
| locale          | Sets the accepted language for your request. Currently only english (eng) is supported. Check back later for more language support. |
| serving_qty     | The quantity of the `exact_match` serving relative to the `serving_uom` parameter |
| serving_uom     | The unit of measurment for the `exact_match` |
| version_date    | A properly formatted date string representing the version of the API |