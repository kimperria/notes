# Introduction
PostgreSQL is a powerful open source database system. Free and easy to learn and use [read more](https://www.postgresql.org/) on their site.

### How to install postgresql
It is important to do ubuntu software update before any new software, package, extension and plug in installation.
Open terminal in home directory:
Run 
```bash
    sudo apt update
```
Run this command to download and install postgresql
```bash
    sudo apt install postgresql postgresql-contrib
```
Ubuntu then prompts you to confirm installation. Press y and click enter.
This command install the latests postgresql and all preinstalled dependacies

Run
```bash
    sudo -i -u postgres
```
This command log in to the ==default role 'postgress'== that and opens postgres terminal that allows you to interact with postgress shell. i.e psql

#### Create a new user with a superuser role priviledge
Below, replace 'server' with your computer name
```bash
    postgres@server:~$ createuser --interactive
```
This command prompts you to fill in your role "username", and to allow the role to have a superuser role by typing "y" then click enter

---
**psql life-saver commands**
##### Check if user have been created
Run this command on psql shell to list all users available
```
    postgres=# \du
```

##### How to change a role password
Run this command to change password of a postgres role/account
```
    postgres=# \password postgres
```
*Command syntax: postgres=# \password "role_username"*


##### List information of all database created
Run this command on psql shell to list all the available database information
```
    postgress=# \li
```
##### Exit psql and postgress terminal
```
    \q
```
This command returns you one step back. i.e from psql interface to postgress terminal

Run this command to kill or quit the postresql terminal
```bash
    postgres@kimperria:~$ exit
```
If you opt:
```bash
    postgres@kimperria:~$ logout
```

Explore more postgress commands using psql interface ```\?``` command or click [here](https://postgrescheatsheet.com/#/tables) to explore and learn postgres cheat sheet.


---

#### Create default database for the new super role account
Run this command to create a new database.
It is important to note that postgress makes an assumption on this first database. Remember this database should be exact as the role_username create above.

Command
```bash
    postgress@server$ createdb username
```
**N/B at this point exit postgress terminal**

#### Open postgress prompt with a new role
Run
```bash
    $ sudo adduser username
```
Once the account is available run
```bash
    $ sudo -i -u username
    $ psql
```

#### How to uninstall postgresql
Open terminal in home directory:

**N/B** Run this commands with sudo privilege

```bash
sudo apt --purge remove postgresql
```
Key in your computer password if prompted to allow uninstalation process to begin. When propted *Do you wish to continue?* Type y and click enter.

What this command does is to remove postgresql from your computer.

Run this command to list all the packages installed with postgresql
```bash
dpkg -l | grep postgres
```

Remove the listed unwanted preinstalled postgres packages with the following command
```bash
sudo apt --purge remove postgresql-12 postgresql-client-12 postgresql-client-common postgresql-common postgresql-contrib
``` 
**N/B** Command syntax is as follows: 
- *sudo apt --purge remove (package_1_name) then (package_2_name) ... etc. For all the packages you want to remove.*

Terminal will prompt you to confirm all the packages uninstalled. Click yes.

See image below:
![uninstall_postgreSQL_prompt](/postgreSQL/images/uninstall_postgreSQL_prompt.png)

All your prosgress files and instance will now be ==permanently== deleted.
