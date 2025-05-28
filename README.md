# FTP-Server
---
##  Configure FTP for RHEL 9 ---
```
 configure FTP for RHEL 9 ---
       for server--
            sudo dnf install vsftpd -y
            
            sudo vi /etc/vsftpd/vsftpd.conf
            anonymous_enable=NO
            local_enable=YES
            write_enable=YES
            local_umask=022
            chroot_local_user=YES
            allow_writeable_chroot=YES
            dirmessage_enable=YES
            xferlog_enable=YES
            connect_from_port_20=YES
            xferlog_std_format=YES
            listen=NO
            listen_ipv6=YES
            pam_service_name=vsftpd
            userlist_enable=YES    

            sudo systemctl start vsftpd
            sudo systemctl enable vsftpd
            sudo systemctl restart vsftpd

        for client--
          check type – ftp
          sudo dnf install ftp # client site only install ftp 
          ftp <server-ip>
          ftp> put file.txt
          ftp> mput file1 file2 (for multiple files)

```
 Configure FTP for Ubuntu ---

```


```
