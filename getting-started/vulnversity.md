# Vulnversity

### **Tasks**:

1. **Deploy the machine**.
2. **Reconnaissance**:
   1. Do nmap version scan , find port used by apache and also OS(Ubuntu)
   2. Answer all questions based on nmap output.
3. **Locating directories using GoBuster**:
   1. Use gobuster to bruteforce directories using any directory word list, There will be /internal/ directory.
   2. /internal/ directory has file upload functionality.
4. **Compromise the webserver**:
   1. Try to upload php shell with various extensions such as .php,.php3,.php4,.php5,.phtml - only .phtml succeeds.
   2. Do one more directory search in /internal/ directory - You will find /internal/uploads/ directory which has uploaded shell in it.
   3. Connect to reverse shell by using nc in linux or ncat in windows - You have got local access to machine now . (you answer all the questions in the task now after cd to /home/ directory)
5. **Privilege Escalation**:
   1. Search for binaries with suid permission
   2. systemctl has suid permission
   3. make a service which copies /root/root.txt to /tmp/ or make a service which startes reverse  shell to attacker machine, make sure User is set as root for service.
   4. Enable and start the service using systemctl - you are now root !!!
   5. Report root flag in /tmp/root.txt or /root/root.txt(reverse shell case).



References:

1. [https://medium.com/@klockw3rk/privilege-escalation-leveraging-misconfigured-systemctl-permissions-bc62b0b28d49](https://medium.com/@klockw3rk/privilege-escalation-leveraging-misconfigured-systemctl-permissions-bc62b0b28d49)

