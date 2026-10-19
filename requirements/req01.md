# API :: Retrieve product information by id

## API Endpoint
* GET /api/products/{id}

### Response code 200 (success)
```json
{
  "id": 1,
  "name": "Product Name",
  "description": "Product Description",
  "price": 100.0,
  "stock": 50
}
```
### Response code 400 (bad request)
```json
{
  "message": "Invalid product ID"
}
```

### Response code 404 (not found)
```json
{
  "message": "Product not found"
}
```

### Response code 500 (internal server error)
```json
{
  "message": "Internal server error"
}
```

## Input validation in table format

| Parameter | Type   | Required | Description       |
|-----------|--------|----------|------------------|
| id        | integer| yes      | The ID of the product |

## Business flow
1. Validate the input ID.
2. Retrieve the product information from table 'products' in the database.
3. If the product is found, return the product information with a 200 status code.
4. If the product is not found, return a 404 status code with an appropriate message.
5. If the input ID is invalid, return a 400 status code with an appropriate message.
6. If there is an internal server error, return a 500 status code with an appropriate message.
7. Insert log to the 'logs_products' table in the database with details of the request and response.


## Tables structure

### products table
| Column      | Type    | Description           |
|-------------|---------|----------------------|
| id          | integer | The ID of the product |
| name        | text    | The name of the product |
| description | text    | The description of the product |
| price       | numeric | The price of the product |
| stock       | integer | The stock quantity of the product |
| created_at  | timestamp | The timestamp of the product creation |
| updated_at  | timestamp | The timestamp of the product last update |

### logs_products table
| Column      | Type    | Description           |
|-------------|---------|----------------------|
| id          | integer | The ID of the log entry |
| product_id  | integer | The ID of the product |
| request     | text    | The request details   |
| response    | text    | The response details  |
| created_at  | timestamp | The timestamp of the log entry |


## API test cases in table format

| TEST ID| Test Case | Input | Expected Status code | Expected JSON response | Description |
|---------|-----------|-------|----------------|-------------|-------------|
| TC001 | Valid ID | 1     | 200 | {"id": 1, "name": "Product Name", "description": "Product Description", "price": 100.0, "stock": 50} | Retrieve product information successfully |
| TC002 | Invalid ID | abc   | 400 | {"message": "Invalid product ID"} | Input ID is not an integer |
| TC003 | Non-existent ID | 9999  | 404 | {"message": "Product not found"} | Product with the given ID does not exist |
| TC004 | Internal Server Error | -     | 500 | {"message": "Internal server error"} | Simulate an internal server error |