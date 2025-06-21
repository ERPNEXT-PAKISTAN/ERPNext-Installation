**Update Your Ubuntu Operating System:**   
**Step-1  Install GIT**  

```
sudo apt-get install git
```
 
**Step-2 Install Python**  

```
sudo apt-get install python3-dev   
```  

**Step-3**   


sudo apt-get install python3-setuptools python3-pip
``` 

**Step-4 Install Python Virtual Enviroment**   

```
sudo apt-get install virtualenv   
```
```
sudo apt install python3.10-venv   
```
 
**Step-5 Install Software Properties Common**   

```
sudo apt-get install software-properties-common   
```
 
**Step-6 // Install MYSQL Server//**   

```
sudo apt install mariadb-server   
```
```
sudo mysql_secure_installation   
``` 

**Step-7 //Install Other Package//**   

```
sudo apt-get install libmysqlclient-dev   
```
 
**Step-8 // Setup the Server//**   

```
sudo nano /etc/mysql/mariadb.conf.d/50-server.cnf   
```

//--Empty or Clear Completly the CNF File and Copy the bellow Code and Paste it.....//   
//Ctrl+s --- To Save file.   
//Ctrl+x --- To Exit/Close the file.   


 
[server]
user = mysql
pid-file = /run/mysqld/mysqld.pid
socket = /run/mysqld/mysqld.sock
basedir = /usr
datadir = /var/lib/mysql
tmpdir = /tmp
lc-messages-dir = /usr/share/mysql
bind-address = 127.0.0.1
query_cache_size = 16M
log_error = /var/log/mysql/error.log
 
 
[mysqld]
innodb-file-format=barracuda
innodb-file-per-table=1
innodb-large-prefix=1
character-set-client-handshake = FALSE
character-set-server = utf8mb4
collation-server = utf8mb4_unicode_ci
 
 
[mysql]
default-character-set = utf8mb4
 
-------------------------------------------------
=================================================
-------------------------------------------------
 
Step-9 //Restart SQL//
sudo service mysql restart
 
Step-10 // Install Redis Server//
sudo apt-get install redis-server
 
Step-11 // Install Curl//
sudo apt install curl 
curl https://raw.githubusercontent.com/creationix/nvm/master/install.sh | bash
source ~/.profile
 
Step-12
// Install Node//
nvm install 18
nvm install 20
nvm install 21
 
Step-13 // Install NPM//
sudo apt-get install npm
 
Step-14 // Install Yarn//
sudo npm install -g yarn
 
Step-15 // Install PDF//
sudo apt-get install xvfb libfontconfig wkhtmltopdf
 
Step-16 // Install Frappe-Bench//
sudo -H pip3 install frappe-bench
bench --version
 
Step-17 // Initialize/Install Frappe-Bench//
 
bench init frappe-bench --frappe-branch version-15
//---OR----//
//For any latest version.
bench init frappe-bench
 
cd frappe-bench/
bench start
 
Step-18 // create a site in frappe bench//
bench new-site site1.local
bench use site1.local
 
Step-19 //Install Payment Module//
bench get-app payments
bench --site site1.local install-app payments
 
Step-20 //Download ERPNExt//
bench get-app erpnext --branch version-15
//---OR----//
bench get-app https://github.com/frappe/erpnext --branch version-15
 
Step-21 //Install ERPNExt//
bench --site site1.local install-app erpnext
 
Step-22 //BENCH START//
bench start
-------------------------------------------------
-------------------------------------------------
  
INSTALL HRMS
-------------
Step-22 //Download & Install HRMS //
To Install the Latest Version:
Latest Vesion is Version-16.xxx
bench get-app hrms
 
or
To Install Version-15
bench get-app hrms --branch version-15
bench --site site1.local install-app hrms
-----------------------------------------
 
INSTALL LOAN / LENDING
----------------------
Step-23 //Download Lending/Loan App//
bench get-app lending
bench --site site1.local install-app lending
--------------------------------------------
// IF ERROR AFTER HRM INSTALLATION//
bench update --reset
 
//IF ERROR Updating...//
//Disable maintenance mode
bench --site site1.local set-maintenance-mode off
 
 
----------------
INSTALL CHAT APP
----------------
Step-24
bench get-app chat
bench --site site1.local install-app chat
-----------------------------------------
 
  
INSTALL Print Designer
----------------------
bench start
bench new-site print-designer.test
bench --site print-designer.test add-to-hosts
bench get-app https://github.com/frappe/print_designer
bench --site print-designer.test install-app print_designer
 
//Check Installed App List
bench --site site1.local list-apps
 
--------------
IF Not Working
--------------
 
bench --site site1.local clear-cache
bench --site site1.local clear-website-cache
bench --site site1.local reload-doc print_designer
bench --site site1.local migrate
 
bench --site site1.local list-apps
 
----------------
//If Not Working..........
----------------
 
//Uninstall the App:
bench --site site1.local uninstall-app print_designer
//Reinstall the App:......
bench --site site1.local install-app print_designer
//Restart Supervisor......
sudo supervisorctl restart all
 
Restart Your Computer.........
 
-----------------------
  
  
-----------------------
INSTALL INSIGHTS
----------------
bench start
bench get-app insights --branch version-3
bench --site site1.local install-app insights
 
 
-------
http://insights.test:8000/insights
 
-----------------------------------------------
  
  
-----------------------------------------------
  
 INSTALL BUILDER FOR WEBSITE
---------------------------
 bench get-app builder
 bench --site sitename.localhost install-app builder
 bench browse sitename.localhost --user Administrator
 sitename.localhost:8000/builder
--------------------------------
   
  
  
// IF ERROR//
bench update --reset
 
 
//Disable maintenance mode
bench --site site1.local set-maintenance-mode off
_________________________________________________
//Enable or Disable Developer Mode
bench set-config developer_mode 1
bench set-config developer_mode 0
 
 
 
 
============================================================
//WARN: restart failed: couldnot find supervisorctl in PATH//
 
sudo apt-get install supervisor
sudo nano /etc/supervisor/supervisord.conf
 
     [inet_http_server]
     port = 127.0.0.1:9001
     username = your_username
     password = your_password
 
sudo nano /etc/supervisor/supervisord.conf
 
 
[program:supervisord]
command=/usr/bin/supervisord -c /etc/supervisor/supervisord.conf
autostart=true
autorestart=true
redirect_stderr=true
environment=PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/path/to/your/virtualenv/bin"
 
sudo service supervisor restart
 
//Check Supervisor Status://
sudo service supervisor status
sudo service supervisor start
which supervisorctl
 
//Check Permissions://
sudo usermod -aG sudo your_username
supervisorctl status
 
//Activate Virtual Environment//
source /path/to/your/virtualenv/bin/activate
 
//supervisorctl status//
sudo supervisorctl status
 
cd ~/frappe-bench
bench restart
 
 
//Restart all services after the update://
$ supervisorctl reload
 
 
  
