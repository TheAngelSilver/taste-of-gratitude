Taste of Gratitude Backend
Overview
This repository contains the backend code for the Taste of Gratitude e-commerce platform. The backend is built with a focus on scalability, security, and efficiency, providing RESTful APIs to support core functionalities such as product management, user authentication, order processing, and secure payment integration.

Key Features
Product Management:

Admin-exclusive APIs for adding, updating, and deleting products.
Public APIs for fetching product catalogs.
Order Management:

Track user-specific order histories.
API for creating and retrieving orders.
Payment Integration:

Seamless Stripe API integration for secure transactions.
User Authentication:

Firebase Authentication for secure and scalable user management.
Database:

MongoDB Atlas for centralized cloud-based storage.
Security:

Middleware for rate limiting, input validation, and centralized error handling.
Deployment:

Hosted on Heroku for reliable and scalable cloud hosting.
Folder Structure
plaintext
Copy code
/backend
├── /controllers # Route handlers for API endpoints
│ ├── productController.js # CRUD operations for products
│ ├── orderController.js # Manage user orders
│ ├── paymentController.js # Stripe payment integration
├── /models # Database schemas
│ ├── product.js # Product schema
│ ├── order.js # Order schema
│ └── user.js # User schema (for references)
├── /routes # API route definitions
│ ├── productRoutes.js # Routes for product-related APIs
│ ├── orderRoutes.js # Routes for order-related APIs
│ ├── paymentRoutes.js # Routes for payment processing
├── /middleware # Middleware for validation and security
│ ├── authMiddleware.js # Firebase authentication middleware
│ ├── rateLimiter.js # Rate limiting to prevent abuse
│ ├── validateInput.js # Input validation middleware
├── /utils # Helper utilities and error handlers
│ ├── errorHandler.js # Centralized error handling
│ └── stripeHelper.js # Helper functions for Stripe API
├── /config # Configuration and setup files
│ ├── db.js # MongoDB connection setup
│ └── stripe.js # Stripe API configuration
├── server.js # Main server entry point
├── package.json # Project dependencies and scripts
├── .env # Environment variables
└── README.md # Project documentation
Tech Stack
Programming Language: JavaScript (Node.js)
Framework: Express.js
Database: MongoDB Atlas
Authentication: Firebase Authentication
Payments: Stripe API
Hosting: Heroku
Security:
Middleware for rate limiting and validation
Environment variable management with .env
Installation

1. Prerequisites
   Ensure you have the following installed:

Node.js (v16 or higher)
MongoDB Atlas (configured database)
Firebase Project (for authentication)
Stripe Account (for payment integration) 2. Clone Repository
bash
Copy code
git clone https://github.com/<your-repository>/taste-of-gratitude-backend.git
cd taste-of-gratitude-backend 3. Install Dependencies
bash
Copy code
npm install 4. Configure Environment Variables
Create a .env file in the root directory and add the following:

plaintext
Copy code
PORT=5000
MONGO_URI=mongodb+srv://<username>:<password>@cluster.mongodb.net/tasteofgratitude
STRIPE_SECRET_KEY=sk_test_your_stripe_secret_key
FIREBASE_PROJECT_ID=<your-firebase-project-id>
FIREBASE_PRIVATE_KEY="<your-firebase-private-key>"
FIREBASE_CLIENT_EMAIL=<your-firebase-client-email> 5. Start Development Server
To run the server locally:

bash
Copy code
npm run dev
The backend will be accessible at http://localhost:5000.

6. Deploy to Heroku
   Create a Heroku app:
   bash
   Copy code
   heroku create taste-of-gratitude-backend
   Set environment variables:
   bash
   Copy code
   heroku config:set PORT=5000 MONGO_URI=... STRIPE_SECRET_KEY=... FIREBASE_PROJECT_ID=...
   Deploy the code:
   bash
   Copy code
   git push heroku main
   API Documentation
   Authentication
   All endpoints require a valid Firebase authentication token passed in the Authorization header as a Bearer token.

Endpoints

1. Product Management
   Method Endpoint Description
   GET /api/products Fetch all products
   POST /api/products Add a new product (Admin)
   PUT /api/products/:id Update a product (Admin)
   DELETE /api/products/:id Delete a product (Admin)
2. Order Management
   Method Endpoint Description
   POST /api/orders Create a new order
   GET /api/orders Fetch order history for a user
3. Payment Processing
   Method Endpoint Description
   POST /api/checkout Create a payment intent
   POST /api/checkout/confirm Confirm payment (if required)
   Security Features
   Authentication:
   Firebase Authentication to validate user identities.
   Rate Limiting:
   Prevent abuse with a limit of 100 requests per 15 minutes.
   Input Validation:
   Sanitizes and validates input data to prevent SQL injection and XSS.
   Centralized Error Handling:
   Provides consistent error responses across all APIs.
   Deployment
   The application is hosted on Heroku with the following configurations:

MongoDB Atlas for database persistence.
Environment Variables for secure configuration management.
Automatic Scaling for handling increased traffic.
Testing
Unit Tests
Run unit tests with:

bash
Copy code
npm test
API Testing
Use tools like Postman or Insomnia to test API endpoints.
Ensure the Authorization header is set with a valid Firebase token.
Contributing
Steps to Contribute
Fork the repository.
Create a new feature branch:
bash
Copy code
git checkout -b feature-name
Commit changes and push to your fork:
bash
Copy code
git add .
git commit -m "Description of changes"
git push origin feature-name
Open a pull request.
Coding Guidelines
Use consistent code formatting (Prettier/ESLint).
Document new endpoints thoroughly.
Write tests for any new features or bug fixes.
Support
For any issues, open a ticket on the repository or contact the project maintainers at support@tasteofgratitude.com.

License
This project is licensed under the MIT License. See the LICENSE file for details.
