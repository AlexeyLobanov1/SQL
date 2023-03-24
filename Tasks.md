1.Вывести всех работников чьи зарплаты есть в базе, вместе с зарплатами.
```sql
SELECT employee_name, monthly_salary FROM employees
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id;
```

2.Вывести всех работников у которых ЗП меньше 2000
```sql
SELECT employee_name, monthly_salary FROM employees
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE monthly_salary < 2000;
```

3.Вывести все зарплатные позиции, но работник по ним не назначен. (ЗП есть, но непонятно кто её получает.
```sql
SELECT employee_name, monthly_salary FROM employees
FULL JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
FULL JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE employee_name IS NULL;
```

4.Вывести все зарплатные позиции меньше 2000 но работник по ним не назначен. (ЗП есть, но непонятно кто её получает.)
```sql
SELECT employee_name, monthly_salary FROM employees
FULL JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
FULL JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE employee_name IS NULL
OR monthly_salary < 2000;
```

5.Найти всех работников кому не начислена ЗП.
```sql
FULL JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
FULL JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE monthly_salary IS NULL;
```

6.Вывести имена и должность только Java разработчиков.
```sql
SELECT employee_name, role_name FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
WHERE role_name LIKE "%java developer%";
```

7.Вывести имена и должность только Python разработчиков.
```sql
SELECT employee_name, role_name FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
WHERE role_name LIKE "%Python developer%";
```

8.Вывести имена и должность всех QA инженеров.
```sql
SELECT employee_name, role_name FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
WHERE role_name LIKE "%QA%";
```

9.Вывести имена и зарплаты Senior Java разработчиков.
```sql
SELECT employee_name, role_name, monthly_salary FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
WHERE roles.role_name LIKE "%Senior Java developer%";
```

10.Вывести имена, должности и ЗП всех специалистов по возрастанию.
```sql
SELECT employee_name, role_name, monthly_salary FROM employees
JOIN roles_employee
ON employees.employee_Id = roles_employee.employee_id
JOIN roles
ON roles_employee.roles_id = roles.roles_id
JOIN employee_salary
ON employees.employee_Id = employee_salary.employee_id
JOIN Salary
ON employee_salary.salary_id = Salary.Salary_Id
ORDER BY employees.employee_name, roles.role_name, Salary.monthly_salary ASC;
```
