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
phone_number VARCHAR(50) UNIQUE,
address VARCHAR(100)
);
```

2. **Accounts:**

```sql
CREATE TABLE Accounts(
account_id INT PRIMARY KEY,
customer_id INT,
account_type VARCHAR(15),
balance DECIMAL(10, 2),
FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);
```

3. **Transactions:**

```Sql
CREATE TABLE Transactions(
transaction_id VARCHAR(20) PRIMARY KEY ,
account_id INT ,
transaction_type VARCHAR(15),
amount DECIMAL(10, 2),
transaction_date DATETIME
FOREIGN KEY (account_id) REFERENCES Accounts(account_id)
);
```

4. **InterestRates:**

```sql
CREATE TABLE InterestRates(
interest_rate_id INT PRIMARY KEY ,
account_type VARCHAR(15) ,
interest_rate DECIMAL(5,2),
);

```

5. **Branches:**

```sql
CREATE TABLE Branches(
branch_id INT PRIMARY KEY ,
branch_name VARCHAR(15) ,
address VARCHAR(150),
);
```

**Questions:**

1. Insert at least 10 sample records into each of the following tables: `Customers`, `Accounts`, `Transactions`, `InterestRates`, `Branches`.

```sql
INSERT INTO Customers
VALUES(1,'Arjun','Patel','2002-02-12','arjun@gmail.com',9876543210,'Hyderabad'),
      (2,'Nidhi','Shah','2000-11-15','nidhi@gmail.com',8876543210,'Mumbai'),
	  (3,'Meera','Iyer','1998-03-05','meera@gmail.com',9866543210,'chennai'),
	  (4,'Riya','Sharma','1994-05-16','riya@gmail.com',9456543215,'Bangalore'),
	  (5,'Aarav','Gupta','2002-04-12','aarav@gmail.com',7876543210,'Hyderabad'),
	  (6,'Rohan','Mehta','2001-10-12','rohan@gmail.com',9676543213,'Bangalore'),
	  (7,'Sanjana','Shah','2002-09-21','sanjana@gmail.com',6376543217,'Pune'),
	  (8,'Ishita','Tiwari','1985-07-25','ishita@gmail.com',7876543218,'Hyderabad'),
	  (9,'Aaradhya','Sharma','1993-06-22','aaradhya@gmail.com',9276543216,'Ahmedabad'),
	  (10,'Avani','Singhania','1968-12-16','avani@gmail.com',9176543217,'Kolkata');
```

```sql

SELECT * FROM Customers;

```

![alt text](images\image.png)

```sql
INSERT INTO Accounts
VALUES (10211, 1, 'current', 25000.00),
       (10212, 2, 'Savings', 50000.00),
       (10213, 3, 'current', 15000.00),
       (10214, 4, 'zero_balance', 3000.00),
       (10215, 5, 'Savings', 37500.00),
       (10216, 6, 'current', 40000.00),
       (10217, 7, 'zero_balance', 6000.00),
       (10218, 8, 'savings', 20000.00),
       (10219, 9, 'zero_balance', 58500.00),
       (10210, 10, 'zero_balance', 58500.00);

```

```sql

SELECT * FROM Accounts;

```

![alt text](images\image-1.png)

```sql

INSERT INTO Transactions
VALUES (123401,10211, 'Deposit', 500.00, '2024-06-01 09:00:00'),
       (123402,10212, 'Withdrawal', 200.00, '2024-06-05 14:30:00'),
       (123403,10213, 'transfer', 1000.00, '2024-06-02 10:15:00'),
       (123404,10214, 'Withdrawal', 300.00, '2024-06-03 11:45:00'),
       (123405,10215, 'transfer', 2000.00, '2024-06-04 13:00:00'),
       (123406,10216, 'Withdrawal', 100.00, '2024-06-06 15:00:00'),
       (123407,10217, 'Deposit', 800.00, '2024-06-07 16:30:00'),
       (123408,10217, 'transfer',1500.00,'2024-06-07 16:30:00'),
       (123409,10219, 'deposit',4000.00,'2024-06-08 17:30:00'),
       (123400,10210,  'withdrawal',5100.00,'2024-06-07 16:30:00');

```

```sql

SELECT * FROM Transactions;

```

![alt text](images\image-2.png)

```sql
INSERT INTO InterestRates
VALUES
(1, 'current', 0.50),
(2, 'Savings', 1.25),
(3, 'zero_balance', 1.00);

```

```sql

SELECT * FROM InterestRates;

```

![alt text](images\image-4.png)

```sql

INSERT INTO Branches
VALUES (12601, 'Banjara Hills', 'Road No. 1, Banjara Hills, Hyderabad'),
       (12602, 'Mount Road', ' 84, Anna Salai, Mount Road, Chennai'),
       (12603, 'Park Street', '31, Park Street, Kolkata'),
       (12604, 'Main Branch', 'Horniman Circle, Fort, Mumbai'),
       (12605, 'Camp ', 'East Street, Camp, Pune'),
       (12606, 'Main Branch', 'Hazratganj Circle, Fort, Bangalore'),
       (12607, 'Ashram Road', 'Nehru Bridge, Ashram Road, Ahmedabad, Bangalore'),
       (12608, 'MI Road Branch ', 'MI Road, Jaipur');
