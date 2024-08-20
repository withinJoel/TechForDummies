# MySQL Assignments
List of Departments:  ✅
SELECT id, name FROM department;

Employee Count per Department: ✅
SELECT department, COUNT(*) AS employee_count
FROM employee
GROUP BY department;

List of Projects: ✅
SELECT id, name, description, employee_id FROM project;

Employees in a Specific Department:
SELECT id, name
FROM employee
WHERE department = 'HR';  -- Replace 'HR' with the specific department name

List of Employees by Project:
SELECT e.id, e.name
FROM employee e
JOIN project p ON e.id = p.employee_id
WHERE p.id = 1;  -- Replace 1 with the specific project ID

Employee Details:
SELECT *
FROM employee
WHERE id = 1;  -- Replace 1 with the specific employee ID or use a name-based search if needed

List of Projects in Each Department:
SELECT p.id AS project_id, p.name AS project_name, d.name AS department_name
FROM project p
JOIN employee e ON p.employee_id = e.id
JOIN department d ON e.department = d.name;

Departments with No Employees:
SELECT d.id, d.name
FROM department d
LEFT JOIN employee e ON d.name = e.department
WHERE e.id IS NULL;

# Complicated Reports

Employee Project Allocation:
SELECT e.name AS employee_name, p.name AS project_name, p.description
FROM employee e
JOIN project p ON e.id = p.employee_id;

Project Allocation per Department:
SELECT d.name AS department_name, COUNT(DISTINCT p.id) AS project_count, COUNT(DISTINCT e.id) AS employee_count
FROM department d
LEFT JOIN employee e ON d.name = e.department
LEFT JOIN project p ON e.id = p.employee_id
GROUP BY d.name;

Employees Working on Multiple Projects:
SELECT e.id, e.name, GROUP_CONCAT(p.name) AS projects
FROM employee e
JOIN project p ON e.id = p.employee_id
GROUP BY e.id
HAVING COUNT(p.id) > 1;

Departmental Employee Turnover:
-- This query assumes a simple turnover calculation and requires date fields
SELECT d.name AS department_name,
       COUNT(CASE WHEN e.start_date <= '2023-01-01' THEN 1 END) AS start_count,
       COUNT(CASE WHEN e.end_date <= '2023-12-31' THEN 1 END) AS end_count,
       (COUNT(CASE WHEN e.end_date <= '2023-12-31' THEN 1 END) / COUNT(CASE WHEN e.start_date <= '2023-01-01' THEN 1 END)) * 100 AS turnover_rate
FROM department d
LEFT JOIN employee e ON d.name = e.department
GROUP BY d.name;

Project Progress Report:
SELECT p.name AS project_name, p.description, COUNT(DISTINCT e.id) AS employees_involved
FROM project p
JOIN employee e ON p.employee_id = e.id
GROUP BY p.id, p.name, p.description;

Employee Tenure in Projects:
-- Assumes tenure is calculated based on start_date and end_date
SELECT e.id, e.name, p.name AS project_name, AVG(DATEDIFF(CURDATE(), e.start_date)) AS avg_tenure
FROM employee e
JOIN project p ON e.id = p.employee_id
GROUP BY e.id, p.name;

Top Performing Departments:
SELECT d.name AS department_name,
       COUNT(p.id) AS completed_projects
FROM department d
JOIN employee e ON d.name = e.department
JOIN project p ON e.id = p.employee_id
WHERE p.status = 'Completed'
GROUP BY d.name
ORDER BY completed_projects DESC;

Employee Cross-Department Collaboration:
SELECT e.id, e.name, d1.name AS department_1, d2.name AS department_2, p.name AS project_name
FROM employee e
JOIN project p ON e.id = p.employee_id
JOIN department d1 ON e.department = d1.name
JOIN department d2 ON p.employee_id IN (SELECT id FROM employee WHERE department <> d1.name);

Departmental Budget vs. Project Costs:
-- Assuming there is a 'budget' column in the department table and a 'cost' column in the project table
SELECT d.name AS department_name,
       d.budget AS allocated_budget,
       SUM(p.cost) AS total_project_cost
FROM department d
LEFT JOIN employee e ON d.name = e.department
LEFT JOIN project p ON e.id = p.employee_id
GROUP BY d.name, d.budget;

Employee Performance Analysis:
SELECT e.id, e.name, COUNT(p.id) AS completed_projects
FROM employee e
JOIN project p ON e.id = p.employee_id
WHERE p.status = 'Completed'
GROUP BY e.id, e.name;

Departments with the Most Active Projects:
SELECT d.name AS department_name, COUNT(p.id) AS active_projects
FROM department d
JOIN employee e ON d.name = e.department
JOIN project p ON e.id = p.employee_id
WHERE p.status = 'Active'
GROUP BY d.name
ORDER BY active_projects DESC;

Overlapping Project Allocations:
SELECT e.id, e.name, p1.name AS project_1, p2.name AS project_2
FROM project p1
JOIN project p2 ON p1.employee_id = p2.employee_id AND p1.id <> p2.id
JOIN employee e ON p1.employee_id = e.id
WHERE p1.start_date < p2.end_date AND p1.end_date > p2.start_date;

Project Delays by Department:
SELECT d.name AS department_name, p.name AS project_name, DATEDIFF(CURDATE(), p.end_date) AS days_delayed
FROM department d
JOIN employee e ON d.name = e.department
JOIN project p ON e.id = p.employee_id
WHERE p.end_date < CURDATE() AND p.status <> 'Completed';

# Data Aggregation and Analytics Reports

Historical Employee Engagement:
SELECT e.name, p.name AS project_name, YEAR(p.start_date) AS year, COUNT(*) AS engagement_count
FROM employee e
JOIN project p ON e.id = p.employee_id
GROUP BY e.name, p.name, YEAR(p.start_date);

Departmental Project Success Rate:

SELECT d.name AS department_name,
       COUNT(CASE WHEN p.status = 'Completed' THEN 1 END) AS successful_projects,
       COUNT(p.id) AS total_projects,
       (COUNT(CASE WHEN p.status = 'Completed' THEN 1 END) / COUNT(p.id)) * 100 AS success_rate
FROM department d
LEFT JOIN employee e ON d.name = e.department
LEFT JOIN project p ON e.id = p.employee_id
WHERE p.end_date >= DATE_SUB(CURDATE(), INTERVAL 1 YEAR)
GROUP BY d.name;

Employee Role Distribution in Projects:

SELECT d.name AS department_name, e.role, COUNT(p.id) AS project_count
FROM department d
JOIN employee e ON d.name = e.department
JOIN project p ON e.id = p.employee_id
GROUP BY d.name, e.role;
