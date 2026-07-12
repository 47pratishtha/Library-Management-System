# Library Management System
A simple Python-based Library Management System that uses MySQL to store books, members, issues, and purchases. The program is a console/IDLE-run script (Sourcecode.py) that shows a menu for library operations.
## Features (menu options)
1. Add Book
2. View Books
3. Search Book by ID
4. Search Book by Name
5. Update Shelf
6. Delete Book
7. View Books by Shelf
8. Add Member
9. View Members
10. Issue Book
11. Update available books
12. Extend Return Date
13. View Issued Books
14. View Overdue Books
15. Calculate Fine
16. Fine Report
17. Purchase Books
18. View Purchases
19. Library Summary
20. Top Borrowed Books
21. Exit
## Prerequisites
- Python 3.7+ (IDLE optional)
- MySQL server
- Python package: mysql-connector-python
Install connector:
```
pip install mysql-connector-python
```
## Database setup (used by Sourcecode.py)
Run these SQL commands in MySQL (database name used by the code is `libraryy`):
```sql
CREATE DATABASE libraryy;
USE libraryy;
CREATE TABLE books_details(
  bid INT(10),
  title VARCHAR(20),
  author VARCHAR(20),
  genre VARCHAR(20),
  total INT(200),
  avail INT(200),
  shelf VARCHAR(30)
);
CREATE TABLE member_details(
  mid INT(10),
  name VARCHAR(20),
  phone INT(10)
);
CREATE TABLE issue_details(
  iid INT(10),
  idate DATE,
  rdate DATE,
  bid INT(10),
  mid INT(10)
);
CREATE TABLE purchases(
  purchase_id INT(7) PRIMARY KEY NOT NULL,
  book_id INT(5),
  copies_purchased INT(3),
  purchase_date DATE,
  vendor VARCHAR(20)
);
```
Keep these table names and columns unless you also update the code.
## Configuration
Create a `config.py` or set environment variables for DB credentials. Example `config.py` used for this project:
```py
DB_CONFIG = {
  'host': 'localhost',
  'user': 'root',
  'password': '',
  'database': 'libraryy'
}
```
Or use the connection snippet as in Sourcecode.py:
```py
import mysql.connector as my
mycon = my.connect(host='localhost', user='root', password='', database='libraryy')
mycur = mycon.cursor()
```
## Running the project
- Using IDLE: open `Sourcecode.py` in IDLE and press Run → Run Module (F5). The menu will appear.
- From terminal: run `python Sourcecode.py` (replace with your entry filename if different).
- 
## Usage (quick)
1. Ensure MySQL server is running and `libraryy` exists with the tables above.
2. Update DB credentials in `config.py` or at the top of `Sourcecode.py`.
3. Run the script and follow the on-screen menu prompts.
4. 
## Manual tests (examples)
- Add Book → View Books to confirm entry.
- Add Member → View Members to confirm.
- Issue Book → View Issued Books and verify `avail` decreased.
- Extend Return Date / View Overdue Books / Calculate Fine.
- Purchase Books → View Purchases and confirm stock increment.
- 
## Troubleshooting
- "Access denied" from MySQL: check DB user/password and host.
- "ModuleNotFoundError: mysql.connector": run `pip install mysql-connector-python`.
- If using IDLE, run pip from the same Python installation that IDLE uses.
- 
## License
This project has no license. All rights reserved.

## Author
Pratishtha
