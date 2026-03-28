

---



- **SELECT** is used to retrieve data.
- **WHERE** is used for filtering.
- **LIKE** is used for pattern matching.
- **ORDER BY** is used for sorting.
- **LIMIT** restricts number of rows.

---

## Queries

### Lesson 1
```sql
SELECT Title FROM movies;
SELECT Director FROM movies;
SELECT Title, Director FROM movies;
SELECT Title, Year FROM movies;
SELECT * FROM movies;
```

---

### Lesson 2
```sql
SELECT * FROM movies
WHERE Id = 6;

SELECT * FROM movies
WHERE Year BETWEEN 2000 AND 2010;

SELECT * FROM movies
WHERE Year NOT BETWEEN 2000 AND 2010;

SELECT Title, Year
FROM movies
ORDER BY Year ASC
LIMIT 5;
```

---

### Lesson 3
```sql
SELECT Title FROM movies
WHERE Title LIKE 'Toy Story%';

SELECT Title FROM movies
WHERE Director = 'John Lasseter';

SELECT Title FROM movies
WHERE Director != 'John Lasseter';

SELECT Title FROM movies
WHERE Title LIKE 'WALL-%';
```

---

### Lesson 4
```sql
SELECT DISTINCT Director
FROM movies
ORDER BY Director;

SELECT Title
FROM movies
ORDER BY Year DESC
LIMIT 4;

SELECT Title
FROM movies
ORDER BY Title
LIMIT 5;

SELECT Title
FROM movies
ORDER BY Title
LIMIT 5 OFFSET 5;
```

---

### Lesson 5 (Question 1)
```sql
SELECT City, Population
FROM north_american_cities
WHERE Country = 'Canada';
```

---


