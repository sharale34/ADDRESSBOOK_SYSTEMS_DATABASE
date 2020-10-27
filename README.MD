# Welcome to Address Book System Database

## UC1 - Create database for addressbook service
```CREATE DATABASE address_book_service;```

### Go to the database created
```USE address_book_service;```

## UC2 - Create addressbook table with necessary details
```CREATE TABLE address_book
    -> ( firstName    VARCHAR(150) NOT NULL,
    ->   lastName     VARCHAR(150) NOT NULL,
    ->   Address      VARCHAR(200) NOT NULL,
    ->   City         VARCHAR(200) NOT NULL,
    ->   State        VARCHAR(200) NOT NULL,
    ->   Zip          BIGINT(10)   NOT NULL,
    ->   Phone Number INT(15)      NOT NULL,
    ->   Email        VARCHAR(300) NOT NULL,
    ->   PRIMARY KEY  (firstName)
    -> );
```
### Viewing the address book table
```DESCRIBE address_book;```
