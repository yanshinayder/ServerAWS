# ServerAWS
 
# This project is about how to create an aws server using EC2, PostgreSQL, Putty and DBeaver, how to manage, load data through python and how to integrate these databases.

## Creating a Cloud Server on AWS.
* Creating a virtual machine.
* Choose OS - Ubuntu Recommended.
* Choose instance type. (Used t2.micro free)
* Configure storage and add tags.
* Create a new security_group to filter the requested IPs and which ports are allowed. (Used SSH keys and port 22 and source 0.0.0.0/0 [For real projects I don't recommend this practice]) 
