# DNS Enumeration

--------------------------

### Nslookup

Enumerate:

````
nslookup url
````

Specific type:

````
nslookop
set type=type
url
````

Zone Transfer:

````
nslookop
set type=ns
server servername
set type=any
url
ls -d url
````


--------------------------
### Dig

Enumerate:

````
dig url
````

Specific type:

````
dig type url
````

Type: NS, MX, A, etc...

Zone Transfer (before this, perform ns enumeration):

````
dig axfr url @servername
````

-----------------------
### Host

Enumerate:

````
host url/ip
````
**ip**. If you use an ip can do a reverse lookup in order to find the domain.


Specific type:

````
host -t type url
````

Zone Transfer (before this, perform ns enumeration):

````
host -l url servername
````


![image](https://github.com/ELRame/HackingTools/assets/82544416/a90dfdf3-2260-4de5-8e13-979ce75167da)

