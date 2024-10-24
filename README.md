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
WHERE length > 60
AND length < 75;
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

