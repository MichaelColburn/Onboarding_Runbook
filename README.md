# IT Onboarding_Runbook

## Overview
This walkthrough outlines a standard Windows IT onboarding process within an enterprise environment, including domain configuration, Active Directory user policy assignment and group permissions, followed by verification using Event Viewer and the implementation of automated administrative protocols via PowerShell.  The attached PDF is an in depth visual [step by step visual guide](https://github.com/MichaelColburn/Onboarding_Runbook/blob/main/Michael%20Colburn%20-%20IT_runbook.pdf)

## ▲ Outline of steps and processes

### ▲ Joining New User to the Domain
- From the _Host/Server_ machine located the IPv4 address utilizing ___"ipconfig"___ - (making note of it/copy it to clipboard)
- Established connection of _User_ machine to the Domain
  - Established network connection
  - Configured DNS to point to domain controller via IPv4 address
  - Joined the User machine to the `contoso.com` domain with administrator credentials
 ---

### ▲ Active Directory User/Group/OU Build
