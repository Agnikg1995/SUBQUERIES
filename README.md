1. Find the number of persons in each country.
SELECT
    C.Country_name,
    COUNT(P.Id) AS Number_of_Persons
FROM
    Country C
LEFT JOIN
    Persons P ON C.Id = P.Country_Id
GROUP BY
    C.Country_name;
2. Find the number of persons in each country sorted from high to low.
SELECT
    C.Country_name,
    COUNT(P.Id) AS Number_of_Persons
FROM
    Country C
LEFT JOIN
    Persons P ON C.Id = P.Country_Id
GROUP BY
    C.Country_name
ORDER BY
    Number_of_Persons DESC;
3. Find out an average rating for Persons in respective countries if the average is greater than 3.0.
SELECT
    C.Country_name,
    AVG(P.Rating) AS Average_Rating
FROM
    Country C
LEFT JOIN
    Persons P ON C.Id = P.Country_Id
GROUP BY
    C.Country_name
HAVING
    Average_Rating > 3.0;
4. Find the countries with the same rating as the USA. (Using Subqueries)
Assuming USA's rating is fetched first:
SELECT
    P.Country_name
FROM
    Persons P
WHERE
    P.Rating = (SELECT Rating FROM Persons WHERE Country_name = 'USA')
    AND P.Country_name != 'USA'
GROUP BY
    P.Country_name;
5. Select all countries whose population is greater than the average population of all nations.
SELECT
    C.Country_name,
    C.Population
FROM
    Country C
WHERE
    C.Population > (SELECT AVG(Population) FROM Country);
