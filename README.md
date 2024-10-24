# DVDRental SQL Queries

This repository contains various SQL queries executed on the DVDRental sample database. Below are some example queries with their solutions.

## 1. Retrieve `title` and `description` columns from the `film` table
```sql
SELECT title, description
FROM film;
```

## 2. Retrieve all columns from the film table where the length is greater than 60 and less than 75 
```sql
SELECT *
FROM film
WHERE length
BETWEEN 60 AND 75;
```

## 3. Retrieve all columns from the film table where rental_rate is 0.99 and replacement_cost is either 12.99 or 28.99
```sql
SELECT *
FROM film
WHERE rental_rate = 0.99
AND replacement_cost IN (12.99, 28.99);
```

## 4. Find the last_name of the customer whose first_name is 'Mary'
```sql
SELECT last_name
FROM customer
WHERE first_name = 'Mary';
```

## 5. Retrieve all columns from the film table where the length is not greater than 50 and the rental_rate is not 2.99 or 4.99
```sql
SELECT *
FROM film
WHERE length <= 50
AND rental_rate NOT IN (2.99, 4.99);
```

## 6. Retrieve all columns from the film table where the replacement_cost is greater than or equal to 12.99 and less than 16.99
```sql
SELECT *
FROM film
WHERE replacement_cost
BETWEEN 12.99 AND 16.99;
```

## 7. Retrieve first_name and last_name columns from the actor table where the first_name is 'Penelope', 'Nick', or 'Ed'
```sql
SELECT first_name, last_name
FROM actor
WHERE first_name IN ('Penelope', 'Nick', 'Ed');
```

## 8. Retrieve all columns from the film table where the rental_rate is 0.99, 2.99, or 4.99 and the replacement_cost is 12.99, 15.99, or 28.99
```sql
SELECT *
FROM film
WHERE rental_rate IN (0.99, 2.99, 4.99)
AND replacement_cost IN (12.99, 15.99, 28.99);
```

## 9. Retrieve country names from the country table where the name starts with 'A' and ends with 'a'
```sql
SELECT country
FROM country
WHERE country LIKE 'A%a';
```

## 10. Retrieve country names from the country table that are at least 6 characters long and end with 'n'
```sql
SELECT country
FROM country
WHERE LENGTH(country) >= 6
AND country LIKE '%n';
```

## 11. Retrieve film titles from the film table that contain at least 4 occurrences of the character 'T' (case insensitive)
```sql
SELECT title
FROM film
WHERE title LIKE '%T%' OR title LIKE '%t%'
GROUP BY title
HAVING (LENGTH(title) - LENGTH(REPLACE(UPPER(title), 'T', ''))) >= 4;
```

## 12. Retrieve all columns from the film table where the title starts with 'C', the length is greater than 90, and the rental_rate is 2.99
```sql
SELECT *
FROM film
WHERE title LIKE 'C%'
AND length > 90
AND rental_rate = 2.99;
```

## 13. Retrieve distinct values from the replacement_cost column in the film table
```sql
SELECT DISTINCT replacement_cost
FROM film
ORDER BY replacement_cost;
```

## 14. Count distinct values in the replacement_cost column of the film table 
```sql
SELECT COUNT(DISTINCT replacement_cost)
AS distinct_replacement_cost_count
FROM film;
```

## 15. Count the number of film titles that start with 'T' and have a rating of 'G'
```sql
SELECT COUNT(*) AS count_of_films
FROM film
WHERE title LIKE 'T%'
AND rating = 'G';
```

## 16. Count the number of country names that are exactly 5 characters long
```sql
SELECT COUNT(*) AS count_of_countries
FROM country
WHERE LENGTH(country) = 5;
```

## 17. Count the number of city names that end with 'R' or 'r'
```sql
SELECT COUNT(*) AS count_of_cities
FROM city
WHERE city LIKE '%R' OR city LIKE '%r';
```

## 18. Retrieve the top 5 longest films whose title ends with 'n'
```sql
SELECT *
FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5;
```

## 19. Retrieve the second 5 shortest films with title ending in 'n' and lengths of 6, 7, 8, 9, or 10
```sql
SELECT *
FROM film
WHERE title LIKE '%n'
AND length IN (6, 7, 8, 9, 10)
ORDER BY length ASC
LIMIT 5 OFFSET 5;
```

## 20. Retrieve the top 4 customers with store_id 1, ordered by last_name in descending order
```sql
SELECT *
FROM customer
WHERE store_id = 1
ORDER BY last_name DESC
LIMIT 4;
```

## 21. Calculate the average value of the rental_rate column in the film table
```sql
SELECT AVG(rental_rate) AS average_rental_rate
FROM film
```

## 22. Count the number of films whose title starts with 'C'
```sql
SELECT COUNT(*) AS count_of_films
FROM film
WHERE title LIKE 'C%';
```

## 23. Retrieve the length of the longest film with a rental_rate of 0.99
```sql
SELECT MAX(length) AS longest_film_length
FROM film
WHERE rental_rate = 0.99;
```

## 24. Count the distinct replacement_cost values for films longer than 150 minutes
```sql
SELECT COUNT(DISTINCT replacement_cost) AS distinct_replacement_cost_count
FROM film
WHERE length > 150;
```

## 25. Group films by their rating values
```sql
SELECT rating, COUNT(*) AS film_count
FROM film
GROUP BY rating;
```

## 26. Retrieve replacement_cost values with more than 50 films and their corresponding counts
```sql
SELECT replacement_cost, COUNT(*) AS film_count
FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```

