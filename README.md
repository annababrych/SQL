# SQL 



**Examples of queries using the clause in MySql. Used skills : SELECT, WHERE, ORDER BY, CAST, CONVERT, GROUP BY, CASE, DATA, JOINS (INNER, RIGHT, LEFT, FULL), SUBQUERIES, .**<br>

<i>The database is from the training program.</i>



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
select top 8 DepartmentID as Numer_Departamentu, Name as<br>
"Nazwa departamentu" <br>
from HumanResources.Department;<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198405221-c43f6707-be3a-42dc-b62c-7d60b8c1ef19.png)


<br>



 </details>
 
 <details>
<summary><b>ORDER BY</b></summary> <br>
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
select top 1 LocationID, Name, CostRate<br>
from Production.Location<br>
order by CostRate desc<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198405424-f4137155-0e2c-452c-83f6-df3d857dc2d2.png)


<br>
  </details>
<details>
<summary><b>CAST & CONVERT</b></summary> <br>
select cast(VacationHours as float)/8 as Kolumna<br>
from HumanResources.Employee<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198734683-9642c777-da5a-4761-9540-4ce8cf072d27.png)

<br>
select getdate() as "Aktualna data z godzina"<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198734771-81ecfb76-19a0-4b69-8476-bed2b00909a4.png)


<br>
select BusinessEntityID, <br>
cast(RateChangeDate as date) as "Data zmiany", <br>
str(Rate, 7,3) as "Sfromatowana stawka"<br>
from HumanResources.EmployeePayHistory<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198735232-357bdcae-75c7-4033-af44-cbadb2ce27ab.png)


<br>
  </details>
<details>
<summary><b>GROUP BY</b></summary> <br>
select TerritoryID, sum(salesYTD) as SUMA,<br>
max(salesYTD) as MAX, <br>
min(salesYTD) as MIN,<br>
avg(SalesYTD) as ŚREDNIA<br>
from Sales.SalesPerson<br>
group by TerritoryID<br>
 <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198735827-ac146689-c280-4084-bc98-70e9f19587ae.png)

 
 <br>
 select JobTitle, gender, sum(vacationhours) as "Suma wolnych godzin" <br>
from HumanResources.Employee <br>
where MaritalStatus = 'M' <br>
GROUp by gender, JobTitle <br>
 <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198735916-141550cb-c688-4fe1-81ca-311dcc5ab439.png)

  <br>
 select JobTitle, sum(vacationhours) as "Suma wolnych godzin"  <br>
from HumanResources.Employee  <br>
GROUp by JobTitle  <br>
   <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198736155-12e68e28-fc94-4963-88c3-7da2ce24b3bc.png)

 
   <br>
   </details>
   <details>
<summary><b>CASE</b></summary> <br>
 
 select Name, <br>
	case name when 'English' then 'Angielski' <br>
	when 'spanish' then 'hiszpanski' <br>
	else 'Jakis inny jezyk'  <br>
	end as "Jezyk po polsku" <br>
from production.culture <br>
  <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198736368-3cddc545-254f-439f-8ca1-9f8df299a38f.png)
 
 <br>
 select BusinessEntityID, Gender, VacationHours, <br>
	case gender when 'F' then + 16 <br>
	else VacationHours <br>
	end as "wolne godziny" -- tworzy nowa kolumne z case  <br>
from HumanResources.Employee <br>
  <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198736482-dd8928d2-1d68-4a34-95e4-bd540131a9cf.png)

  <br>
 select Description, DiscountPct, <br>
case when DiscountPct <=0.1 then 'Mala znizka'  <br>
when DiscountPct <=2.0 then 'srednia znizka' <br>
when DiscountPct <=3.0 then 'Dobra znizka' <br>
when DiscountPct <=0.4 then 'super znizka' <br>
else 'Prawie darmo' <br>
end as "Status obnizki" <br>
from Sales.SpecialOffer <br>
  <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198736635-46caacb8-9e31-499a-9f9a-29bc018981dd.png)

  <br>
 
 select BusinessEntityID, MaritalStatus, Gender, VacationHours, <br>
