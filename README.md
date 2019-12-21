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
Some applications determine the user's access rights or role at login, and then store this information in a user-controllable location, such as a hidden field, cookie, or preset query string parameter. The application makes subsequent access control decisions based on the submitted value. For example:

```code
https://insecure-website.com/login/home.jsp?admin=true
https://insecure-website.com/login/home.jsp?role=1
```

This approach is fundamentally insecure because a user can simply modify the value and gain access to functionality to which they are not authorized, such as administrative functions. 
Configuration browser
```conf
127.0.0.1:8080
```
Intercept under proxy tab in Burp -> action send to repeater -> change admin from ```False``` to ```True``` click on send. 
Copy the cookie in the browser, turn of intercepter under proxy, and login into the admin pannel. 

Change role
``` https://insecure-website.com/login/home.jsp?role=1 ```
to change the role, update the email, from proxy sen to the repeater and you will see the role in json body as response, then update the json and resend it. Turn off proxy and go to main page and complete the task. 
