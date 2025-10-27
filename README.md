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

---

### 🔹Step 2 – Configure the WDS Server
Goal: Initialize WDS and set up deployment folder.

1. In WDS console → Right-click Server Name → Configure Server
2. Select:
   - Integration with Active Directory
   - RemoteInstall folder: C:\RemoteInstall
   - Respond to all PXE clients: ✅ (for testing)
     
3. Wait for configuration to finish and start the WDS service.

<p align="center">
  ✅ <strong> Result: WDS configuration wizard.</strong>✅  
<p align="center">
<img src="https://i.imgur.com/FeW9UGJ.png" width="60%">
</p>

---

### 🔹Step 3 – Add Boot and Install Images
Goal: Import images from your Windows ISO.

1. Mount the Windows 10/11 ISO on DC01
2. In WDS console:
   - Right-click Boot Images → Add Boot Image
   - Path: X:\sources\boot.wim
   - Right-click Install Images → Add Install Image
   - Create a new image group (e.g., “Windows 11 Pro”)
   - Path: X:\sources\install.wim

  
<p align="center">
  ✅ <strong> Result: Boot and Install images added.</strong>✅  
<p align="center">
<img src="https://i.imgur.com/6QGiBHN.png" width="60%">
<p align="center">
<img src="https://i.imgur.com/Z0RXU8c.png" width="60%">
</p>

---

### 🔹Step 4 – Configure PXE Boot Response
Goal: Allow clients to boot and install via PXE.

1. In WDS console → Server Properties → PXE Response
    - ✔ Respond to all client computers
    - ✔ Allow unknown clients
2. Restart WDS service:
   ```Powershell
   Restart-Service wdsserver
   ```
<p align="center">
  ✅ <strong> Result: WDS ready to respond to PXE clients.</strong>✅  
<p align="center">
<img src="https://i.imgur.com/HFX8e7b.png" width="60%">
</p>


---   
