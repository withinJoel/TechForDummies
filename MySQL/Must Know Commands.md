# Demo
```
select name, id from department;
```

```
select distinct name from department where id > 1;
```

```
select * from department where id > 1;
```

```
select name from department group by name;
```

```
select department from employee group by department;
```


`select employee.age , employee.department from employee where employee.age > 1 and employee.department is not null;

`select employee.age, employee.department from employee where employee.age > 1 or employee.name = 'joel';

`select employee.age from employee where employee.age is not null;

`select min(age) from employee where age> 1;

`select max(age) from employee where age > 1;

`select avg(age) from employee where age > 1;

select sum(age) from employee where age > 1;

select count(age) from employee where age > 1;

select min(age) as min_age, max(age) as max_age, avg(age) as avg_age, sum(age) as sum_age, count(age) as count_age from employee where age > 1;

select name from employee where name like 'joe_';

select name from employee where name like '%jo%';

select department from employee where department in ('Legal', 'Frontend');

select name, age from employee where age between 20 and 24 order by name, age;

select department as dept from employee;

select employee.department from employee where department = 'Legal' group by department having count(1);

select employee.department from employee where department is not null group by department;

select employee.department from employee where exists(select department.name from department where department.name = employee.department);

select all employee.name from employee where true;

select all employee.department from employee where employee.department = any (select department.name from department where department.name is not null);

select count(age) from employee where age > 20;

select name from department union select department from employee; -- only the distinct values

select name from department union all select department from employee; -- will return all the values

select age,
case
    when age > 20 then 'they are above 20'
    when age < 20 then 'they are below 20'
    else 'there is no one'
end
from employee;

select department.name, employee.department from employee right join department on department.name = employee.department;
select department.name, employee.department from employee right join department on employee.department = department.name;

select employee.department, department.name from employee right outer join department on employee.department = department.name;
select employee.department, department.name from employee left outer join department on employee.department = department.name;

select employee.department, department.name from employee left join department on employee.department = department.name;
select employee.department, department.name from employee left join department on department.name = employee.department;

select employee.department, department.name from department join employee on department.name = employee.department;

select employee.name, department.name from employee, department where employee.name <> department.name;

select * from employee where age > 21 limit 3;

select * from employee where name like 'e%'; -- start with e

select * from employee where name like '%e'; -- ends with e

select distinct project.name from project;

select project.description, project.name from project where employee_id is not null order by project.name, project.description;

select * from employee where name != 'dave' and age > 20;

select  * from employee where department != 'Legal' and age > 21 and name like 'j%';

select employee.department, employee.name from employee where employee.name like '%a';

select employee.name, employee.id, employee.age,
       case
           when employee.age >= 18 then 'You are a major'
           when employee.age < 18 then 'You are a minor'
           end from employee;

select count(employee.id),
       case
           when count(employee.id) <= 1 then 'You are an indie developer'
           when count(employee.id) < 5 then 'You are a team'
           when count(employee.id) < 10 then 'You are a startup'
           when count(employee.id) > 100 then 'You are a company'
           else 'You are a multinational company'
           end
from employee;

select sum(employee.id) from employee where employee.name like 'j%' and employee.age > 10;

select * from employee where age > 10 and id < 5;

describe project;

describe employee;

select employee.name from employee where employee.name = 'Joel' || 'Elsa';
select employee.name from employee where employee.name = 'Joel' && employee.id = '1';

describe department;

select name, age from employee where age > 10 and name like 'j%' or name like 'e%' order by age desc limit 2;

select employee.name from employee where name like 'e%' or name like 'j%' and age > 18 and department like 'D%' or department like 'M%' and id is not null;

select employee.name from employee where employee.id = 1;

describe project;

describe employee;

select employee.name from project join employee where project.employee_id = employee.id;

select distinct employee.name from project join employee where project.employee_id = employee.id;

/*
    Pre Defined Functions
*/

select employee.name,
case
    when ascii(employee.name) > 80 then 'Your name has more than 80 in ascii value'
    when ascii(employee.name) > 70 then 'Your name has more than 70 in ascii value'
    when ascii(employee.name) > 60 then 'Your name has more than 60 in ascii value'
    else 'I dont see a name here'
end
from employee;

select employee.name,
case
    when char_length(employee.name) < 10 then 'Your name has less than 10 letters.'
    when char_length(employee.name) > 20 then 'Your name has more than 20 letters.'
    else 'I dont see a name here'
end
from employee;

select ucase(employee.name) as name from employee where name like 'j%';
select lcase(employee.name) as name from employee where name like 'd%';

select employee.name from employee where name != 'dave' and id < 5;

select employee.name from employee where id is not null and name between 'Elsa' and 'Joel' order by name asc;

select employee.name from employee where employee.name is not null and employee.name like 'j%';
select employee.name from employee where employee.name and employee.name like 'e%';

select employee.name from employee right join project on employee.id = project.employee_id;
select distinct employee.name from employee left join project on employee.id = project.employee_id; -- Remove distinct if you want it raw (includes duplication)

/*
    Assignments
*/

-- List of Departments:
select * from department;

-- Employee Count per Department:
select count(department) from employee;

-- List of projects
select * from project;

-- Employees in a Specific Department:
select * from employee where department = 'Legal';

-- Employees from department (Experimental)
select employee.name , department.name from employee join department on employee.department = department.name;

-- List of employees by project
select project.name, project.employee_id from project;

-- List of employees by a specific project (Experimental)
select project.name, project.description, employee_id from project where project.name = 'Starship';
select * from project where project.name = 'Teamsync';

-- Count of projects (Experimental)
select count(project.name) from project;

-- Employee Details:
select * from employee where employee.name = 'Joel';
select * from employee where employee.id = 2;

-- List of projects in each departments
select project.name , project.description from project order by project.name , project.description;

-- Experimentation start
select employee.name from employee join project on employee.id = project.employee_id;
select department.name from department join project where department.name = project.description;
select distinct department.name from project right join department on project.description = department.name;
-- Experimentation end

-- list of projects in each department.
select project.name, project.description from project left join department on project.description = department.name;

-- department with employees (Experimental)
select department.name from employee left join department on department.name = employee.department where employee.id is not null;

-- department with no employees
select department.name from employee right join department on department.name = employee.department where employee.id is null;

-- Employees Project Allocation
select employee.name, project.name, project.description from employee left join project on employee.id = project.employee_id where employee_id is not null;

-- Project Allocation per department
select project.name , project.description from department right join project on project.name = department.name;

-- Employees working on multiple projects
select employee.name from employee join project on employee.id = project.employee_id where project.employee_id < 2 group by employee.name;

-- Project Progress Report
select project.name, project.description, count(employee_id) from project group by project.name, project.description;
