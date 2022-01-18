# OWASP Juice Shop CTF

</br>

## Setup

1. For your own convenience use any distribution of Linux.

2. Install Docker:

    ```
    sudo apt install docker.io
    ```
    
3. Get Juice Shop:
    
    ```
    docker pull bkimminich/juice-shop
    ```
    
4. Run Juice Shop in CTF mode:

    ```
    docker run -d -e "NODE_ENV=ctf" -p 3000:3000 bkimminich/juice-shop
    ```

5. Browse to localhost port 3000:

    ```
    http://127.0.0.1:3000
    ```
    
6. In a new tab browse to http://192.168.222.131 and register. Your username should be of *firstname_lastname* format.

</br>
</br>

## Exercises

### 1. Login Admin (Injection)
  The name says it all but you can solve it with even more basic knowledge.
   
</br>   
   
### 2. DOM XSS (XSS)
  Use Document Object Model (DOM, API for HTML and XML documents) to craft a Cross-Site Scripting Attack (XSS).

</br>

### 3. CSRF (Broken Access Control)
  Change username using a Cross-Site Request Forgery attack from another source. Things that could come in handy:
  - this page: http://htmledit.squarefree.com
  - this piece of HTML:
  
    ```
    <form action="http://localhost:3000/profile" method="POST">
    <input name="username" value="CSRF"/>
    <input type="submit"/>
    </form>
    <script>document.forms[0].submit();</script>
    ```
    
</br>

### 4. Admin Registration (Improper Input Validation)
  Register as a user with admin privileges. You can perform it using browser tools or [*Postman*](https://www.postman.com/).

</br>

### 5. Christmas Special (Injection)
  Order a product from the Christmas offer of 2014 which isn't available anymore. Find out how the application hides deleted products from the clients. Craft an attack that will make the products visible again. Add this certain product to the basket and proceed to checkout. This solution requires (half-)Blind SQL Injection - unless you find some other idea here. 

</br>

### 6. Any challenge from Miscellaneous
  Solve any challenge from Miscellaneous category. 
