# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting
# Name : PRIYADARSHINI K
# Reg no : 212224100046
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

# Find out the ip address of the attackers system
## OUTPUT:
<img width="903" height="409" alt="image" src="https://github.com/user-attachments/assets/2db77e85-320b-448e-892c-ad98eaeb673a" />

This command is used to display the network configuration details of the Kali Linux system. It provides information such as the IP address, MAC address, network interface status, transmitted packets (TX), and received packets (RX). During the experiment, this command helped identify the active network interface and the IP address of the Kali Linux machine connected to the local network. The obtained IP address was later used for communication and network-related tasks with other systems.


# Invoke msfconsole:
## OUTPUT:
<img width="940" height="788" alt="image" src="https://github.com/user-attachments/assets/3b20bbb1-033f-4248-8707-f878df4095b2" />

This command is used to start the Metasploit Framework in Kali Linux using the msfconsole command. Metasploit is a penetration testing tool used for vulnerability assessment, exploitation, and security testing. The screen displays the Metasploit console interface along with details such as the version, number of exploits, auxiliary modules, payloads, encoders, and evasion modules available in the framework. During the experiment, this command was used to initialize the Metasploit environment for performing penetration testing and security analysis tasks.


# Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
<img width="958" height="945" alt="Screenshot 2026-05-20 103435" src="https://github.com/user-attachments/assets/2dde7342-db56-4f7c-872d-ed3d424f403a" />

This command displays the help menu of the Metasploit Framework using the help command inside the msfconsole. It provides a list of available commands along with their descriptions, including core commands and module-related commands. The screen shows commands used for navigation, session handling, module searching, configuration, and exploitation tasks. During the experiment, this command was used to understand the available Metasploit commands and learn how to navigate and operate the framework effectively.

# Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:
<img width="557" height="141" alt="Screenshot 2026-05-20 103747" src="https://github.com/user-attachments/assets/eaaa290f-54f8-4042-9cef-a546af4c71e3" />

This command uses the nmap tool inside the Metasploit Framework to perform a TCP SYN scan (-sT) on the target IP address 192.168.181.130 for ports ranging from 1 to 1000 (-p1-1000). The output indicates that the scan failed because the target host could not be reached or no route to the target was found. As a result, Nmap reported that 0 hosts were up and no ports were scanned. During the experiment, this command was intended to identify open ports and active services on the target machine within the local network.

step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

# scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="692" height="107" alt="Screenshot 2026-05-20 103839" src="https://github.com/user-attachments/assets/b75d7399-257b-45c7-94af-b8de0ba36b0d" />

This command uses the db_nmap feature inside the Metasploit Framework to scan the target IP address 192.168.181.130 and store the scan results directly into the Metasploit database. The output shows that the scan could not be completed because the target host was unreachable or no valid network route was available. As a result, Nmap reported that 0 hosts were active and no scan results were stored. During the experiment, this command was intended to identify active hosts, open ports, and services on the target system for further penetration testing activities.


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
# cd /usr/share /metasploit-framework/modules/auxiliary
# kali > ls -l
## OUTPUT:
<img width="717" height="493" alt="Screenshot 2026-05-20 104157" src="https://github.com/user-attachments/assets/0736f892-e7ef-40c2-8d8f-c086c373cc4a" />

This command navigates to the auxiliary directory inside the Metasploit Framework modules using the cd command and then lists all available auxiliary module categories using the ls command. The displayed folders, such as scanner, spoof, dos, fuzzers, and sniffer, represent different types of auxiliary modules used for tasks like scanning, information gathering, spoofing, denial-of-service testing, and network analysis. During the experiment, this command was used to explore the available Metasploit auxiliary modules for performing various penetration testing and security assessment activities.


Search is a powerful command in Metasploit that you can use to find what you want to locate. 
# msf >search name:Microsoft type:exploit
## OUTPUT:
<img width="922" height="912" alt="Screenshot 2026-05-20 104440" src="https://github.com/user-attachments/assets/29fc1aba-32c5-40f6-9bf3-b278cdbaee61" />

