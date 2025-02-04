# Lab #3 Code: Intro to SQL

For the details of this lab please follow along with the description/instructions [here](https://docs.google.com/document/d/1j998D-0Fmo3s2TZEpvTqmSdYT0mjT4KRgGMvB-by7P4/edit?usp=sharing).

This document is only meant to make copying and pasting the SQL commands a bit easier. 

## Section 2 Setting up MySQL on your EC2 Instance
Download the mysql server install file from the Internet onto your EX2 instance using `wget`:
```
sudo wget https://dev.mysql.com/get/mysql80-community-release-el9-1.noarch.rpm
```

Install the file we just downloaded:
```
sudo yum localinstall mysql80-community-release-el9-1.noarch.rpm
```

Type `y` to complete the install.

Then, have `yum` install mysql community server:
```
sudo rpm --import https://repo.mysql.com/RPM-GPG-KEY-mysql-2023
sudo yum install mysql-community-server
```

Again, type `y` whenever prompted. You should see "Complete!" if all went well. 

Next, Start the mysql service with the following command:
```
sudo service mysqld start
```

Securing the installation and changing the password:

Find the temporary password by using the `cat` command on the log file:
```
sudo cat /var/log/mysqld.log
```

Make a note of the password (copy it to a note, etc)

Finish the installation with the following command:

```
sudo mysql_secure_installation
```
Follow the instructions in the lab description for updating passwords.

Answer `y` to all of the security questions. 

You should see `All Done!` which means the installation is complete. 

## Section 3: Launching MySQL and Loading some data

Let's download some starter SQL code that I've made available via the following command:

```
wget https://analytics.drake.edu/~urness/CS178/CollegeSchema.sql
```

Next, we'll import this data into MySQL by using the following command

```
mysql -u root -p < CollegeSchema.sql
```

It will prompt your for your password (the mysql password you entered earlier)

Next, we can enter MySQL with the following command. This means "run the mysql program as the root user, and I want to enter the password".

```
mysql -u root -p
```
Now you should see a prompt from mysql that looks like `mysql>`. 

Now we'll tell MySQL to use the College Applications Schema that you just inserted:

Enter the following after the `mysql>` prompt:
``` 
use CollegeApplications;
```

Now try:

```
show tables;
```
See Lab 3 for a description of these tables. 

## Section 4: Your First SQL Query, `select all`

Type in your first SQL query:
```
select * from College;
```
This will select all (`*`) rows from the `College` table. 

## Section 5: Selecting specific columns, filtering with WHERE

Type the following into the terminal:

```
SELECT sID, sName, GPA
FROM Student
WHERE GPA > 3.6;
```


