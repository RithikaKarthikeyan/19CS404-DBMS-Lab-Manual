# Experiment 4: Aggregate Functions, Group By and Having Clause

## AIM
To study and implement aggregate functions, GROUP BY, and HAVING clause with suitable examples.

## THEORY

### Aggregate Functions
These perform calculations on a set of values and return a single value.

- **MIN()** – Smallest value  
- **MAX()** – Largest value  
- **COUNT()** – Number of rows  
- **SUM()** – Total of values  
- **AVG()** – Average of values

**Syntax:**
```sql
SELECT AGG_FUNC(column_name) FROM table_name WHERE condition;
```
### GROUP BY
Groups records with the same values in specified columns.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name;
```
### HAVING
Filters the grouped records based on aggregate conditions.
**Syntax:**
```sql
SELECT column_name, AGG_FUNC(column_name)
FROM table_name
GROUP BY column_name
HAVING condition;
```

**Question 1**
--
How many patients have insurance coverage valid in each year?

Sample table:Insurance Table

name               type
-----------------  ----------
InsuranceID        INTEGER
PatientID          INTEGER
InsuranceCompany   TEXT
PolicyNumber       TEXT
PolicyHolder       TEXT
ValidityPeriod     TEXT
```sql
select strftime('%Y',validityperiod) as ValidityYear,count(patientid) as TotalPatients
from Insurance group by ValidityYear;
```

**Output:**

<img width="691" height="367" alt="image" src="https://github.com/user-attachments/assets/002f449b-4539-4d39-a325-bd6c90fbac87" />

**Question 2**
---
How many prescriptions were written by each doctor?


```sql
select DoctorID, count(*) as TotalPrescriptions
from Prescriptions group by DoctorID;
```

**Output:**

<img width="791" height="736" alt="image" src="https://github.com/user-attachments/assets/244daded-1d48-42c6-9420-98cf0868a601" />

**Question 3**
---
How many prescriptions were written in each frequency category (e.g., once daily, twice daily)?


```sql
select Frequency, count(*) as TotalPrescriptions 
from Prescriptions group by Frequency;
```

**Output:**

<img width="761" height="515" alt="image" src="https://github.com/user-attachments/assets/95426fe2-049a-42c7-90f2-0fae5ccde04e" />

**Question 4**
---
Write a SQL query to find the difference between the maximum and minimum price of fruits?
```sql
select MAX(price) - MIN(price) as price_diff
from fruits;
```

**Output:**

<img width="381" height="295" alt="image" src="https://github.com/user-attachments/assets/e4d4e638-2e00-4af1-8587-6fa4c2ab3c73" />

**Question 5**
---
Write a SQL query to find the youngest employee in the company?


```sql
select  name as Employee_Name , MIN(age) as Age
from employee;
```

**Output:**

<img width="592" height="296" alt="image" src="https://github.com/user-attachments/assets/def96a03-4bb6-47d5-aefc-ea37a0b8c7e8" />

**Question 6**
---
Write a SQL query to Calculate the average income of the employees with names starting with 'A': 


```sql
select avg(income) as avg_income from employee where name LIKE 'A%';
```

**Output:**

<img width="407" height="300" alt="image" src="https://github.com/user-attachments/assets/d35be873-7672-442d-bc0d-e1335d968a23" />

**Question 7**
---
Write a SQL query to calculate the total number of working hours of all employees


```sql
select SUM(workhour) as "Total working hours"
from employee1;
```

**Output:**

<img width="507" height="302" alt="image" src="https://github.com/user-attachments/assets/25f55ec7-425c-47a3-ba1a-2a85042a1ff8" />

**Question 8**
---
Write the SQL query that accomplishes the selection of average price for each category from the "products" table and includes only those products where the average price falls between 10 and 15.
```sql
select category_id, AVG(Price) from  products group by category_id having AVG(price) 
between 10 and 15;
```

**Output:**

<img width="577" height="322" alt="image" src="https://github.com/user-attachments/assets/7759df83-37ff-4caf-89da-5038ad961d02" />

**Question 9**
---
Write the SQL query that accomplishes the selection of total number of products for each category from the "products" table, and includes only those products where the minimum category ID is less than 3.
```sql
select category_id,count(product_name) from products
group by category_id
having MIN(category_id) <3;
```

**Output:**
<img width="737" height="352" alt="Screenshot 2026-09-02 124504" src="https://github.com/user-attachments/assets/1600d631-a03d-4815-afaf-9401e5c1dcba" />



**Question 10**
---
Write the SQL query that achieves the selection of product names and the maximum price for each category from the "products" table, and includes only those products where the maximum price is greater than 15.
```sql
select category_id,product_name, price as Price
from products group by category_id having MAX(Price) >15;
```

**Output:**

<img width="817" height="370" alt="image" src="https://github.com/user-attachments/assets/3653d8e3-fc16-401e-a21b-56479f4df8b8" />



## RESULT
Thus, the SQL queries to implement aggregate functions, GROUP BY, and HAVING clause have been executed successfully.
