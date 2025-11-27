# Experiment 6: Joins

## AIM
To study and implement different types of joins.

## THEORY

SQL Joins are used to combine records from two or more tables based on a related column.

### 1. INNER JOIN
Returns records with matching values in both tables.

**Syntax:**
```sql
SELECT columns
FROM table1
INNER JOIN table2
ON table1.column = table2.column;
```

### 2. LEFT JOIN
Returns all records from the left table, and matched records from the right.

**Syntax:**

```sql
SELECT columns
FROM table1
LEFT JOIN table2
ON table1.column = table2.column;
```
### 3. RIGHT JOIN
Returns all records from the right table, and matched records from the left.

**Syntax:**

```sql
SELECT columns
FROM table1
RIGHT JOIN table2
ON table1.column = table2.column;
```
### 4. FULL OUTER JOIN
Returns all records when there is a match in either left or right table.

**Syntax:**

```sql
SELECT columns
FROM table1
FULL OUTER JOIN table2
ON table1.column = table2.column;
```

**Question 1**
--
<img width="1250" height="713" alt="image" src="https://github.com/user-attachments/assets/6d016414-ccb1-4d07-9d68-38bf9ceac1a2" />


```sql
select p.* from patients p inner join test_results t on p.patient_id=t.patient_id 
where t.test_name in ('Blood Test', 'Blood Pressure') and t.result not like '%Normal%';
```

**Output:**

<img width="1284" height="495" alt="image" src="https://github.com/user-attachments/assets/4ac4fd3c-e04c-47a4-bbe9-a1da79bd0974" />


**Question 2**
---
<img width="1229" height="500" alt="image" src="https://github.com/user-attachments/assets/5648c1b3-93e7-44df-933a-91b769c4ed67" />


```sql
select s.name, c.cust_name, c.city, c.grade, c.salesman_id from salesman s left join customer c on s.salesman_id=c.salesman_id;

```

**Output:**

<img width="1243" height="837" alt="image" src="https://github.com/user-attachments/assets/d757e5c7-5331-4d19-8993-a8e3c34f8739" />


**Question 3**
---
<img width="1253" height="614" alt="image" src="https://github.com/user-attachments/assets/5deac82f-5e18-4c2c-8ff2-e00805c72d81" />


```sql
select c.cust_name as "Customer Name", c.city, s.name as "Salesman", s.commission from customer c inner join salesman s on c.salesman_id=s.salesman_id;
```

**Output:**

<img width="1277" height="844" alt="image" src="https://github.com/user-attachments/assets/b1c21bdf-200a-4c3e-a9b6-00988bb4fa41" />


**Question 4**
---
<img width="1250" height="775" alt="image" src="https://github.com/user-attachments/assets/ca20ce3c-e652-4116-bc0c-a9eb8073c1bd" />
<img width="1278" height="712" alt="image" src="https://github.com/user-attachments/assets/9be1dee6-e9c8-4f9f-ae9d-c9cef14cc95b" />


```sql
select o.ord_no, o.purch_amt, o.ord_date, c.cust_name, c.city as "customer_city", c.grade, s.name as "salesman_name", s.city as "salesman_city", commission
from orders o
inner join customer c on o.customer_id=c.customer_id
inner join salesman s on o.salesman_id=s.salesman_id;
```

**Output:**

<img width="1274" height="785" alt="image" src="https://github.com/user-attachments/assets/ea9541e7-7533-42bc-a011-747dfdee8e4f" />


**Question 5**
---
<img width="1269" height="395" alt="image" src="https://github.com/user-attachments/assets/c0075705-9f1a-4a80-8e37-d49711aac330" />


```sql
select c.* from customer c left join orders o on c.customer_id=o.customer_id where o.ord_date between '2012-08-01' and '2012-08-30';
```

**Output:**

<img width="1267" height="563" alt="image" src="https://github.com/user-attachments/assets/f6c4e336-9b32-448f-9711-7cbf96a085f4" />


**Question 6**
---
<img width="1247" height="778" alt="image" src="https://github.com/user-attachments/assets/239d5903-8620-4372-a5e1-5495d32ad572" />


```sql
select p.first_name, p.last_name from patients p inner join surgeries s on p.patient_id=s.patient_id where s.surgery_date between  '2024-01-01' and '2024-01-31';
```

**Output:**

<img width="769" height="469" alt="image" src="https://github.com/user-attachments/assets/a9170fd4-5b09-4881-ab95-a0ae159c4cd7" />


**Question 7**
---
<img width="1235" height="768" alt="image" src="https://github.com/user-attachments/assets/d14d8c6a-b799-48bf-b888-79dc705d5e9a" />

```sql
select o.ord_no, o.purch_amt, c.cust_name, c.city from orders o inner join customer c on o.customer_id=c.customer_id where o.purch_amt between 500 and 2000;
```

**Output:**

<img width="1271" height="568" alt="image" src="https://github.com/user-attachments/assets/317f5190-fff1-43db-9c9d-7bf0a76bdd34" />


**Question 8**
---
<img width="1252" height="811" alt="image" src="https://github.com/user-attachments/assets/c9f86786-2bfe-45ad-a4ca-e8cc5e9b9dba" />


```sql
select p.*, d.specialization as "doctor_specialization" from patients p inner join doctors d on p.doctor_id=d.doctor_id;
```

**Output:**

<img width="1266" height="650" alt="image" src="https://github.com/user-attachments/assets/279cb0cf-3389-4e22-a1aa-bb63d1068840" />


**Question 9**
---
<img width="1224" height="780" alt="image" src="https://github.com/user-attachments/assets/69b703b4-db62-4918-a649-a50e36299a0c" />
<img width="1050" height="725" alt="image" src="https://github.com/user-attachments/assets/dcabdfdf-bdc1-4feb-9d7b-258555302c11" />


```sql
select o.ord_no, o.ord_date, o.purch_amt, c.cust_name as "Customer Name", c.grade, s.name as "Salesman", s.commission 
from orders o
inner join customer c on o.customer_id=c.customer_id
inner join salesman s on o.salesman_id=s.salesman_id;
```

**Output:**

<img width="1303" height="788" alt="image" src="https://github.com/user-attachments/assets/75751c04-35f2-44fc-bf29-618048bd8247" />


**Question 10**
---
<img width="1211" height="755" alt="image" src="https://github.com/user-attachments/assets/a5cf3d31-bc05-4201-864d-c341f683c00d" />
<img width="1002" height="709" alt="image" src="https://github.com/user-attachments/assets/3dc737c0-4b39-47cd-b5cc-ad371b32ce76" />


```sql
select c.cust_name, c.city, o.ord_no, o.ord_date, o.purch_amt as "Order Amount", s.name, s.commission 
from customer c 
left join orders o on c.customer_id=o.customer_id
left join salesman s on c.salesman_id=s.salesman_id;
```

**Output:**

<img width="1276" height="790" alt="image" src="https://github.com/user-attachments/assets/f01d9a80-a0e7-4031-886b-4cdea54595e6" />



## RESULT
Thus, the SQL queries to implement different types of joins have been executed successfully.
