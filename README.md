# IT Onboarding_Runbook

## Overview
This walkthrough outlines a simulation of standard Windows IT onboarding process within an enterprise environment, including domain configuration, Active Directory user policy assignment and group permissions, followed by verification using Event Viewer and the implementation of automated administrative protocols via PowerShell.  The attached PDF is an in depth [step by step visual guide](https://github.com/MichaelColburn/Onboarding_Runbook/blob/main/Michael%20Colburn%20-%20IT_runbook.pdf)

## ▲ Outline of steps and processes

### ▲ 1: Joining New User to the Domain
- From the _Host/Server_ machine located the IPv4 address utilizing `ipconfig` - (making note of it/copy it to clipboard)
- Established connection of _User_ machine to the Domain
  - Established network connection
  - Configured DNS to point to domain controller via IPv4 address
  - Joined the _User_ machine to the `contoso.com` domain with administrator credentials
 ---

### ▲ 2: Active Directory User/Group Build
- Utilizing Active Directory the New User is created, assigned to a Group and inserted into "Department" OU
  - The User is defined and initial credentials set with mandatory reset password policy enacted
  - In this sim the Group was newly created as well (but migration of User into existing Group would be probable)
- Associations and memberships were linked
- Verification of membership confirmed
---

### ▲ 3: Shared Drive Build and test 
- Created of 2 directories on the Department drive
  - One for the "Department"
  - One for Scripts
- Created "test.txt" file for proof of function test
- The sharing and association for the directories are set via Advanced Sharing Properties
---

### ▲ 4: Create and Link a GPO (Group Policy Object)
- Configured startup messages via:
  - `Computer Configuration > Policies > Administrative Templates > System`
- Enabled:
  - **Login Message Title**
  - **Login Message Text**
  - Disabled **Command Prompt** access
  - Disabled **Run** menu
 ---
 
 ### ▲ 5: Create .bat script for shared drive intialization
- Created and deployed a `.bat` script to map network drives
- Linked the script via:
  - `User Configuration > Policies > Windows Settings > Scripts`
---

### ▲ 6: Active Directory OU Build Linkage
- Utilizing Active Directory the OU "Human Resources" was also newly established with centralized control of all subordinate entities
- Associations and memberships were linked
- Verification of membership confirmed
---

### ▲ 7: Push GPO
- Forced GPO with `gpupdate/force`
---

### ▲ 8: Verification of configuration and policies
- Ran through list of policy installments and permissions attempting each violation for check down of confirmed setup
- Events Viewer verify machine is live and throughput it registering
  - Confirmed Event "4624" to verify proper logon
---

### ▲ 9: Powershell to View and Confirm latest programs installed
```powershell
Get-WmiObject -Class Win32_Product | Sort-Object -Property InstallDate -Descending | Select-Object -First 1
```
---

### ▲ 10: Powershell to Write report of Install
```powershell
Get-Service | Where-Object {$_.Status -eq 'Running'} | Out-File -FilePath "C:\Services\running_services.txt”
```

