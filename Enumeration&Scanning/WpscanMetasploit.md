## Wpscan or Metasploit Wordpress Enumeration ##
------------------------

### WPSCAN ###

In order to use wpscan for enumerate, first check if your wpscan is working, since mine didn't on a full update parrot OS machine:

![image](https://github.com/ELRame/HackingTools/assets/82544416/0f606437-000a-4cb2-8ba3-dfde3e70e58e)

There could be several reasons why wpscan is not working, the one that fixed my problem was typing the following command:

**gem install wpscan**

with that, wpscan ran without problems:

![image](https://github.com/ELRame/HackingTools/assets/82544416/6bdb0487-7ff8-486c-9547-bab44fa5892e)

And well, finally just run the command to scan the url or ip you want to scan.

**wpscan --url ulr/ip**

![image](https://github.com/ELRame/HackingTools/assets/82544416/70c9ec51-597b-4c14-bc01-2180c629c630)

If for any reason you want to enumerate users, you can type the following command:

**wpscan --url url/ip -e u**

![image](https://github.com/ELRame/HackingTools/assets/82544416/f0288676-7ab5-46d4-943f-77216c557d94)

This will ran the scan and gives you the information you need, also, if you want to check more arguments for your scans, you can always use **wpscan --help**.

In order to test a bruteforce, you can use:

**wpscan --url url/ip --usernames file --passwords file**

![image](https://github.com/ELRame/HackingTools/assets/82544416/f1299a91-01df-4bc1-99e6-8164f22f2ae8)

If you already have the username you want to test, u can use de argument **-u** instead **--usernames**.

and done!

------------------------------------

### Metasploit ###

In case wpscan doesn't work and you need to enumerate users and perform a bruteforce test on users, you can always relay on Metasploit, run it with **msfconsole** and search the auxiliary which can be **use auxiliary/scanner/http/wordpress_login_enum**. Make sure that after that, use command **show options** so you can see which are the fields you need to fill in order to execute the test.

![image](https://github.com/ELRame/HackingTools/assets/82544416/35ddff21-73f3-4479-b4a1-96f3cca2413a)

After filling the fields with "**SET** **FIELD**", just run the attack test with **exploit**

![image](https://github.com/ELRame/HackingTools/assets/82544416/50ac8572-a2b4-40de-8707-9023e0f4f3d6)

That should help you to test the site you want.
