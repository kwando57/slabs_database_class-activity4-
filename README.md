# AUTHOR:Kwandokuhle


1.1 Database Purpose

The purpose of the Library Management System database is to store and organise information about books, authors, library members and borrowing activities. It aims to maintain accurate records and make library information easy to manage and access.

1.2 Table Separation

1. Books: Stores information about books available in the library.
2. Members: Stores information about registered library members.
3. Borrowings: Records books borrowed and returned by library members.

1.3 Fields & Primary Keys

member_id| SERIAL
first_name| VARCHAR(50)
last_name| VARCHAR(50)
email| VARCHAR(100)
phone| VARCHAR(20)
address| VARCHAR(150)



postgres=# CREATE DATABASE library_db;
CREATE DATABASE
postgres=# \c library_db
You are now connected to database "library_db" as user "postgres".
library_db=# CREATE TABLE authors(
library_db(# author_id SERIAL PRIMARY KEY,
library_db(# author_name VARCHAR(100)
library_db(# );
CREATE TABLE
library_db=# CREATE TABLE books(
library_db(# CREATE TABLE books (
library_db(#     book_id SERIAL PRIMARY KEY,
library_db(#     title VARCHAR(150),
library_db(#     published_year INT,
library_db(#     author_id INT REFERENCES authors(author_id)
library_db(# );
library_db(# CREATE TABLE books (
library_db(# book_id SERIAL PRIMARY KEY,
library_db(# title VARCHAR(150),
library_db(# published_year INT,
library_db(# author_id INT REFERENCES authors(author_id)
library_db(# );
library_db(# CREATE TABLE books (
library_db(#     book_id SERIAL PRIMARY KEY,
library_db(#     title VARCHAR(150),
library_db(#     published_year INT,
library_db(#     author_id INT REFERENCES authors(author_id)
library_db(# );
library_db(# \dt
           List of tables
 Schema |  Name   | Type  |  Owner
--------+---------+-------+----------
 public | authors | table | postgres
(1 row)


library_db(# CREATE TABLE books(
library_db(# book_id SERIAL PRIMARY KEY,
library_db(# title VARCHAR(150),
library_db(# published_year INT,
library_db(# author_id INT REFERENCES authors(author_id)_id)
library_db(# );
ERROR:  syntax error at or near "CREATE"
LINE 2: CREATE TABLE books (
        ^
library_db=# CREATE TABLE books (
library_db(#     book_id SERIAL PRIMARY KEY,
library_db(#     title VARCHAR(150),
library_db(#     published_year INT,
library_db(#     author_id INT REFERENCES authors(author_id)
library_db(# );
CREATE TABLE
library_db=# \dt
           List of tables
 Schema |  Name   | Type  |  Owner
--------+---------+-------+----------
 public | authors | table | postgres
 public | books   | table | postgres
(2 rows)


library_db=# INSERT INTO authors (author_name)VALUES
library_db-# ('Kwandokuhle'),
library_db-# ('Nsuku'),
library_db-# ('Koketso),
library_db'# ('Lemart);
ERROR:  syntax error at or near "Lemart"
LINE 5: ('Lemart);
          ^
library_db=# INSERT INTO authors (author_name)VALUES
library_db-# ('Kwandokuhle'),
library_db-# ('Nsuku'),
library_db-# ('Koketso'),
library_db-# ('Lemart');
INSERT 0 4
library_db=# SELECT * FROM authors;
 author_id | author_name
-----------+-------------
         1 | Kwandokuhle
         2 | Nsuku
         3 | Koketso
         4 | Lemart


library_db=# INSERT INTO books (title, published_year, author_id)
library_db-# VALUES
library_db-# ('The wife', 2022, 1),
library_db-# ('Positive thinking, 2020, 2),
library_db'# ('One day', 2024, 3),
library_db'# ('Things Fall Apart', 2025, 4);
library_db'# INSERT INTO books (title, published_year, author_id) VALUES
library_db'# ('The wife', 2022, 1),
library_db'# ('Positive thinking, 2020, 2),
library_db-# ('One day', 2024, 3),
library_db-# ('Things Fall Apart', 2025, 4);
ERROR:  syntax error at or near "One"
LINE 5: ('One day', 2024, 3),
          ^
library_db=# SELECT * FROM books;
 book_id | title | published_year | author_id
---------+-------+----------------+-----------
(0 rows)


library_db=# INSERT INTO books (title, published_year, author_id)
library_db-# VALUES
library_db-# ('The Wife', 2022, 1),
library_db-# ('Positive Thinking', 2020, 2),
library_db-# ('One Day', 2024, 3),
library_db-# ('Things Fall Apart', 2025, 4);
INSERT 0 4
library_db=# SELECT * FROM books;
 book_id |       title       | published_year | author_id
---------+-------------------+----------------+-----------
       1 | The Wife          |           2022 |         1
       2 | Positive Thinking |           2020 |         2
       3 | One Day           |           2024 |         3
       4 | Things Fall Apart |           2025 |         4
(4 rows)


library_db=# SELECT
library_db-#     b.book_id,
library_db-#     b.title,
library_db-#     b.published_year,
library_db-#     a.author_name
library_db-# FROM books b
library_db-# JOIN authors a
library_db-# ON b.author_id = a.author_id;
 book_id |       title       | published_year | author_name
---------+-------------------+----------------+-------------
       1 | The Wife          |           2022 | Kwandokuhle
       2 | Positive Thinking |           2020 | Nsuku
       3 | One Day           |           2024 | Koketso
       4 | Things Fall Apart |           2025 | Lemart
(4 rows)


library_db=# \q


