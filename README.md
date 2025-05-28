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
---
 ## Configure FTP for Ubuntu ---

```
sudo apt update
sudo apt install vsftpd

sudo nano /etc/vsftpd.conf

# Enable local users
local_enable=YES

# Allow uploads
write_enable=YES

# Restrict users to their home directory
chroot_local_user=YES

# Enable passive mode (recommended for firewalls)
pasv_enable=YES
pasv_min_port=40000
pasv_max_port=50000

# Optional: Disable anonymous access (recommended for security)
anonymous_enable=NO

# Enable logging
xferlog_enable=YES
# Allow writing
write_enable=YES

# Allow local users to write
local_enable=YES

# If using chroot, allow writing in chroot
allow_writeable_chroot=YES

sudo adduser ftpuser
sudo usermod -d /home/ftpuser ftpuser

sudo chmod 755 /home/ftpuser/

sudo systemctl start vsftpd
sudo systemctl enable vsftpd
sudo systemctl status vsftpd

For client
sudo apt install ftp
ftp> cd /path/to/destination # server destination
ftp> pwd
ftp> lcd /path/to/local/files  # Local change directory
ftp> !pwd 
```
