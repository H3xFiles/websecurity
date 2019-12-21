# websecurity
Notes about web hacking

## Access control vulnerabilities and privilege escalation
- vertical:
  User -> super-user -> admin
- horizontal:
  User1(local admin) - User2(local admin) - User3(local admin)


## Unprotected functionality
```html
 https://insecure-website.com/admin 
 https://insecure-website.com/robots.txt 
```
Or the functionalities are inside a js script
```js
 <script>
var isAdmin = false;
if (isAdmin) {
  ...
  var adminPanelTag = document.createElement('a');
  adminPanelTag.setAttribute('https://insecure-website.com/administrator-panel-yb556');
  adminPanelTag.innerText = 'Admin panel';
  ...
}
</script> 
```

## Parameter-based access control methods
For this lab I used burb

Configuration browser
```conf
127.0.0.1:8080
```
Intercept under proxy tab in Burp -> action send to repeater -> change admin from ```False``` to ```True``` click on send. 
Copy the cookie in the browser, turn of intercepter under proxy, and login into the admin pannel. 
