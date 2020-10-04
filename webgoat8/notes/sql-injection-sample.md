# Example of SQL injection

SQL query in the code
```"SELECT * FROM users WHERE name = '" + userName + "'";```

Possible injections
- `Smith’ OR '1' = '1`
   results in SELECT * FROM users WHERE name = 'Smith' OR TRUE; and that way will return all entries from the users table

- `Smith’ OR 1 = 1; --`
   results in SELECT * FROM users WHERE name = 'Smith' OR TRUE;--'; and that way will return all entries from the users table

- `Smith’; DROP TABLE users; TRUNCATE audit_log; --`
   chains multiple SQL-Commands and deletes the USERS table as well as entries from the audit_log

# What is SQL query chaining?
Query chaining is exactly what it sounds like. 
When query chaining, you try to append one or more queries to the end of the actual query. 
You can do this by using the `;` metacharacter which marks the end of a query and that way allows to start another one right after it within the same line.

# Special Characters
```
/* */ 	 are inline comments
-- , # 	 are line comments

Example: SELECT * FROM users WHERE name = 'admin' --AND pass = 'pass'
```  

```
;        allows query chaining

Example: SELECT * FROM users; DROP TABLE users;
```

```
',+,||	 allows string concatenation
Char()	 strings without quotes

Example: SELECT * FROM users WHERE name = '+char(27) OR 1=1
```

# Special Statements
Union
```SELECT first_name FROM user_system_data UNION SELECT login_count FROM user_data;```

Joins
```SELECT * FROM user_data INNER JOIN user_data_tan ON user_data.userid=user_data_tan.userid;```

# Blind SQL Injection

Blind SQL injection is a type of SQL injection attack that asks the database true or false questions and determines the answer based on the applications response. 
This attack is often used when the web application is configured to show generic error messages, but has not mitigated the code that is vulnerable to SQL injection.

There are several different types of blind SQL injections: content-based and time-based SQL injections.

## Example
In this case we are trying to ask the database a boolean question based on for example an unique id, for example suppose we have the following url: https://my-shop.com?article=4 On the server side this query will be translated as follows:
```
SELECT * FROM articles WHERE article_id = 4
```

When we want to exploit this we change the url into: https://shop.example.com?article=4 AND 1=1 This will be translated to:
```
SELECT * FROM articles WHERE article_id = 4 and 1 = 1
```

- If the browser will return the same page as it used to when using https://shop.example.com?article=4 you know the website is vulnerable for a blind SQL injection
- If the browser responds with a page not found or something else you know a blind SQL injection might not work.
-  You can now change the SQL query and test for example: https://shop.example.com?article=4 AND 1=2 which will not return anything because the query returns false

Ask more information, e.g. database version
```
https://shop.example.com?article=4 AND substring(database_version(),1,1) = 2
```

## Time-based SQL Injection
Another way is called a time-based SQL injection, in this case you will ask the database to wait before returning the result. You might need to use this if you are totally blind so there is no difference between the response you can use for example:
```
article = 4; sleep(10) --
```
