# Active-Directory-Management-Lab
Practical Active Directory &amp; Group Policy Management Lab using Windows Server 2022 and Windows 11.
# 🛠️ Active Directory User & Computer Management Lab

![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-0078D6?style=for-the-badge&logo=windows-server&logoColor=white)
![Windows 11](https://img.shields.io/badge/Windows%2011-Pro-0078D4?style=for-the-badge&logo=windows11&logoColor=white)
![Active Directory](https://img.shields.io/badge/Active%20Directory-AD%20DS-005A9E?style=for-the-badge&logo=microsoft&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed%20%E2%9C%85-success?style=for-the-badge)

## 📌 Project Overview
This project demonstrates hands-on **Active Directory Domain Services (AD DS)** administration and **Group Policy Management** within an enterprise Windows Server 2022 environment. 

The lab focuses on real-world IT Support and System Administration tasks, including managing domain users, client computer objects, security groups, Organizational Units (OUs), enforcing domain security policies via GPOs, and performing CLI-based troubleshooting from a domain-joined Windows 11 workstation.

---

## 🧰 Environment Architecture

| Component | Hostname | Operating System / Role | IP / Domain Details |
| :--- | :--- | :--- | :--- |
| **Domain Controller** | `DC01` | Windows Server 2022 | Domain Controller (`mohahamedlab.local`) |
| **Client Workstation**| `WIN11-LAB` | Windows 11 Pro (v10.0.26200)| Domain-Joined Client |
| **Domain User** | `MOHAMED.IT` | Active Directory User Account | Assigned to `IT` Organizational Unit |
| **Security Group** | `IT SUPPORT` | Domain Local / Security Group | Role-Based Access Control |
---

## 🚀 Key Tasks & Implementation

### 1. Active Directory User & OU Structure
- Provisioned and configured the domain user account `MOHAMED.IT` within **Active Directory Users and Computers (ADUC)**.
- Established a structured Organizational Unit (`IT`) to isolate administrative accounts and apply target policies.
- Configured object properties, ensuring correct group membership assignment.

### 2. Computer Account Management
- Joined `WIN11-LAB` (Windows 11 Pro workstation) to the `mohahamedlab.local` domain.
- Verified DNS resolution, computer object attributes, and active domain membership under default containers.

### 3. Role-Based Access Control (Security Groups)
- Created the `IT SUPPORT` Security Group for Access Control Management.
- Populated membership with the `MOHAMED.IT` account to simulate Role-Based Access Control (RBAC) practices.

### 4. Group Policy Object (GPO) Configuration
Created a custom GPO named **`IT SECURITY POLICY`** linked directly to the `IT` Organizational Unit to enforce security baselines:

#### 🔐 Password Policy Settings
| Policy Setting | Target Configuration |
| :--- | :--- |
| **Minimum Password Length** | `10 Characters` |

#### 🔒 Account Lockout Policy Settings
| Policy Setting | Target Configuration |
| :--- | :--- |
| **Account Lockout Threshold** | `5 Invalid Logon Attempts` |
| **Account Lockout Duration** | `15 Minutes` |
| **Reset Lockout Counter After** | `15 Minutes` |
| **Administrator Account Lockout**| `Enabled` |
---

## 🔍 Verification & CLI Troubleshooting

To ensure policies were successfully applied and processed by the client workstation (`WIN11-LAB`), the following administrative commands were executed:

### Policy Refresh
Forcefully updated Group Policy settings on the client machine:
```cmd
gpupdate /force

Policy Verification
Verified applied Computer and User policy processing via CLI:
gpresult /r /scope computer
Applied GPOs Confirmed in Output:
 ⁠IT SECURITY POLICY⁠ (Linked to IT OU)
 ⁠Default Domain Policy⁠
 ⁠COMPANY SECURITY POLICY⁠
🛠️ Troubleshooting Workflow Executed
1. Network Connectivity: Validated IP reachability between ⁠WIN11-LAB⁠ and ⁠DC01⁠.
2. DNS Validation: Verified client DNS points correctly to the Domain Controller.
3. Domain Trust: Confirmed workstation secure channel trust relationship.
4. GPO Scope Verification: Verified GPO link status and OU inheritance settings in Group Policy Management Console (GPMC).
💡 Key Skills Demonstrated
 Directory Services: Active Directory Users and Computers (ADUC), Organizational Units (OUs), Security Group Management.
 System Administration: Windows Server 2022 configuration, Windows 11 Domain Join, Role-Based Access Control (RBAC).
 Security & Compliance: Group Policy Management (GPMC), Security Baselines, Password & Account Lockout Policies.
 Troubleshooting & Tools: ⁠gpupdate⁠, ⁠gpresult⁠, DNS diagnostics, Domain trust validation.

### 📸 Screenshots & Evidence
All documentation screenshots are organized in the ⁠/screenshots⁠ directory, including:
 Active Directory User & Computer object configurations.
 GPO settings in Group Policy Management Console.
 Command Prompt execution outputs (⁠gpupdate⁠ and ⁠gpresult⁠).
