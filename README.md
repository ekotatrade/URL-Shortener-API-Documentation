
# URL Shortener API Documentation

This API allows users to generate short URLs for a given long URL.

## Endpoint

### Generate Short URL

**POST** `/api/v1/url/generate`

This endpoint generates a short URL based on the provided long URL.

---

### Request

**URL:**  
`https://www.ekotatrade.com/api/v1/url/generate`

**Method:**  
`POST`

**Headers:**  
- `Content-Type: application/json`

**Body:**  
Provide the long URL to shorten in the request body as JSON:
```json
{
  "url": "https://www.ekotatrade.com.bd/product/xiaomi-mibro-watch-lite-2-watch"
}
```

---

### Responses

#### **Success Response (200)**

If the URL is provided and the short URL is generated successfully:

```json
{
  "status": true,
  "message": "Short URL generated successfully",
  "url": "https://ekotatrade.com/V9Mc-y"
}
```

- `status`: Indicates whether the operation was successful (`true`).
- `message`: A message confirming that the short URL was generated successfully.
- `url`: The generated short URL.

#### **Error Response (400)**

If the URL is missing from the request body:

```json
{
  "success": false,
  "message": "URL is required!",
  "errorSources": [
    {
      "path": "",
      "message": "URL is required!"
    }
  ],
  "err": {
    "statusCode": 400
  }
}
```

- `success`: Indicates the failure of the operation (`false`).
- `message`: A message explaining the error ("URL is required!").
- `errorSources`: An array containing details about the error.
  - `path`: The problematic field (in this case, it's empty since the entire URL is missing).
  - `message`: Further information on the error.
- `err.statusCode`: The HTTP status code (`400` for bad request).

---

### Example Requests

#### **cURL Example**

```bash
curl -X POST "https://www.ekotatrade.com/api/v1/url/generate" \
-H "Content-Type: application/json" \
-d '{
    "url": "https://www.ekotatrade.com.bd/product/xiaomi-mibro-watch-lite-2-watch"
}'
```

#### **Example with Missing URL**

```bash
curl -X POST "https://www.ekotatrade.com/api/v1/url/generate" \
-H "Content-Type: application/json" \
-d '{}'
```

---

### Notes
- Ensure that the `url` field is provided in the request body for a successful response.
- If no URL is provided, the API will return a `400 Bad Request` error, indicating that the URL is required.
