# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:
<img width="928" height="376" alt="image" src="https://github.com/user-attachments/assets/b2411c85-618f-4894-937b-16245250b485" />


Invoke msfconsole:
## OUTPUT:
<img width="928" height="376" alt="image" src="https://github.com/user-attachments/assets/a85e245d-d684-444b-9b9c-c1abe74411a2" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

<img width="928" height="376" alt="image" src="https://github.com/user-attachments/assets/29047dc7-87e7-4519-a07a-47a1e1378544" />



Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="928" height="376" alt="image" src="https://github.com/user-attachments/assets/f6b5d24c-4535-49b1-a1b4-e67b186af8bc" />

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="928" height="376" alt="image" src="https://github.com/user-attachments/assets/dd18bfb5-d08c-4c0d-aaba-c2772734aee1" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="722" height="463" alt="image" src="https://github.com/user-attachments/assets/de3e21a5-2f0e-41e8-ac22-da912bf40896" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="722" height="463" alt="image" src="https://github.com/user-attachments/assets/b1fbfaa3-d5de-4d36-a714-d8abaca2de91" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="722" height="463" alt="image" src="https://github.com/user-attachments/assets/ba36cdbd-6c6c-4651-845d-f1c3f9f1e142" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="722" height="463" alt="image" src="https://github.com/user-attachments/assets/6088a218-11f1-41b7-9e14-016d3b8a6f5c" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1045" height="541" alt="image" src="https://github.com/user-attachments/assets/ae8db23f-0699-44b6-af84-3a40d132c9ce" />

use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="1045" height="541" alt="image" src="https://github.com/user-attachments/assets/5eb3f0ee-29ac-478b-9028-c15c4c88de0f" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="1045" height="541" alt="image" src="https://github.com/user-attachments/assets/05506886-83b3-4e53-86f1-9d41ab0bd170" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="1045" height="541" alt="image" src="https://github.com/user-attachments/assets/956f6f59-b73a-429b-82f4-f6f7fd7e0345" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:



<img width="1045" height="541" alt="image" src="https://github.com/user-attachments/assets/de1c224d-b361-469e-96d5-daf56213e4e7" />



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
