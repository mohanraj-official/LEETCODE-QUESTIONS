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
