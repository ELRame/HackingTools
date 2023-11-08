# SQL Injection

------------------------------

## Most known

Most known query used for SQL Injection is ````'OR 1=1````

**Medium difficulty dvwa example**

Inspect the site and select the button, then change the value and click on submit:

![image](https://github.com/ELRame/HackingTools/assets/82544416/da9242d0-b0dd-401b-8371-52dbb66c8db6)

**High difficulty dvwa example**

Same as low level on dvwa, the textbox has the same vulnerability, just that the form is prompted on another tab, you can just run it and the information will be displayed on the main page. Query:

````
1’ UNION SELECT user, password FROM users#
````

-------------------------------------

## Blind 

Sometimes when the site doesn't show any information on a login page you can use blind injection, this mean just to try sql commands and see what happend, for example:

````
' OR 1=1 --
````

Where the double dash just comment all the following query in the execution when you submit it. 
