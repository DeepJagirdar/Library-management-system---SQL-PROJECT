# Library-management-system---SQL-PROJECT

Description: Create a database for a library system to manage books, authors, members, and borrowing records.
Skills Demonstrated:
Creating tables for books, authors, customers, and loans.
Implementing relationships between tables (e.g., many-to-many relationships for books and authors).
Writing queries to manage book inventory, track borrowed books, and generate overdue notices.

Here is the code of the project in MySQL Workbench:

create database library_management;

use library_management;

create table books(
	book_id int primary key,
    book_name varchar(50),
    author varchar(50),
    year_published int,
    genre varchar(50)
);
ALTER TABLE customer 
MODIFY COLUMN phone_number VARCHAR(15);
create table customer(
	customer_id int primary key,
    first_name varchar(50),
    last_name varchar(50),
    email varchar(100),
    phone_number varchar(15)
);

create table loan(
	loan_id int primary key,
    book_id int,
	customer_id int,
    loan_date date,
    return_date date,
    foreign key (book_id) references books(book_id),
    foreign key (customer_id) references customer(customer_id)
    
);

ALTER TABLE Books MODIFY COLUMN year_published INT;

insert into books(book_id,book_name,author,year_published,genre) values
(4,'A Christmas Carol','Charles Dickens', 1843,'ghost story'),
(8,'The Secret','Rhonda Byrne', 2006,'Spiritual'),
(3,'Harry Potter and the Chamber of Secrets','J K Rowling', 1998,'Fantacy literature'),
(7,'The Great Gatsby','F.Scott Fitzberg', 1925,'Fiction'),
(5,'1984','George Orwell', 1949,'Dystopian');

select * from books;

update customer set phone_number= '123-789-4567' where customer_id='1';

insert into customer(customer_id,first_name,last_name,email,phone_number) values
(1,'John','Hastings', 'johnhastings@example.com','123-789-4567'),
(2,'James','Blunt', 'james@example.com','786-234-6987'),
(3,'Daniel','Short', 'daniel@example.com','435-654-9976'),
(4,'Alexander','Taylor', 'alextaylor@example.com','654-324-6785'),
(5,'Shaun','Astle', 'sastle@example.com','213-435-6754');

select * from customer;

insert into loan(loan_id,book_id,customer_id,loan_date,return_date) values 
(1,3,2,'2024-01-23','2024-02-04'),
(2,4,5,'2024-01-15','2024-02-07'),
(3,5,3,'2024-02-06','2024-02-26'),
(4,7,1,'2024-04-21','2024-05-10'),
(5,8,4,'2024-05-20','2024-06-05');

select * from loan;

 

select customer_id from loan where book_id='7';
