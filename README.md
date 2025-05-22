#SQL-Injection

#SQL Injection Demo using DVWA (Damn Vulnerable Web Application)

This project demonstrates how SQL Injection can be utilised on web applications. Using Damn Vulnerable Web Application (DVWA), I tested and documented the methodology and techniques used to exploit poorly secured input fields.

Environment & Tools
- Base OS: Debian 12.x (ARM64) via Kali Linux 
- VMware Fusion on macOS M3
- Web App: [DVWA](https://github.com/digininja/DVWA)
- Database: MariaDB 11.x
- Web Server: Apache2
- Language: PHP 8.4


Through these various tools, we got to see how SQL injections vulnerabilities were exploited, along with the security level changes that can occur and the effects.


Installation:

Within Kali Linux:

Go into terminal:
sudo apt install apache2 mariadb-server php php-mysqli git

Once installed, do the following command:

sudo git clone https://github.com/digininja/DVWA.git
cd DVWA

This will Clone the DVWA git, and then enter the DVWA directory when installed

Within the DVWA directory:
There will be a sample config file under the name of ‘config.inc.php.dist’, using this file we copy and rename into ‘config.inc.php’ and then edit the contents of the file
sudo nano config/config.inc.php
When within the config file, edit the ‘db_user’ and ‘db_password’ inside of the file.
Start the SQL Server and connect it to DVWA:

sudo service mysql start sudo mysql -u root -p CREATE DATABASE dvwa; exit;
Once this is all done, start the apache server using the command:

sudo systemctl start apache2
Once done, access DVWA via your browser using the link: http://localhost/DVWA/setup.php
Within the website, login using user: admin, password: password. Locate the ‘Security’ Tab, and change the security settings to low. 

Go to SQL Injection and input the payload ‘ OR ‘1’=’1


![terminal commands](https://github.com/user-attachments/assets/d57823fe-f988-4a85-874a-cf1066057627)


Checking connection between DVWA and database.

![Editing Database Config in Terminal](https://github.com/user-attachments/assets/a5f2f6b2-a46e-428c-8e9f-6b07ce0cda7c)

Edit Database Config in Terminal

<img width="1065" alt="DVWA Setup Page" src="https://github.com/user-attachments/assets/3ea7b0b5-7467-4fa0-b844-25acf63700a5" />

Database setup page

<img width="892" alt="Create" src="https://github.com/user-attachments/assets/1640fec9-4aaa-4473-99aa-20e9fb1446f7" />

Create database

<img width="776" alt="Security" src="https://github.com/user-attachments/assets/caae780b-1d6e-4a97-8b6d-92875d8c8bfc" />

Change Security level to Low

<img width="1062" alt="SQL Injection" src="https://github.com/user-attachments/assets/6f9abddc-48c5-4bc6-a5a7-5390f195607a" />

Inject SQL 
' OR '1'='1


<img width="1470" alt="data extraction" src="https://github.com/user-attachments/assets/9227ab86-e022-4b6a-b13c-15cbac6b6c87" />
Payload for extracting data
Payload' UNION SELECT user(), database()






