-- Exported from QuickDBD: https://www.quickdatabasediagrams.com/
-- NOTE! If you have used non-SQL datatypes in your design, you will have to change these here.


CREATE TABLE departments (
    dept_no VARCHAR   NOT NULL,
    dept_name VARCHAR   NOT NULL,
    CONSTRAINT pk_departments PRIMARY KEY (
        dept_no
     )
);

CREATE TABLE dept_emp (
    emp_no INTEGER   NOT NULL,
    dept_no VARCHAR   NOT NULL,
    CONSTRAINT pk_dept_emp PRIMARY KEY (
        emp_no,dept_no
     )
);

CREATE TABLE dept_managers (
    dept_no VARCHAR   NOT NULL,
    emp_no INTEGER   NOT NULL,
    CONSTRAINT pk_dept_managers PRIMARY KEY (
        dept_no,emp_no
     )
);

CREATE TABLE employees (
    emp_no INTEGER   NOT NULL,
    emp_title VARCHAR   NOT NULL,
    birth_date DATE   NOT NULL,
    first_name VARCHAR   NOT NULL,
    last_name VARCHAR   NOT NULL,
    sex VARCHAR   NOT NULL,
    hire_date DATE   NOT NULL,
    CONSTRAINT pk_employees PRIMARY KEY (
        emp_no
     )
);

CREATE TABLE salaries (
    id SERIAL   NOT NULL,
    emp_no INTEGER   NOT NULL,
    salary INTEGER   NOT NULL,
    CONSTRAINT pk_salaries PRIMARY KEY (
        id
     )
);

SELECT * FROM salaries

CREATE TABLE titles (
    title_id VARCHAR   NOT NULL,
    title VARCHAR   NOT NULL,
    CONSTRAINT pk_titles PRIMARY KEY (
        title_id
     )
);

ALTER TABLE dept_emp ADD CONSTRAINT fk_dept_emp_emp_no FOREIGN KEY(emp_no)
REFERENCES employees (emp_no);

ALTER TABLE dept_emp ADD CONSTRAINT fk_dept_emp_dept_no FOREIGN KEY(dept_no)
REFERENCES departments (dept_no);

ALTER TABLE dept_managers ADD CONSTRAINT fk_dept_managers_dept_no FOREIGN KEY(dept_no)
REFERENCES departments (dept_no);

ALTER TABLE dept_managers ADD CONSTRAINT fk_dept_managers_emp_no FOREIGN KEY(emp_no)
REFERENCES employees (emp_no);

ALTER TABLE employees ADD CONSTRAINT fk_employees_emp_title FOREIGN KEY(emp_title)
REFERENCES titles (title_id);

ALTER TABLE salaries ADD CONSTRAINT fk_salaries_emp_no FOREIGN KEY(emp_no)
REFERENCES employees (emp_no);

SELECT * FROM departments
SELECT * FROM dept_emp LIMIT 5
SELECT * FROM dept_managers
SELECT * FROM employees LIMIT 5
SELECT * FROM salaries LIMIT 5
SELECT * FROM titles

-- Query 1
SELECT e.emp_no, e.last_name, e.first_name, e.sex, s.salary
FROM employees AS e
INNER JOIN salaries as s
ON e.emp_no = s.emp_no;

--Query 2
SELECT first_name, last_name, hire_date
FROM employees
WHERE hire_date >= '1986-01-01' AND hire_date < '1987-01-01'; 

--Query 3
SELECT m.dept_no, d.dept_name, e.emp_no, e.last_name, e.first_name
	FROM departments AS d
	LEFT JOIN dept_managers AS m
	ON m.dept_no = d.dept_no
	LEFT JOIN  employees as e
	ON e.emp_no = m.emp_no
WHERE emp_title IN(
	SELECT title_id
	FROM titles
	WHERE title = 'Manager'
	);

--Query 4
SELECT e.emp_no, e.last_name, e.first_name, d.dept_name
FROM employees as e
LEFT JOIN dept_emp as de
ON e.emp_no = de.emp_no
LEFT JOIN departments as d
ON de.dept_no = d.dept_no
LIMIT 10;

--Query 5
SELECT first_name, last_name, sex
FROM employees
WHERE first_name = 'Hercules' AND last_name LIKE 'B%';

--Query 6
SELECT e.emp_no, e.last_name, e.first_name, d.dept_name
FROM  employees as e
	LEFT JOIN dept_emp AS de
	ON e.emp_no = de.emp_no
	LEFT JOIN departments AS d 
	ON de.dept_no = d.dept_no 
WHERE dept_name = 'Sales';

--Query 7
SELECT e.emp_no, e.last_name, e.first_name, d.dept_name
FROM  employees as e
	LEFT JOIN dept_emp AS de
	ON e.emp_no = de.emp_no
	LEFT JOIN departments AS d 
	ON de.dept_no = d.dept_no 
WHERE dept_name = 'Sales' OR dept_name = 'Development';

--Query 8
SELECT last_name, COUNT(last_name) AS "Name Count" 		
FROM employees
GROUP BY last_name
ORDER BY last_name DESC;


