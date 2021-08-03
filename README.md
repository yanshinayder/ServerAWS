# ServerAWS
 
# This project is about how to create an aws server using EC2, PostgreSQL, Putty and DBeaver, how to manage, load data through python and how to integrate these databases.

## Creating a Cloud Server on AWS.
* Creating a virtual machine.
* Choose OS - Ubuntu Recommended.
* Choose instance type. (Used t2.micro free)
* Configure storage and add tags.
* Create a new security_group to filter the requested IPs and which ports are allowed. (Used SSH keys and port 22 and source 0.0.0.0/0 [For real projects I don't recommend this practice]) 

![EC2](https://user-images.githubusercontent.com/78814110/127931516-a6161284-31a2-41da-8b95-f0019a313dce.jpg)

* Convert the generated SSH key (in this case I used PuttyGen).
* I recommend updating the virtual machine on first use "sudo apt-get update" 

# Install PostGreSQL
* In this virtual machine "sudo apt install postgresql"

Create a user:
CREATE USER "user" WITH PASSWORD "Password"

To administrator:
ALTER USER "user" WITH SUPERUSER

* For a secure connection from the machine to the database, create an "SSH Tunnel".
* ![serverdb](https://user-images.githubusercontent.com/78814110/127931729-165e6214-0427-40c9-804f-398b86e5e31d.jpg) ![tunnel](https://user-images.githubusercontent.com/78814110/127931736-c6c8e199-5e57-49cc-b73b-82cd891fa519.jpg)

# Importing CSV into Database
* Inspired by original data from kaggle Hospital Charges for Inpatients Breast Cancer Wisconsin.
* Python Version 3.9
* Import csv file and do exploratory activities before creating tables for better data presentation and runtime.
* Create a function to load the data and if everything is ok approve this csv and export.
* Since you have login and password in the code, it is recommended to use AWS secrets Manager (but in this project it was not used)

* Create an RDS relational database service (This database eliminates the worry of security updates and server versions, streamlining the process.)
![RDS](https://user-images.githubusercontent.com/78814110/127932610-ddea9446-5208-4cd7-9f0f-c07a13399a17.jpg)

* Through Putty, configure so that the postgres connection through port 5432 is directed to our endpoint created in RDS.

![endpoint](https://user-images.githubusercontent.com/78814110/127932709-af8f5992-0123-4694-969c-eba81ffae8d1.jpg)

Don't make your endpoint key available, here it is for a demo.

* For migration use EC2 backup via pg_dump
* restore the EC2 backup on RDS via pg_restore informing the necessary flags.

After that, the migration from EC2 Local Database to RDS Relational Database is done, which will now receive security updates and automatic backups according to the chosen settings.









