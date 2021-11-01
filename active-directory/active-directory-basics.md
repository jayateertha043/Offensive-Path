# Active Directory Basics

### **Tasks:**

1. **Introduction**:
2. **Physical Active Directory**:
3. **The Forest**:
4. **Users + Groups**:
5. **Trusts + Policies**:
6. **Active Directory Domain Services + Authentication**:
7. **AD in the Cloud**:
   1. Answer after reading and understanding basics about AD. \[For Task 1-7]
8. **Hands-On Lab**:
   1. `cd Downloads`, `powershell -ep bypass`, `. .\PowerView.ps1`
   2. `Get-NetComputer -fulldata | select operatingsystem` - Windows 10 Enterprise Evaluation
   3. `Get-NetUser | select cn` - Admin2
   4. `net localgroup` - Hyper-V Administrators
   5. `Get-ADUser -identity SQLService -properties "PasswordLastSet"` - 5/13/2020 8:26:58 PM
9. Conclusion:
   1. Just Click Submit