```

```sql

SELECT * FROM Branches;

```

![alt text](images\image-3.png)

2. Write a SQL query to retrieve the name, account type, and email of all customers.

```sql
SELECT concat(first_name,' ',last_name) AS name,account_type,email
FROM Customers
JOIN Accounts
ON Customers.customer_id=Accounts.customer_id;

```

![alt text](images\image-5.png)

3. Write a SQL query to list all transactions along with the corresponding customer.

```sql
SELECT concat(first_name,' ',last_name) AS customer_Name,transactions.*
FROM Transactions
JOIN Accounts
ON Transactions.account_id=Accounts.account_id
JOIN Customers
ON Accounts.Customer_id=Customers.customer_id;
```

![alt text](images\image-6.png)

4. Write a SQL query to increase the balance of a specific account by a certain amount.

```sql
UPDATE Accounts
SET balance = balance + 5000 -- 5000-> certain amount
WHERE account_id = 10215; --10213-> account_id

SELECT * FROM Accounts
WHERE account_id=10215;
```

![alt text](images\image-7.png)

5. Write a SQL query to combine the first and last names of customers as `full_name`.

```sql
SELECT concat(first_name ,' ',last_name) AS full_name
FROM Customers;

UPDATE Accounts
SET balance = balance + 5000 -- 5000-> certain amount
WHERE account_id = 10215;
```

![alt text](images\image-8.png)

6. Write a SQL query to remove accounts with a balance of zero where the account type is savings.

```sql
DELETE FROM ACCOUNTS
WHERE balance = 0 AND account_type like 'savings';

SELECT * FROM Accounts;
```

![alt text](images\image-9.png)

7. Write a SQL query to find customers living in a specific city.

```sql
SELECT * FROM Customers
WHERE address like '<%city_name%>';

SELECT * FROM Customers
WHERE address like '%Hyderabad%';
```

![alt text](images\image-10.png)

8. Write a SQL query to get the account balance for a specific account.

```sql
SELECT * FROM Accounts
WHERE account_id = <account_id>; -- Give account_id;

SELECT account_id,balance FROM Accounts
WHERE account_id = 10211;
```

![alt text](images\image-11.png)

9. Write a SQL query to calculate the interest accrued on savings accounts based on a given interest rate.

```sql
SELECT account_id,balance,interest_rate,(balance*interest_rate/100) AS interest_accured
FROM Accounts
JOIN InterestRates
ON Accounts.account_type=InterestRates.account_type
WHERE Accounts.account_type like 'savings';
```

![alt text](images\image-12.png)

10. Write a SQL query to find the average account balance for all customers.

```sql
SELECT avg(balance) AS avg_balance
FROM Accounts;
```

![alt text](images\image-13.png)

11. Write a SQL query to calculate the average daily balance for each account over a specified period.

```sql
SELECT account_id,avg(daily_balance) AS avg_daily_bal FROM (
                       SELECT account_id, transaction_date,sum(amount) AS daily_balance
                       FROM Transactions
                       WHERE transaction_date BETWEEN '2024-06-01' AND '2024-06-06'
                       GROUP BY  account_id,transaction_date) AS daily_balance
GROUP BY account_id;

```

![alt text](images\image-19.png)

12. Identify accounts with the highest number of transactions ordered by descending order.

```sql
SELECT account_id,count(transaction_id) AS t_count FROM Transactions
GROUP BY account_id
ORDER BY t_count desc;
```

![alt text](images\image-14.png)

13. List customers with high aggregate account balances, along with their account types.

```sql
SELECT concat(first_name,' ',last_name) AS full_name,sum(balance) aggregate_bal,account_type
FROM Customers
JOIN Accounts
ON Customers.customer_id=Accounts.customer_id
GROUP BY Customers.customer_id,first_name,last_name,account_type
ORDER BY aggregate_bal DESC;
```

![alt text](images\image-15.png)

14. Identify and list duplicate transactions based on transaction amount, date, and account.

```sql
---some duplicate data is added
INSERT INTO Transactions
	 VALUES (123411,10211, 'Deposit', 500.00, '2024-06-01 09:00:00'),
                (123412,10212, 'Withdrawal', 200.00, '2024-06-05 14:30:00'),
                (123413,10213, 'transfer', 1000.00, '2024-06-02 10:15:00');
INSERT INTO InterestRates
```

![alt text](images\image-16.png)

```sql
---To get duplicate transactions
Select * from transactions

SELECT t1.account_id,t1.amount,t1.transaction_date FROM Transactions t1
WHERE t1.account_id  IN (SELECT t2.account_id
                         FROM Transactions t2
                         GROUP BY t2.amount ,t2.transaction_date,t2.account_id
                         Having count(*)>1
					 )
GROUP BY t1.account_id, t1.amount, t1.transaction_date;

Select * from transactions
```

![alt text](images\image-17.png)

15. Calculate the total balance for each account type, including a subquery within the SELECT clause.

```sql
SELECT account_type,
                   (SELECT SUM(balance)
                   FROM Accounts
                   WHERE account_type = a.account_type) AS total_balance
FROM Accounts a
GROUP BY account_type;

```

![alt text](images\image-18.png)
