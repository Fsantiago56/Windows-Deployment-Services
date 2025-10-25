# 🧩 Windows Deployment Services (WDS) Lab

## 🎯 Goal
Set up Windows Deployment Services (WDS) on Windows Server 2022 (DC01) to automate OS installation for network clients (PXE boot).

---

## 🖥️ Environments Used
- Host OS: Windows 11

- Server VM: Windows Server 2022 (Domain Controller: DC01.company.local)

- Client VM: Windows 10 / 11 

- Virtualization: VirtualBox
  
- Network Mode: Internal Network (so DC01 can provide DHCP/DNS/WDS services
  
---  

## 🧰 Prerequisites

Before beginning:

- ✅ DC01 is configured with AD DS, DHCP, and DNS

- ✅ Client01 can ping DC01 

- ✅ A Windows 10 or 11 ISO is available
  
- ✅ Internet or mounted ISO for WDS role installation

---  

## 🛠️ Lab Walkthrough

### 🔹Step 1 – Install the WDS Role
Goal: Add the Windows Deployment Services role.

On DC01 (Server Manager):

1. Open Server Manager → Manage → Add Roles and Features
2. Select Windows Deployment Services → include Deployment Server and Transport Server
3. Click Install
4. Once installed, open Windows Deployment Services console

<p align="center">
  ✅ <strong> Result: WDS role installation progress.</strong>✅  
<p align="center">
<img src="https://i.imgur.com/VyXEyou.png" width="60%">
</p>

