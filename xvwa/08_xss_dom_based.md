# Cross Site Scripting (XSS) – DOM

## Testing (UNSUCCESSFUL)
Note that browsers behave differently with regards to URL-encoding, Chrome, Firefox, and Safari will URL-encode location.search and location.hash, 
while IE11 and Microsoft Edge (pre-Chromium) will not URL-encode these sources. If your data gets URL-encoded before being processed, then an XSS attack is unlikely to work.


Payload: <script>alert(document.cookie)</script>

## References
https://owasp.org/www-community/attacks/DOM_Based_XSS
https://portswigger.net/web-security/cross-site-scripting/dom-based
