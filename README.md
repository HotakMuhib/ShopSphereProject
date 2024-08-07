Project Name: ShopSphere

Overview:
This project represent e-commerce platform, it is designed to provide secure and comprehensive online shopping experience. This project can be used by users and Administrators, offering a wide range of functionalities from product browsing to order management system. This document outlines the technical foundation, features, and endpoint details of ShopSphere, highlighting its microservice architecture and angular based front-end design. 

Technology used:
Backend: Java SpringBoot Spring Data JPA, Spring Security with JWT, Spring Batch
Frontend: Angular and bootstrap,
Database: MySQL

The MicroServices Architecture used:

User service: It takes care of all the user services like registration, authentication and user management, it is integrated with Spring Security for secure authentication. 
Product service: It takes care of product listing and its categories, used Spring Data JPA for database operations.
Cart Service:  It takes care of shopping cart operation, including adding, removing, and updating items in the user cart, basically it is doing all the CRUD operations. 
WishList Service: It takes care of the wishlist of the user, adding product to the wishlist or removing product from the wish list. 
Order Service: It takes care of processing orders, and keeps record of user purchases and order history. 
Discount Service: It takes care of discount codes and coupon application for orders, enhancing the shopping experience. 

config-service: micro project is created where we wired all the projects in the config-server,  and made it a complete project. Config-server includes yml files for all the micro projects. We need to run config-server in order to start our project. 

To run the code :
1: download the whole project 
2: create databases for each project in MySQL workbench
3: start the cofig-server first
4: then all the other micro projects. 
The Commands that have been used to check the endPoints are as follows: 



Checking product endpoints 
1st: register 
POST: localhost:8080/auth/register
Body Json format:
{
    "name": {
        "firstName": "John",
        "lastName": "J"
    },
    
    "address": {
        "city": "Clark",
        "street": "Indian Creek",
        "number": "888",
        "zipcode": 30033
    },
    "email": "john@gmail.com",
    "pass": "77777",
    "phoneNumber": "44444",
    "role": "admin"
}
2nd get the token
POST: localhost:8080/auth/login
Body: 
{
    "email": "john@gmail.com",
    "password": "77777"
}

Registering products
POST: localhost:8080/product/admin/products
Body:
{
    "name": "regular cooker",
    "description": "used",
    "price": "20.98",
    "category": "kitchen ware",
    "imageUrl": "ebay.com/regularCooker"
}
Add token to Auth.

Getting products:
GET: localhost:8080/product/products
Add token

Getting product by id:
GET: localhost:8080/product/products/6 
Need token


Deleting by pid:
DELETE: localhost:8080/product/admin/products/3
Need to provide token

GET: localhost:8080/product/products/categories/1 //getting by categories
localhost:8080/product/products/categories/home

Checking Cart Endpoints
POST: localhost:8080/cart/1/add
Body:
Choose form-data and 
Enter productid as key and value as value
Need to provide token

GET: localhost:8080/cart/1
Getting all the items in the cart

DELETE: localhost:8080/cart/1/remove/1
Need to provide token

POST: localhost:8080/cart/init/1
Adding token

 Checking orders endpoints
POST: localhost:8080/orders/1
Need to provide token

GET: localhost:8080/orders/5
Need to provide token

Checking endpoint for discount
POST: localhost:8080/discount/admin/add
Body:
{
    "saving": 10,
    "code":"July4thSaving"
}
Need to provide auth token

POST: localhost:8080/discount/code?code=July4thSaving
Params
Key = code
Value = July4thSaving

DELETE: localhost:8080/discount/admin/1
Need to provide auth token.
Wishlist endpoints
POST: localhost:8080/wishlist/1?productId=2
Need to provide auth token
Query params
Key = producid 
Value = 2

GET: localhost:8080/wishlist/1
Provide auth token
DELETE: localhost:8080/wishlist/1/remove/1
Auth token


POST: localhost:8080/wishlist/init/2
Provide authorization token
