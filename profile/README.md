# Welcome to The Squad! 👋🏻

We are a group of passionate software engineers who are interested in building scalable and robust software systems.

Our mission is to simulate builing a microservices architecture e-commerce app.

## About the team

[@Muhammad Saad](https://github.com/muhammad-saad-01)

[@Abdulrahman Essam](https://github.com/orgs/Null-Pointer-Squad/people/horus208)

[@Mohamed Eid](https://github.com/Mohammed-eid35)

[@Mohammed Samih](https://github.com/Muhammed-Sameih)

[@Abdelaziz Ashraf](https://github.com/abdelaziz-ashraf)

[@Mohamed Taha](https://github.com/MohamedTahaCS)

Let's get started! and have a look at what we are trying to build! 🎉.

# E-Commerce Microservices Platform

we are simulating building an e-commerce platform using microservices architecture. We are building a platform that allows customers to browse products, add them to their cart, and purchase them and track thier shippment. We are also building a platform that allows admins to manage products, categories, brands, stors stock and coupons.

## 1. Bank Management System

The Bank Management System is a standalone web-based application developed using Spring Boot that aims to streamline various banking operations. This system offers features to manage customer accounts and perform transactions. (we are using this system to simulate the payment process in our e-commerce platform)

Check out the full details here 👉🏻 [Bank Management System README file.](https://github.com/Null-Pointer-Squad/bank-management-system-springboot)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
    User {
        SERIAL id PK
        VARCHAR name
        VARCHAR password
        VARCHAR phone "UNIQUE"
        VARCHAR email "UNIQUE"
    }

    Account {
        SERIAL id PK
        VARCHAR card_number "UNIQUE"
        VARCHAR cvv
        DOUBLE balance
        SERIAL user_id FK
    }

    Transaction {
        SERIAL id PK
        VARCHAR type
        DOUBLE amount
        TEXT notes
        DATE timestamp
        SERIAL account_id FK
    }

    User ||--o{ Account : "has"
    Account ||--o{ Transaction : "history"
```

## 2. Admin Management and Authentication Service

This service is an admin management and authentication service built using Spring Boot, Spring Security, and JSON Web Tokens (JWT). It provides a secure and efficient way to manage admin users, authenticate them using email and password, and generate JWTs for accessing protected resources. Additionally, admins have the ability to add other admins and activate or deactivate their accounts.
(we are using this system to simulate the admin management and authentication process in our e-commerce platform)

Check out the full details here 👉🏻 [Admin Management and Authentication Service README file.](https://github.com/Null-Pointer-Squad/admin-service-api)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
    CUSTOMER {
        BIGINT id
        VARCHAR firstname
        VARCHAR lastname
        VARCHAR email
        VARCHAR password
        BOOLEAN  enabled
    }

```

## 3. Product Catalog API Service

This service is built for managing a product catalog [adding, updating, deleting, and retrieving products] for an E-Commerce Application. (we are using this system to simulate the product catalog management process in our e-commerce platform)

Check out the full details here 👉🏻 [Product Catalog API README file.](https://github.com/Null-Pointer-Squad/Product-Catalog-API)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
    BRAND ||--o{ PRODUCT : "has"
    CATEGORY ||--o{ PRODUCT : "has"
    PRODUCT {
        long id
        string Code
        string name
        string description
        string imageUri
        BigDecimal price
        boolean active
        long category_id
        long brand_id
    }

    BRAND {
        long id
        string name
        string about
        string imageUri
        string WebsiteUri
        boolean active
    }

    CATEGORY {
        long id
        string name
        string description
        boolean active
        string imageUri
    }

```

## 4. Orders API Service

The Orders API Service is an important component of our e-commerce platform, designed to efficiently handle the creation, management, and processing of our customers' orders. And it encapsulates order-related functionalities.

Check out the [Orders API README file.](https://github.com/Null-Pointer-Squad/OrderAPIs)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
    ORDER {
        Integer id PK
        Integer customer_email
        TIMESTAMP order_date
        DECIMAL total_price
        VARCHAR status
        VARCHAR code
    }

    ORDER_ITEM {
        Integer id PK
        Integer order_id FK
        Integer product_code
        Integer quantity
        DECIMAL price
        VARCHAR code
    }




    CUOPON{
        Integer id PK
        Integer coupon_code
        VARCHAR coupon_Type
        DECIMAL discount_value_or_percentage
    }



    ORDER }o..|| CUOPON : has
    ORDER ||--|{ ORDER_ITEM : has
```

## 5. Shipping API

The Shipping Service is an important component of our e-commerce platform, designed to efficiently manage the shipping and delivery aspects of our customers' orders. And it encapsulates shipping-related functionalities (we are using this system to simulate the shipping management process in our e-commerce platform)

Check out the full details here 👉🏻 [Shipping API README file.](https://github.com/Null-Pointer-Squad/ShippingAPIs)

and here is the ERD for the database used in this service:

```mermaid
erDiagram



    SHIPMENT {
        Integer id PK
        Integer customer_id FK
        TIMESTAMP shipment_date
        VARCHAR status
        Integer store_id
        VARCHAR order_code
        VARCHAR shipping_location
    }





    SHIPMENT ||--|{ SHIPMENT_ITEM : contains

    SHIPMENT_ITEM {
        Integer id PK
        Integer shipment_id FK
        Integer store_id
        Integer quantity
        VARCHAR product_code
    }

    SHIPMENT_ITEM }|--|| STORE : is_located_at
    SHIPMENT }|--|| STORE : is_located_at


    STORE {
        Integer id PK
        Integer store_code
        VARCHAR location
    }
```

## 6. Coupons Service API

Check out the full details here 👉🏻 [Coupons Service API README file.](https://github.com/Null-Pointer-Squad/CouponsServiceAPI)

## 7. Store Service

The Store Service is a key part of our e-commerce platform, focused on managing all store operations, stock inventory, and stock history. (we are using this system to simulate the shipping management process in our e-commerce platform)

Check out the full details here 👉🏻 [Store Service README file.](https://github.com/Null-Pointer-Squad/store_service)

and here is the ERD for the database used in this service:

```mermaid
erDiagram
    store {
        VARCHAR code PK
        VARCHAR name
        VARCHAR locatoin
        VARCHAR phone_number
    }


    stock {
        VARCHAR code PK
        VARCHAR store_code FK
        VARCHAR product_code 
        Integer quantity
    }

    stock_history {
        VARCHAR code PK
        VARCHAR store_code FK
        VARCHAR product_code
        VARCHAR action
        TIMESTAMP action_date
        Integer previous_quantity
        Integer new_quantity
    }

    store ||..o{ stock : has
    store ||..o{ stock_history : has
```

---

> Questions? Here’s how to reach us: [Notion](https://muhammad-saad-01.notion.site/Leave-your-comment-e47baf8aed714e44813bcf7d15a9589e?pvs=4)
