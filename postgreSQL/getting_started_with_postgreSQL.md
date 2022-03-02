# Introduction


### How to install postgresql

### How to create user in postgresql


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

All your protgress files and instance will now be ==permanently== deleted.
