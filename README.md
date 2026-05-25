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
<img width="920" height="1090" alt="image" src="https://github.com/user-attachments/assets/ac565c69-b5ea-4e92-bb89-8dea8a08bb12" />



Invoke msfconsole:
## OUTPUT:

<img width="920" height="1090" alt="image" src="https://github.com/user-attachments/assets/42b86c65-38e9-402c-ab98-3a4be7317b80" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

## OUTPUT:

<img width="920" height="1090" alt="image" src="https://github.com/user-attachments/assets/dad15cf4-6f0b-4f9e-bbec-ac4237a2ae43" />





Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="920" height="1090" alt="image" src="https://github.com/user-attachments/assets/f74f71c3-58a1-4a8b-a3aa-1b7bfdeaece9" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:

<img width="561" height="294" alt="image" src="https://github.com/user-attachments/assets/487488cf-f550-4331-ae6c-b096a412bb1b" />


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:

<img width="1920" height="1043" alt="image" src="https://github.com/user-attachments/assets/4696f567-3e9a-4097-b898-84192795c97b" />


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="831" height="835" alt="image" src="https://github.com/user-attachments/assets/a25c6513-a0de-45fd-a23d-7764c84923f7" />



The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:

<img width="1016" height="713" alt="image" src="https://github.com/user-attachments/assets/f81d7065-8513-42a6-81b4-33f6a3aac11a" />



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="1000" height="421" alt="image" src="https://github.com/user-attachments/assets/a3fba192-8da5-4b78-b95d-e107645a72bb" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="830" height="242" alt="image" src="https://github.com/user-attachments/assets/2e1cc2b5-eeb2-4807-8700-a25004b1524a" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="869" height="169" alt="image" src="https://github.com/user-attachments/assets/5d4dc26b-d33c-4ae9-9bd2-2d039aa54307" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="960" height="337" alt="image" src="https://github.com/user-attachments/assets/21da7129-4bdb-4280-baae-379a7b2e85a5" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:

<img width="960" height="337" alt="image" src="https://github.com/user-attachments/assets/3af5c54c-02fb-4c4e-935f-a408bb6fa2dd" />



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true






## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
