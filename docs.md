# Logic Sheet documentation

Thanks for using the Logic Sheet Google Workspace add-on. Logic Sheet is an all-in-one data processing tool for Google Sheets. You can use it to pull data from an API, enrich your spreadsheet with an external API, sort your data, and do math.

## Work with APIs
This section will cover how to use Logic Sheet's API-related functions.

### Pull from an API

![API screenshot](./img/ss-api.png)

**Method:** Chose the http method to pull data from an API endpoint. Currently we only support the GET and POST methods, though we will add more. Please check your API reference to decide which method you want to use.

**API url:** Type in the url and full path of the API endpoint, including all parameters. For example: https://mydata.com/api/v2/dataset1?para1=value1&para2=values.

Parameters are usually used to pass in API keys for simple authentication methods.

**Headers** Headers let you pass additional information with the API request. Request headers can be used in the request to provide information about the request context to help the server tailor the response. You can use, for example, the Authorization header to provide authentication credentials.

If the server responded with a 401 Unauthorized status, usually you should provide credentials to authenticate the request. To do so, you will need to use the Authorization header.

The value of the the Authorization header should be :

    <type> <credentials>

_Common types_:
- Basic: Base64-encoded credentials.
- Bearer: Bearer tokens to access OAuth 2.0-protected resources

**Path:** If provided, the funtion will only retrieve data that is located in the path. For example, You can enter key1.key2[1].key3 to retrieve to value of key3 of the second object of array key2 of the object key1.

If the JSON response looks like this:

        {
            "id": 1001,
            "person": [
                {
                    "name": "John",
                    "age": 45,
                    "city": "New York"
                },
                {
                    "name": "Rich",
                    "age": 34,
                    "city": "London"
                }
            ]
        }
the path person[1].name will return "Rich", while the path person[0] will return all information about John.

**Request body:** Enter the JSON format request body. This will only apply to the POST method.