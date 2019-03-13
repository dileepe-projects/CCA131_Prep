Cloudera uses MySQL for storage
MySQL forked as MariaDB currently

1. Create an new EC instance with CentOS.
2. Login using putty.
3. update OS(using yum package installer)
    ```
    sudo su
    yum -y update
    ```

4. Install mysql server and java connector
    ```
    yum -y install mysql-server mysql-connector-java
    ```
5. Check the status of mysql server
    ```
    service mysqld status
    ```
6. Start the service
    ```
    service mysqld Start
    ```
7. Start service always on system restart
    ```
    chkconfig mysqld on
    ```
8. Secure the installation by setting password for mysql database
    ```
    /usr/bin/mysql_secure_installation
    ```
9. Login into mysql console (mysql as user root from locahost with password)
    ```
    mysql -u  root -h  localhost -p
    ```
10. Check databases
    ```
    show databases;
    ```
11. Create an user logging in from any host
    ```
    create user 'guest'@'%' identified by 'password';
    ```
12. Grant all the privileges to guest
    ```
    grant all privileges on *.* to 'guest'@'%' with grant option;
    quit;
    ```
13. Login as guest
    ```
    mysql -u guest -h locahost -p
    ```
14. Can login through other applications like heidisql using hostname of EC2 instance

15. Access is blocked by linux firewall

16. Check firewall status
    ```
    service iptables status
    ```
17. Stop iptables
    ```
    service iptables stop 
    ```
18. Stop iptables always on system restart
    ```
    chkconfig iptables off
    iptables --flush
    ```
19. Create a database

    ```
    mysql -u root -h locahost -p 
    create database reportmanager;
    create user 'reportmanager'@'%' identified by 'password';
    grant all privileges on reportmanager.* to 'reportmanager'@'%';
    ```
