# WHO-COVID-19-ANALYSIS
## 1. What is a Subquery?
A subquery is a query inside another query. It helps retrieve data that will be used in the main query. It is also called an inner query or nested query.
Example: Imagine you want to find employees who earn more than the average salary in a company. First, you need to calculate the average salary (subquery), then find employees earning above that value (main query).
## 2. Basic Syntax
SQL syntax for subqueries:
SELECT column_name
FROM table_name
WHERE column_name OPERATOR (SELECT column_name FROM table_name WHERE condition);
- The inner query runs first and provides a result.
- The outer query uses this result to filter or compute data.
## 3. Example: Students & Scores
Consider a students table:
student_id	name	score
-	Alice	85
-	Bob	75
-Carol	90
-	David	70
-	Eve	80
Find students who scored above the average score:
SELECT name, score
FROM students
WHERE score > (SELECT AVG(score) FROM students);
## 4. Types of Subqueries
a) Subquery in WHERE Clause (Filtering Data)
Find employees who earn more than the company’s average salary:
SELECT name, salary 
FROM employees 
WHERE salary > (SELECT AVG(salary) FROM employees);
b) Subquery in SELECT Clause (Returning a Computed Value)
Show each student's score along with the average score for comparison:
SELECT name, score, (SELECT AVG(score) FROM students) AS avg_score
FROM students;
c) Subquery in FROM Clause (Derived Table)
Find the top three highest-paid employees:
SELECT * FROM 
  (SELECT name, salary FROM employees ORDER BY salary DESC LIMIT 3) AS top_earners;
## 5. Practice Exercises
1. Find products priced above the average product price.
2. Find employees who have the same salary as the lowest-paid employee.
3. Find students whose scores match the highest score in the class.
## 6. Common Mistakes to Avoid
- Subquery returning multiple rows when only one is expected
  ❌ WHERE salary = (SELECT salary FROM employees)
  ✅ Use IN if multiple values are possible:
  WHERE salary IN (SELECT salary FROM employees WHERE department = 'IT')
- Using subqueries where a JOIN is more efficient
**NOTE:** It is best to use JOINs instead of subqueries when appropriate.

NAME| AGE| SEX| LOCATION|
WALE| 12| MALE| AJAH
