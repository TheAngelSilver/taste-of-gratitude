backend.md
Taste of Gratitude - Backend Documentation
1. Main Backend Documentation
Project Overview
The backend provides core functionality for the e-commerce application, ensuring secure, scalable, and efficient operations.

Key Features
Product Management:
CRUD operations for managing the product catalog.
Endpoints secured with admin authentication.
Order History:
Tracks and retrieves user-specific order histories.
Payment Processing:
Stripe API integration for secure transactions.
User Authentication:
Firebase Auth for secure user identity management.
Database:
MongoDB Atlas for scalable cloud storage.
Hosting:
Deployed on Heroku for reliability.
Enhanced Security:
Rate limiting, input validation, and centralized error handling.
Folder Structure
plaintext
Copy code
/backend
├── /controllers              # Route handlers
│   ├── productController.js  # CRUD operations for products
│   ├── orderController.js    # Order history operations
│   ├── paymentController.js  # Stripe payment integration
├── /models                   # MongoDB schemas
│   ├── product.js            # Schema for products
│   ├── order.js              # Schema for orders
│   └── user.js               # Schema for users
├── /routes                   # API endpoints
│   ├── productRoutes.js      # Endpoints for products
│   ├── orderRoutes.js        # Endpoints for orders
│   ├── paymentRoutes.js      # Endpoints for payments
├── /middleware               # Middleware for security
│   ├── authMiddleware.js     # Firebase authentication
│   ├── rateLimiter.js        # Rate limiting
│   ├── validateInput.js      # Input validation
├── /utils                    # Utility functions
│   ├── errorHandler.js       # Centralized error handling
│   └── stripeHelper.js       # Stripe helper utilities
├── /config                   # Configuration files
│   ├── db.js                 # MongoDB connection setup
│   └── stripe.js             # Stripe configuration
├── server.js                 # Main server entry point
├── package.json              # Project dependencies
├── .env                      # Environment variables
└── README.md                 # Project documentation
Key Endpoints
Product Management
POST /api/products: Add a new product.
PUT /api/products/:id: Update product details.
DELETE /api/products/:id: Delete a product.
GET /api/products: Retrieve all products.
Order History
POST /api/orders: Create a new order.
GET /api/orders: Retrieve user-specific orders.
Payment Processing
POST /api/checkout: Create a payment intent.
POST /api/checkout/confirm: Confirm payment (if needed).
Security and Deployment
Authentication:
Firebase Authentication ensures secure user access.
Admin roles for managing sensitive operations.
Hosting:
Hosted on Heroku.
Environment variables for keys and secrets securely managed.