# SQL



**Examples of queries using the clause in MySql. Used skills :  SELECT, WHERE, OREDR BY, JOINS, CASE, WHERE, SUBQUERIES, DATA, GROUP BY**<br>The database is from the training program.



<details>
<summary><b>SELECT & WHERE</b></summary>

 <br>
select BusinessEntityID, JobTitle, HireDate <br> 
from HumanResources.Employee <br> 
where HireDate >'20120112'; <br>
 <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198397801-908d6bde-f875-4dd5-8806-ce890ab4c6a3.png)
 
<br>
 select BusinessEntityID, JobTitle, HireDate, OrganizationLevel, Gender<br>
 from HumanResources.Employee<br>
 where OrganizationLevel <2 and (Gender ='F' or Gender='M');<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198398097-737d0364-7f49-41ab-90a8-6c4c6120ef03.png)

<br>
 select BusinessEntityID, SickLeaveHours<br>
 from HumanResources.Employee<br>
 where SickLeaveHours between 40 and 50;<br>
 <br>
 
![image](https://user-images.githubusercontent.com/115644864/198403066-4bfdabc3-0fc5-4c03-92b6-04914e3485d8.png)

<br>
select *<br>
from Person.CountryRegion<br>
where Name like 'A%';<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198403274-e7e07a6e-08a5-4154-b0a9-bf6828c65175.png)

<br>
 select *<br>
from Person.CountryRegion<br>
where CountryRegionCode like '[B-E]%';<br>
 <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198403742-c81a6bab-abc7-451a-ba2c-cc345b2f5b29.png)

 <br>
 
 select * <br>
from Person.CountryRegion <br>
where Name like '_o%'; <br>
  <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198403850-6340dc0f-01b9-45c0-8e23-50e7afd0e461.png)
 
  <br>

 </details>
 
 <details>
<summary><b>OREDR BY</b></summary> <br>
 select BusinessEntityID, JobTitle as "Stanowisko pracownika", HireDate, MaritalStatus<br>
from HumanResources.Employee<br>
where MaritalStatus='M'<br>
order by 1 desc;<br>
 <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198404464-49a51dae-d0df-4e4d-829e-cc5302cf8bc5.png)

  <br>
 
 select BusinessEntityID, JobTitle as "Stanowisko pracownika", HireDate, MaritalStatus  <br>
from HumanResources.Employee  <br>
where MaritalStatus='M'  <br>
order by 1 desc, HireDate  <br>
   <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198404676-51d35c10-9441-4401-b3ef-62d2079b0517.png)

 
   <br>
  </details>
