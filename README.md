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
<img width="928" height="376" alt="image" src="https://github.com/user-attachments/assets/5fdf199a-2c84-4e14-8313-5e48d2601e89" />

Invoke msfconsole:
## OUTPUT:

<img width="646" height="405" alt="image" src="https://github.com/user-attachments/assets/09f8526d-144c-40b0-a7c5-c3cdf7d503b2" />


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


<img width="842" height="531" alt="image" src="https://github.com/user-attachments/assets/4edf53d2-981e-4425-84b6-7a1baf504842" />


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="1617" height="532" alt="image" src="https://github.com/user-attachments/assets/ff9911a6-90a5-4a01-87f6-38c8f1e09f1a" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="1605" height="370" alt="image" src="https://github.com/user-attachments/assets/18d5409f-f9d6-40e9-b534-c5bade742603" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="722" height="463" alt="image" src="https://github.com/user-attachments/assets/1cfdf2ca-1006-4688-b5fe-b0d5b12b5deb" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="986" height="973" alt="image" src="https://github.com/user-attachments/assets/6a4aed68-a83d-4867-ab0d-e795a2c9b5f8" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="1095" height="754" alt="image" src="https://github.com/user-attachments/assets/2c506216-eea2-427a-845a-86552f1030fa" />




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:
<img width="1598" height="326" alt="image" src="https://github.com/user-attachments/assets/dd8bb585-b25a-4d33-984d-9c24f6de082a" />

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="1045" height="541" alt="image" src="https://github.com/user-attachments/assets/db7965e7-9b58-4a8e-a635-203fadc791e0" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="665" height="133" alt="image" src="https://github.com/user-attachments/assets/593be06c-8dc9-4fc6-979d-a0674b5ca4c1" />





Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="934" height="372" alt="image" src="https://github.com/user-attachments/assets/29ba4c28-74c2-49af-a5b0-956948ba7b87" />



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:
<img width="923" height="607" alt="image" src="https://github.com/user-attachments/assets/6eac588e-31c9-43ea-b01c-60e088747fba" />




set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:

<img width="802" height="222" alt="image" src="https://github.com/user-attachments/assets/b89b8d66-41df-45d1-b9b6-c5101796a1ee" />





## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
