# Library Management System

## Project Description
The **Library Management System** is a SQL-based database project developed to manage library operations efficiently. It stores information about books, authors, categories, and library members. It also manages book issuing, returning, overdue books, and fines using MySQL.

This project demonstrates practical SQL concepts such as table creation, relationships, joins, indexes, stored procedures, triggers, views, and aggregate functions.

## Technologies Used
- **Database:** MySQL
- **Language:** SQL
- **Tool:** MySQL Workbench or MySQL Command Line Client

## Features
- Manage books, authors, and categories.
- Store library member details.
- Track book availability and total copies.
- Issue books to active members.
- Return books and calculate overdue fines.
- Search books by title, author, or category.
- Identify overdue books and active issues.
- Maintain borrowing history.
- Generate library statistics.
- Find the most borrowed books and active members.
- Maintain data integrity using database constraints.

## Database Structure

| Table | Description |
|---|---|
| `authors` | Stores author details. |
| `categories` | Stores book categories. |
| `books` | Stores book information and copy availability. |
| `members` | Stores library member details. |
| `book_issues` | Tracks book issuing, returning, and fines. |

### Database Objects
- **Stored Procedures:** `issue_book`, `return_book`, `search_books`
- **Trigger:** `before_issue_update`
- **Views:** `book_details`, `active_issues`, `overdue_books`
- **Indexes:** Improve the performance of common searches.
- **Constraints:** Primary keys, foreign keys, unique constraints, and check constraints.

## Repository Structure

```text
Library-Management-System/
├── library_management.sql
└── README.md
```

## Installation and Setup

### Step 1: Install MySQL
Install MySQL Server and optionally MySQL Workbench.

### Step 2: Download the Project
Clone the repository:

```bash
git clone <your-github-repository-url>
```

Alternatively, download the repository as a ZIP file.

### Step 3: Open the SQL File
Open `library_management.sql` in MySQL Workbench or another MySQL client.

### Step 4: Execute the Script
Run the SQL script to create the database, tables, indexes, stored procedures, trigger, views, and sample records.

**Important:** The script starts with `DROP DATABASE IF EXISTS library_management;`. Running it again deletes and recreates the database, including its existing data.

## Example Queries

### 1. Display All Books

```sql
USE library_management;
SELECT * FROM books;
```

### 2. Display Complete Book Details

```sql
SELECT * FROM book_details;
```

### 3. Display Available Books

```sql
SELECT title, total_copies, available_copies
FROM books
WHERE available_copies > 0;
```

### 4. Search for Java Books

```sql
CALL search_books('Java');
```

### 5. Display Overdue Books

```sql
SELECT * FROM overdue_books;
```

### 6. Issue a Book

```sql
CALL issue_book(2, 1, 14);
```

This issues book ID `2` to member ID `1` for 14 days, provided the book and member satisfy the validation rules.

### 7. View Book Issue Records

```sql
SELECT * FROM book_issues;
```

### 8. Display Library Statistics

```sql
SELECT
    (SELECT COUNT(*) FROM books) AS book_titles,
    (SELECT SUM(total_copies) FROM books) AS total_copies,
    (SELECT SUM(available_copies) FROM books) AS available_copies,
    (SELECT COUNT(*) FROM members
     WHERE status = 'ACTIVE') AS active_members;
```

## Fine Calculation

The project calculates a fine of **5 units per overdue day** when a book is returned after its due date.

**Formula:**

Fine = Number of Overdue Days × 5

For example, if a book is returned 3 days late, the fine is 15 units.

## Learning Outcomes
- Understanding relational database design.
- Creating tables with primary and foreign keys.
- Using SQL joins and aggregate functions.
- Implementing stored procedures and triggers.
- Creating views for reports.
- Applying constraints and indexes.
- Managing transactions and handling database errors.

## Future Enhancements
- Develop a web interface for librarians and members.
- Add member login and authentication.
- Generate printable reports.
- Add book reservations and renewal functionality.
- Configure fine rates and payment tracking.
- Implement automated backups and improved access control.

## Conclusion
The Library Management System demonstrates how MySQL can organize library data and manage book circulation. It provides a foundation for developing a complete library application with a frontend and backend in the future.

## Author Details
- **Name:** KURUBA CHANDRAMOULI 
- **Domain:** SQL
- **Internship ID:** CITS9354