case when MaritalStatus ='M'and Gender = 'F' then VacationHours + 32  <br>
when gender = 'F' then VacationHours + 16  <br>
end as "Wolne godziny po zmianie."  <br>
from HumanResources.Employee  <br>
  <br>
 
 ![image](https://user-images.githubusercontent.com/115644864/198736881-ca648f81-5081-41e0-8377-1aabd5edcac2.png)

  <br>
 select BusinessEntityID, JobTitle,  <br>
case when OrganizationLevel is Null then 'Szef wszystkich szefów'  <br>
 when OrganizationLevel <3 then 'Wiceprezesi i managerowie'  <br>
 else 'Pracownicy'  <br>
 end as 'STATUS'  <br>
from HumanResources.Employee   <br>
ORDER BY OrganizationLevel  <br>
      <br>
 
![image](https://user-images.githubusercontent.com/115644864/198737043-61d50c23-e3d4-4d95-a35e-664b120b4f45.png)
                           
 <br>                         
</details>
<details>
<summary><b>DATA</b></summary> <br>
select dateadd(day,5,getdate())<br>
<br>
	
![image](https://user-images.githubusercontent.com/115644864/198737469-9adc292d-e977-4f84-aa1c-d3f91e8ebd5b.png)
	
<br>
select dateadd(year,3,getdate()) as "aktualny rok + 3 lata"
<br>
	
![image](https://user-images.githubusercontent.com/115644864/198737607-1b0a40fc-e8e7-4b6c-9cc6-6c690ce4252e.png)

<br>
select day(getdate()) as "dzien",<br>
month(getdate()) as "msc",<br>
year(getdate()) as rok<br>
<br>
	
![image](https://user-images.githubusercontent.com/115644864/198737668-1f5685ce-9ee2-4bda-8c15-d58133733509.png)

	
<br>
select datediff(YEAR, '19841010', getdate()) as "Różnica lat."<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198738299-2af2be44-0204-4ba8-ac6d-00f953822d70.png)

	
<br>
</details>
 <details>
<summary><b>INNER JOIN</b></summary> <br>
select * <br>
from HumanResources.EmployeeDepartmentHistory as EDH, HumanResources.Shift as S  <br>
where EDH.ShiftID = S.ShiftID  <br>
order by BusinessEntityID  <br>
<br>
	
![image](https://user-images.githubusercontent.com/115644864/198738528-b2e4cb4d-b60e-4ac2-809a-2d51b6d3f28b.png)

 <br>
 select EDH.BusinessEntityID, P.FirstName, P.LastName, S.name <br>
from HumanResources.EmployeeDepartmentHistory as EDH  <br>
inner join HumanResources.Shift as S on EDH.ShiftID=S.ShiftID --tu sie powtarza kolumna shift id <br>
inner join Person.person as P on EDH.businessEntityID=P.BusinessEntityID  <br>
order by BusinessEntityID <br>
 <br>
	
![image](https://user-images.githubusercontent.com/115644864/198738622-06713fcd-d5b5-41a1-afcb-15dd56f4c039.png)
	
 <br>
select B.BusinessEntityID, T.Name, A.AddressLine1, A.PostalCode, A.city <br>
from Person.BusinessEntityaddress as B  <br>
inner join person.address as A on B.AddressID=A.AddressID <br>
inner join Person.AddressType as T on b.AddressTypeID=T.AddressTypeID;  <br>
 <br>
	
![image](https://user-images.githubusercontent.com/115644864/198738695-d979d957-1807-4f09-8b71-6975b6fb74ac.png)
	
 <br>


	
	
</details>
 <details>
<summary><b>LEFT-RIGHT-FULL JOIN</b></summary> <br>
SELECT E.OrganizationNode, D. * <br> 
FROM HumanResources.Employee AS E  <br>
LEFT JOIN Production.Document AS D  <br>
ON E.OrganizationNode = D.DocumentNode <br>
 <br>
	
![image](https://user-images.githubusercontent.com/115644864/198739078-4cfee707-8580-4ccc-b940-e8b733174ca7.png)

 <br>
SELECT E.OrganizationNode, D. *  <br>
FROM HumanResources.Employee AS E  <br>
RIGHT JOIN Production.Document AS D  <br>
ON E.OrganizationNode = D.DocumentNode <br>
 <br>
	
![image](https://user-images.githubusercontent.com/115644864/198739151-7ec38b71-90a2-4e83-be0b-2fa93baa4a62.png)

 <br>
SELECT E.OrganizationNode, D. *  <br>
FROM HumanResources.Employee AS E  <br>
FULL JOIN Production.Document AS D  <br>
ON E.OrganizationNode = D.DocumentNode <br>
 <br>
	
![image](https://user-images.githubusercontent.com/115644864/198739202-35c1d96a-e92f-41db-9ba4-f8f809710ef4.png)

 <br>
select JC.JobCandidateID, HR.* <br>
from HumanResources.Employee as HR <br>
RIGHT join HumanResources.JobCandidate as JC <br>
ON HR.BusinessEntityID=JC.BusinessEntityID <br>
ORDER BY BusinessEntityID DESC <br>
 <br>
	
![image](https://user-images.githubusercontent.com/115644864/198739293-23a42e4e-0cb2-47c6-ba77-979660738505.png)

 <br>
</details>
<details>
<summary><b>SUBQUERIES</b></summary> <br>
select BusinessEntityID, VacationHours <br>
from HumanResources.Employee --z tej tabeli <br>
where VacationHours > (select VacationHours  <br>
			from HumanResources.Employee <br>
			where BusinessEntityID=49)<br>
<br>
	
![image](https://user-images.githubusercontent.com/115644864/198739601-e18cebea-55e7-4813-bced-6b58c8d4b717.png)
	
<br>
select BusinessEntityID, VacationHours <br>
from HumanResources.Employee --z tej tabeli <br>
where VacationHours > (select VacationHours <br> 
		       from HumanResources.Employee <br>
		       where BusinessEntityID=49)<br>
and MaritalStatus=(select MaritalStatus <br>
		       from HumanResources.Employee<br>
		       where BusinessEntityID =49) <br>
<br>
	
![image](https://user-images.githubusercontent.com/115644864/198739727-f123568f-259c-4ed2-bb02-85f4204d0ba6.png)

<br>	
select *<br>
from (select BusinessEntityID, VacationHours<br>
		from HumanResources.Employee) as Podzapytanie<br>
where BusinessEntityID between 100 and 150; <br>
	
![image](https://user-images.githubusercontent.com/115644864/198739819-7646ca4e-88e7-4449-a72e-506eeda23f19.png)

<br>
select ProductID, Name, ProductNumber, Color, SafetyStockLevel<br>
from Production.Product<br>
	where Color = (select Color  <br>
		from Production.Product <br>
		where ProductNumber='FL-2301')<br>
and SafetyStockLevel>= (select SafetyStockLevel <br>
		from Production.Product <br>
		where Name='Chain')<br>
<br>

![image](https://user-images.githubusercontent.com/115644864/198739946-6c7ddd6d-d71b-47a0-a1ab-93f677a7d204.png)

	
<br>
</details>
