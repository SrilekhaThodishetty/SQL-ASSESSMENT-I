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
