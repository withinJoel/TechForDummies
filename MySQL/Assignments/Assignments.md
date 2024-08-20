# MySQL Assignments
1. **List of Departments:** ✅
   - Query to list all departments with their respective IDs and names.
```
SELECT * FROM department;
```
2. **Employee Count per Department:** ✅
   - Query to count the number of employees in each department.

```
SELECT id, COUNT(*) AS employee_count
FROM employee
GROUP BY id;
```
3. **List of Projects:**✅
   - Query to list all projects with their respective IDs, names, and department associations.

```
SELECT * FROM project;
```
4. **Employees in a Specific Department:**
   - Query to retrieve the names and IDs of all employees in a specific department (e.g., HR, IT, etc.).

```
SELECT id, name
FROM employee
WHERE department_id = (SELECT id FROM department WHERE name = 'HR');  -- Replace 'HR' with the department name you want
```
5. **List of Employees by Project:**
   - Query to list all employees working on a specific project.

```
SELECT e.id, e.name
FROM employee e
JOIN project_employee pe ON e.id = pe.employee_id
WHERE pe.project_id = (SELECT id FROM project WHERE name = 'ProjectName');  -- Replace 'ProjectName' with the project name
```

6. **Employee Details:** ✅
   - Query to retrieve all details (e.g., name, job title, department) of a specific employee based on their ID or name.

```
SELECT * FROM employee where id = 1;
```
7. **List of Projects in Each Department:**
   - Query to list the projects associated with each department.

```
SELECT d.name AS department_name, p.id AS project_id, p.name AS project_name
FROM project p
JOIN department d ON p.department_id = d.id;
```
8. **Departments with No Employees:**
   - Query to find departments that currently have no employees.

```
SELECT d.id, d.name
FROM department d
LEFT JOIN employee e ON d.id = e.department_id
WHERE e.id IS NULL;
```
### **Complicated Reports:**

1. **Employee Project Allocation:**
   - Query to list each employee along with the projects they are currently working on, including the project start and end dates.

```
SELECT e.name AS employee_name, p.name AS project_name, pe.start_date, pe.end_date
FROM employee e
JOIN project_employee pe ON e.id = pe.employee_id
JOIN project p ON pe.project_id = p.id;
```
2. **Project Allocation per Department:**
   - Query to find out how many projects are managed by each department and how many employees are working on each project.

```
SELECT d.name AS department_name, COUNT(DISTINCT p.id) AS project_count, COUNT(DISTINCT e.id) AS employee_count
FROM department d
LEFT JOIN project p ON d.id = p.department_id
LEFT JOIN project_employee pe ON p.id = pe.project_id
LEFT JOIN employee e ON pe.employee_id = e.id
GROUP BY d.name;
```
3. **Employees Working on Multiple Projects:**
   - Query to list employees who are working on more than one project, including the names of these projects.

```
SELECT e.id, e.name, GROUP_CONCAT(p.name) AS projects
FROM employee e
JOIN project_employee pe ON e.id = pe.employee_id
JOIN project p ON pe.project_id = p.id
GROUP BY e.id
HAVING COUNT(p.id) > 1;
```
4. **Departmental Employee Turnover:**
   - Query to calculate the employee turnover rate per department by comparing the number of employees at the start and end of a specified period.

```
-- Assumes turnover calculation is based on the number of employees at the start and end of a period
-- For simplicity, the following query assumes start_date and end_date fields are present in employee records

SELECT d.name AS department_name,
       COUNT(CASE WHEN e.start_date <= '2023-01-01' THEN 1 END) AS start_count,
       COUNT(CASE WHEN e.end_date <= '2023-12-31' THEN 1 END) AS end_count,
       (COUNT(CASE WHEN e.end_date <= '2023-12-31' THEN 1 END) / COUNT(CASE WHEN e.start_date <= '2023-01-01' THEN 1 END)) * 100 AS turnover_rate
FROM department d
LEFT JOIN employee e ON d.id = e.department_id
GROUP BY d.name;
```
5. **Project Progress Report:**
   - Query to generate a report showing the progress of each project, including the number of tasks completed, employees involved, and estimated completion date.

```
SELECT p.name AS project_name, COUNT(t.id) AS tasks_completed, COUNT(DISTINCT e.id) AS employees_involved, p.estimated_completion_date
FROM project p
JOIN task t ON p.id = t.project_id AND t.status = 'Completed'
JOIN project_employee pe ON p.id = pe.project_id
JOIN employee e ON pe.employee_id = e.id
GROUP BY p.name, p.estimated_completion_date;
```
6. **Employee Tenure in Projects:**
   - Query to calculate the average tenure of employees in each project, with a breakdown of tenure by department.

```
SELECT e.id, e.name, p.name AS project_name, AVG(DATEDIFF(pe.end_date, pe.start_date)) AS avg_tenure
FROM employee e
JOIN project_employee pe ON e.id = pe.employee_id
JOIN project p ON pe.project_id = p.id
GROUP BY e.id, p.name;
```
7. **Top Performing Departments:**
   - Query to rank departments based on the number of successfully completed projects and the average duration of project completion.

