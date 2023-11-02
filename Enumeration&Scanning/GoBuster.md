# GoBuster
------------------

## Dir Enumerate 

To enumerate directories on a site with GoBuster first it would be useful have the seclists wordlists:

````
sudo apt install seclists
````
After that, you can use the following command using the top 1 million list of seclists for enumerate directories:

````
GoBuster vhost -u url -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-20000.txt -k -- append-domain
````

**Argument details:**

vhost will perform a virtual host enumeration

-u use specified url

-w use specified dictionary

-k ignore any certificate issue

double - add domains to the dictionary 

![image](https://github.com/ELRame/HackingTools/assets/82544416/8081c8de-dab1-414a-9c5a-655aa56713f0)
