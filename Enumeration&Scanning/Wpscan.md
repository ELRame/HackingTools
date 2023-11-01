## Wordpress and Wpscan ##
------------------------

### WPSCAN ###

In order to use wpscan for enumerate, first check if your wpscan is working, since mine didn't on a full update parrot OS machine:

![image](https://github.com/ELRame/HackingTools/assets/82544416/0f606437-000a-4cb2-8ba3-dfde3e70e58e)

There could be several reasons why wpscan is not working, the one that fixed my problem was typing the following command:

** gem install wpscan **

with that, wpscan ran without problems:

![image](https://github.com/ELRame/HackingTools/assets/82544416/6bdb0487-7ff8-486c-9547-bab44fa5892e)

And well, finally just run the command to scan the url or ip you want to scan.

** wpscan --url ulr/ip **

and done!
