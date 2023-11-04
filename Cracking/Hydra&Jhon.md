# Cracking passwords

-------------------------------------

## Jhon the Ripper

**Quick command**

To crack a hash with a known wordlist (rockyou is the most common for ctfs), you can just type de following:

````
jhon -w="/usr/share/wordlists/rockyou.txt" file --format=NT
````

Consider that -w argument sets the path file for your wordlist and file should be a txt file with the hash to crack inside.
