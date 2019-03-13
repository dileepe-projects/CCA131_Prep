# AWS


1.  Create an AWS account
    - Provide credit card details (might be charged 2 INR initially)
    - Eligible for Free tier 12 months.
    - Check pricing in https://calculator.s3.amazonaws.com/index.html

2.  Start a EC2 Instance
    Elastic Compute Cloud - Rent virtual computers on which users can run their own applications

    - Select an OS for Instance (ex: CentOS)
    - Select Instance Type
    - Configure Instance
    - Add storage
    - Add tags
    - Configure Security Group (allow connection through SSH 22 port for allIPS/Custom/Only you)
    - Configure public and private keys. Download and save the PEM file.

3.  Amazon S3 Simple Storage Service
    Provides object storage through a webservice interface
    
    - Create a bucket

4.  Connect to an instance using Putty
    - Keep the PEM file ready
    - Use putty gen to seperate public and private keys from PEM file. Save private key
    - Open putty, load the instance using IP, port 22 and private key.
    - For centos, username is centos

5.  Amazon Machine Image:
    image with OS, EC2 instance along with snapshot of HDD. Using this image we can create multiple EC2 instances with same configurations/data.
    - Create an EC2 instance, login with Putty.
    - Create a file in the instance
    ```
        sudo su
        mkdir test
        cd test
        yum install wget
        wget http://files.grouplens.org/datasets/movielens/ml-1m-README.txt
        ls
    ```

    - Change few system settings.
        - Disable selinux. Update SELINUX=disabled in the file
        
        ```    
            vi /etc/selinux/config
        ```
        
        - Disable caching of huge files
        
        ```
            cat /sys/kernel/mm/transparent_hugepage/enabled
            echo never > /sys/kernel/mm/transparent_hugepage/enabled
            car /sys/kernel/mm/transparent_hugepage/enabled
        ```
        Keep the above value to never everytime system restarts
        ```    
            echo "echo never > /sys/kernel/mm/transparent_hugepage/enabled" >> /etc/rc.local
            cat /etc/rc.local
        ```

    - 2 configuration changes done and 1 file created on HDD in this instance. 
    - Select this instance and under actions choose create Image. An AMI along with Snapshot is created.
    - While creating an new EC2 instance, we can select the AMI under myAMIs.

6.  Spot EC2 instances. Same instance as on demand but at low price by bidding.

7.  RDS - relational data services - pay as you go database service
    
    - create a db instance
    - can be accessed through EC2 or other 3rd party applications like Heidisql
