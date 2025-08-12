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
  
### Step 1: Access Group Policy Management

Open Server Manager, navigate to Tools, and select Group Policy Management. This console allows centralized management of security and configuration settings across multiple computers in the domain.<br>
<br>
- Launch the Group Policy Management Console.
- Required to create and manage Group Policy Objects (GPOs).
- Server Manager → Tools → Group Policy Management.<br>
<br>
<img src="https://github.com/user-attachments/assets/c3d81fac-128d-49b9-9414-87458be1755c" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 2: Create New Group Policy Object

In the Group Policy Objects folder, right-click and select New. Name the GPO Workstation Security Baseline.<br>
<br>
- Create a new GPO container.
- Establish a baseline security configuration for domain workstations.
- Right-click → New → Enter “Workstation Security Baseline”.<br>
<br>
<img src="https://github.com/user-attachments/assets/42189e5e-dc8f-4b65-94a6-baffffef46ff" width="1000"><br>


<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 3: Configure Delegation Permissions
Click the Workstation Security Baseline policy, go to the Delegation tab, and add the user Bucky Barnes with Read permissions.<br>
<br>
- Assign read-only rights to a user.
- Allows a user or admin to review GPO settings without making changes.
- Select GPO → Delegation → Add → Assign Read permissions.<br>
<br>
<img src="https://github.com/user-attachments/assets/960e1862-be8b-46be-b536-03930ff032d1" width="1000"><br>
<br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 4: Edit the New Group Policy Object
Right-click Workstation Security Baseline and select Edit. Navigate through User Configuration and Computer Configuration folders to locate settings for:<br>
- Control Panel and Settings App restrictions
- Registry Editor access
- Block storage/removable media
- Restrict application execution
- Desktop environment restrictions
- Remove change password option
<br>
- Begin applying restrictions.
- Prevent unauthorized system changes, protect data, and enforce security standards.
- Right-click GPO → Edit → Select relevant folders and settings.<br>
<br>
<img src="https://github.com/user-attachments/assets/655a92d5-cedf-4b76-b8ed-e0e8aff61586" width="1000"><br>
<br>
<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 5: Restrict Control Panel & Settings App
Policy Path: User Configuration → Administrative Templates → Control Panel → Prohibit access to Control Panel and PC settings<br>
<br>
- Removes ability to open Control Panel and Windows Settings.
- Prevents changes to system configurations by standard users.
- Enable “Prohibit access to Control Panel and PC settings” → Apply → OK.<br>
<br>
<img src="https://github.com/user-attachments/assets/7b407b9d-ac49-4f93-960f-b4c4ffca566d" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 6: Login Restored and Issue Resolved
User (Bucky Barnes) is now successfully able to log in. Account is no longer locked and regular access is restored.<br>
<br>
- Account access successfully restored
- Steps followed to reset and unlock user properly
- Verified login success after password reset<br>
<br>
<img src="https://github.com/user-attachments/assets/e8aecc5b-17f6-4b82-81b2-dbc91ec3ebcd" width="1000"><br>

