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

### Step 6: Block Registry Editor Access

Policy Path: User Configuration → Administrative Templates → System → Prevent access to registry editing tools<br>
<br>
- Prevents modifications to Windows Registry.
- Stops unauthorized or harmful registry changes.
- Enable “Prevent access to registry editing tools” → Apply → OK.<br>
<br>
<img src="https://github.com/user-attachments/assets/6fdb06cf-190a-4789-99f1-eb4fff90f1d6" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 7: Block Removable Storage Access

Policy Path: Computer Configuration → Administrative Templates → System → Removable Storage Access<br>
<br>
- Deny read/write to USB and external drives.
- Prevents data theft and malware from removable devices.
- Enable “All Removable Storage classes: Deny all access” → Apply → OK.<br>
<br>
<img src="https://github.com/user-attachments/assets/108d46db-de04-44a4-a6f0-e85cb2af725e" width="1000"><br>
<br>
<img src="https://github.com/user-attachments/assets/8932ea83-2025-476e-a44c-b7e7b0fd5a90" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 8: Disable Task Manager

Policy Path: User Configuration → Administrative Templates → System → Ctrl+Alt+Del Options → Remove Task Manager<br>
<br>
- Prevents users from ending processes or viewing running tasks.
- Stops termination of security-related processes or critical applications.
- Enable “Remove Task Manager” → Apply → OK.<br>
<br>
<img src="https://github.com/user-attachments/assets/1e008d05-4103-4640-94ac-52221275a603" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 9: Remove Change Password Option

Policy Path: User Configuration → Administrative Templates → System → Ctrl+Alt+Del Options → Remove Change Password<br>
<br>
- Prevents users from changing their Windows password.
- Enforces password change policies set by administrators only.
- Enable “Remove Change Password” → Apply → OK.<br>
<br>
<img src="https://github.com/user-attachments/assets/214ba2dd-c232-4ee6-80ed-4a27183eca0a" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 10: Enforce the Group Policy

Right-click the Workstation Security Baseline policy and select Enforced.<br>
<br>
- Ensures the policy takes precedence and applies fully.
- Prevents other GPOs from overriding this baseline policy.
- Right-click GPO → Enforced.<br>
<br>
<img src="https://github.com/user-attachments/assets/98ef6a1d-5080-40ef-9ac4-d949d1c96fc7" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 11: Force Group Policy Update on Client Machine

Sign in as Bucky Barnes on a Windows 11 workstation. Open Command Prompt and run:<br>
gpupdate /force<br>
<br>
- Forces the workstation to apply the latest GPO changes.
- Ensures the new policy is active without waiting for automatic refresh.
- Command Prompt → gpupdate /force.<br>
<br>
<img src="https://github.com/user-attachments/assets/f9a355f7-78c2-4f49-8a63-fdd28e33fb59" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 12: Verify Applied Policies
Review the Applied Group Policy Objects list and confirm “Workstation Security Baseline” is active. Run the following command:<br>
gpresult /r<br>
<br>
- Generates Resultant Set of Policy (RSOP) data.
- Confirms the policy is applied to the user/computer.
- Command Prompt → gpresult /r.<br>
<br>
<img src="https://github.com/user-attachments/assets/a14b16f1-5d02-4538-a7ef-71f923f28d79" width="1000"><br>

<hr style="border: 0.15px solid rgba(0, 0, 0, 0.05);">

### Step 13: Test Group Policy Restrictions
Attempt to open Task Manager as Bucky Barnes. A warning or access denial message should appear, confirming the policy works.<br>
<br>
- Validate the applied restriction.
- Ensures the security policy is functioning as intended.
- Ctrl+Shift+Esc or Ctrl+Alt+Del → Select Task Manager → Observe block message.<br>
<br>
<img src="https://github.com/user-attachments/assets/b7f28d34-5d28-4de4-9a6f-759337d21427" width="1000"><br>


