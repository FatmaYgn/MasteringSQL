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








