# SQL_PRACTICE
This SQL project focuses on creating and analyzing an Employee-Department database. It includes data retrieval, filtering, and use of aggregate functions like SUM, AVG, and COUNT. INNER JOIN is used to connect tables and solve real-world queries, improving SQL skills and analytical thinking.

show databases;
use assignment2;
# 1. Create a table named Employees with columns for EmployeeID, FirstName, LastName, BirthDate, HireDate, Salary, and DepartmentID. 
#Set EmployeeID as the Primary Key.

create table Departments(
DepartmentID int primary key,
DepartmentName varchar(50) not null,
Location varchar(255) not null
);

create table Eemployees(
EmployeeID int primary key,
FirstName varchar(50)not null,
LastName varchar(50)not null,
BirthDate date,
HireDate timestamp,
Salary decimal(10,2) not null,
DepartmentID int, foreign key (DepartmentID) references Departments (DepartmentID)
);


# 2. Create a table named Departments with columns for DepartmentID, DepartmentName, and Location. Set DepartmentID as the Primary Key. 
#3. Insert records into the Departments table for departments: HR (New York), IT (San Francisco), Finance (Chicago), and Marketing (Los Angeles).
insert into  Departments ( DepartmentID, DepartmentName, Location)
values( '1' , 'HR', 'New York'),
('2' , 'IT','San Francisco'),('3' , 'Finance', 'Chicago'),('4','Marketing', 'Los Angeles');
 
 
 #4. Insert five records into the Employees table with relevant data for each column. Include at least one record for each department. 
 insert into Eemployees(EmployeeID ,FirstName ,LastName ,BirthDate ,HireDate,Salary ,DepartmentID )
 values(101, 'John', 'Smith', '1985-06-15', '2012-03-01', 75000, 2),
(102, 'Emma', 'Johnson', '1990-09-20', '2016-07-15', 68000, 1),
(103, 'Michael', 'Brown', '1982-11-10', '2010-01-10', 82000, 3),
(104, 'Sophia', 'Davis', '1995-02-25', '2018-05-20', 60000, 4),
(105, 'Daniel', 'Wilson', '1988-12-05', '2014-09-30', 72000, 2);
 
 
#5. Write a query to select all columns for all employees. 
show tables ;
select * from Eemployees;
select * from Departments;

#6. Write a query to select only FirstName, LastName, and Salary from the Employees table. 
select FirstName, LastName, Salary 
from Eemployees;

#7. Write a query to select distinct DepartmentID values from the Employees table. 
select distinct (DepartmentID) from Eemployees;

#8. Write a query to select employees who have a salary greater than 70,000. 
select FirstName, LastName, Salary from Eemployees
where salary >70000;

#9. Write a query to select employees whose FirstName is 'John'. 
select * from Eemployees
where FirstName = 'John';

#10. Write a query to select employees hired between '2010-01-01' and '2015-12-31'. 
select * from Eemployees
where HireDate between '2010-01-01' and '2015-12-31';

#11. Write a query to select employees who belong to the IT or Finance department. 
SELECT *FROM Eemployees
INNER JOIN Departments
ON Eemployees.DepartmentID = Departments.DepartmentID;

#12. Write a query to select employees whose LastName does not start with 'D'.
select *from Eemployees
where LastName not like'D%' ;

 #13. Write a query to select employees who belong to the HR department and have a salary less than 70,000. 
select * from Eemployees e
inner join Departments d
on e. DepartmentID = d. DepartmentID
where DepartmentName= 'HR'
and salary <=70000 ;

#14. Write a query to select employees who were either hired after '2015-01-01' or have a salary greater than 80,000. 
select * from Eemployees
where HireDate =' 2015-01-01-' or salary>= 80000;

#15. Write a query to select employees who do not work in the Marketing department. 
select * from Eemployees e
inner join Departments d
on e.DepartmentID = d.DepartmentID
where d.DepartmentName != 'Marketing';

 
#16. Write a query to find the total salary paid to all employees.
select sum(salary) as Total_slary from Eemployees;
 
#17. Write a query to find the average salary of employees in the IT department. 
select avg(salary) as avg_slary from Eemployees
where DepartmentID ='2';
select * from Departments;

#18. Write a query to find the number of employees in the Finance department. 
select count(*)  as Total_Employees 
from eemployees e
inner join Departments d
on e. DepartmentID = d. DepartmentID
where d. DepartmentName =' Finance';

 
#19. Write a query to find the highest and lowest salary in the company. .
SELECT 
    MAX(Salary) AS HighestSalary,
    MIN(Salary) AS LowestSalary
FROM Employees;



#20. Write a query to find employees who were hired after '2012-01-01' and earn more than 70,000. 
select* from eemployees
where  HireDate >'2012-01-01' and salary>=780000;
