# Group-Policy_Workstation-Security-Baseline

### Objective
Implement a Workstation Security Baseline Group Policy Object (GPO) to enforce restrictions on domain workstations, preventing unauthorized changes, protecting system integrity, and ensuring compliance with organizational security standards. The policy limits access to system settings, blocks dangerous tools, and controls removable media usage for standard users.


### Skills Learned
- Group Policy Object creation, editing, and delegation in Windows Server
- Applying administrative templates to enforce security controls
- Configuring user and computer restrictions in Active Directory
- Implementing storage device access controls to prevent data exfiltration
- Using gpupdate and gpresult for GPO verification and troubleshooting
- Understanding Resultant Set of Policy (RSOP) data for applied settings<br>
  <br>
### Tools Used
- Windows Server 2022 with Active Directory Domain Services (AD DS)
- Group Policy Management Console (GPMC)
- Administrative Templates for User and Computer Configuration
- Command Prompt (gpupdate /force, gpresult /r)
- Test environment with Windows 11 client workstation

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">
  
### Step 1: Login Failure Reported by User

User reports they are unable to sign in and receive the following error:<br>

“The referenced account is currently locked out and may not be logged on to.”<br>
<br>
This commonly happens due to multiple failed login attempts caused by saved credentials on devices, mapped network drives, or background services repeatedly trying to authenticate.<br>
<br>
- User’s account is locked due to multiple failed authentication attempts
- Password was entered incorrectly too many times, often by background processes
- Investigate potential causes including saved passwords on other systems or devices<br>
<br>
<img src="https://github.com/user-attachments/assets/01c80fde-243c-4f33-8026-3ad4e1e73307" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 2: Locate User in Active Directory

Launch Active Directory Users and Computers from Server Manager. Ensure Advanced Features is enabled from the "View" tab.
Search the user (e.g., Bucky Barnes) in the directory and go to Properties > Object tab to find the user's OU path.<br>
<br>
- Find the user’s exact OU location in AD
- AD may have multiple OUs; exact path is needed to manage the account
- Enable Advanced Features, then use Properties > Object to view the path<br>
<br>
<img src="https://github.com/user-attachments/assets/7acfc6d4-6893-4746-a23b-da2e222587cc" width="1000"><br>


<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 3: Reset User Password
Navigate to the user's OU (e.g., Management > Bucky Barnes).<br>
<br>
Right-click the user, select All Tasks > Reset Password, assign a temporary password, and unlock account.<br>
<br>
<br>
- Reset the locked account with a temporary password
- Allows user to regain access after account lockout
- Right-click user > Reset Password > enter and confirm new password<br>
<br>
<img src="https://github.com/user-attachments/assets/c8fd1961-dfd9-4175-9932-050f57433e59" width="1000"><br>
<br>
<br>
<img src="https://github.com/user-attachments/assets/70b989ff-f49b-4e41-9558-cb56ab6c81be" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 4: Force User to Change Password at Next Login
In the Account tab of the user's properties, check the box for User must change password at next logon.<br>
<br>
- Enforce password change upon next login
- Encourages strong, personalized password creation
- Set policy in Account tab of AD user properties<br>
<br>
<img src="https://github.com/user-attachments/assets/7607c046-66e9-487d-8fd8-7052dbf37bcf" width="1000"><br>
<br>
<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 5: User Creates New Secure Password
User logs in with the temporary password and is prompted to set a new one. Ensure password policy is enforced for strength.<br>
<br>
- User sets their own new password
- Helps prevent shared/default password reuse
- Occurs automatically on login after previous step<br>
<br>
<img src="https://github.com/user-attachments/assets/601986f1-132b-4803-9746-0629490e2277" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 6: Login Restored and Issue Resolved
User (Bucky Barnes) is now successfully able to log in. Account is no longer locked and regular access is restored.<br>
<br>
- Account access successfully restored
- Steps followed to reset and unlock user properly
- Verified login success after password reset<br>
<br>
<img src="https://github.com/user-attachments/assets/e8aecc5b-17f6-4b82-81b2-dbc91ec3ebcd" width="1000"><br>

