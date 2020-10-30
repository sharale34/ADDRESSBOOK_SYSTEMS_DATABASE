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

## UC13 - Ensure all retrieve queries done are working with new table structure
### Drop table address_book
``` DROP TABLE address_book;```

### Creating table Address_Book_Dictionary
```
CREATE TABLE Address_Book_Dictionary
    -> (
    -> Address_Book_Name VARCHAR(200) NOT NULL PRIMARY KEY,
    -> Address_Book_Type VARCHAR(150) NOT NULL
    -> );
```
### Creating table Contacts
```
CREATE TABLE contacts
    -> (
    -> firstName    varchar(150) NOT NULL,
    -> lastName     varchar(150) NOT NULL,
    -> Address_Book_Name VARCHAR(200) NOT NULL,
    -> FOREIGN KEY (Address_Book_Name) REFERENCES Address_Book_Dictionary (Address_Book_Name),
    -> Address      varchar(200) NOT NULL,
    -> City         varchar(200) NOT NULL,
    -> State        varchar(200) NOT NULL,
    -> Zip          int(10)      NOT NULL,
    -> Phone_Number int(15)      NOT NULL,
    -> Email        varchar(300) NOT NULL,
    -> PRIMARY KEY  (firstName,lastName)
    -> );
```
### Inserting records into Address_Book_Dictionary table
```
INSERT INTO Address_Book_Dictionary VALUES
    -> ('Personal','Family'),
    -> ('Corporate','Professional'),
    -> ('Casual','Friends');
```

### Inserting records into Contacts
```
INSERT INTO contacts VALUES
    -> ('M S','Dhoni','Casual','Balaji nagar','Chennai','Tamil Nadu',500001,9440293758,'msdhoni@gmail.com'),
    -> ('Virat','Kohli','Personal','Shanthi nagar','Bangalore','Karnataka',500050,9494118273,'vkohli@gmail.com'),
    -> ('Rohit','Sharma','Corporate','Anderi','Mumbai','Maharashtra',500010,7207020464,'rohit@gmail.com');
```
### Ability to Retrieve Person belonging to a City or State
```
SELECT * FROM contacts WHERE City='Bangalore';
SELECT * FROM contacts WHERE State='Maharashtra';
```
### Ability to understand the size of address book by City and State
```
SELECT city,COUNT(city) FROM contacts GROUP BY city;
SELECT state,COUNT(state) FROM contacts GROUP BY state;
```
### Ability to retrieve entries sorted alphabetically by Person’s name for a given city
```
SELECT * FROM contacts WHERE city='Chennai' ORDER BY firstName;
```
### Ability to get number of contact persons(count by type)
```
SELECT a.Address_Book_Type,COUNT(a.Address_Book_Type) FROM Address_Book_Dictionary a LEFT JOIN contacts c ON c.Address_Book_Name=a.Address_Book_Name GROUP BY a.Address_Book_Type;
```
