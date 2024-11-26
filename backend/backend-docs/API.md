# API Documentation for Taste of Gratitude Backend

## Base URL

`https://api.tasteofgratitude.com/v1`

## Authentication

All protected endpoints require Firebase authentication token in the Authorization header:

Authorization: Bearer <firebase_token>

## Endpoints

### Products API

#### Get All Products

GET /api/products
Query Parameters:

- page (optional): Page number for pagination
- limit (optional): Items per page
- category (optional): Filter by category
- search (optional): Search products by name

#### Get Single Product

GET /api/products/:id

#### Create Product (Admin)

POST /api/products
Body:
{
"name": string,
"description": string,
"price": number,
"category": string,
"imageUrl": string,
"inventory": number
}

#### Update Product (Admin)

PUT /api/products/:id
Body: Same as Create Product

#### Delete Product (Admin)

DELETE /api/products/:id

### Orders API

#### Create Order

POST /api/orders
Body:
{
"products": [
{
"productId": string,
"quantity": number
}
],
"shippingAddress": {
"street": string,
"city": string,
"state": string,
"zipCode": string
},
"paymentIntentId": string
}

#### Get User Orders

GET /api/orders
Query Parameters:

- page (optional): Page number
- limit (optional): Items per page

#### Get Order Details

GET /api/orders/:orderId

### Payment API

#### Create Payment Intent

POST /api/checkout
Body:
{
"amount": number,
"currency": string,
"paymentMethodType": string
}

#### Confirm Payment

POST /api/checkout/confirm
Body:
{
"paymentIntentId": string
}

### Admin Analytics API

#### Get Sales Analytics

GET /api/admin/analytics/sales
Query Parameters:

- startDate: ISO date string
- endDate: ISO date string

#### Get Product Performance

GET /api/admin/analytics/products
Query Parameters:

- period: "daily" | "weekly" | "monthly"

### Geolocation API

#### Get Delivery Zones

GET /api/admin/geolocation/zones

#### Update Delivery Zone

PUT /api/admin/geolocation/zones/:id
Body:
{
"coordinates": [
{
"lat": number,
"lng": number
}
],
"deliveryFee": number
}

### Bulk Operations API

#### Bulk Upload Products

POST /api/admin/bulk/products
Content-Type: multipart/form-data
Body:

- file: CSV/Excel file

## Error Responses

{
"error": {
"code": string,
"message": string,
"details": object (optional)
}
}

## Rate Limits

- Public APIs: 100 requests per 15 minutes
- Admin APIs: 300 requests per 15 minutes

## Data Models

### Product

{
id: string;
name: string;
description: string;
price: number;
category: string;
imageUrl: string;
inventory: number;
createdAt: string;
updatedAt: string;
}

### Order

{
id: string;
userId: string;
products: Array<{
productId: string;
quantity: number;
price: number;
}>;
total: number;
status: 'pending' | 'processing' | 'completed' | 'cancelled';
shippingAddress: {
street: string;
city: string;
state: string;
zipCode: string;
};
paymentIntentId: string;
createdAt: string;
updatedAt: string;
}
