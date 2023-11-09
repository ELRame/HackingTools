# Cracking/brute force passwords

-------------------------------------

## Jhon the Ripper

**Quick command**

To crack a hash with a known wordlist (rockyou is the most common for ctfs), you can just type de following:

````
jhon -w="/usr/share/wordlists/rockyou.txt" file --format=NT
````

Consider that -w argument sets the path file for your wordlist and file should be a txt file with the hash to crack inside.

---------------------------------------------

## Hydra

**Quick command**

To bruteforce a password for an especific user over ftp service:

````
hydra -l user -P /usr/share/wordlists/rockyou.txt -v ip ftp
````

-----------------------------------------------

## Aircrack-ng

**Quick command for wireless cracking**

````
$ aircrack-ng '*/target file.cap*' -w */wordlist*
````

