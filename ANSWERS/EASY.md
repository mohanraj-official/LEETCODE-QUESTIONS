# 175.COMBINE TWO TABLES

```SQL
SELECT FIRSTNAME, LASTNAME, CITY, STATE
FROM ADDRESS A
LEFT JOIN PERSON P ON A.PERSONID = P.PERSONID;
```

![175](175.png)

<BR><BR><BR>




# 181.Employees Earning More Than Their Managers

```SQL
SELECT E1.NAME NAME
FROM EMPLOYEE E1
JOIN EMPLOYEE E2 ON E1.MANAGERID = E2.ID
WHERE E1.SALARY > E2.SALARY;
```

![181](181.png)

<br><br><br>





# 182. Duplicate Emails

```SQL
SELECT EMAIL
FROM PERSON
GROUP BY EMAIL
HAVING COUNT(*) > 1;
```
![182](182.png)

<BR><BR><BR>






# 183. Customers Who Never Order

```SQL
SELECT NAME
FROM CUSTOMERS C
LEFT JOIN ORDERS O ON C.ID = O.CUSTOMERID
WHERE O.CUSTOMERID IS NULL;
```
![183](183.png)

<BR><BR><BR>






# 196. Delete Duplicate Emails

```SQL
DELETE FROM PERSON
WHERE ID NOT IN (SELECT MIN(ID) 
		         FROM PERSON 
		         GROUP BY EMAIL);
```
![196a](196a.png)

![196b](196b.png)

<BR><BR><BR>







# 197. Rising Temperature

```SQL
SELECT T.ID ID
FROM WEATHER Y
JOIN WEATHER T ON Y.RECORDDATE = T.RECORDDATE-1
WHERE Y.TEMPERATURE < T.TEMPERATURE;
```
![197](197.png)

<br><br><br>






# 511. Game Play Analysis I

```sql
SELECT PLAYER_ID, MIN(EVENT_DATE) FIRST_LOGIN
FROM ACTIVITY
GROUP BY PLAYER_ID
```
![511](511.png)

<BR><BR><BR>







# 512 - Game Play Analysis II

```SQL
SELECT A.PLAYER_ID PLAYER_ID, A.DEVICE_ID DEVICE_ID
FROM ACTIVITY A
JOIN (SELECT PLAYER_ID, MIN(EVENT_DATE) EVENTDATE
	  FROM ACTIVITY
	  GROUP BY PLAYER_ID) FL 
ON A.PLAYER_ID = FL.PLAYER_ID AND
	   A.EVENT_DATE = FL.EVENTDATE;
```
![512](512.png)

<BR><BR><BR>







# 577 - Employee Bonus

```SQL
SELECT NAME, BONUS
FROM EMPLOYEE E
LEFT JOIN BONUS B ON E.EMPID = B.EMPID
WHERE B.BONUS < 1000 OR
      B.BONUS IS NULL;
```
![577](577.png)

<br><br><br>





# 584. Find Customer Referee

```SQL
SELECT C.NAME NAME
FROM CUSTOMER C
LEFT JOIN CUSTOMER R ON C.REFEREE_ID = R.ID
WHERE R.ID IS NULL OR 
      R.ID != 2;
```
![584](584.png)

<BR><BR><BR>







# 586. Customer Placing the Largest Number of Orders

```SQL
SELECT CUSTOMER_NUMBER
FROM (SELECT CUSTOMER_NUMBER, COUNT(ORDER_NUMBER) COUNT
      FROM ORDERS
      GROUP BY CUSTOMER_NUMBER
      ORDER BY COUNT DESC)
WHERE ROWNUM = 1;
```
![586](586.png)

<BR><BR><BR>







# 595. Big Countries

```SQL
SELECT NAME, POPULATION, AREA
FROM WORLD
WHERE POPULATION > 25000000 OR
	   AREA > 6000000;
```
![595](595.png)

<BR><BR><BR>





# 596. Classes More Than 5 Students

```SQL
SELECT CLASS
FROM COURSES
GROUP BY CLASS
HAVING COUNT(*) >= 5;
```
![596](596.png)

<BR><BR><BR>





# 597. Friend Requests I: Overall Acceptance Rate

```SQL
SELECT 
	ROUND((SELECT COUNT(*) FROM REQUESTACCEPTED) / (SELECT COUNT(*) FROM FRIENDREQUEST), 2) ACCEPT_RATE
FROM DUAL;
```
![597](597.png)

<BR><BR><BR>