This command uses the search feature in the Metasploit Framework to find exploit modules related to Microsoft products. The command search name:microsoft type:exploit filters and displays exploit modules whose names contain “Microsoft.” The output lists various exploit modules along with details such as module name, disclosure date, rank, target operating systems, and vulnerability descriptions. During the experiment, this command was used to identify suitable Microsoft-related exploit modules for vulnerability assessment and penetration testing purposes.


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
# systemctl start postgresql
# msfdb init
## OUTPUT:
<img width="713" height="215" alt="Screenshot 2026-05-20 104559" src="https://github.com/user-attachments/assets/900d5ccc-aec2-4eea-827e-414bdfbb2a74" />
<img width="542" height="72" alt="Screenshot 2026-05-20 104631" src="https://github.com/user-attachments/assets/b0b6b9b4-970c-4cc2-b2a8-be7a7c70e129" />

This command starts the PostgreSQL database service using sudo systemctl start postgresql and initializes the Metasploit database using the msfdb init command. The output indicates that the PostgreSQL database service was already running and the Metasploit database had already been configured, so the initialization process was skipped. During the experiment, these commands were used to ensure that the Metasploit Framework database service was active and properly configured for storing scan results, session details, and other penetration testing data.



## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
# db_nmap -sV -sC -p 3306 <metasploitable_ip_address>
## OUTPUT:
<img width="747" height="160" alt="Screenshot 2026-05-20 104720" src="https://github.com/user-attachments/assets/5a6d1cbf-c461-4d00-b3ab-4c8648a93d43" />

This command first checks the status of the Metasploit database connection using the db_status command. The output confirms that the Metasploit Framework is successfully connected to the PostgreSQL database. Next, the db_nmap -sV -sC -p 3306 192.168.120.142 command is used to perform an Nmap scan with service version detection (-sV), default script scanning (-sC), and scanning of port 3306 on the target IP address. However, the output indicates that the target host could not be reached or no valid route to the target was available, resulting in 0 hosts being scanned. During the experiment, these commands were used to verify database connectivity and perform service enumeration on the target system.

# Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
# search type:auxiliary mysql
## OUTPUT:
<img width="936" height="652" alt="Screenshot 2026-05-20 104758" src="https://github.com/user-attachments/assets/b1ee8195-47ba-4b2f-8967-b791cc3e80c7" />
This command uses the search feature in the Metasploit Framework to find auxiliary modules related to MySQL databases. The command search type:auxiliary mysql filters and displays various MySQL-related auxiliary modules available in Metasploit. The output includes modules for MySQL login testing, version detection, password hash dumping, schema enumeration, file enumeration, and authentication bypass techniques. During the experiment, this command was used to identify suitable auxiliary modules for MySQL database scanning, enumeration, and security assessment activities.



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:
<img width="953" height="397" alt="Screenshot 2026-05-20 104846" src="https://github.com/user-attachments/assets/fa0a24b9-c53a-4379-8fa6-5b4cc8460e39" />

This command selects the MySQL version scanning module in the Metasploit Framework using use 11, which refers to the module auxiliary/scanner/mysql/mysql_version. The show options command then displays the configurable parameters required for the module, such as RHOSTS (target host IP address), RPORT (target port number, default 3306 for MySQL), and THREADS (number of concurrent threads). The output also shows that the module can work with an existing session or a remote host connection. During the experiment, this command was used to configure the MySQL version scanning module before performing enumeration on the target database server.




Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:
<img width="902" height="233" alt="Screenshot 2026-05-20 105041" src="https://github.com/user-attachments/assets/f159e658-d23a-498f-952f-e473c4824842" />

This command attempts to configure the MySQL version scanning module in the Metasploit Framework by setting different parameters such as a password file, target host IP address, username, and blank password option. The output shows that options like PASS_FILE, USERNAME, and BLANK_PASSWORDS are not supported by the selected mysql_version module, resulting in “Unknown datastore option” messages. However, the RHOSTS option was successfully set to the target IP address 192.168.181.130. During the experiment, these commands were used to configure the MySQL scanning module and prepare the target settings for database enumeration and security testing.


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:
<img width="793" height="441" alt="Screenshot 2026-05-20 105245" src="https://github.com/user-attachments/assets/1aab16f6-f0f5-4dfc-a05e-114adf862926" />

This command displays the configured options of the mysql_version auxiliary module using the show options command and then executes the module using the run command. The output shows that the target host IP address 192.168.181.130 and MySQL port 3306 were configured successfully. After execution, the module scanned the specified host and completed the auxiliary scanning process. During the experiment, this command was used to perform MySQL version enumeration on the target system to identify the running MySQL service and gather information for further security analysis.



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
