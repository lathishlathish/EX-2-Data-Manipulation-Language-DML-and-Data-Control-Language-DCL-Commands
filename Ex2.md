# EX 2 Data Manipulation Language (DML) Commands and built in functions in SQL
## AIM:
To create a manager database and execute DML queries using SQL.


## DML(Data Manipulation Language)
<div align="justify">
The SQL commands that deal with the manipulation of data present in the database belong to DML or Data Manipulation Language and this includes most of the SQL statements. It is the component of the SQL statement that controls access to data and to the database. Basically, DCL statements are grouped with DML statements.
</div>

## List of DML commands: 
<div align="justify">
INSERT: It is used to insert data into a table.<br>
UPDATE: It is used to update existing data within a table.<br>
DELETE: It is used to delete records from a database table.<br>
</div>

## Create the table as given below:
```sql
create table manager(enumber number(6),ename char(15),
salary number(5),commission number(4),
annualsalary number(7),Hiredate date,designation char(10),
deptno number(2),reporting char(10));
```
## insert the following values into the table
```sql
insert into manager values(7369,'Aarik',2500,500,30000,
'30-June-81','clerk',10,'John');
insert into manager values(7839,'Riyaz',3000,400,36000,
'1-Jul-82','manager',null,'Khan');
insert into manager values(7934,'Zayn',3500,300,42000,
'1-May-82','manager',30,NULL);
insert into manager values(7788,'Sam',4000,0,48000,
'12-Aug-82','clerk',50,'Joel');
```

### Q1) Update all the records of manager table by increasing 10% of their salary as bonus.

### QUERY:
```
UPDATE manager
SET salary = salary + (salary * 0.10),
annualsalary = annualsalary + (annualsalary * 0.10);
```
### OUTPUT:
![db2 1](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/41d05f31-7ad3-4895-9d4f-6cc94bc302be)

### Q2) Delete the records from manager table where the salary less than 2750.

### QUERY:
```
DELETE FROM manager WHERE salary < 2750;
```
### OUTPUT:
![db2 0](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/c81ee338-384f-4b6a-b3de-578c303b3fb9)

### Q3) Display each name of the employee as “Name” and annual salary as “Annual Salary” (Note: Salary in emp table is the monthly salary)

### QUERY:
```
SELECT ename AS "Name", salary * 12 AS "Annual Salary"
FROM manager;
```
### OUTPUT:
![db2 2](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/053aaa01-1a30-4531-996a-41fe4a364430)

### Q5)	List the names of Clerks from emp table.
### QUERY:
```
SELECT ename from manager where designation='clerk';
```
### OUTPUT:
![db2 3](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/84563f22-1f95-442f-855a-d996b00a1df8)


### Q6)	List the names of employee who are not Managers.
### QUERY:
```
SELECT ename from manager where designation!='manager';
```
### OUTPUT:
![db2 3](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/b5e87b50-9fb3-4491-9e12-9d050f926198)


### Q7)	List the names of employees not eligible for commission.

### QUERY:
```
SELECT ename from manager where commission=0;
```
### OUTPUT:
![db2 4](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/3ed7c6ea-d9f2-4f86-86d4-a3055f9751fb)


### Q8)	List employees whose name either start or end with ‘s’.

### QUERY:
```
SELECT ename
FROM manager
WHERE ename LIKE 'S%' OR ename LIKE '%s';
```
### OUTPUT:
![db2 4](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/96734473-2ae0-4998-b61f-c105f92780e4)


### Q9) Sort emp table in ascending order by hire-date and list ename, job, deptno and hire-date.
### QUERY:
```
select ename,designation,deptno,Hiredate from manager
order by Hiredate asc;
```

### OUTPUT:
![db2 5](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/ee902495-0a02-41d3-bd96-34ee6f6df992)


### Q10) List the Details of Employees who have joined before 30 Sept 81.

### QUERY:
```
SELECT *
FROM manager
WHERE Hiredate < TO_DATE('1981-09-30', 'YYYY-MM-DD');
```

### OUTPUT:
![db2 6](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/35948f01-a00a-4041-b8c9-041af22b403c)


### Q11)	List ename, deptno and sal after sorting emp table in ascending order by deptno and then descending order by sal.

### QUERY:
```
select ename,deptno,salary from manager order by deptno asc;
select ename,deptno,salary from manager order by salary desc;
```

### OUTPUT:
![db2 7](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/2b12925f-d7ed-4e49-a372-dbd15b0f1480)

### Q12) List the names of employees not belonging to dept no 30,40 & 10

### QUERY:
```
select ename from manager where deptno not in (10,30,40);
```
### OUTPUT:
![db2 3](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/16a7ef15-e62e-4784-a6ba-789266482439)

### Q13) Find number of rows in the table EMP

### QUERY:
```
select count(*) from manager;
```

### OUTPUT:
![db2 8](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/b9153165-bbb6-409c-aafd-c8bf674873bb)


### Q14) Find maximum, minimum and average salary in EMP table.

### QUERY:
```
select ename ,salary,annualsalary from manager
where salary = (select max(salary) from manager);

select ename ,salary,annualsalary from manager
where salary = (select min(salary) from manager);

select avg(salary) from manager;
```

### OUTPUT:
![db2 9](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/5ed33a58-45af-4026-9aad-d8a241f3c8df)


### Q15) List the jobs and number of employees in each job. The result should be in the descending order of the number of employees.

### QUERY:
```
SELECT designation, COUNT(*) AS "Number of Employees"
FROM manager
GROUP BY designation
ORDER BY COUNT(*) DESC;
```

### OUTPUT:
![db2 10](https://github.com/Brindha77/EX-2-Data-Manipulation-Language-DML-and-Data-Control-Language-DCL-Commands/assets/118889143/84094e10-fff3-47c3-94e0-9d67121a7305)

### RESULT:
Thus, Manager database is created and DML queries such as insertion, updation, deletion are executed using SQL.
