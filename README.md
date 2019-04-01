# Project 8 - Pentesting Live Targets

Time spent: **10** hours spent in total

> Objective: Identify vulnerabilities in three different versions of the Globitek website: blue, green, and red.

The six possible exploits are:
* Username Enumeration
* Insecure Direct Object Reference (IDOR)
* SQL Injection (SQLi)
* Cross-Site Scripting (XSS)
* Cross-Site Request Forgery (CSRF)
* Session Hijacking/Fixation

Each version of the site has been given two of the six vulnerabilities. (In other words, all six of the exploits should be assignable to one of the sites.)

## Blue

Vulnerability #1: SQL Injection (SQLi)

  ![SQL Injection (SQLi)](https://github.com/Jamaliela/week_9_Assignment_Jamali_Ela/blob/master/SQLi.gif)

  > Notes: First we need to identify if the website that has SQLi vulnerability which means the input is not
    being sanitized before being used in an SQL query. Going to the list of Salesperson, we see that by changing 
    the id to ' we get Database query failed. so now we know that it is vulnerable. now we want to change 
    the session id and go from one user to another one. we use or ' or id=(number of the id we are changing to) --' 
    and we encode it to URL and paste it to our URL. 

Vulnerability #2: Session Hijacking/Fixation

  ![Session Hijacking/Fixation](https://github.com/Jamaliela/week_9_Assignment_Jamali_Ela/blob/master/Session_Hijacking.gif)
  
  > Notes: Here I have tried session hijacking. First, I logged the target in Chrome and inspected the page to find the session ID,
    then I copied the index.php URL to another browser like Firefox here and it gave me the log in page. I used burp to see the 
    session ID and they are different so I gave the logged-in session ID to the attacker in Firefox and submit it. We can see 
    the page that it is logged in so it is vulnerable.

## Green

Vulnerability #1: Username Enumeration

   ![Username Enumeration](https://github.com/Jamaliela/week_9_Assignment_Jamali_Ela/blob/master/User_Enumeration.gif)
  
   > Notes: First I used the existing username "jmonroe99" as a test and a random password. We can see the error message
    is bold. Then I tried a random username and a password that does not exist and the error is not bold for that. We can see
    the developer has created a username enumeration vulnerability.

Vulnerability #2: Cross-Site Scripting (XSS)

   ![Cross-Site Scripting (XSS)](https://github.com/Jamaliela/week_9_Assignment_Jamali_Ela/blob/master/XSS.gif)
 
   >Notes: Green Website is  vulnerable to XSS attack. To see this we can use a stored XSS. In feedback section 
   we put the Javascript <script>alert('Ela found the XSS!');</script> then we submit the feedback. We log in as
   an admin and when we want to open the feedback page we can see that we get an alert box and if we press ok we 
   see different names and finally we are redirected to a website. I have blocked the JavaScript in the browser 
   so we can see the first person that has stored the XSS and therefore their alert box and website apears when 
   we click on the feedback section.

## Red

Vulnerability #1: Insecure Direct Object Reference (IDOR)

   ![Insecure Direct Object Reference (IDOR)](https://github.com/Jamaliela/week_9_Assignment_Jamali_Ela/blob/master/IDOR.gif)
 
   >Notes: Red Website is missing code which prevents some sensitive information from being made public. How do we know that? 
   There are some users like user with id=11 and id=10 that are not in the salesperson lists because they are fired or 
   they are a private user for now but with changing the URL to their id we can see their information. 
   The other websites redirect you to the salesperson list when you change the id to either 10 or 11. 
   so they are not vulnerable like red.

Vulnerability #2: Cross-Site Request Forgery (CSRF)

   ![Cross-Site Request Forgery (CSRF)](https://github.com/Jamaliela/week_9_Assignment_Jamali_Ela/blob/master/CSRF.gif)
   
   >Notes: As the attacker in website red I designed a form that made a change to the spelling of the database content.
   I used GitHub.io to create my Github page and use it as my source. I took the form for updating the spelling of one 
   of the countries in the form and changed it from Canadaaaa to ElahehCanada and used the link to the github page 
   in the feedback section. The target would open the URL suggested in the feedback and without seeing the form 
   the database content gets updated.

## Notes

Describe any challenges encountered while doing the work

> One of the big challenges for me was reminding myself about each vulnerabilities and how to approach them. 
It was very fun and exciting to work with several vulnerabilities at the same time. I struggled a bit with CSRF as I was not sure
what to use as my source until I learned about github pages. Other than that I think it was a challenging but rewarding assignment. 


