1. Create an EC2 instance
2. Login using Putty
3. Change below four system settings

    a. Disable selinux, update SELINUX=disabled in the file
    
        vi /etc/selinux/config  
        
    b. Stop iptables
    
        service iptables status
        service iptables stop
        chkconfig iptables off
        iptables --flush        
        
    c. Check drives to resize if required    
       
        df -h       
        
    ebs has known issue where drives are not completely utilized, so need to resize
              
        resize2fs  /dev/xvde
        df -h

    d. Disable swappiness
        
        cat /proc/sys/vm/swappiness
        
    change to lower value. Higher value is agressive caching/swapping of memory
        
        cat /etc/sysctl.conf

        echo "vm.swappiness=1" >> /etc/sysctl.conf
        
4. Reboot the instance and check the updated sytem settings.
5. Can save this instance as image so in future can be used to create multiple clusters.
