Backend Structure for Taste of Gratitude
Overview
The backend is designed to handle e-commerce operations efficiently, including product management, order processing, user authentication, payment integration, and analytics. It consists of two distinct parts:

Main Backend: Focuses on user-facing functionalities like browsing products, placing orders, and managing user accounts.
Admin Backend: Provides tools for administrative tasks, analytics, and advanced management.

1. Main Backend Structure
   Folder Structure
   plaintext
   Copy code
   /backend
   ├── /controllers
   │ ├── productController.js # Manages product-related operations (CRUD)
   │ ├── orderController.js # Handles order creation and retrieval
   │ ├── paymentController.js # Integrates with Stripe for payment processing
   ├── /models
   │ ├── product.js # Schema for product data
   │ ├── order.js # Schema for orders and order history
   │ └── user.js # Schema for users (used for order references)
   ├── /routes
   │ ├── productRoutes.js # API endpoints for product management
   │ ├── orderRoutes.js # API endpoints for order handling
   │ ├── paymentRoutes.js # API endpoints for Stripe payment integration
   ├── /middleware
   │ ├── authMiddleware.js # Middleware for Firebase user authentication
   │ ├── validateInput.js # Utility for input validation
   │ ├── rateLimiter.js # Middleware for rate limiting
   ├── /utils
   │ ├── errorHandler.js # Centralized error handling utility
   │ └── stripeHelper.js # Helper functions for Stripe API
   ├── /config
   │ ├── db.js # MongoDB connection configuration
   │ └── stripe.js # Stripe API configuration
   ├── server.js # Main entry point for the backend server
   ├── package.json # Dependencies and scripts
   ├── .env # Environment variables
   └── README.md # Documentation for the main backend
   Core Functionalities
   Product Management:

CRUD operations for product inventory.
Supports filtering and pagination for large catalogs.
Order History:

Stores user-specific orders in MongoDB.
Provides endpoints to fetch order history.
Payment Processing:

Stripe integration for secure payments.
Generates client secrets for frontend payment flows.
User Authentication:

Firebase Authentication to manage user identities securely.
Security Features:

Rate limiting to prevent abuse.
Input validation to ensure data integrity.
Centralized error handling.
Key Components
Controllers
productController.js:
Handles product CRUD operations.
orderController.js:
Manages order creation and retrieval.
paymentController.js:
Handles payment intent creation and confirmation.
Models
product.js:
Defines the schema for product details.
order.js:
Captures order details, including user reference and status.
user.js:
Tracks user-specific data for orders.
Middleware
authMiddleware.js:
Verifies Firebase tokens for protected routes.
rateLimiter.js:
Limits API requests per IP.
validateInput.js:
Validates request payloads.
Utilities
errorHandler.js:
Centralized error response.
stripeHelper.js:
Simplifies Stripe API interactions. 2. Admin Backend Structure
Folder Structure
plaintext
Copy code
/admin-backend
├── /controllers
│ ├── authController.js # Handles admin login and authentication
│ ├── productController.js # CRUD operations for product management
│ ├── analyticsController.js # Provides analytics data
│ ├── geolocationController.js # Manages delivery zones and shop locations
│ ├── bulkUploadController.js # Handles bulk product uploads
├── /models
│ ├── adminUser.js # Schema for admin users
│ ├── product.js # Schema for product details
│ ├── order.js # Schema for order details
│ └── analytics.js # Schema for analytics data
├── /routes
│ ├── authRoutes.js # API endpoints for admin authentication
│ ├── productRoutes.js # Endpoints for product CRUD operations
│ ├── analyticsRoutes.js # Endpoints for analytics queries
│ ├── geolocationRoutes.js # Endpoints for geolocation management
│ ├── bulkUploadRoutes.js # Endpoints for bulk uploads
├── /middleware
│ ├── authMiddleware.js # RBAC-based authentication middleware
│ ├── rateLimiter.js # Stricter rate limiting for admins
│ ├── validateInput.js # Validates admin input
│ └── errorHandler.js # Handles errors
├── /utils
│ ├── geoHelper.js # Utilities for geolocation services
│ ├── fileParser.js # CSV/Excel parsing for bulk uploads
│ ├── analyticsHelper.js # Utilities for processing analytics data
│ └── logger.js # Logging utility
├── /config
│ ├── db.js # MongoDB connection setup
│ └── authConfig.js # JWT and RBAC settings
├── /scripts
│ ├── seedAdminUsers.js # Script to seed admin accounts
│ ├── generateReports.js # Automated analytics report generation
│ └── migrateProducts.js # Product migration utilities
├── server.js # Main entry point for admin backend
├── package.json # Dependencies and scripts
├── .env # Environment variables
└── README.md # Admin backend documentation
Core Functionalities
Authentication:

Admins authenticate via JWT tokens.
RBAC ensures role-specific access.
Product Management:

CRUD operations for managing the product catalog.
Bulk upload via CSV/Excel files.
Analytics:

Aggregated sales and performance metrics.
Geolocation-based analytics for delivery optimization.
Geolocation Services:

Update and retrieve delivery zones.
Support for popup shop locations.
Security Features:

Stricter rate limiting and IP whitelisting.
Logging for audit trails.
Key Components
Controllers
authController.js:
Manages admin authentication and RBAC.
productController.js:
Handles product management tasks.
analyticsController.js:
Fetches aggregated analytics data.
geolocationController.js:
Updates delivery zones and shop locations.
bulkUploadController.js:
Processes CSV/Excel files for bulk uploads.
Models
adminUser.js:
Schema for admin accounts with roles.
product.js:
Schema for product details.
order.js:
Tracks orders for analytics.
analytics.js:
Stores processed analytics data.
Middleware
authMiddleware.js:
Verifies JWT tokens and enforces RBAC.
rateLimiter.js:
Enforces stricter rate limits for admins.
validateInput.js:
Ensures admin data integrity.
Utilities
geoHelper.js:
Supports geolocation services like reverse geocoding.
fileParser.js:
Parses CSV/Excel files for bulk uploads.
analyticsHelper.js:
Aggregates and processes analytics data.
logger.js:
Logs errors and activity for auditing.
Scripts
seedAdminUsers.js:
Seeds initial admin accounts for testing.
generateReports.js:
Automates the generation of analytics reports.
migrateProducts.js:
Migrates product data between environments.
Security Features
RBAC:
Role-specific access enforced via middleware.
Rate Limiting:
Stricter limits for sensitive endpoints.
IP Whitelisting:
Admin access restricted to trusted IPs.
Logging:
Comprehensive activity logs for auditing. 3. Conclusion
This structure ensures a modular, scalable, and secure backend for Taste of Gratitude, supporting seamless user experiences and robust administrative operations. Each component is designed to align with the project's goals of scalability, security, and maintainability.
