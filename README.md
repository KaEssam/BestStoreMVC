# BestStore MVC

A modern e-commerce web application built with ASP.NET Core MVC, providing a robust and scalable solution for online retail businesses.

## ✨ Features

- User Authentication and Authorization
- Product Management
- Shopping Cart Functionality
- Order Processing
- Admin Dashboard
- Responsive Design
- Secure Payment Integration

## 🛠 Technology Stack

- **Framework**: ASP.NET Core MVC
- **Language**: C#
- **Database**: SQL Server
- **ORM**: Entity Framework Core
- **Front-end**:
  - HTML5
  - CSS3
  - JavaScript
  - Bootstrap
- **Authentication**: ASP.NET Core Identity
- **Development Tools**:
  - Visual Studio 2022
  - Visual Studio Code
  - Git

## 📁 Project Structure

```
BestStoreMVC/
├── Controllers/         # MVC Controllers
├── Models/             # Data models and ViewModels
├── Views/              # Razor views
├── Services/           # Business logic and services
├── wwwroot/           # Static files (CSS, JS, images)
├── Migrations/         # Database migrations
├── Properties/         # Project properties
└── Program.cs         # Application entry point
```

```

## 📊 Application Workflow

### Feature Interaction Diagram

```mermaid
graph TD
    subgraph User Actions
        A[User Registration/Login] --> B[Browse Products]
        B --> C[Add to Cart]
        C --> D[Checkout Process]
        D --> E[Order Confirmation]
    end

    subgraph Authentication Flow
        A --> AA[Identity Service]
        AA --> AB[JWT Token Generation]
        AB --> AC[Role Assignment]
    end

    subgraph Shopping Flow
        B --> BA[Product Catalog Service]
        BA --> BB[Filter/Search]
        BB --> BC[Product Details]
        C --> CA[Cart Service]
        CA --> CB[Cart Management]
    end

    subgraph Order Processing
        D --> DA[Order Service]
        DA --> DB[Payment Processing]
        DB --> DC[Inventory Update]
        DC --> E
    end

    subgraph Admin Operations
        F[Admin Login] --> FA[Dashboard]
        FA --> FB[Product Management]
        FA --> FC[Order Management]
        FA --> FD[User Management]
        FB --> DC
    end
```

### Application Cycle Explanation

1. **User Journey**:

   - Registration/Login through ASP.NET Core Identity
   - Browse product catalog with filtering and search
   - Add items to shopping cart
   - Proceed to checkout
   - Receive order confirmation

2. **Authentication Cycle**:

   - User credentials validation
   - JWT token generation for API security
   - Role-based access control
   - Session management

3. **Shopping Experience**:

   - Product browsing with pagination
   - Advanced search functionality
   - Real-time inventory checking
   - Cart management with persistent storage

4. **Order Processing**:

   - Cart validation
   - Payment processing integration
   - Inventory management
   - Order status tracking
   - Email notifications

5. **Admin Operations**:
   - Product CRUD operations
   - Order management and tracking
   - User management
   - Sales analytics and reporting

### Technical Implementation

```mermaid
graph LR
    subgraph Frontend Layer
        A[Views] --> B[Controllers]
        Z[JavaScript] --> A
        Y[CSS/Bootstrap] --> A
    end

    subgraph Business Layer
        B --> C[Services]
        C --> D[Repositories]
    end

    subgraph Data Layer
        D --> E[Entity Framework]
        E --> F[SQL Server]
    end

    subgraph Cross-Cutting
        G[Authentication]
        H[Logging]
        I[Caching]
        J[Error Handling]
    end

    G --> B
    H --> C
    I --> C
    J --> B
```

### MVC Architecture Flow

1. **Presentation Layer (MVC Pattern)**:

   - Views: Razor pages for UI
   - Controllers: Handle user requests
   - Models: Data representation

2. **Service Layer**:

   - Business logic implementation
   - Data validation
   - Transaction management

3. **Data Access Layer**:

   - Entity Framework Core
   - Repository pattern
   - CRUD operations

4. **Cross-Cutting Concerns**:
   - Authentication & Authorization
   - Logging & Monitoring
   - Caching
   - Exception handling

## 📊 Database Design

### ERD Diagram

```mermaid
erDiagram
    User ||--o{ Order : places
    User {
        int Id
        string Email
        string Password
        string FirstName
        string LastName
        string Address
    }

    Order ||--|{ OrderItem : contains
    Order {
        int Id
        int UserId
        datetime OrderDate
        decimal TotalAmount
        string Status
    }

    Product ||--o{ OrderItem : "included in"
    Product {
        int Id
        string Name
        string Description
        decimal Price
        int StockQuantity
        string Category
    }

    OrderItem {
        int Id
        int OrderId
        int ProductId
        int Quantity
        decimal UnitPrice
    }

    Cart ||--|{ CartItem : contains
    Cart {
        int Id
        int UserId
        datetime CreatedDate
    }

    CartItem {
        int Id
        int CartId
        int ProductId
        int Quantity
    }

    Category ||--o{ Product : contains
    Category {
        int Id
        string Name
        string Description
    }
```
