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

## UC3 - Insert new contacts to address book
```
INSERT INTO address_book(firstName,lastName,Address,City,State,Zip,Phone,Email) VALUES
    -> ('Virat','Kohli','Shivaji Nagar','Bangalore','Karnataka',560001,9494118273,'virat@gmail.com'),
    -> ('Rohit','Sharma','Anderi','Mumbai','Maharashtra',400001,7207020464,'rohit@gmail.com');
    -> ('M S','Dhoni','Balaji Nagar','Chennai','Tamil Nadu',600001,9440293758,'msdhoni@gmail.com');
    -> ('K L','Rahul','Sarojini Bagh','Chandigarh','Punjab',430001,8341127689,'rahul@gmail.com');
```
### View address book
```SELECT * FROM address_book;```

## UC4 - Ability To Edit Existing Contact with Name
### Editing contact for given name
```UPDATE address_book SET phone=9491041559 WHERE firstName='K L';```

### View address book
```SELECT * FROM address_book;```

## UC5 - Ability To Delete Existing Contact with Name
```DELETE FROM address_book WHERE firstName='K L';

### View address book
```SELECT * FROM address_book;```
