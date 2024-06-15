## SQL Assessment

**Database Tables:**

1. **Customers:**

```sql
CREATE TABLE Customers(
customer_id INT PRIMARY KEY,
first_name VARCHAR(50) NOT NULL,
last_name VARCHAR(50) ,
DOB DATE ,
email NVARCHAR(200) UNIQUE,
phone_number INT UNIQUE,
address VARCHAR(100)
);
```

2. **Accounts:**

```sql
CREATE TABLE Accounts(
account_id INT PRIMARY KEY,
customer_id INT,
account_type CHAR(15),
balance DECIMAL(10, 2),
FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);
```

3. **Transactions:**

```Sql
CREATE TABLE Transactions(
transaction_id VARCHAR(20) PRIMARY KEY ,
account_id INT ,
transaction_type CHAR(15),
amount DECIMAL(10, 2),
transaction_date DATETIME
FOREIGN KEY (account_id) REFERENCES Accounts(account_id)
);
```