## 27. Retrieve the customer counts for each store_id in the customer table
```sql
SELECT store_id, COUNT(*) AS customer_count
FROM customer
GROUP BY store_id;
```

## 28. Retrieve the country_id with the highest number of cities and the corresponding city count
```sql
SELECT country_id, COUNT(*) AS city_count
FROM city
GROUP BY country_id
ORDER BY city_count DESC
LIMIT 1;
```

## 29. Create a table named employee in the test database with the following column information: id (INTEGER), name (VARCHAR(50)), birthday (DATE), and email (VARCHAR(100))
```sql
CREATE TABLE employee (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    birthday DATE,
    email VARCHAR(100) UNIQUE
);
```

## 30. Add 50 records to the employee table using the Mockaroo service.

To add 50 records to the employee table using the Mockaroo service, you can follow these steps:

### Step 1: Generate Data with Mockaroo
#### 1. Go to Mockaroo: Visit the Mockaroo website.
#### 2. Define Your Schema:
<ul>
<li>id: Integer (set to start from 1 and increment by 1)</li>
<li>name: Full Name (or First Name + Last Name)</li>
<li>birthday: Date (you can set a range, e.g., between 1960-01-01 and 2000-12-31)</li>
<li>email: Email (ensure it’s unique)</li>
</ul>

#### 3. Set the Number of Rows: Change the number of rows to 50

#### 4. Download the Data: Click on the "Download Data" button to get the data in CSV format.

### Step 2: Import Data into Your Database
#### 1. Prepare Your Database Environment: Ensure you have access to your database where the employee table is located.
#### 2. Use SQL to Import Data: If you have the CSV file ready, you can use a SQL command to import it. The command will depend on your database system (e.g., MySQL, PostgreSQL).

Here’s a general example using MySQL:

```sql
LOAD DATA INFILE '/path/to/your/file.csv'
INTO TABLE employee
FIELDS TERMINATED BY ','
ENCLOSED BY '"'
LINES TERMINATED BY '\n'
IGNORE 1 ROWS;
```
#### Important Notes:
<ul>
<li>File Path: Make sure to replace '/path/to/your/file.csv' with the actual path to your CSV file.</li>
<li>Permissions: Ensure your database user has the necessary permissions to load data from a file.</li>
<li>Format: The format of the CSV should match the structure of your employee table.</li>
  </ul>
By following these steps, you can successfully populate the employee table with 50 records using Mockaroo. If you need specific instructions for a certain database system or further assistance, let me know!

## 31. Perform 5 UPDATE operations that will update other columns based on each of the columns.
Here are five examples of UPDATE statements that you can use to update different columns in the employee table. Each example demonstrates updating one column while maintaining the integrity of the other columns.

#### Example 1: Update Name
This updates the name of the employee with id 1 to 'John Doe'.
```sql
UPDATE employee
SET name = 'John Doe'
WHERE id = 1;
```

#### Example 2: Update Birthday
This updates the birthday of the employee with id 2 to May 15, 1990.
```sql
UPDATE employee
SET birthday = '1990-05-15'
WHERE id = 2;
```

#### Example 3: Update Email
This updates the email of the employee with id 3 to 'jane.smith@example.com'.
```sql
UPDATE employee
SET email = 'jane.smith@example.com'
WHERE id = 3;
```

#### Example 4: Update Multiple Columns
This updates the name and birthday of the employee with id 4 to 'Alice Johnson' and December 1, 1985, respectively.
```sql
UPDATE employee
SET name = 'Alice Johnson', birthday = '1985-12-01'
WHERE id = 4;
```

#### Example 5: Update with Conditional Logic
This updates the email of all employees whose birthday is before January 1, 1990, to their name followed by '@example.com' in lowercase.
```sql
UPDATE employee
SET email = CONCAT(LOWER(name), '@example.com')
WHERE birthday < '1990-01-01';
```

## 32. 
Here are five examples of DELETE statements that you can use to delete specific rows from the employee table based on different conditions:
#### Example 1: Delete by ID
This deletes the employee record with id 1.
```sql
DELETE FROM employee
WHERE id = 1;
```

#### Example 2: Delete by Name
This deletes the employee record where the name is 'John Doe'.
```sql
DELETE FROM employee
WHERE name = 'John Doe';
```

#### Example 3: Delete by Birthday
This deletes the employee record with a birthday of May 15, 1990.
```sql
DELETE FROM employee
WHERE birthday = '1990-05-15';
```

#### Example 4: Delete by Email
This deletes the employee record with the specified email.
```sql
DELETE FROM employee
WHERE email = 'jane.smith@example.com';
```

#### Example 5: Delete with Conditional Logic
This deletes all employee records whose birthday is before January 1, 1980.
```sql
DELETE FROM employee
WHERE birthday < '1980-01-01';
```

## 33. Write an INNER JOIN query to display the city names from the city table and country names from the country table together
```sql
SELECT city.name AS city_name, country.name AS country_name
FROM city
INNER JOIN country
ON city.country_id = country.country_id;
```

## 34. Write an INNER JOIN query to display the payment_id from the payment table along with the first_name and last_name from the customer table
```sql
SELECT payment.payment_id, customer.first_name, customer.last_name
FROM payment
INNER JOIN customer
ON payment.customer_id = customer.customer_id;
```

## 35. Write an INNER JOIN query to display the rental_id from the rental table along with the first_name and last_name from the customer table
```sql
SELECT rental.rental_id, customer.first_name, customer.last_name
FROM rental
INNER JOIN customer
ON rental.customer_id = customer.customer_id;
```





