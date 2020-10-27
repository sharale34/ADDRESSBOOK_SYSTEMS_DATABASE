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
```DELETE FROM address_book WHERE firstName='K L';```

### View address book
```SELECT * FROM address_book;```

## UC6 - Ability to Retrieve Person belonging to a City or State
### Contact of person belonging to particular city
```SELECT * FROM address_book WHERE City='Chennai';```

### Contact of person belonging to particular state
```SELECT * FROM address_book WHERE State='Tamil Nadu';```

## UC7 - Ability to understand the size of address book by City and State
### Count Contacts by City and State
```SELECT City, COUNT(firstName) FROM address_book GROUP BY City;```

### Count Contacts by City and State
```SELECT State, COUNT(firstName) FROM address_book GROUP BY State;```

## UC8 - Ability to retrieve entries sorted alphabetically by Person’s name for a given city
### For a given city, sort contacts in alphabetical order
```SELECT * FROM address_book WHERE city='Chennai' ORDER BY firstName;```

## UC9 - Alter Address Book to add Name and Type
```
ALTER TABLE address_book ADD address_book_name VARCHAR(20) NOT NULL;
ALTER TABLE address_book ADD Type VARCHAR(20) NOT NULL;
DESCRIBE address_book;
UPDATE address_book SET address_book_name='IPLT20' , Type='friends' WHERE firstName='M S';
UPDATE address_book SET address_book_name='IPLT20', Ttype='family' WHERE firstName='Virat';
UPDATE address_book SET address_book_name='IPLT20', Type='profession' WHERE firstName='Rohit';
SELECT * FROM address_book;
```
## UC10 - Count Person in Address Book by Type
```SELECT Type, COUNT(firstName) FROM address_book GROUP BY Type;```

## UC11 - Ability to add person to both Friend and Family
```
INSERT INTO address_book(firstName,lastName,Address,City,State,Zip,Phone,Email,Type,AddressBookName) VALUES
    -> ('David','Warner','Alwal','Hyderabad','Telangana',500010,949123455,'davidbhai@gmail.com','Family','IPLT20'),
    -> ('Shreyas','Iyer','Karol Bagh','Delhi','Delhi',400125,9874651232,'shreyas@gmail.com','Friends','IPLT2O');
```
