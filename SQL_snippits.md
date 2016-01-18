SELECT DISTINCT(CITY) FROM STATION WHERE
RIGHT(CITY, 1) IN ('a', 'e', 'i', 'o' 'u')
ORDER BY CITY;


SELECT DISTINCT(CITY) from STATION where
LEFT(CITY, 1) in ('a', 'e', 'i', 'o', 'u');
/*SUBSTRING(CITY, 1) in ('A', 'E', 'I', 'O', 'U'); */

SELECT distinct(CITY) FROM STATION
WHERE RIGHT(CITY, 1) in ('a', 'e', 'i', 'o', 'u')
ORDER BY CITY

WHERE RIGHT(CITY, 1) IN ('a', 'e', 'i', 'o' 'u')

# ROUNDS DOWN
SELECT ROUND(AVG(POPULATION)) FROM CITY 
# TWO DEcimal places
 ROUND(SUM(LAT_N), 2)

# SELECT ALL  below a certain value
 SELECT ROUND(MAX(LAT_N), 4) FROM 
 (SELECT LAT_N FROM STATION WHERE LAT_N < 137.2345) as STATION

# Illogical solutions
SELECT ROUND(MAX(LAT_N), 4) FROM STATION
WHERE LAT_N < 137.2345

SHOULD BE 258

# More work on the Manhattan distance. I didn't realize that they were points
SELECT ROUND(ABS(MAX(LAT_N)-MAX(LONG_W))+ABS(MIN(LAT_N)-MIN(LONG_W)),4) FROM STATION;

# Pivot only works on Oracle/ MS SQL
select Doctor,Professor,Singer,Actor
from (select Name,Occupation ,row_number() over(partition by Occupation order by Name) rn
      from Occupations) as source 
pivot ( max(name) 
       for Occupation in (Doctor,Professor,Singer,Actor) ) as PVT;


# Interesting if else statement
# See [here](http://dev.mysql.com/doc/refman/5.0/en/control-flow-functions.html) for more
SELECT N,
IF(P IS NULL,'Root',
   IF((SELECT COUNT(*) FROM BST WHERE P=B.N)>0,'Inner','Leaf'))
FROM BST AS B ORDER BY N;

SELECT teamID, SUM(Salary) as sal 
from Salaries GROUP BY teamID
ORDER BY sal DESC;


teamID|sal
NYA|3085575427.0
BOS|2293681006.0
LAN|2020752103.0
NYN|1934987231.0

SELECT playerID, min(yearID), max(yearID),
max(yearID) - min(yearID)  as better_stint
from Fielding Group By (playerID)
LIMIT 10;

SELECT count(*) as cnt, playerID
FROM AllstarFull
GROUP BY (playerID)
ORDER BY cnt DESC
LIMIT 5;


SELECT COUNT(DISTINCT(playerID)) as cnt, schoolID
FROM SchoolsPlayers
group by schoolID
Order By cnt desc
limit 10;

SELECT player_name,
       weight,
       CASE WHEN weight > 250 THEN 'over 250'
            WHEN weight > 200 AND weight <= 250 THEN '201-250'
            WHEN weight > 175 AND weight <= 200 THEN '176-200'
            ELSE '175 or under' END AS weight_group
  FROM benn.college_football_players
