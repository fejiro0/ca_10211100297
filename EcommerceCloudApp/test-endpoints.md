# Backend API Endpoint Testing Guide

## Server Setup
```bash
cd EcommerceCloudApp
npm run dev
```

Server runs on: `http://localhost:3000`

---

## Test Endpoints One by One

### 1. Test Categories API - GET all categories
```bash
curl -X GET http://localhost:3000/api/categories
```

### 2. Test Categories API - GET single category
```bash
curl -X GET http://localhost:3000/api/categories/{categoryId}
```

### 3. Test Products API - GET all products
```bash
curl -X GET http://localhost:3000/api/products
```

### 4. Test Products API - GET single product
```bash
curl -X GET http://localhost:3000/api/products/{productId}
```

### 5. Test Customers API - GET all customers
```bash
curl -X GET http://localhost:3000/api/customers
```

### 6. Test Customers API - POST create customer
```bash
curl -X POST http://localhost:3000/api/customers ^
  -H "Content-Type: application/json" ^
  -d "{\"firstName\":\"John\",\"lastName\":\"Doe\",\"email\":\"john@example.com\",\"phoneNumber\":\"0241234567\",\"password\":\"password123\",\"region\":\"Greater Accra\",\"city\":\"Accra\"}"
```

### 7. Test Customers API - GET single customer
```bash
curl -X GET http://localhost:3000/api/customers/{customerId}
```

### 8. Test Auth Login API - POST login
```bash
curl -X POST http://localhost:3000/api/auth/login ^
  -H "Content-Type: application/json" ^
  -d "{\"identifier\":\"john@example.com\",\"password\":\"password123\"}"
```

### 9. Test Vendors API - GET all vendors
```bash
curl -X GET http://localhost:3000/api/vendors
```

### 10. Test Vendors API - GET single vendor
```bash
curl -X GET http://localhost:3000/api/vendors/{vendorId}
```

### 11. Test Cart API - GET cart
```bash
curl -X GET "http://localhost:3000/api/cart?customerId={customerId}"
```

### 12. Test Cart API - POST add to cart
```bash
curl -X POST http://localhost:3000/api/cart ^
  -H "Content-Type: application/json" ^
  -d "{\"customerId\":\"{customerId}\",\"productId\":\"{productId}\",\"quantity\":1}"
```

### 13. Test Reviews API - GET all reviews
```bash
curl -X GET http://localhost:3000/api/reviews
```

### 14. Test Reviews API - GET single review
```bash
curl -X GET http://localhost:3000/api/reviews/{reviewId}
```

### 15. Test Payments API - GET all payments
```bash
curl -X GET http://localhost:3000/api/payments
```

### 16. Test Payments API - GET single payment
```bash
curl -X GET http://localhost:3000/api/payments/{paymentId}
```

### 17. Test Products Stock API - PATCH update stock
```bash
curl -X PATCH http://localhost:3000/api/products/{productId}/stock ^
  -H "Content-Type: application/json" ^
  -d "{\"quantityChange\":-1}"
```

---

## Testing with PowerShell (Windows)

For better formatting in PowerShell, use:

```powershell
# Test GET Categories
Invoke-RestMethod -Uri "http://localhost:3000/api/categories" -Method GET | ConvertTo-Json

# Test GET Products
Invoke-RestMethod -Uri "http://localhost:3000/api/products" -Method GET | ConvertTo-Json

# Test POST Customer Registration
$body = @{
    firstName = "John"
    lastName = "Doe"
    email = "john@example.com"
    phoneNumber = "0241234567"
    password = "password123"
    region = "Greater Accra"
    city = "Accra"
} | ConvertTo-Json

Invoke-RestMethod -Uri "http://localhost:3000/api/customers" -Method POST -Body $body -ContentType "application/json" | ConvertTo-Json

# Test POST Login
$loginBody = @{
    identifier = "john@example.com"
    password = "password123"
} | ConvertTo-Json

Invoke-RestMethod -Uri "http://localhost:3000/api/auth/login" -Method POST -Body $loginBody -ContentType "application/json" | ConvertTo-Json
```

---

## Expected Response Format

All endpoints should return JSON in this format:
```json
{
  "status": "success" | "error",
  "message": "Description",
  "data": { ... }
}
```

