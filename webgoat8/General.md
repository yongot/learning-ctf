# General

## HTTP Basics

### 2 - Try It!

Enter your name = `tonnctf`

### 3 - The Quiz

Was the HTTP command a POST or a GET = `POST /WebGoat/HttpBasics/attack1 HTTP/1.1`
Answer = `POST` 

What is the magic number = hidden field `magic_num` in the page source. 
Answer = `13`


## HTTP Proxies

### 5 - Configure a breakpoint filter

Intercept the request and change it to
1. Change the Method to GET
2. Add a header 'x-request-intercepted:true'
3. Remove the request body and instead send 'changeMe' as query string parameter and set the value to 'Requests are tampered easily' (without the single quotes)

Final raw payload
```
GET /WebGoat/HttpProxies/intercept-request?changeMe=Requests%20are%20tampered%20easily HTTP/1.1
Host: www.webgoat.local
Accept: */*
X-Requested-With: XMLHttpRequest
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/85.0.4183.83 Safari/537.36
Origin: http://www.webgoat.local
Referer: http://www.webgoat.local/WebGoat/start.mvc
x-request-intercepted: true
Accept-Encoding: gzip, deflate
Accept-Language: en-US,en;q=0.9
Cookie: JSESSIONID=KZIimzw-yD0gEk9c4ciKVwHJNgbEeeO5sRNetZeK
Connection: close
```

## Developer Tools

### 4 - Try It! Using the console

Use developer tool console - run javascript function
``` webgoat.customjs.phoneHome()```

Output is
```
phone home said {"lessonCompleted":true,"feedback":"Congratulations. You have successfully completed the assignment.","output":"phoneHome Response is 1433628319","assignment":"DOMCrossSiteScripting","attemptWasMade":true}
```

Paste the random number `1433628319` and submit

### 6 - Try It! Working with the Network tab

First request body
```networkNum=16.88851870898751```

Second request body
```number=16.88851870898751&network_num=16.88851870898751```

## The CIA Triad

### 5 - Quiz
1. How could an intruder harm the security goal of confidentiality?
```Solution 3: By stealing a database where names and emails are stored and uploading it to a website.```

2. How could an intruder harm the security goal of integrity?
```Solution 1: By changing the names and emails of one or more users stored in a database.```

3. How could an intruder harm the security goal of availability?
```Solution 4: By launching a denial of service attack on the servers.```

4. What happens if at least one of the CIA security goals is harmed?
```Solution 2: The systems security is compromised even if only one goal is harmed.```


## Crypto Basics

### 2 - Base64 Encoding

HTTP Header with basic authentication
```Authorization: Basic dG9ubmN0ZjphZG1pbg==```

Decode with base 64 return result
```tonnctf:admin```

Username = tonnctf
Password = admin

### 3 - Other Encoding

Database password encoded as `{xor}Oz4rPj0+LDovPiwsKDAtOw==`

