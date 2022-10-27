# SQL



**Examples of queries using the clause in MySql. Used skills :  SELECT, JOINS, CASE, WHERE, SUBQUERIES, DATA, OREDR BY, GROUP BY**



----------------------------------------------------
>  SELECT & WHERE 


 <P>select BusinessEntityID, JobTitle, HireDate</P> <P>from HumanResources.Employee</P><P> where HireDate >'20120112';</P>
 
 
![image](https://user-images.githubusercontent.com/115644864/198397801-908d6bde-f875-4dd5-8806-ce890ab4c6a3.png)



###### select BusinessEntityID, JobTitle, HireDate, OrganizationLevel, Gender

###### from HumanResources.Employee

###### where OrganizationLevel <2 and (Gender ='F' or Gender='M');

![image](https://user-images.githubusercontent.com/115644864/198398097-737d0364-7f49-41ab-90a8-6c4c6120ef03.png)


###### select BusinessEntityID, SickLeaveHours

###### from HumanResources.Employee

###### where SickLeaveHours between 40 and 50;

![image](https://user-images.githubusercontent.com/115644864/198398274-35bab77c-0f35-4712-871b-479884e30dec.png)