```
SELECT d.name AS department_name,
       COUNT(p.id) AS completed_projects,
       AVG(DATEDIFF(p.end_date, p.start_date)) AS avg_duration
FROM department d
JOIN project p ON d.id = p.department_id
WHERE p.status = 'Completed'
GROUP BY d.name
ORDER BY completed_projects DESC, avg_duration ASC;
```
8. **Employee Cross-Department Collaboration:**
   - Query to list employees who have worked on projects across different departments, including the details of these projects and departments.

```
SELECT e.id, e.name, d1.name AS department_1, d2.name AS department_2, p.name AS project_name
FROM employee e
JOIN project_employee pe ON e.id = pe.employee_id
JOIN project p ON pe.project_id = p.id
JOIN department d1 ON e.department_id = d1.id
JOIN department d2 ON p.department_id = d2.id
WHERE d1.id <> d2.id;
```
9. **Departmental Budget vs. Project Costs:**
   - Query to compare the budget allocated to each department with the actual costs incurred on projects managed by that department.

```
SELECT d.name AS department_name,
       d.budget AS allocated_budget,
       SUM(p.cost) AS total_project_cost
FROM department d
LEFT JOIN project p ON d.id = p.department_id
GROUP BY d.name, d.budget;
```
10. **Employee Performance Analysis:**
    - Query to analyze the performance of employees based on the number of projects they have completed, their role in each project, and feedback scores if available.

```
SELECT e.id, e.name, COUNT(p.id) AS completed_projects, AVG(pe.feedback_score) AS avg_feedback
FROM employee e
JOIN project_employee pe ON e.id = pe.employee_id
JOIN project p ON pe.project_id = p.id
GROUP BY e.id, e.name;
```
11. **Departments with the Most Active Projects:**
    - Query to find out which departments are currently handling the most active projects, along with details about these projects.

```
SELECT d.name AS department_name, COUNT(p.id) AS active_projects
FROM department d
JOIN project p ON d.id = p.department_id
WHERE p.status = 'Active'
GROUP BY d.name
ORDER BY active_projects DESC;
```
12. **Overlapping Project Allocations:**
    - Query to identify employees who are allocated to projects that have overlapping timelines, potentially indicating over-scheduling.

```
SELECT pe1.employee_id, e.name, p1.name AS project_1, p2.name AS project_2
FROM project_employee pe1
JOIN project p1 ON pe1.project_id = p1.id
JOIN project_employee pe2 ON pe1.employee_id = pe2.employee_id
JOIN project p2 ON pe2.project_id = p2.id
JOIN employee e ON pe1.employee_id = e.id
WHERE p1.id <> p2.id
  AND pe1.start_date < pe2.end_date
  AND pe1.end_date > pe2.start_date;
```
13. **Project Delays by Department:**
    - Query to identify projects that are delayed, grouped by department, with reasons for delay if available.

```
SELECT d.name AS department_name, p.name AS project_name, DATEDIFF(CURDATE(), p.end_date) AS days_delayed
FROM department d
JOIN project p ON d.id = p.department_id
WHERE p.end_date < CURDATE() AND p.status <> 'Completed';
```

### **Data Aggregation and Analytics Reports:**

1. **Historical Employee Engagement:**
   - Query to analyze the historical engagement of employees in projects over time, with trends indicating peak periods of activity.

```
SELECT e.name, p.name AS project_name, YEAR(pe.start_date) AS year, COUNT(*) AS engagement_count
FROM employee e
JOIN project_employee pe ON e.id = pe.employee_id
JOIN project p ON pe.project_id = p.id
GROUP BY e.name, p.name, YEAR(pe.start_date);
```
2. **Departmental Project Success Rate:**
   - Query to calculate the success rate of projects managed by each department over the last year, including project failure reasons if available.

```
SELECT d.name AS department_name,
       COUNT(CASE WHEN p.status = 'Completed' THEN 1 END) AS successful_projects,
       COUNT(p.id) AS total_projects,
       (COUNT(CASE WHEN p.status = 'Completed' THEN 1 END) / COUNT(p.id)) * 100 AS success_rate
FROM department d
LEFT JOIN project p ON d.id = p.department_id
WHERE p.end_date >= DATE_SUB(CURDATE(), INTERVAL 1 YEAR)
GROUP BY d.name;
```
3. **Employee Role Distribution in Projects:**
   - Query to analyze the distribution of roles (e.g., manager, developer, analyst) across projects within each department.

```
SELECT d.name AS department_name, e.role, COUNT(p.id) AS project_count
FROM department d
JOIN project p ON d.id = p.department_id
JOIN project_employee pe ON p.id = pe.project_id
JOIN employee e ON pe.employee_id = e.id
GROUP BY d.name, e.role;
```
4. **Future Resource Allocation Forecast:**
   - Query to predict future resource allocation needs based on upcoming projects, employee availability, and department workloads.
```
SELECT d.name AS department_name, p.name AS project_name, p.start_date, p.end_date
FROM department d
JOIN project p ON d.id = p.department_id
WHERE p.start_date > CURDATE();
```