It was WebSphere Password Decorder [here](http://www.sysman.nl/wasdecoder/)

The decoded result is `databasepassword`


### 4 - Plain Hasing

1. Which password belongs to this hash:
`21232F297A57A5A743894A0E4A801FC3`

Solution:
Using reverse MDS 5 [here](https://md5.gromweb.com/?md5=21232f297a57a5a743894a0e4a801fc3)
Answer: admin

2. Which password belongs to this hash:
`8F0E2F76E22B43E2855189877E7DC1E1E7D98C226C95DB247CD1D547928334A9`

Solution:
Using sha256 reverse [here](https://hashtoolkit.com/decrypt-sha256-hash/8f0e2f76e22b43e2855189877e7dc1e1e7d98c226c95db247cd1d547928334a9)
Answer: passw0rd


### 5 - RAW Signatures
Here is a simple assignment. A private RSA key is sent to you. Determine the modulus of the RSA key as a hex string, and calculate a signature for that hex string using the key.
```
-----BEGIN PRIVATE KEY-----
MIIEuwIBADANBgkqhkiG9w0BAQEFAASCBKUwggShAgEAAoIBAQC211+K2XwnYX8KNNCZOGKprYqgxqroXijTuUVlAOxLLwv6VoznB81CcfaJtAfKSuo+np9wgrsx/CZhPcATHXoRxGRnYVz3WlsU4q3RjMa3x1OnekzV3kCr7vU//3oFk89Kue8JZEnDE9saizQ0Laj+2pIi5hi2001K2dmavFCi1qhDV7sNdF7vv4kvMhXkn9w0mA9ohfEXb8LM53b9rw0wjFlGir7k0r7hZ5y5GQ9/uLuWfAF5hod4+HHyzBxTFwjCOyqN0mAjT+2LSCOxKLczXlW8RSskiPsbS43HsbkYnnYk5ZwlXMrr8UHT9uNLB3mBbGseeFI2g2YCbIkP+l+bAgEFAoIBAEki8wRW/nYm/52uudbjWqpFaqa13faMEFSwgihmxOrfnmQinsLP67QtldCuaYQd90w/cvnN5Hpk3CblgAelZAcbW1yNWGLw8TuN3yCeteMch9yXUe8ls3f5LuZmMM8H7IRKX51bULRuV6Q3rntFdsxXbaePPRXuHuq9ij3k7Q3uyHPG6Enh8M87MB0oRjRlLZHVAhwPj5JiSfjrJ2V39zHqA3vEjs2X6jAmCb57tWzXo392kFHywwCfW7KyCbwlEZk+Sou1wqHdm1/IeKTwVlzsCdfDWpOWb435y3Ewp93+8nTB2M8kCs+25Le6uS3iOCrOhSUTDMGXfovWoKlrFx0CgYEA8Imd7nTsdnjrKqoMDh4QVndf3TvcQGeSBYP4hPZgfumLJgoGUUb6OUP8RBaLRutV+oiyTJWCmbGd+wFVyRM3MwQO8Y5r5wk21f9i8QRrDW5WTh9OhgX9y/Mh9MDr8i996aSVZ5ZZxP/Nv2RiP6ikeBkV4iwfcM4RjKME2OiVh00CgYEAwphIh9/TDnDAZjxBWEOSk9CjrOaCycHoBFqjD4mipEo4KocZCJvcvCUMQEZYgwRHqE8hTBclBkXMEbK5OumDKb8QfqIgEoVvExxwBRBk0dy57wGOQq2TGEU5HGvMIz4jLlxrloko6uTaRqRB1K+tdP1SPBWpQYR3HQHPHn/ZHocCgYEAwG4X8fcjkfpVu7s82BgNEfkZfcl9AFLbN5zG0MUZ/yE8Hm5rdDjILc/9A0U8OLxEyG1bcHebriexlZqrB0KSjzZyWthWUm3Fd/+CWmnvPfHepOXYazf+PMKBkJpWW1kxh7bd7HhH0MykmR0bZiCDk0dEtPAZJwtBPU83E+1EbD0CgYBN1oNpjLrSk4Ao5ObwGwduU3Srj2eD5ymbV3RsnXRBt0mqnHBp1/Hk256AHCNnm0/c7HO4CUICglGgreOxKjR3GTnMQNmhAixuC2ACBo66WEpfmjjneKE86H0+kYTa5aesJPfV0HbEW4qCqBpVExIuy7p+bxCAm2LYZx+lzL0/aQKBgD2iTqdi2WmD2ZuxabHEDKCRoJRRmlIOaIeQnf1yOT1/BJoGi2qhxLmPRTwssPCTQlNonnJvYGfzkAdsuqtz5KTalYrj44HU06R0SxE14sAzz4wGJI6n0QsswrdN5Np4SnEx8jVFyTMsWdXfIXPVT9HKylcIIDVQrEQthkHtS3IV
-----END PRIVATE KEY-----
```

1. Then what was the modulus of the public key

Solution:

Steps:
1. Using Windows Ubuntu LTS, create id_rsa private key with above content
2. Make sure the permission of id_rsa file is 700
```chmod 700 id_rsa```
3. Run command to generate public key from private key
```openssl rsa -in id_rsa -pubout > id_rsa.pub```
4. Cat the content of id_rsa.pub
```
-----BEGIN PUBLIC KEY-----
MIIBIDANBgkqhkiG9w0BAQEFAAOCAQ0AMIIBCAKCAQEAttdfitl8J2F/CjTQmThi
qa2KoMaq6F4o07lFZQDsSy8L+laM5wfNQnH2ibQHykrqPp6fcIK7MfwmYT3AEx16
EcRkZ2Fc91pbFOKt0YzGt8dTp3pM1d5Aq+71P/96BZPPSrnvCWRJwxPbGos0NC2o
/tqSIuYYttNNStnZmrxQotaoQ1e7DXRe77+JLzIV5J/cNJgPaIXxF2/CzOd2/a8N
MIxZRoq+5NK+4WecuRkPf7i7lnwBeYaHePhx8swcUxcIwjsqjdJgI0/ti0gjsSi3
M15VvEUrJIj7G0uNx7G5GJ52JOWcJVzK6/FB0/bjSwd5gWxrHnhSNoNmAmyJD/pf
mwIBBQ==
-----END PUBLIC KEY-----
```
4. Find the modulus of this public key
```openssl rsa -pubin -in id_rsa.pub -modulus -noout```
5. The output of the above command
```
Modulus=B6D75F8AD97C27617F0A34D0993862A9AD8AA0C6AAE85E28D3B9456500EC4B2F0BFA568CE707CD4271F689B407CA4AEA3E9E9F7082BB31FC26613DC0131D7A11C46467615CF75A5B14E2ADD18CC6B7C753A77A4CD5DE40ABEEF53FFF7A0593CF4AB9EF096449C313DB1A8B34342DA8FEDA9222E618B6D34D4AD9D99ABC50A2D6A84357BB0D745EEFBF892F3215E49FDC34980F6885F1176FC2CCE776FDAF0D308C59468ABEE4D2BEE1679CB9190F7FB8BB967C0179868778F871F2CC1C531708C23B2A8DD260234FED8B4823B128B7335E55BC452B2488FB1B4B8DC7B1B9189E7624E59C255CCAEBF141D3F6E34B0779816C6B1E7852368366026C890FFA5F9B
```

Answer:
```
B6D75F8AD97C27617F0A34D0993862A9AD8AA0C6AAE85E28D3B9456500EC4B2F0BFA568CE707CD4271F689B407CA4AEA3E9E9F7082BB31FC26613DC0131D7A11C46467615CF75A5B14E2ADD18CC6B7C753A77A4CD5DE40ABEEF53FFF7A0593CF4AB9EF096449C313DB1A8B34342DA8FEDA9222E618B6D34D4AD9D99ABC50A2D6A84357BB0D745EEFBF892F3215E49FDC34980F6885F1176FC2CCE776FDAF0D308C59468ABEE4D2BEE1679CB9190F7FB8BB967C0179868778F871F2CC1C531708C23B2A8DD260234FED8B4823B128B7335E55BC452B2488FB1B4B8DC7B1B9189E7624E59C255CCAEBF141D3F6E34B0779816C6B1E7852368366026C890FFA5F9B
```

2. provide a signature for us based on that modulus

Solution:
Steps:
1. generate signature binary file
```echo -n "B6D75F8AD97C27617F0A34D0993862A9AD8AA0C6AAE85E28D3B9456500EC4B2F0BFA568CE707CD4271F689B407CA4AEA3E9E9F7082BB31FC26613DC0131D7A11C46467615CF75A5B14E2ADD18CC6B7C753A77A4CD5DE40ABEEF53FFF7A0593CF4AB9EF096449C313DB1A8B34342DA8FEDA9222E618B6D34D4AD9D99ABC50A2D6A84357BB0D745EEFBF892F3215E49FDC34980F6885F1176FC2CCE776FDAF0D308C59468ABEE4D2BEE1679CB9190F7FB8BB967C0179868778F871F2CC1C531708C23B2A8DD260234FED8B4823B128B7335E55BC452B2488FB1B4B8DC7B1B9189E7624E59C255CCAEBF141D3F6E34B0779816C6B1E7852368366026C890FFA5F9B" | openssl dgst -sha256 -sign id_rsa -out sign.sha256```

2. encode signature binary file with base64
```openssl enc -base64 -in sign.sha256 -out sign.sha256.base64```

3. Cat the content of sign.sha256.base64
```
cbOvyLltR3FfrbuVG+X365Et4DYdLtrJIrai2idcfsd+CxGd+3tpUnu4q9twlRW9
rJ21NikVihp2Kf61adqm/OhrjV4F+66FnT0GeFiZXIgRrpkfSbpOd0r0xUdpOaUa
713u6ZDipVBvpoE/8ljy2iRIqF0IklzQun6ajNSg2lZlpnIZmAq/mSg2oY4kN27D
A0X4cyS6g9EWLxZdkI65Y4xxKExLXelITeDe1tR0psEAS2fgo9BBYrqTCLz96Bzh
8LuT0U9SZKrKZQutNhaYeS/J1OuRB22bEcORguK42hMECx5ak2RLS/D9d6vuNjYR
ELy54AKOs3VoLlcumeDvfA==
```

Answer:
```
cbOvyLltR3FfrbuVG+X365Et4DYdLtrJIrai2idcfsd+CxGd+3tpUnu4q9twlRW9
rJ21NikVihp2Kf61adqm/OhrjV4F+66FnT0GeFiZXIgRrpkfSbpOd0r0xUdpOaUa
713u6ZDipVBvpoE/8ljy2iRIqF0IklzQun6ajNSg2lZlpnIZmAq/mSg2oY4kN27D
A0X4cyS6g9EWLxZdkI65Y4xxKExLXelITeDe1tR0psEAS2fgo9BBYrqTCLz96Bzh
8LuT0U9SZKrKZQutNhaYeS/J1OuRB22bEcORguK42hMECx5ak2RLS/D9d6vuNjYR
ELy54AKOs3VoLlcumeDvfA==
```


Useful SSH and OpenSSL command reference
```
# Convert the public key into PEM format
ssh-keygen -f path/to/id_rsa.pub -e -m pem > ~/id_rsa.pub.pem

# Using the public pem file to encrypt a string
echo "sometext" | openssl rsautl -encrypt -pubin -inkey ~/id_rsa.pub.pem > ~/encrypted.txt

# Or a file
cat ~/some_file.txt | openssl rsautl -encrypt -pubin -inkey ~/id_rsa.pub.pem > ~/encrypted.txt

# To decrypt, you'll need the private key
cat ~/encrypted.txt | openssl rsautl -decrypt -inkey path/to/id_rsa > ~/decrypted.txt

```

### 8 - Default Configuration Assignment

Decrypt the message: `U2FsdGVkX199jgh5oANElFdtCxIEvdEvciLi+v+5loE+VCuy6Ii0b+5byb5DXp32RPmT02Ek1pf55ctQN+DHbwCPiVRfFQamDmbHBUpD7as=`

Steps:
1. Run the docker that has the secret
```docker run -d webgoat/assignments:findthesecret```

2. Find the container ID of the docker
```docker ps```

3. The container ID is `9511f178355e`

4. Get bash shell in the container as root user
```docker exec -it -u 0 9511f178355e /bin/bash```

5. Cat the secret file content
```cat /root/default_secret```

6. Output of /root/default_secret
```ThisIsMySecretPassw0rdF0rY0u```

7. Run the command to get the unencrypted message
```echo "U2FsdGVkX199jgh5oANElFdtCxIEvdEvciLi+v+5loE+VCuy6Ii0b+5byb5DXp32RPmT02Ek1pf55ctQN+DHbwCPiVRfFQamDmbHBUpD7as=" | openssl enc -aes-256-cbc -d -a -kfile /root/default_secret```

8. Output of the command is
```
Leaving passwords in docker images is not so secure
```

1. What is the unencrypted message
Answer: `Leaving passwords in docker images is not so secure`

2. What is the name of the file that stored the password
Answer: `default_secret

## Writing new lesson

### 4 - Add An Assignment to Your lesson

Parameter 1: `secr37Value`
Parameter 2: `abc``
  







