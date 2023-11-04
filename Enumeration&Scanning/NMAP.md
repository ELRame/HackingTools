# NMAP for enumeration and scanning ports #

## Enumeration ##

Part of Reconnainsance, is the enumeration part which can show you hosts, SOs, versions and port status of a network you are trying to know. In this stage, most used tool is NMAP which is an enumeration and scanning tool that can allows you to gathered information of a network (and check for vulnerabilities, but this post is for enumeration and scanning host only).

-----------------------

### Hands on ###

-----------------------

**Simple scan**

In order to get information about the network, you can use the most easy command to get it:

**nmap Ip/IpRange**: Scan a single ip or ip range. eg: nmap 192.168.1.1 (for scan just a single ip) / nmap 192.168.1.0/24 (scan the hole subnet).

![image](https://github.com/ELRame/HackingTools/assets/82544416/250477ec-f993-4ff2-913a-5b4e2ad6a2ed)

After a few seconds (considering a home or small network) we'll see the results:

![image](https://github.com/ELRame/HackingTools/assets/82544416/c66a8bc8-6aff-4d34-9007-ec46c03ea1a8)

Scan services version and SOs:

**namp -sV -O ip/range**: Scan a single or an ip range with arguments -sV for versions and -O for SO:

![image](https://github.com/ELRame/HackingTools/assets/82544416/be20ea02-4ba7-48e5-96be-faf3d3ca3791)

This scan take more time, so chill and wait.

Also you can use **nmap -sS -O ip/range** fot this scan.

Aggresive scan:

**nmap -A ip/range**: Scan a single or an ip range in aggresive mode, this will give you a lot of information, but can be detected more easily by security controls.

![image](https://github.com/ELRame/HackingTools/assets/82544416/3ef2c470-488c-4b63-a1f9-79d43d6a1375)

Stealth mode scan:

**nmap -sS ip/range**: SYN Scan a single or an ip range. This will scan the network or device performing a 3 way handshake not finishing it.

![image](https://github.com/ELRame/HackingTools/assets/82544416/d07734da-40b0-47c6-87af-dfaf69bef74b)

Alive hosts:

**nmap -sn ip/range**: This scan will lookup for any alive host in the network or an specific host without sending packages to the target:

![image](https://github.com/ELRame/HackingTools/assets/82544416/2f4d816d-869d-4878-adef-79054b97f686)

Ports on specific target/range:

**nmap -sT ip/range**: Scan a single ip or an ip range that will show you any open port:

![image](https://github.com/ELRame/HackingTools/assets/82544416/ee3a24bd-6cf5-4981-9f67-50d9e92f3766)

UDP most known ports:

**nmap -sU -F ip/range**: Scan a single ip or a range UDP 100 most known ports.

![image](https://github.com/ELRame/HackingTools/assets/82544416/63cec07c-8f2c-4031-819d-d92d2cbe002d)

--------------------------

### Scripts

Some scripts can be useful to run:

***Run common scripts against a host***

````
nmap -A -sC ip
````

***Run script to find vulnerabilities on a host:***

````
sudo nmap --script vuln ip
````

***SMB enumeration***

````
sudo nmap --script smb-os-discovery.nse ip
nmap -p 445 --script=smb-enum-shares.nse,smb-enumusers.nse ip
````

Even when this post is for nmap, you can always use enum4linux:

````
enum4linux -a ip
````

***Dns Enumeration***

````
nmap -p 53 --script dns-brute domain
````

***Netbios enumeration***

````
nmap -sV -v --script nbstat.nse ip
nmap -sU -p 137 --script nbstat.nse ip
````

---------------------------

### Summary ###

Most of these commands can be used together in order to get more specific information, even more, you can use **-v** argument to get more details on the scan, and more vs you add, more details gonna show eg: **-vv**.
For scripts and automate some scans, you can always search for them, typing:

````
cd /usr/share/nmap/scripts; ls | grep service
````

Where service would be what you need, dns, netbios, etc...
